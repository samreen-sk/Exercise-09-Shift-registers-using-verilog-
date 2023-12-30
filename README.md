
# Experiment--09-Implementation-of Shift-registers-using-verilog-
### AIM: 
To implement PISO , PIPO,PISO  using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:
– PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:
Quartus prime
### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

### Procedure

# STEP 1
Use quartus software and import required modules.
# STEP 2
Assign inputs and outputs for shift registers.
# STEP 3
Assign logic for input to give output at positive edge.
# STEP 4
Perform opertaions and produce rtl circuit.
# STEP 5
End module.


## Program 1:
```

module SIPO(c,si,po);
input c,si;
output [7:0] po;
reg [7:0] temp;
always @ (posedge c)
begin
temp = {temp[6:0],si};
end
assign po = temp;
endmodule

```

### RTL LOGIC  REGISTERS   

![172343226-35e7994d-fd15-474b-8ad3-d0b5951361d7](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/6a7ed159-ed47-4dea-994b-6cd77e1ad170)


### TIMING DIGRAMS FOR SHIFT REGISTERS

![172343477-d655b5aa-1425-4a76-bca7-0de2ab5bc82f](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/68146566-6c8d-4667-985a-14ca514dfef8)


## program 2:

```
mmodule PISO(Clk,Pin,load,so);
input load,Clk;
input [3:0] Pin;
output reg so;
reg [3:0] temp;
always @ (posedge Clk)
begin 
if(load)
temp <= Pin;
else
begin
so<=temp[3];
temp <={temp[2:0],1'b0};
end
end
endmodule

```

### RTL LOGIC REGISTERS:

![201101903-d0bc6010-1a46-4616-bcd9-4f36ad0bbc1c](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/2862065a-fdc7-42a2-b48d-0e8110013433)

### TIMING DIGRAMS FOR SHIFT REGISTERS:

![201103309-82b8f143-8301-486c-a86b-a21bd5a5408c](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/52d1e70a-8298-443f-947a-8307afd87fa1)

## program 3:
```
module PIPO (Po,Pi,clk);
input clk;
input[3:0] Pi;
output reg[3:0] Po;
always@(posedge clk)
begin
Po=Pi;
end 
endmodule
```

### RLT LOGIC REGISTERS:

![201100899-974ad5ff-f6dc-4052-9b78-9a1a778e7daf](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/f3cb4b52-38b6-4336-a068-c2a2c7a53c04)

### TIMINGS DIAGRAMS FOR SHIFT REGISTERS:

![201100957-c0671c2d-bccc-4a58-9b7e-2e9cd1e35607](https://github.com/samreen-sk/Exercise-09-Shift-registers-using-verilog-/assets/149347632/41b5e602-57e7-4b88-93d6-76422d35468f)

### RESULTS 
Thus the program to implement shift registers is done successful.
