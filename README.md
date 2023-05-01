Download Link: https://assignmentchef.com/product/solved-cs2106-tutorial-3-process-scheduling
<br>
<ol>

 <li>(Walking through Scheduling Algorithms) Consider the following execution scenario:</li>

</ol>




<table width="530">

 <tbody>

  <tr>

   <td width="530">Program A, Arrives at time 0</td>

  </tr>

  <tr>

   <td width="530">Behavior (C<strong>X</strong> = Compute for <strong>X</strong> Time Units, IO<strong>X</strong> = I/O for <strong>X</strong> Time Units):  C<strong>3</strong>, IO<strong>1</strong>, C<strong>3</strong>, IO<strong>1</strong></td>

  </tr>

 </tbody>

</table>




<table width="530">

 <tbody>

  <tr>

   <td width="530">Program B, Arrives at time 0</td>

  </tr>

  <tr>

   <td width="530">Behavior:C<strong>1</strong>, IO<strong>2</strong>, C<strong>1</strong>, IO<strong>2</strong>, C<strong>2</strong>, IO<strong>1</strong></td>

  </tr>

 </tbody>

</table>




<table width="530">

 <tbody>

  <tr>

   <td width="530">Program C, Arrives at time 3</td>

  </tr>

  <tr>

   <td width="530">Behavior:  C<strong>2</strong></td>

  </tr>

 </tbody>

</table>







<ol>

 <li>Show the scheduling time chart with First-Come-First-Serve algorithm. For simplicity, we assume all tasks block on the same I/O resource.</li>

</ol>







<ol>

 <li>What are the turnaround time and the waiting time for program A, B and C? In this case, waiting time includes all time units where the program is ready for execution but could not get the CPU.</li>

</ol>




<ol>

 <li>Use <strong>Round Robin </strong>algorithm to schedule the same set of tasks. Assume time quantum of <strong>2 time units</strong>. Draw out the scheduling time chart. State any assumptions you may have.</li>

</ol>




<ol>

 <li>What is the response time for tasks A, B and C? In this case, we define response time as the time difference between the arrival time and the first time when the task receives CPU time.</li>

</ol>




<ol start="2">

 <li>(MLFQ) As discussed in the lecture, the simple MLFQ has a few shortcomings. Describe the scheduling behavior for the following two cases.</li>

</ol>




<ol>

 <li>(Change of heart) A process with a lengthy CPU-intensive phase followed by I/Ointensive phase.</li>

</ol>




<ol>

 <li>(Gaming the system) A process repeatedly gives up CPU just before the time quantum lapses.</li>

</ol>




The following are two simple tweaks. For each of the rules, identify which case (a or b above) it is designed to solve, then briefly describe the new scheduling behavior.




<ol>

 <li>(Rule – Accounting matters) The CPU usage of a process is now accumulated across time quanta. Once the CPU usage exceeds a single time quantum, the priority of the task will be decremented.</li>

</ol>




<ol>

 <li>(Rule – Timely boost) All processes in the system will be moved to the highest priority level periodically.</li>

</ol>




<ol start="3">

 <li>(Adapted from Midterm 1516/S1 – Understanding of Scheduler)</li>

</ol>




<ol>

 <li>Give the <strong>pseudocode</strong> for the <strong>RR</strong> <strong>scheduler function. </strong>For simplicity, you can assume that all tasks are CPU intensive that runs forever (i.e. there is no need to consider the cases where the task blocks / give up CPU). Note that this function is invoked by timer interrupt that triggers once every time unit.</li>

</ol>




<strong>Please use the following variables and function in your pseudocode.  </strong>

<table width="529">

 <tbody>

  <tr>

   <td width="529"><strong>Variable / Data type declarations </strong></td>

  </tr>

  <tr>

   <td width="529">Process <strong>PCB</strong> contains: <strong>{ PID, TQLeft, … }</strong>  // TQ = Time Quantum, other PCB info irrelevant.<strong>RunningTask</strong> is the PCB of the current task running on the CPU.<strong>TempTask</strong> is an empty PCB, provided to facilitate context switching.<strong>ReadyQ</strong> is a FIFO queue of PCBs which supports standard operations like <strong>isEmpty()</strong>, <strong>enqueue()</strong> and <strong>dequeue()</strong>.<strong>TimeQuatum</strong> is the predefined time quantum given to a running task.</td>

  </tr>

  <tr>

   <td width="529"><strong>“Pseudo” Function declarations </strong></td>

  </tr>

  <tr>

   <td width="529"><strong>SwitchContext( <em>PCBout</em>, <em>PCBin</em> ); </strong></td>

  </tr>

 </tbody>

