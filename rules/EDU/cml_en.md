[日本語](./cml_ja.md) | [English](./cml_en.md)

# Carry My Luggage（CML）
Reference video: [https://youtu.be/dzyJ1dHTulc](https://youtu.be/dzyJ1dHTulc)

> Note The reference video is not perfect. The task may differ depending on the rules of each year RoboCup, so please use it as a reference only. If you have any concerns or points you would like to discuss, please write them in the [Issues](https://github.com/RoboCupAtHomeJP/Rule2023/issues) section of GitHub.

## Focus

This task focuses on finger-pointing recognition, manipulation, mapping and navigation in known and unknown environments, human-following, voice dialogue, task planning, etc.

## Settings
- **Location**: An arena environment that mimics a home environment will be used. The competition takes place inside and outside the arena. The `inside` of the arena may be mapped in advance (`known environment`).

- **Starting location**: The robot will start in the center of the `Room 2: Dining Room` facing towards the middle point between the chairs position.

- **Luggage (paper bags)**: Two paper bags will be placed near the operator (within 2\[m\] of the robot and visible to it).
    - **Size**: 260 x 10 x 310\[mm\] [Amazon Link](https://www.amazon.co.jp/dp/B0173OZPSW/?th=1)．
    - **Placement**: The team will place the luggage (paper bags) on chairs. The bags will be placed on chairs in the same configuration as the [Tidy Up for OPL](https://github.com/RoboCupAtHomeJP/Rule2023/blob/main/rules/OPL/tu_en.md#object-category-and-placement-goal) task, so they don't overlap with the robot's path.
- **Operator**: The operator will point to the paper bag to be used during the competition while standing in front of the robot. Please select an operator from your team.

## Scenario
### Starting Phase

1. **Competition time**: The competition will last for **7 minutes**.
2. **Setup**: The referee instructs the team to move the robot to the starting position.
3. **Start**: The referee gives the start signal and starts the timer. At the same time, the team completes the final simple setup (pressing the starting button, etc.) and leaves the area. Complex setup procedures such as pressing more than two buttons are not allowed.
4. **Pointing**: The operator points to the paper bag that was specified in advance at the same time as the start signal.
5. **Grasping**: The robot recognizes the bag pointed to by the operator and grasps it.

### Follow-Me Phase

1. **Delivery**: When the robot is able to grasp the paper bag and be in a state where it can follow the human, it informs the operator of its intention.
2. **Walking**: After that, the operator starts walking from a known environment towards an unknown environment. At this time, the goal outside the arena is fixed.
3. **Follow-Me**: The robot starts to follow the walking operator and moves with him/her. If the operator reaches the goal, he/she will inform to the robot of his/her intention.

> Warning When the operator is walking, he/she cannot look back to the robot or stop during the walk.

### Navigation Phase

1. **Handover**：After the operator and the robot reach the goal, the operator receives the bag from the robot and thanks the robot.
2. **Navigation**: The robot autonomously moves from the `unknown environment` to the `Starting Point` in the `known environment`. At this time, the robot performs autonomous driving while avoiding various obstacles. However, each team can decide whether to challenge these obstacles (points are added for each obstacle avoided). There are four types of obstacles:
    - A crowd of people (3-4 people) that obstructs in a static state
    - Small objects on the ground (such as building blocks)
    - Hard-to-see 3D objects (such as chairs or glasses)
    - Opening and closing barriers (such as guide poles)
3. **Goal**: When the robot returns to the `Starting Point`, the task is complete.

### Local Rules

1. the duration of the competition is 7 minutes.
1. 4 referees,, one from the OC and  one from each team that has completed the competition (3 referees in total)
    - OC: 1
    - TC: 3
1. Bonus Tasks
    - No points will be awarded for stepping on the feet of the retractable barriers (guide poles).
    - The crowd will consist of two members from each team
    - Regardless of the size of each team's robot, all small objects must be equally spaced.
1. The "starting point" is within a radius of 50 cm from the mark on the starting position.
(If you are within this radius, even a little bit, you are valid)
1. "Re-entry to the arena" is valid as long as the entire robot is inside the arena.
1. the bag may not be placed vertically
1. Follow-me skipping is allowed

## Deus ex machina

The following deus ex machina is employed in this task. Deus ex machina reduces the score of the corresponding action by **half**, but allows the operator to skip the partial task and continue with the overall task in a simpler way.

<table>
  <tr>
    <th> <b>Action<b> </th>
    <th> <b>Bypassing<b> </th>
  </tr>
  <tr>
    <td> Selection of paper bag </td>
    <td>
      <ul>
        <li> Limit selection to one of the two paper bags placed </li>
        <li> Only one paper bag is placed </li>
      </ul> 
    </td>
  </tr>
   <tr>
    <td> Gripping paper bag </td>
    <td>
      <ul>
        <li> The robot makes the operator to hold the selected bag </li>
        <li> At this time, the robot informs the operator of the position of the paper bag </li>
      </ul> 
    </td>
  </tr>
  <tr>
    <td> Person-following movement using markers </td>
    <td>
      <ul>
        <li> Perform person-following movement with a marker attached to or held by the operator </li>
      </ul> 
    </td>
  </tr>
  <tr>
    <td> Skipping Person-following movement  </td>
    <td>
      <ul>
        <li> In the follow-me phase, the vehicle is transported to the car without following the person </li>
      </ul> 
    </td>
  </tr>
  <!--
   <tr>
    <td> 未知環境のマッピング </td>
    <td>
      <ul>
        <li> 事前にマッピングしてはいけない屋外の範囲にマッピングを行う
 </li>
        <li> この場合，マッピングが影響する自律移動の得点は半分とする（スコアシート中の「☆」の箇所）
 </li>
      </ul> 
    </td>
  </tr>
  -->
</table>

## Score Sheet

<table>
  <tr>
    <th> <b>Action</b> </th>
    <th> <b>Score</b> </th>
  </tr>
  <tr>
    <td colspan="2" align="center"> <b>Main Task</b> </td>
  </tr>
  <tr>
    <td> Transport the paper bag to the goal outside the arena <br> 
      <ul>
        <li> Detection of the operator-selected paper bag </li>
        <li> Grasping the selected bag </li>
        <li> Following the operator out of the arena </li>
        <li> Arriving at the goal outside the arena while following the operator </li>
      </ul> 
    </td>
<!--     <td> 250 <br> 
      <ul  style="list-style: none;">
        <li> 50 </li>
        <li> 100 </li>
        <li> 50 </li>
        <li> 50 </li>
      </ul> 
    </td> -->
    <td align="center"> <!-- 250 <br> --> 100 <br> 200 <br> 100 <br> 100 </td>
  </tr>
  <tr>
    <td colspan="2" align="center"> <b>Bonus Tasks</b> </td>
  </tr>
  <tr>
    <td> Re-enter the arena
      <ul>
        <li> Autonomously enter the arena </li>
        <li> Autonomously return to the `starting point` </li>
    </td>
    <td align="center"> <!-- 50 <br> --> 50 <br> 50 </td>
  </tr>
  <tr>
    <td> Avoid static crowds of people (2 people) <br> </td>
    <td align="center"> 100 </td>
  </tr>
  <tr>
    <td> Avoid small objects on the ground (such as blocks) <br> </td>
    <td align="center"> 100 </td>
  </tr>
  <tr>
    <td> Avoid visually confusing 3D objects (such as chairs or glasses) <br> </td>
    <td align="center"> 100 </td>
  </tr>
  <tr>
    <td> Avoid opening and closing barriers (such as guide posts) <br> </td>
    <td align="center"> 100 </td>
  </tr>
  <tr>
    <td colspan="2" align="center"> <b>Penalty</b> </td>
  </tr>
  <tr>
    <td> Non-participation (without previous instance) </td>
    <td align="center"> -500 </td>
  </tr>
  <tr>
    <td> <b>Total (including bonus tasks)</b> </td>
    <td align="center"> <b>1000</b> </td>
  </tr>
</table>

> **Note**
> Three triangular open-close barriers (such as guide poles) will be used. They will be available for use from the `Setup Day` (planned)．

## Instructions from the Executive Committee(EC)

- Preparation
  - Select 2 people from the competing team  to act as obstacles for robot on the outdoor path.
  - Choose the position of the paper bag and assign the bag to the operator.
  - Select obstacles that the robot will face when it is outside.
  - Choose the position of the goal (car).
  - Be careful with the robot when it exits the arena.
- Announcement (Setup day)
  - Select the robot's `starting point` and announce it.
  - Select which bag to be grasped and announce it.

## Role of the Referees (TC)

- Gather 30 minutes before the competition, receive instructions, and receive the score sheet.
- Act as the referee as described during the task.
- Score the competition.
- Verify scoring content with other TCs.
- Submit the score sheet.

> **Note**
> Members of each teams are selected to be TCs and score the tasks of other teams' competitions. For details, please refer to the [Scoring System](./gr_en.md#scoring-system).
