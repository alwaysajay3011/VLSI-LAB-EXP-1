# AIM: 
To simulate and synthesis Logic Gates,Adders and Subtractor using Vivado 2023.1

# APPARATUS REQUIRED: 
Vivado 2023.1

# PROCEDURE: 
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design


Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)


# HALF ADDER
VERILOG CODE
~~~
module half_adder(Sum,carry,a,b);
input a,b;
output Sum,carry;
assign Sum = a ^ b;
assign carry = a & b;
endmodule
~~~


OUTPUT:
<img width="745" alt="320198889-6c4f319b-6117-4f80-ab75-0828a105d2a5" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/039b61a6-2608-4b32-ab68-0d4e255ffb0c">
<img width="962" alt="320198935-312df9ed-ef21-424f-a4d7-8d81a4c64eae" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/79b8e891-b02c-4166-b67e-6489a60ffadb">



# HALF SUBTRACTOR

VERILOG CODE:
~~~
module half_sub(Diff,Borrow,a,b);
input a,b;
output Diff,Borrow;
wire w1;
not(w1,a);
xor(Diff,a,b);
and(Borrow,b,w1);
endmodule
~~~

OUTPUT:
<img width="826" alt="320198998-fff6face-f63a-4172-b5a9-6a95022deab8" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/c3675959-8a98-455d-9dee-0098efc72527">
<img width="962" alt="320199034-50e5c3d6-8f3c-4712-8fe2-fa0114dae014" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/7a0da717-11b7-4cfd-8c3c-9d60464046a2">



# FULL ADDER
VERILOG CODE:
~~~
module fulladder(sum,cout,a,b,c);
input a,b,c;
output sum,cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and a1(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,c1,c2);
or o2(cout,w5,c3);!
endmodule
~~~

OUTPUT:
<img width="962" alt="320199228-0f99f497-5145-41cb-971d-0b96a339897b" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/96ffee78-fc09-42fc-ae57-7fc5d7f6188a">
<img width="962" alt="320199301-19d4ec03-ae75-493d-b998-798c356a1069" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/5b8513ce-de50-4859-a270-f971b78d81a3">



# FULL SUBTRACTOR
VERILOG CODE:
~~~
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
~~~

OUTPUT:
<img width="692" alt="320199386-cb986e1c-8a11-4bc0-906d-d4a5fd6a3682" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/0fa504d4-830e-4462-960f-375e507bbc9b">
<img width="962" alt="320199408-e6dc405d-a723-483f-88f3-1132dd037dae" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/d0c079b1-53c8-4487-ad8c-d73c1dc984c8">


# LOGIC GATES
VERILOG CODE:
~~~
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
~~~

OUTPUT:
<img width="822" alt="320199565-7b1685d4-2018-43e2-aac4-96684266e0c6" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/3e0fe74b-128b-4ce5-9880-e787f077aaa0">
<img width="962" alt="320199601-32d0f8af-5dea-47fd-ab65-e64aaa0d03ee" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/bad14874-6ea4-4791-9af4-f85efb36a5dd">


# 4-BIT RIPPLE CARRY ADDER
VERILOG CODE:
~~~
module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;
input Cin;
output [3:0] S;
output Cout;
wire w1, w2, w3;
fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout, X[3], Y[3], w3);
endmodule

module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
~~~
OUTPUT:
<img width="962" alt="320199782-deb0ca19-1fc3-4a6c-9168-1c59e4105e6d" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/880ef584-fdca-4c2b-bd76-d6705d64062d">
<img width="962" alt="320199737-270b38f9-6725-4118-8ef8-98ca78e7be87" src="https://github.com/alwaysajay3011/VLSI-LAB-EXP-1/assets/161150132/ac214aa7-766a-4660-b9a4-e4f5c8be392b">


# 8-BIT RIPPLE CARRY ADDER
VERILOG CODE:
~~~
module rippe_adder(S, Cout, X, Y,Cin);
input [7:0] X, Y;// Two 4-bit inputs
input Cin;
output [7:0] S;
output Cout;
wire w1, w2, w3, w4, w5, w6, w7;
 // instantiating 8 1-bit full adders in Verilog
fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], w4,X[3], Y[3], w3);
fulladder u5(S[4], w5,X[4], Y[4], w4);
fulladder u6(S[5], w6,X[5], Y[5], w5);
fulladder u7(S[6], w7,X[6], Y[6], w6);
fulladder u8(S[7], Cout,X[7], Y[7], w7);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
  //Structural code for one bit full adder
xor G1(w1, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or G5(Co, w2, w3);
endmodule
~~~

OUTPUT:


RESULT:
THUS THE LOGIC GATES,ADDERS,SUBTRACTORS VERILOG CODE IS SIMULATED  USING VIVADO 2023.1 AND OUTPUT VERIFIED SUCCESSFULLY



