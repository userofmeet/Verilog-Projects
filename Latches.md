# SR Latch
``` Verilog
module sr(s,r,q,qbar);
  input s,r;
  output reg q;
  output reg qbar;
  
  always @(s,r) begin
  if (r == 1'b1) begin
      q <= 1'b0;
      qbar <= 1'b1;
    end else if (s == 1'b1) begin
      q <= 1'b1;
      qbar <= 1'b0;
    end
  end
endmodule
```
# SR Latch Testbech
``` Verilog
module srtestbench();
  reg s,r;
  wire q,qbar;
  sr testsr(s,r,q,qbar);
  initial 
  begin
    s = 1'b0;
    r = 1'b0;
    #10
    s = 1'b0;
    r = 1'b1;
    #10
    s = 1'b1;
    r = 1'b0;
    #10
    s = 1'b1;
    r = 1'b1;
    #10
    s = 1'b0;
    r = 1'b0;
    #10
    $stop;
  end
endmodule
```
# Output 
![image](https://github.com/userofmeet27/Verilog-Projects/assets/154442221/2eb4b396-29ad-4e89-b77e-f800e1b2530c)

# D Latch
``` Verilog
module dlatch(d,en,q,qbar);
  input d,en;
  output reg q;
  output qbar;
  assign qbar = ~q;
  always @(d,en)begin
    if (en) begin
      q <= d;
    end
  end
endmodule
```
# D Latch Testbench
``` Verilog
module dtestbench();
  reg d,en;
  wire q,qbar;
  dlatch dtest(d,en,q,qbar);
  initial begin
    d = 1'b0;
    en = 1'b0;
    #10
    en = 1'b1;
    d = 1'b0;
    #10
    d = 1'b1;
    #10
    en = 1'b0;
    d = 1'b0;
    #10
    d = 1'b1;
    #10 $stop;
  end
endmodule
```
# Output
![image](https://github.com/userofmeet27/Verilog-Projects/assets/154442221/393eab57-a33c-4bfc-822e-2f1d3b827773)
