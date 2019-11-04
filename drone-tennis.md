# Drone Tennis

```text

// Do not remove the include below
#include "PlutoPilot.h"
#include "Sensor.h"
#include "Estimate.h"
#include "utils.h"
#include "User.h"
#include "Control.h"
#include "Motor.h"
#include "XRanging.h"

int16_t LRange=0;
int16_t RRange=0;

//The setup function is called once at Pluto's hardware startup
void plutoInit()
{
// Add your hardware initialization code here
	XRanging.init(LEFT);  //left sensors is initialized
	XRanging.init(RIGHT);  //right sensors is initialized
}



//The function is called once before plutoLoop when you activate Developer Mode
void onLoopStart()
{
  // do your one time stuff here

	LED.flightStatus(DEACTIVATE); //disable LED behavior
}


// The loop function is called in an endless loop
void plutoLoop()
{

//Add your repeated code here
LRange=XRanging.getRange(LEFT); //will get left sensors values of drone
RRange=XRanging.getRange(RIGHT); //will get right sensors values of drone

if(LRange<350 && LRange>0)  //if the sensor detects an obstacle on  left side i.e. range less than 350 then roll right
{
  RcCommand.set(RC_ROLL,1540);
  LED.set(RED,ON);
  LED.set(BLUE,OFF);
}

else   //if the sensor detects an obstacle on right side i.e. range less than 350 then roll left
{
	if(RRange<350 && RRange>0)
	{
		  RcCommand.set(RC_ROLL,1460);
		  LED.set(RED,OFF);
		  LED.set(BLUE,ON);
	}

    else  //no obstacle
    {
	  RcCommand.set(RC_ROLL,RcData.get(RC_ROLL));
	  LED.set(RED,OFF);
	  LED.set(BLUE,OFF);
    }
  }
}


//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here

	LED.flightStatus(ACTIVATE);

}
```



