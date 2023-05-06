Download Link: https://assignmentchef.com/product/solved-ecse222-assignment-2-combinational-circuit-using-vhdl-concurrent-statements
<br>
In this assignment you will be required to write simple logic functions in VHDL employing the techniques you learned in class. This document contains material obtained directly from <a href="https://www.allaboutcircuits.com/technical-articles/concurrent-conditional-and-selected-signal-assignment-in-vhdl/">“all about circuits”</a><a href="https://www.allaboutcircuits.com/technical-articles/concurrent-conditional-and-selected-signal-assignment-in-vhdl/">.</a>

<h1>1        Concurrent Statements in VHDL</h1>

Combinational circuits can be described in VHDL using “Concurrent statements”. There are different types of concurrent statements in VHDL.

<h2>1.1       Direct Assignment</h2>

The simplest form of concurrent statements is the direct assignment. In VHDL assignment #1, you learned how to describe a 2-to-1 multiplexer using the direct assignment. Below is an example of direct assignment which performs XOR operation between two variables:

c &lt;= a XOR b;

<h2>1.2       Selected Signal Assignment or the “With/Select” Statement</h2>

Consider an <em>n</em>-to-1 multiplexer shown below. This block selects one of its <em>n </em>inputs and transfers the value of this input to the output terminal, <em>i.e.</em>, <em>output_signal</em>.

The selected signal assignment allows to implement the functionality of a multiplexer:

<table width="673">

 <tbody>

  <tr>

   <td width="249">with control_expression s e l e c t output_signal &lt;= value_1 when</td>

   <td width="424">option_1,</td>

  </tr>

  <tr>

   <td width="249">value_2 when</td>

   <td width="424">option_2,</td>

  </tr>

  <tr>

   <td width="249">…value_n when</td>

   <td width="424">option_n;</td>

  </tr>

 </tbody>

</table>

Here, the value of the <em>control_expression </em>will be compared with the <em>n </em>possible options, <em>i.e.</em>, <em>option_1</em>, <em>option_2</em>, …, <em>option_n</em>. When a match is found, the value corresponding to that particular option will be assigned to the output signal, <em>i.e.</em>, <em>output_signal</em>. For example, if <em>control_expression </em>is the same as <em>option_2</em>, then <em>value_2 </em>will be assigned to the <em>output_signal</em>. Note that the options of a “with/select” assignment must be mutually exclusive, <em>i.e.</em>, one option cannot be used more than once. Moreover, all possible values of the <em>control_expression </em>must be included in the set of options.

<h2>1.3       Conditional Signal Assignment or the “When/Else” Statement</h2>

The “when/else” statement is another way to describe concurrent signal assignments. In general, the syntax of the “when/else” statement is:

<table width="673">

 <tbody>

  <tr>

   <td width="127">output_signal &lt;=</td>

   <td width="95">value_1 when</td>

   <td width="89">expression_1</td>

   <td width="362">else</td>

  </tr>

  <tr>

   <td width="127"></td>

   <td width="95">value_2 when …value_n;</td>

   <td width="89">expression_2</td>

   <td width="362">else</td>

  </tr>

 </tbody>

</table>

In this case, the expressions after “when” are evaluated successively until a true expression is found. The assignment corresponding to this true expression will be performed. If none of these expressions are true, the last assignment will be executed. We should emphasize that the expressions after the “when” clauses are evaluated successively. As a result, expressions evaluated earlier have higher priority as compared to later expressions. Considering this, we can obtain the conceptual diagram of this assignment as shown below. This figure illustrates a conditional signal assignment with three “when” clauses.

<h2>1.4       Concurrent Statements at a Glance</h2>

Concurrent statements are executed at the same time and there is no significance to the order of these statements. This type of code is quite different from what we have learned in basic computer programming where the lines of code are executed one after the other.

The selected signal assignment or the “with/select” assignment allows us to implement the functionality of a multiplexer.

The options of a “with/select” assignment must be mutually exclusive, <em>i.e.</em>, one option cannot be used more than once. Moreover, all possible values of control_expression must be included in the set of options.

