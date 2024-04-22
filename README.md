# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS
# AIM:
To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

# APPARATUS REQUIRED:
vivado 2023.2.

# PROCEDURE:
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

# LOGIC DIAGRAM
# ENCODER
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/53987fa0-be50-447c-b63b-306e7bf4ca6d)


# DECODER
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/76b7c504-0cc5-4716-9f92-6e508a524e79)


# MULTIPLEXER
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/e2255c91-120c-4627-8dd3-ba02b57b0332)


# DEMULTIPLEXER
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/39e0917b-5c18-4f21-ad8d-fd8232dcc14c)


# MAGNITUDE COMPARATOR
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/d92b3724-bfd0-437e-a8f4-43257bb08411)


# VERILOG CODE
# 8-3 ENCODER:
module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule

# 3-8 DECODER:
module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule

# 8-1 MULTIPLEXER:
module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase end

endmodule

# 1-8 DEMULTIPLEXER:
module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i); and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

# 2 BIT MAGNITUDE COMPARATOR :
module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule

# OUTPUT WAVEFORM:
# ENCODER:
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/7ae0fd82-aa34-4cb6-b454-f1d2978e2fcd)


# DECODER:
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/56afcc27-e36f-4f2f-86d5-6e38fcb5c9c9)


# MULTIPLEXER:
![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/1c0c147a-4a0f-4c46-8688-e6a7e87f81a6)


# DEMULTI![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/634b22ef-f238-425c-8fcf-38274c8640b3)


# 2 BIT MAGNITUDE COMPARATOR:

![image](https://github.com/nikil190/VLSI-LAB-EXP-2/assets/161817112/da987ab4-fb18-4489-a875-906d793b3740)

# RESULT:
Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.
