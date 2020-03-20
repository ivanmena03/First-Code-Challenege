// Created on Thu March 19 2020

int r_motor = 2;																 //ist of integers
int l_motor = 0;																
int l_bump = 8;
int r_bump = 9;
int mid_speed = 100;
int slow_speed = 20;

void forward() {																//Goes forward
	motor(r_motor, mid_speed);
	motor(l_motor, mid_speed);
	}
void right_turn() {															//Turns right 
	motor(l_motor, mid_speed);
	motor(r_motor, -slow_speed);
	}

int main()
{
	printf("Hello, World!\n");												
	while(digital(r_bump)==0) {										//Sensor is on and moves forward
		forward();
		if(digital(r_bump)==1){											//Right bumper moves forward 
			break;																//Enter next loop
			}
	}
	ao();												//reset motion
	while(digital(l_bump)==0) {							//turns toward wall til left bumper is activated
		right_turn();															//Turns right
	}
	
	return 0;
}
