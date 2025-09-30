# Exp-5-Design-and-Simulate the-Memory-Design-using-Verilog-HDL
#Aim
To design and simulate a RAM,ROM,FIFO using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment.
Apparatus Required
Vivado 2023.1
Procedure
1. Launch Vivado 2023.1
Open Vivado and create a new project.
2. Design the Verilog Code
Write the Verilog code for the RAM,ROM,FIFO
3. Create the Testbench
Write a testbench to simulate the memory behavior. The testbench should apply various and monitor the corresponding output.
4. Create the Verilog Files
Create both the design module and the testbench in the Vivado project.
5. Run Simulation
Run the behavioral simulation to verify the output.
6. Observe the Waveforms
Analyze the output waveforms in the simulation window, and verify that the correct read and write operation.
7. Save and Document Results
Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

# Code
# RAM
## RTL Verilog code ##
```verilog

module ram (input clk,input rst,input en,input [7:0] datain,input [9:0] address,output reg [7:0] dataout);
    reg [7:0] mem [1023:0];
    always @(posedge clk) begin
    if (rst) begin
    dataout <= 8'b0;
    end
    else if (en) begin
    mem[address] <= datain;
    end
    else begin
    dataout <= mem[address];
    end
end
endmodule
```
# Test bench
verilog
```
module ram_tb;
reg clk_t, rst_t, en_t;
reg [7:0] datain_t;
reg [9:0] address_t;
  wire [7:0] dataout_t;
  ram dut (
  .clk(clk_t),
  .rst(rst_t),
  .en(en_t),
  .datain(datain_t),
  .address(address_t),
  .dataout(dataout_t)
);

  initial begin
    clk_t = 1'b0;
    rst_t = 1'b1;
    #100
    rst_t = 1'b0;
    en_t=1'b1;
    address_t = 10'd800;
    datain_t = 8'd50;
    #100;
    address_t = 10'd950;
    datain_t = 8'd60;
    #100;
    en_t = 1'b0;
    address_t = 10'd800;
    #100;
    address_t = 10'd950;
    #100;
  end
    always #10 clk_t = ~clk_t;
endmodule

```
## output Waveform
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/02232c2c-b83c-47bf-b402-fb4b98c7bbaa" />

# ROM
 // write verilog code for ROM using $random
 
 // Test bench

// output Waveform

 # FIFO
 // write verilog code for FIFO
 
 // Test bench

// output Waveform



# Conclusion
The RAM, ROM, FIFO memory with read and write operations was designed and successfully simulated using Verilog HDL. The testbench verified both the write and read functionalities by simulating the memory operations and observing the output waveforms. The experiment demonstrates how to implement memory operations in Verilog, effectively modeling both the reading and writing processes.
 
 

