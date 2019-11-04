# ACRO MODE

```text
// Do not remove the include below
#include "PlutoPilot.h"
#include "Estimate.h" //gives access to drone rates, angles,velocities, positions
#include "utils.h" //gives you access to the LED,graphs, print
#include "User.h"

//The setup function is called once at Pluto's hardware startup
void plutoInit()
{
// Add your hardware initialization code here
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
	FlightMode.set(RATE);
	LED.set(RED, OFF);
    LED.set(GREEN, ON);
}


//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here
	LED.flightStatus(ACTIVATE);

}
```