</table>

Save the context of the running task in <strong><em>PCBout</em></strong>, then setup the new running environment with the PCB of <strong><em>PCBin</em></strong>, i.e. vacating <strong><em>PCBout</em></strong> and preparing for <strong><em>PCBin</em></strong> to run on the CPU.




<ol>

 <li>Suppose when a process gets blocked waiting for I/O and the process scheduler runs only at the next timer interrupt and chooses another process to run. Discuss any shortcomings that might arise? How would you solve those?</li>

</ol>




<ol start="4">

 <li>(Adapted from AY1920S1 Midterm – Evaluating scheduling algorithms)</li>

</ol>




Briefly answer each of the following questions regarding process scheduling, stating your assumptions, if any.




<ol>

 <li>Under what conditions does FCFS (FIFO) scheduling result in the shortest possible average response time?</li>

</ol>




<ol>

 <li>Under what conditions does round-robin (RR) scheduling behave identically to FIFO?</li>

</ol>




<ol>

 <li>Under what conditions does RR scheduling perform poorly compared to FIFO?</li>

</ol>




<ol>

 <li>Does reducing the time quantum for RR scheduling help or hurt its performance relative to FIFO, and why?</li>

</ol>




<ol>

 <li>Do you think a CPU-bound (CPU-intensive) process should be given a higher priority for I/O than an I/O-bound process? Justify your answers.</li>

</ol>







<h1>Questions for your own exploration</h1>

<ol start="5">

 <li>(Putting it together) Take a look at the given mysterious program <strong>c</strong>. This program takes in one integer command line argument <strong>D</strong>, which is used as a <strong>delay </strong>to control the amount of computation work done in the program. For the part (a) and (b), use ideas you have learned from <strong>Lecture 3: Process Scheduling</strong> to explain the program behavior.</li>

</ol>




Use the command taskset –cpu-list 0 ./Behaviors D

This restricts the process to run on only one core.

Warning: you may not have the taskset command on your Linux system. If so, install the util-linux package using your package manager (apt, yum, etc).




Note: If you are using Windows Subsystem for Linux (WSL), make sure that you are using WSL2 kernel instead of WSL1. You can check by running wsl -l -v and upgrade using wsl –set-version &lt;distro-name&gt; 2




