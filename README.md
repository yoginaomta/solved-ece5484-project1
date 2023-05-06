Download Link: https://assignmentchef.com/product/solved-ece5484-project1
<br>
The objective of this project is to reinforce your understanding of binary codes, combinational logic design, and logic simulation. You must:

<ul>

 <li>design a combinational logic circuit that displays the hexadecimal value of a gray code input according to the specifications given below;</li>

 <li>debug and test your design by simulating it using the Logisim simulator; and 3) document your work in a short report.</li>

</ul>

<h1>1.      Gray Codes</h1>

Consider a system where a value is changed by being incremented or decremented by one. The value is encoded by <em><sub>n </sub></em>binary signals. As a specific example, consider a value, represented with 4 bits, being incremented from 3 to 4. In a traditional weighted binary encoding, 3 is represented as 0011 and 4 is represented as 0100. For the change from 3 to 4, three bits must change. Since the time of the transitions in the actual signals will always be different if examined at a sufficiently fine scale, the value will not change instantaneously from 3 to 4. As an example, the transition could occur as follows, where the transitions to value 7 and then value 5 are transient in nature.

0011 (3) <em>→ </em>0111 (7) <em>→ </em>0101 (5) <em>→ </em>0100 (4)

The physical reality of such signal transitions can create problems for applications including mechanical encoders and asynchronous (clock-free) systems. This problem can be overcome using Gray codes, which are non-weighted codes that can be used to represent values. Gray codes have the special property that any two adjacent values differ in just one bit. For example, the standard four-bit Gray code for 3 is 0010 and the code for 4 is 0110. These two codes differ in just one bit, the second bit from the left. So, only a single signal needs to change from 0 to 1 (or 1 to 0 for other values) to represent an adjacent value. You can read more about Gray codes at <a href="https://en.wikipedia.org/wiki/Gray_code"><em>http://en.wikipedia.org/wiki/Gray_code</em></a><a href="https://en.wikipedia.org/wiki/Gray_code">.</a>

For this project we consider a special type of Gray code called a Balanced Gray code. In a Balanced Gray code, the number of transitions for each bit position is the same when counting through the values. For example, a four-bit Balanced Gray code can be used to count from 0 to 15 (hexadecimal F). There are 16 transitions as the count goes from 0 to 1 to 2 and so on to 15 and then back to 0. For a Balanced Gray code, there are four bit transitions for each of the four bit positions during the 16 total transitions. This property is useful in some applications.

Table I below shows the encoding of hexadecimal values 0 through F using a 4-bit Balanced Gray code.

Table I. Hexadecimal Values and Associated 4-bit Balanced Gray Code and Binary Code

<strong>Hexadecimal                              Balanced Gray Code                                                Binary Code</strong>

<strong>Value                                          </strong>(X3X2X1X0)                                                                       (Y3Y2Y1Y0)

<ul>

 <li>0 0 0 0 0 0 0 0</li>

 <li>1 0 0 0 0 0 0 1</li>

 <li>1 1 0 0 0 0 1 0</li>

 <li>1 1 0 1 0 0 1 1</li>

 <li>1 1 1 1 0 1 0 0</li>

 <li>1 1 1 0 0 1 0 1</li>

 <li>1 0 1 0 0 1 1 0</li>

 <li>0 0 1 0 0 1 1 1</li>

 <li>0 1 1 0 1 0 0 0</li>

 <li>0 1 0 0 1 0 0 1</li>

 <li>0 1 0 1 1 0 1 0</li>

 <li>0 1 1 1 1 0 1 1</li>

 <li>0 0 1 1 1 1 0 0</li>

 <li>1 0 1 1 1 1 0 1</li>

 <li>1 0 0 1 1 1 1 0</li>

 <li>0 0 0 1 1 1 1 1</li>

</ul>

<h1>2.      Design Specification</h1>

You are to design a combinational logic circuit that accepts a four-bit Balanced Gray code (X<sub>3</sub>X<sub>2</sub>X<sub>1</sub>X<sub>0</sub>) as its input and creates a four-bit output (Y<sub>3</sub>Y<sub>2</sub>Y<sub>1</sub>Y<sub>0</sub>) that uses standard binary encoding to represent the same hexadecimal value. In other words, the circuit translates between the Balanced Gray code input and the binary code output as indicated in Table I. Figure 1 provides a block diagram of the function. You do <em><sub>not </sub></em>need to minimize the logic function or associated circuit, but you may choose to do so.

Note that Table I is not a true truth table in that it is not ordered by input. You need to rearrange the rows in Table I to construct a standard truth table with inputs X<sub>3</sub>X<sub>2</sub>X<sub>1</sub>X<sub>0 </sub>appearing in order from 0000, 0001, 0010, …, 1111.

Figure 1. Block diagram of the converter function.

<h1>3.      Modeling the Circuit in Logisim</h1>

