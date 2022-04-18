# dual_port_RAM
Dual port ram in Verilog HDL
module comparator2_bit(A,B,eq,gt,lt);
  input [1:0] A,B;
  output reg eq,gt,lt;
  
  always@(A,B)
    begin
      eq=0;
      gt=0;
      lt=0;
      
      if(A==B)
        eq=1;
      else if(A > B)
        gt=1;
      else
        lt=1;
    end
endmodule

module comparator2_bit_tb();
reg  [1:0] A,B;
wire reg eq,gt,lt;
  comparator2_bit cmp2bit(.A(A),.B(B),.eq(eq),.gt(gt),.lt(lt));
initial
begin
A= 2'b01;
B= 2'b10;
#10 A= 2'b10; B= 2'b01;
#10 A= 2'b11; B= 2'b11;
#10 $finish;
end

initial
begin
  $monitor("At time=%t, A=%2b, B=%2b, eq=%b, gt=%b, lt=%b", $time, A, B, eq, gt, lt );
end
endmodule
