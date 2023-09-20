module TLC(clk,rst,Go,Highway_TL1,Highway_TL2,Farm_TL1,Farm_TL2);

input rst,Go,clk;
output reg [1:0] Highway_TL1,Highway_TL2,Farm_TL1,Farm_TL2;

 
integer counter;

  //define all states using array
reg [4:0] State_i [0:17] = '{5'b00000, 5'b00001, 5'b00010,5'b00011,5'b00100,5'b00101,5'b00110,
								5'b00111,5'b01000,5'b01001,5'b01010,5'b01011,5'b01100,5'b01101,
								5'b01110,5'b01111,5'b10000,5'b10001}; 
reg [4:0] State = State_i [0];
parameter Red = 2'b10,		  //define colors using parameters
	Red_Yellow = 2'b11,
	Yellow = 2'b01,
	Green = 2'b00;
	
always @(posedge clk or posedge rst )	
	begin 
if (rst)begin				 // if reset 1 back to state 0 
	
	State = State_i[0];
	counter = 0;

end else begin	//reset = 0	
	
		if( Go == 1)		 //if go =1 start the system
		begin 
			case (State)
				State_i [0]:
					begin
					if (counter == 1 )		 //if the delay of the state done go to next state
						begin
						counter = 0;
						State = State_i [1];
						end
					else 					   //else increase counter	and so on for other states
						counter++ ;
					end 
				State_i [1]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [2];
						end
					else 
						counter++ ;
					end 
				State_i [2]:
					begin
					if (counter == 30 )
						begin
						counter = 0;
						State = State_i [3];
						end
					else 
						counter++ ;
					end 
				State_i [3]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [4];
						end
					else 
						counter++ ;
					end 
				State_i [4]:
					begin
					if (counter == 10 )
						begin
						counter = 0;
						State = State_i [5];
						end
					else 
						counter++ ;
					end 
				State_i [5]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [6];
						end
					else 
						counter++ ;
					end 
				State_i [6]:
					begin
					if (counter == 1 )
						begin
						counter = 0;
						State = State_i [7];
						end
					else 
						counter++ ;
					end
				State_i [7]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [8];
						end
					else 
						counter++ ;
					end 
				State_i [8]:
					begin
					if (counter == 15 )
						begin
						counter = 0;
						State = State_i [9];
						end
					else 
						counter++ ;
					end 
				State_i [9]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [10];
						end
					else 
						counter++ ;
					end 
				State_i [10]:
					begin
					if (counter == 5 )
						begin
						counter = 0;
						State = State_i [11];
						end
					else 
						counter++ ;
					end 
				State_i [11]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [12];
						end
					else 
						counter++ ;
					end 
				State_i [12]:
					begin
					if (counter == 10 )
						begin
						counter = 0;
						State = State_i [13];
						end
					else 
						counter++ ;
					end 
				State_i [13]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [14];
						end
					else 
						counter++ ;
					end	
				State_i [14]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [15];
						end
					else 
						counter++ ;
					end	
				State_i [15]:
					begin
					if (counter == 2 )
						begin
						counter = 0;
						State = State_i [16];
						end
					else 
						counter++ ;
					end 
				State_i [16]:
					begin
					if (counter == 15 )
						begin
						counter = 0;
						State = State_i [17];
						end
					else 
						counter++ ;
					end 
				State_i [17]:
					begin
					if (counter == 3 )
						begin
						counter = 0;
						State = State_i [0];
						end
					else 
						counter++ ;
					end
		endcase
		
end // go = 1

end //reset = 0

end	// always 




