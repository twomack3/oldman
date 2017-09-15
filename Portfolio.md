### Created for a variety Unity projects using Visual Studio
### AttackAction.cs
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;

[CreateAssetMenu(menuName = "PluggableAI/Actions/Attack")]
public class AttackAction : Action
{
    /* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
    * Performs the Move to and attack actions for computer controlled avatars
    * T.Womack 8-2017
    * 
    * Make use fo new Class AvatarProperties for aiming - TTW 9/2017
    * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */    private PlayerMovement thisAIPlayer;
    private GameObject playersBall = null;
    private NavMeshAgent thisAIAgent;
    private ArenaMatchManager matchManager;

    public override void Act(PlayerStateController controller)
    {
        thisAIPlayer = controller.GetComponent<PlayerMovement>();
        playersBall = thisAIPlayer.myBall;
        thisAIAgent = controller.playerNavMeshAgent;
        Attack(controller);
    }

    private void Attack(PlayerStateController controller)
    {
        GameObject enemy1 = null;
        GameObject enemy2 = null;
        GameObject closeEnemy = null;
        matchManager = FindObjectOfType<ArenaMatchManager>();
        //If not in attack zone move to attack zone
        if (!thisAIPlayer.inAttackArea)
        {
            thisAIAgent.destination = thisAIPlayer.myStart;
            thisAIAgent.stoppingDistance = 2.0f;
        }
        else
        {
            //Find closest enemy
            if (thisAIPlayer.redTeam)
            {
                //if (GameObject.FindGameObjectWithTag("Player1").GetComponent<PlayerHealth>().Alive)
                if (matchManager.player1.GetComponent<PlayerHealth>().Alive)
                {
                    enemy1 = matchManager.player1;
                }
                if (matchManager.player3.activeSelf && matchManager.player3.GetComponent<PlayerHealth>().Alive)
                {
                    enemy2 = matchManager.player3;
                }
            }
            else
            {
                if (matchManager.player2.GetComponent<PlayerHealth>().Alive)
                {
                    enemy1 = matchManager.player2;
                }
                if (matchManager.player4.activeSelf && matchManager.player4.GetComponent<PlayerHealth>().Alive)
                {
                    enemy2 = matchManager.player4;
                }
            }
            if (controller.stateTimeElapsed < thisAIPlayer.powerTime) //only attack at full power
            {
                thisAIPlayer.UpdatePlayerUI();
                return; //no enemies found do nothing more
            }
            // check all cases of available enemies
            if (enemy1 == null && enemy2 == null)
            {
                thisAIPlayer.UpdatePlayerUI();
                return; //no enemies found do nothing more
            }

            if (enemy2 != null && enemy1 != null)
            {
                if (Vector3.Distance(enemy1.transform.position, thisAIAgent.transform.position) <=
                    Vector3.Distance(enemy2.transform.position, thisAIAgent.transform.position))
                {
                    closeEnemy = enemy1;
                }
                else
                {
                    closeEnemy = enemy2;
                }
            }
            else if (enemy2 == null)
            {
                closeEnemy = enemy1;
            }
            else
            {
                closeEnemy = enemy2;
            }

            //Face and aim
            Vector3 faceDirection = closeEnemy.transform.position - thisAIAgent.transform.position;
            Quaternion lookRotation = Quaternion.LookRotation(faceDirection);
            thisAIAgent.transform.rotation = Quaternion.Lerp(thisAIAgent.transform.rotation, lookRotation, Time.deltaTime * thisAIPlayer.rotateSpeed);
            float angletoTarget = Vector3.Angle(faceDirection, thisAIPlayer.transform.forward);
            //Throw ball
            if (angletoTarget < 1.0f) // aiming at target
            {
                //Debug.Log("AA-A " + angletoTarget + " "+ playersBall);
                //throw ball - sound from avatar
                Rigidbody ballRB = playersBall.GetComponent<Rigidbody>();
                float ballImpulse = playersBall.GetComponent<CommonBallClass>().initialImpulse;
                ballRB.isKinematic = false;
                //holding += holdTime; //force time ring off
                float effort = ballImpulse;
                ballRB.constraints = RigidbodyConstraints.None;
                //Debug.Log ("AA_A throw ball " + playersBall +" " +effort);
                ballRB.velocity = thisAIPlayer.transform.forward * effort;
                thisAIPlayer.ReleaseBall();
                controller.stateTimeElapsed = 0.0f;
            }
        }
        //Update hold UI for player and drop ball if stateTime > hold time
        thisAIPlayer.powerClock.value = 100.0f * controller.stateTimeElapsed / thisAIPlayer.powerTime;
        thisAIPlayer.holdClock.value = 100.0f * (thisAIPlayer.holdTime - controller.stateTimeElapsed) / thisAIPlayer.holdTime;
        if (controller.stateTimeElapsed > thisAIPlayer.holdTime)
        {
            //Debug.Log("PM DropBall: " + holding + " " + holdTime);
            //Drop ball - move ball to start point
            Rigidbody ballRB = playersBall.GetComponent<Rigidbody>();
            ballRB.isKinematic = false;
            CommonBallClass theBall = playersBall.GetComponent<CommonBallClass>();
            theBall.BallState = ArenaMatchManager.BallStates.Inactive;
            thisAIPlayer.ReleaseBall();
            controller.stateTimeElapsed = 0.0f;
            //thisAIPlayer.UpdatePlayerUI();
        }
    }
}
```
### CanThrowDecision.cs
```c#
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

