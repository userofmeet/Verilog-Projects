# Comparator
``` Verilog
module comparator(a,b,equal,less,greater,ina,inb);
  input [2:0]a;
  input [2:0]b;
  output reg equal,less,greater,ina,inb;
  always @(a,b) begin
    if (a == b) begin
      equal <= 1'b1;
      less <= 1'b0;
      greater <= 1'b0;
      ina <= 1'b1;
      inb <= 1'b1;
    end else if (a > b) begin  
      equal <= 1'b0;
      less <= 1'b0;
      greater <= 1'b1;
      ina <= 1'b1;
      inb <= 1'b0;
    end else if (a < b) begin
      equal <= 1'b0;
      less <= 1'b1;
      greater <= 1'b0;
      ina <= 1'b0;
      inb <= 1'b1;
    end
  end
endmodule
```
# Comparator Testbench
``` Verilog
module comparatortest();
  reg [2:0]a;
  reg [2:0]b;
  wire equal,less,greater,ina,inb;
  
comparator comp(a,b,equal,less,greater,ina,inb);
initial 
begin
  a = 3'b000; 
  b = 3'b000;
  #10
  a = 3'b111;
  b = 3'b010;
  #10
  a = 3'b100;
  b = 3'b110;
  #10 $stop;
end
endmodule
```
# Output
![image](https://github.com/userofmeet27/Verilog-Projects/assets/154442221/67529507-cbb1-4d8f-901d-ace70d2b5700)
