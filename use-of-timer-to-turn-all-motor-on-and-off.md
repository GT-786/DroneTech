# Use Of Timer To Turn All Motor On And Off

```text
// Do not remove the include below
#include "PlutoPilot.h"
#include "Estimate.h" //gives access to drone rates, angles,velocities, positions
#include "utils.h" //gives you access to the LED,graphs, print
#include "Motor.h"

Interval motorTimer;

//The setup function is called once at Pluto's hardware startup
void plutoInit()
{
// Add your hardware initialization code here
}


//The function is called once before plutoLoop when you activate Developer Mode
void onLoopStart()
{
  // do your one time stuff here

	LED.flightStatus(DEACTIVATE); //disable LED behaviuour

}


// The loop function is called in an endless loop
void plutoLoop()
{

//Add your repeated code here
	bool flag;
	static uint8_t state=0;
	flag=motorTimer.set(2000,true); //will check for every 2s
	if(flag)
	{
		if(state==0)
		{
			Motor.set(M5,1200);
			Motor.set(M6,1200);
			Motor.set(M7,1200);
			Motor.set(M8,1200);
			state=1;

		}
		else if (state==1)
		{
			Motor.set(M5,1000);
			Motor.set(M6,1000);
			Motor.set(M7,1000);
			Motor.set(M8,1000);
			state=0;
		}
	}

}


//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here
	Motor.set(M5,1000);
	Motor.set(M6,1000);
	Motor.set(M7,1000);
	Motor.set(M8,1000);
	LED.flightStatus(ACTIVATE);
}
```

![Desired Output\(See the 4 Motors\)](.gitbook/assets/ezgif.com-video-to-gif.gif)