always @(posedge clk)
	begin
		case(State)
			State_i[0]: begin 
					Highway_TL1 = Red;
					Highway_TL2 = Red;
					Farm_TL1 = Red;
					Farm_TL2 = Red;
				end
			State_i[1]: begin 
					Highway_TL1=  Red_Yellow;
					Highway_TL2=  Red_Yellow;
					Farm_TL1= Red;
					Farm_TL2= Red;
				end
			State_i [2]: begin
					Highway_TL1= Green;
					Highway_TL2= Green;
					Farm_TL1= Red;
					Farm_TL2= Red;
				end
			State_i [3]:begin	 
					Highway_TL1= Green;
					Highway_TL2=  Yellow;
					Farm_TL1= Red;
					Farm_TL2= Red;
				end	
			State_i [4]: begin 	 
					Highway_TL1= Green;
					Highway_TL2= Red;
					Farm_TL1= Red;
					Farm_TL2= Red;
				end
			State_i [5]: begin	 
					Highway_TL1= Yellow;
					Highway_TL2= Red;
					Farm_TL1= Red;
					Farm_TL2= Red;
				end
			State_i [6]: begin	 
					Highway_TL1= Red;
					Highway_TL2=Red;
					Farm_TL1= Red ;
					Farm_TL2= Red;
				end
			State_i [7]:begin	 
					Highway_TL1=Red;
					Highway_TL2=Red;
					Farm_TL1= Red_Yellow ;
					Farm_TL2= Red_Yellow ;
				end
			State_i [8]: begin 	 
					Highway_TL1=Red;
					Highway_TL2=Red;
					Farm_TL1= Green;
					Farm_TL2= Green;
				end
			State_i [9]: begin	 
					Highway_TL1= Red;
					Highway_TL2= Red;
					Farm_TL1= Green;
					Farm_TL2= Yellow;
				end
			State_i [10]: begin	 
					Highway_TL1=Red;
					Highway_TL2= Red;
					Farm_TL1=  Green;
					Farm_TL2= Red;
				end
			State_i [11]:begin	 
					Highway_TL1= Red;
					Highway_TL2 = Red;
					Farm_TL1 = Yellow;
					Farm_TL2 = Red_Yellow;
				end
			State_i [12]: begin 	 
					Highway_TL1 = Red;
					Highway_TL2 = Red;
					Farm_TL1 = Red;
					Farm_TL2 = Green;
				end
			State_i [13]: begin	 
					Highway_TL1 = Red;
					Highway_TL2 = Red;
					Farm_TL1 =  Red;
					Farm_TL2 =Yellow;
				end			   
			State_i [14]: begin	 
					Highway_TL1 =  Red;
					Highway_TL2 = Red;
					Farm_TL1 =  Red;
					Farm_TL2 =  Red;
				end
			State_i [15]:begin	 
					Highway_TL1 = Red;
					Highway_TL2 = Red_Yellow;
					Farm_TL1 = Red;
					Farm_TL2 =  Red;
				end
			State_i [16]: begin 	 
					Highway_TL1 =  Red;
					Highway_TL2 = Green;
					Farm_TL1 =	Red;
					Farm_TL2 = Red;
				end
			State_i [17]: begin	 
					Highway_TL1 = Red;
					Highway_TL2 = Yellow;
					Farm_TL1 = Red;
					Farm_TL2 = Red;
				end
			
		endcase
	end

endmodule
//1 sec represents by 15ps 2 sec represents by 30ps  and so on
//testbench for traffic light system	 

module traffic_light_Tb;
	reg reset,go,clock;		//input
	wire [1:0] Highway_TL1,Highway_TL2,Farm_TL1,Farm_TL2;  //output
	
	TLC tt (clock,reset,go,Highway_TL1,Highway_TL2,Farm_TL1,Farm_TL2); // instance of  Traffic_light module	
	
	initial begin 
		// test reset
		clock = 1'b0;
		reset = 1'b1;
		repeat (5)
		#5ps clock = ~clock;	
		
		// test go
		reset = 1'b0;
		go = 1'b0;
		repeat (10)
		#5ps clock = ~clock;
		
		go = 1'b1;
		repeat (150)
		#5ps clock = ~clock;
		
		// test go
		go = 1'b0;
		repeat (10)
		#5ps clock = ~clock;
		
		 go = 1'b1;
		repeat (250)
		#5ps clock = ~clock;  
		// test reset again
		reset = 1'b1;
		repeat (5)
		#5ps clock = ~clock;
		
		go = 1'b1;
		repeat (100)
		#5ps clock = ~clock; 
		
		end
	
endmodule	