[CreateAssetMenu(menuName = "PluggableAI/Decisions/CanThrow")]
public class CanThrowDecision : Decision
{
    public override bool Decide(PlayerStateController controller)
    {
        return controller.GetComponent<PlayerMovement>().canThrow;
    }
}
```
### Abstract class Decision.cs
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public abstract class Decision : ScriptableObject
{
    public abstract bool Decide(PlayerStateController controller);
}
```
### GetBAllAction.cs
```c#
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;

[CreateAssetMenu(menuName = "PluggableAI/Actions/GetBall")]
public class GetBallAction : Action
{
    /* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
    * Performs the Get ball action for computer controlled avatars
    * T.Womack 8-2017
    * 
    * Make use fo new Class AvatarProperties for 'grabbing' ball - TTW 9/2017
    * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */
    private PlayerStateController thisAIPlayer;
    private GameObject closestBall = null;
    private Vector3 position;
    //private ArenaMatchManager matchManager;

    public override void Act(PlayerStateController controller)
    {
        thisAIPlayer = controller;
        GetBall();
    }

    private void GetBall()
    {
        //Find Closest
        Vector3 nearBallPosition = new Vector3();
        //Find closest idle or inactive ball on the playing floor
        GameObject[] balls;
        balls = GameObject.FindGameObjectsWithTag("Ball");
        float distance = Mathf.Infinity;
        position = thisAIPlayer.transform.position;
        foreach (GameObject ball in balls)
        {
            if ((ball.GetComponent<CommonBallClass>().BallState == ArenaMatchManager.BallStates.Idle ||
                 ball.GetComponent<CommonBallClass>().BallState == ArenaMatchManager.BallStates.Inactive) &&
                 (ball.transform.position.y > thisAIPlayer.surface))
            {
                float curDistance = Vector3.Distance(ball.transform.position, position);
                if (curDistance < distance)
                {
                    distance = curDistance;
                    closestBall = ball;
                    nearBallPosition = ball.transform.position;
                    //Debug.Log("GB " + (ArenaMatchManager.BallStates)ball.GetComponent<CommonBallClass>().BallState + " " +
                    //          ball.transform.position.y + " " + thisAIPlayer.surface + " " + curDistance + " " + distance);
                }
            }
        }
        if (closestBall == null)
        {
            //Debug.Log("GBA_GB No ball found");
            return;
        }
        //Move to closest ball
        thisAIPlayer.playerNavMeshAgent.destination = nearBallPosition;
        thisAIPlayer.playerNavMeshAgent.stoppingDistance = 0.22f;
        //Exit if not close enough
        if ((Vector3.Distance(nearBallPosition, position)) > thisAIPlayer.GetComponent<PlayerMovement>().grabDistance)
        {
            thisAIPlayer.GetComponent<PlayerMovement>().hasBall = false;
            return;  //no ball in range to grab/catch
        }
        //Put ball in hand
        closestBall.transform.SetParent(thisAIPlayer.GetComponent<PlayerMovement>().myRightHand);
        closestBall.GetComponent<Rigidbody>().isKinematic = true;
        closestBall.transform.localPosition = Vector3.zero;
        //Set ball status to player's color at this time
        CommonBallClass theBall = closestBall.GetComponent<CommonBallClass>();
        if (thisAIPlayer.GetComponent<PlayerMovement>().redTeam)
            theBall.BallState = ArenaMatchManager.BallStates.Red;
        else
            theBall.BallState = ArenaMatchManager.BallStates.Blue;

        thisAIPlayer.stateTimeElapsed = 0.0f;
        thisAIPlayer.GetComponent<PlayerMovement>().hasBall = true;
        thisAIPlayer.GetComponent<PlayerMovement>().myBall = closestBall;
        //Debug.Log("GBA-GB "+ (ArenaMatchManager.BallStates)closestBall.GetComponent<CommonBallClass>().BallState +" "+ closestBall);
    }
}
```
### State.cs
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

[CreateAssetMenu (menuName = "PluggableAI/State")]
public class State : ScriptableObject
{
    public Action[] actions;
    public Transition[] transitions;

    public void UpdateState(PlayerStateController controller)
    {
        //Debug.Log("S-US " + controller);
        DoActions(controller);
        CheckTransitions(controller);
    }

    private void DoActions(PlayerStateController controller)
    {
        for (int i = 0; i < actions.Length; i++)
        {
            actions[i].Act(controller);
        }
    }

    private void CheckTransitions(PlayerStateController controller)
    {
        for (int i = 0; i < transitions.Length; i++)
        {
            bool decisionSucceeded = transitions[i].decision.Decide(controller);
            if (decisionSucceeded)
            {
                controller.TransitionToState(transitions[i].trueState);
            }
            else
            {
                controller.TransitionToState(transitions[i].falseState);
            }
        }
    }
}
,,,