<ol>

 <li><strong>D </strong>= 1.</li>

 <li><strong>D</strong> = 100,000,000 (note: don’t type in the “,” &#x263a;)</li>

</ol>




<ol>

 <li>Now, find the <strong>smallest D </strong>that gives you the following interleaving output pattern:</li>

</ol>




<table width="510">

 <tbody>

  <tr>

   <td width="510"><strong>Interleaving Output Pattern</strong></td>

  </tr>

  <tr>

   <td width="510"><strong>[6183]: Step 0</strong><strong>[6184]: Step 0</strong>[6183]: Step 1[6184]: Step 1<strong>[6183]: Step 2</strong><strong>[6184]: Step 2</strong>[6183]: Step 3[6184]: Step 3<strong>[6183]: Step 4</strong><strong>[6184]: Step 4</strong>  [6184] Child Done![6183] Parent Done!</td>

  </tr>

 </tbody>

</table>




What do you think “<strong>D</strong>” represents?




<em>Note: “<strong>D</strong>” is machine dependent, you may get very different value from your friends’.</em>










<ol start="6">

 <li>(Predicting CPU time) In the lecture, the <strong><em>exponential average </em></strong>technique is briefly discussed as a way to estimate the CPU time usage for a process. Let us try to see this technique in action. Use <strong>Predicted<sub>0</sub> = 10 TUs</strong> and <strong>α = 0.5</strong>. Predicted<strong><sub>0</sub></strong> is the estimate used when a process is first admitted. All subsequent predictions use the formula:</li>

</ol>




<strong>Predict</strong><strong>N+1 = αActual</strong><strong>N + (1- α)Predict</strong><strong>N </strong>

<strong> </strong>

Calculate the error percentage ( <strong>Abs(Actual – Predict)  / Actual * 100%</strong>) to gauge the effectiveness of this simple technique. CPU time usage of two processes are given below, fill in the table as described and explain the differences in error percentage observed.







<table width="547">

 <tbody>

  <tr>

   <td width="100"> </td>

   <td width="154"><strong>P</strong></td>

   <td width="153"><strong>rocess A </strong></td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100"><strong>Sequence </strong></td>

   <td width="154"><strong>Predicted </strong></td>

   <td width="153"><strong>Actual </strong></td>

   <td width="140"><strong>Percentage Error </strong></td>

  </tr>

  <tr>

   <td width="100">1</td>

   <td width="154"><strong>10 </strong></td>

   <td width="153">9</td>

   <td width="140">11.1%</td>

  </tr>

  <tr>

   <td width="100">2</td>

   <td width="154"> </td>

   <td width="153">8</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">3</td>

   <td width="154"> </td>

   <td width="153">8</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">4</td>

   <td width="154"> </td>

   <td width="153">7</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">5</td>

   <td width="154"> </td>

   <td width="153">6</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100"> </td>

   <td width="154"> </td>

   <td width="153"><strong>Average Error: </strong></td>

   <td width="140"> </td>

  </tr>

 </tbody>

</table>




<table width="547">

 <tbody>

  <tr>

   <td width="100"> </td>

   <td width="154"><strong>P</strong></td>

   <td width="153"><strong>rocess B </strong></td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100"><strong>Sequence </strong></td>

   <td width="154"><strong>Predicted </strong></td>

   <td width="153"><strong>Actual </strong></td>

   <td width="140"><strong>Percentage Error </strong></td>

  </tr>

  <tr>

   <td width="100">1</td>

   <td width="154"><strong>10 </strong></td>

   <td width="153">8</td>

   <td width="140">25%</td>

  </tr>

  <tr>

   <td width="100">2</td>

   <td width="154"> </td>

   <td width="153">14</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">3</td>

   <td width="154"> </td>

   <td width="153">3</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">4</td>

   <td width="154"> </td>

   <td width="153">18</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100">5</td>

   <td width="154"> </td>

   <td width="153">2</td>

   <td width="140"> </td>

  </tr>

  <tr>

   <td width="100"> </td>

   <td width="154"> </td>

   <td width="153"><strong>Average Error: </strong></td>

   <td width="140"> </td>

  </tr>

 </tbody>

</table>










<ol start="7">

 <li>(Scheduler Case Study – Linux) Let us look at the Linux scheduler, which is at the heart of one of the most widely used server OS (100% of the 2019 top 500 supercomputers in the world use Linux!) Instead of a full coverage, we will pick and choose several aspects to discuss, depending on the available time in your tutorial.</li>

</ol>




Linux scheduler (in kernel 2.6.x) can be understood as a MLFQ variant. There are 140 priority levels (0 = highest, 139 = lowest) split into two ranges (real time task has priority 0 to 99 and time sharing task has priority 100 to 139). For our purpose, we will consider only time sharing tasks (i.e. normal user processes).




<ol start="2">

 <li>In older Linux kernel, the scheduler maintains a single linked list to keep track of all runnable tasks. When picking a task, this list is iterated through to find the task with the highest priority. In kernel 2.6.x, an array of 140 linked lists (i.e. each priority level has a linked list) is maintained instead. Assuming everything else remains unchanged, what is the benefit of this change?</li>

</ol>




<ol>

 <li>In the scheduler, there are two sets of tasks:</li>

</ol>

<ul>

 <li>“<strong>Active tasks</strong>”: Tasks ready to run.</li>

 <li>“<strong>Expired tasks</strong>”: Tasks which have exhausted their time quantum but runnable (i.e. they are not blocked).</li>

</ul>




Based on the priority level, each task on the “Active” set will eventually get a time quantum to run. If the task gives up early or exhausted its time quantum, it will be placed on the “Expired” set. When the “Active” set is empty, the scheduler will then swap the two sets, i.e. the “Expired” set is now the new “Active” set. What do you think is the benefit of this design?




<ol>

 <li>The time quantum (known as <strong><em>time slice</em></strong> in Linux terminology) is not a constant value, instead it is proportional to the priority level (i.e. priority level 100 has the shortest time slices while 139 has the longest). What do you think is the rationale?</li>

</ol>




<ol>

 <li>The scheduler applies penalty (up to +5) or bonus (up to -5) to the task’s priority level depending on the execution behavior. So, a task at priority level 110 can be placed at level 105 (received bonus) or level 115 (penalized) between scheduling. This adjustment is based on a value <em>sleep_avg</em> kept with the task. This value:</li>

</ol>

<ul>

 <li>Increased by the amount of time the process is sleeping (i.e. blocked).</li>

 <li>Decreased by the amount of time the process actively runs.</li>

</ul>

A high sleep value corresponds to a large bonus while a low sleep value would cause a large penalty. What is the rationale of this mechanism?

<strong> </strong>