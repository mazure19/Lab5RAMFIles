# Lab5RAMFIles
All of the files in the RAM LAB

//Decoder

module Decoder2to4(a,b,en,CS0,CS1,CS2,CS3);

input a, b, en;

output CS0,CS1,CS2,CS3;

assign CS0= (~a) & (~b) & en;

assign CS1= (~a) & b & en;

assign CS2= a & (~ b) & en;

assign CS3= a & b & en;


endmodule 

//TristateBuffer


module TriStateBuffer(a, en, x);

input a, en;

output x;

assign x = en? a: 'bz;



endmodule 


//RAM


module RAM( input [7:0] adrs, input [7:0] data, output [7:0] out);

reg [7:0] mem[0:63];

reg [7:0] result;

assign out = result;


always@(*)

begin

	result = data;
  
end

endmodule 


//FullRAM


module FullRAM(a, b, c, d, in, csin, out32, out1, out2, out3, out4, out5, out6, out7, out8, out9, out10, out11, out12, out13, out14, out15, out16);


input [7:0] a, b, c, d, in;

input [1:0] csin;

output [31:0] out32;

output [7:0] out1;

output [7:0] out2;

output [7:0] out3;

output [7:0] out4;

output [7:0] out5;

output [7:0] out6;

output [7:0] out7;

output [7:0] out8;

output [7:0] out9;

output [7:0] out10;

output [7:0] out11;

output [7:0] out12;

output [7:0] out13;

output [7:0] out14;

output [7:0] out15;

output [7:0] out16;


reg [31:0] result;

assign out32 = result;


RAM row1_1(a, in, out1);

RAM row1_2(b, in, out2);

RAM row1_3(c, in, out3);

RAM row1_4(d, in, out4);


RAM row2_1(a, in, out5);

RAM row2_2(b, in, out6);

RAM row2_3(c, in, out7);

RAM row2_4(d, in, out8);


RAM row3_1(a, in, out9);

RAM row3_2(b, in, out10);

RAM row3_3(c, in, out11);

RAM row3_4(d, in, out12);


RAM row4_1(a, in, out13);

RAM row4_2(b, in, out14);

RAM row4_3(c, in, out15);

RAM row4_4(d, in, out16);


always @(*)

begin

	if (csin == 2'd0)
  
		result = {out1, out2, out3, out4};
    
	if(csin == 2'd1)
  
		result = {out5, out6, out7, out8};
    
	if(csin == 2'd2)
  
		result = {out9, out10, out11, out12};
    
	if(csin == 2'd3)
  
		result = {out13, out14, out15, out16};
    
end 

endmodule 