Use the Pin device in Logisim’s Wiring library to control the four inputs (X<sub>3</sub>X<sub>2</sub>X<sub>1</sub>X<sub>0</sub>) to the combinational circuit. The Pin device is also available on Logisim’s toolbar. Each pin can be interactively set to 0 or 1 using Logisim’s Poke tool to test the circuit for different Balanced Gray code input values. If the proper connections are in place when Logisim is running, signals with logic level 1 appear in bright green and signals with logic level 0 are shown in dark green.

The circuit’s four output bits should be used to control a hexadecimal display to show values 0 through F, inclusive. Use the Hex Digit Display device in Logisim’s Input/Output library. It accepts a 4-bit binary encoded value as input and displays the hexadecimal digit corresponding to the binary-encoded input. Use the Splitter device in Logisim’s Wiring library to interface the four individual single bits produced by the combinational circuit (Y<sub>3</sub>Y<sub>2</sub>Y<sub>1</sub>Y<sub>0</sub>) to the four-bit wide input to the Hex Digit Display. The Hex Digit Display device has a second input to control the decimal (hexadecimal) point. The decimal point input can be left unconnected. Figure 2 shows a possible layout for the design. The associated Logisim circuit file is provided

with this assignment.

Figure 2. Possible circuit layout including logic to produce output <em><sub>Y</sub></em><sub>0 </sub>(input is for Balanced Gray Code value 0011 which produces output 1100 or hexadecimal C).

The design in Figure 2 includes the combinational logic to produce output Y<sub>0</sub>. By observation, we see that output Y<sub>0 </sub>is true if and only if there are an odd number of logic 1 inputs. Thus, Y<sub>0 </sub>is implemented by the exclusive-or (XOR) function, i.e., Y<sub>0 </sub>= X<sub>3 </sub><em><sub>⊕ </sub></em>X<sub>2 </sub><em><sub>⊕ </sub></em>X<sub>1 </sub><em><sub>⊕ </sub></em>X<sub>0</sub>. For the Logisim XOR Gate, the Multiple-Input

Behavior attribute needs to be set to “When an odd number are on.”

<h1>4.      Simulation</h1>

After you create your design, use Logisim to simulate the code conversion circuit. You should test all 16 possible input combinations and verify that the correct values of Y<sub>3</sub>, Y<sub>2</sub>, Y<sub>1</sub>, and Y<sub>0 </sub>are produced and that the correct hexadecimal value is displayed.

<h2>5.1.       Report</h2>

You must document the design, simulation, and outcomes in a brief written report. Your report should contain the following items.

<ul>

 <li>At the top of the first page of your report, include: your name (as recorded by the university); your email address; and the assignment name (e.g., “ECE 5484, Project 1”). Do <em><sub>not </sub></em>include your Virginia Tech ID number or your social security number.</li>

 <li>The body of the report must contain the following sections. Use section numbers and headings to organize your report.</li>

</ul>

<em>Section 1 – Objectives</em>: Provide a brief summary of the design objectives and general approach to the design. <em>Section 2 – Truth Table</em>: Provide a truth table with inputs X<sub>3</sub>, X<sub>2</sub>, X<sub>1</sub>, and X<sub>0 </sub>and outputs Y<sub>3</sub>, Y<sub>2</sub>, Y<sub>1</sub>, and Y<sub>0</sub>. Each row should also be labeled with the corresponding hexadecimal value. The inputs must be in standard truth table order, from “0000” down to “1111.” Thus, the truth table will look similar to Table I above, but will be reordered.

<em>Section 3 – Logic Expressions</em>: Specify the Boolean logic expressions for Y<sub>3</sub>, Y<sub>2</sub>, Y<sub>1</sub>, and Y<sub>0</sub>. Show any work that led to the expressions. (You can just state the expression for Y<sub>0 </sub>given above, assuming you implement <em>Y</em><sub>0 </sub>as shown in Figure 2.) The Boolean expressions shown in this section for the report should correspond exactly to what is shown in the circuit diagram of the next section.

<em>Section 4 – Circuit Design</em>: Include a schematic diagram of the logic circuit that you created using Logisim. Within Logisim, you can select Export Image from the File menu to produce an image file that can then be incorporated into your report. Uncheck the “Printer View” box when exporting the image from Logisim. Show the circuit with input X<sub>3</sub>X<sub>2</sub>X<sub>1</sub>X<sub>0 </sub>= 0100 (hexadecimal value 9) applied. For full credit, the Logisim schematic must be neat and easy to read. The four input pins and the four output signals should be labeled, as shown in Figure 2. The diagram should also be labeled with a title, your name, and the date.

<em>Section 5 – Conclusions</em>: Briefly discuss the outcome of your design and any problems or aspects that do not work properly; what you learned by doing this project; and any experiences that were particularly good or bad. Also, specify the approximate number of hours that you devoted to the project. (The number of hours is just for the instructor to assess the suitability of this project assignment.)