For the “when/else” statement, the expressions following the “when” clauses are evaluated successively. As a result, the expressions evaluated earlier have a higher priority as compared to the following expressions.

One important difference between the “with/select” and “when/else” assignment can be seen by comparing the conceptual implementation of these two statements. The “when/else” statement has a priority network; however, the “with/select” assignment avoids this chain structure and has a balanced structure.

<h1>2        Objective</h1>

Consider the truth table given below for functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2</sub>.

You are required to implement the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>using different VHDL concurrent statements. For all of your VHDL descriptions, use the following entity declaration:

<table width="673">

 <tbody>

  <tr>

   <td width="673">library              IEEE;use IEEE.STD_LOGIC_1164.ALL;entity entity_name i sPort (x1 : in std_logic ; x2 : in std_logic ; x3 : in std_logic ; x4 : in std_logic ; f1 : out std_logic ; f2 : out std_logic );end entity_name;</td>

  </tr>

 </tbody>

</table>

Perform the following tasks:

<ol>

 <li>Derive the canonical SOP expressions for the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>and calculate the cost of the canonical SOP expressions. Implement the given functions using direct assignment and the canonical SOP expressions. Use can_SOP as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Derive the canonical POS expressions for the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>and calculate the cost of the canonical POS expressions. Implement the given functions using direct assignment and the canonical POS expressions. Use can_POS as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Derive the reduced (simplified/optimized) SOP expressions for the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>and calculate the cost of the reduced SOP expressions. You can use the techniques you have learned so far in this course to derive the optimized expressions. Implement the obtained functions using direct assignment and the reduced SOP expressions. Use sim_SOP as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Derive the reduced (simplified/optimized) POS expressions for the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>and calculate the cost of the reduced POS expressions. You can use the techniques you have learned so far in this course to derive the optimized expressions. Implement the obtained functions using direct assignment and the reduced POS expressions. Use sim_POS as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Implement the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>using the select signal assignment. Perform an exhaustive test on your implementation. Use select_assignment as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Implement the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>using the conditional signal assignment. Perform an exhaustive test on your implementation. Use when_assignment as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

 <li>Find the most joint-optimized SOP expressions of the functions <em>f</em><sub>1 </sub>and <em>f</em><sub>2 </sub>and calculate the cost of your implementation. Implement the joint-optimized SOP expressions using Direct assignment. Use joint_SOP as the <em>entity_name</em>. Perform an exhaustive test on your implementation.</li>

</ol>

<h1>3        Deliverables</h1>

Once completed, you are required to submit a report explaining your work in detail (the techniques you used to optimize the functions), including answers to the questions related to this lab. You will find the questions in the next section. You must also submit all the design files (<em>i.e.</em>, your VHDL code) along with Log content of the synthesized circuits. You must also submit one of your testbench files. If you fail to submit any part of the required deliverables, you will incur grade penalaties as described in the syllabus.

<h1>4        Questions</h1>

<ol>

 <li>Explain your VHDL code.</li>

 <li>Report the costs and the number of logic modules used to fit your designs on the FPGA board.</li>

</ol>

<table width="570">

 <tbody>

  <tr>

   <td width="200">Task</td>

   <td width="47">1</td>

   <td width="47">2</td>

   <td width="47">3</td>

   <td width="47">4</td>

   <td width="67">5</td>

   <td width="67">6</td>

   <td width="47">7</td>

  </tr>

  <tr>

   <td width="200">Cost</td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="67">N/A</td>

   <td width="67">N/A</td>

   <td width="47"></td>

  </tr>

  <tr>

   <td width="200">Logic Utilization (in LUTs)</td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="47"></td>

   <td width="67"></td>

   <td width="67"></td>

   <td width="47"></td>

  </tr>

 </tbody>

</table>

<ol start="3">

 <li>Show representative simulation plots of all tasks for all the possible input values (exhaustive test results). Note that you can simply include snapshots from the waveform that you obtained from EPWave. In order to fully capture all the signals from the waveform, you can adjust the display range using the magnifier icons. Make sure that all signal names and axes are properly visible.</li>

</ol>