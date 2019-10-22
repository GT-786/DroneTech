# exp baro graph

```text

// Do not remove the include below
#include "PlutoPilot.h"
#include "Sensor.h"
#include "utils.h"

int32_t initialreading;
int32_t currentreadings;
int32_t finalreading;



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
	initialreading =Barometer.get(PRESSURE);
	Monitor.println("initial readings are=",initialreading);


}



// The loop function is called in an endless loop
void plutoLoop()
{

//Add your repeated code here
	currentreadings =Barometer.get(PRESSURE);
	Monitor.println("current readings are=",currentreadings);

	finalreading=initialreading - currentreadings;
	Monitor.println("final readings are=",finalreading);

	Graph.red(finalreading, 3);
}



//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here

	LED.flightStatus(ACTIVATE);

}





```

