# Throw And Go

```text

// Do not remove the include below
#include "PlutoPilot.h"
#include "Sensor.h"
#include "utils.h"
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

	LED.flightStatus(DEACTIVATE); //disable LED behaviuour


}



// The loop function is called in an endless loop
void plutoLoop()
{

//Add your repeated code here
	int16_t readings =Acceleration.get(Z);
	Monitor.println("Acceleration readings are=",readings);

	if((readings<0)&&(!FlightStatus.check(FS_CRASHED)))
	{
		Command.arm();
		Monitor.println("Pluto Is Armed!!!!");
		LED.set(GREEN, ON);

	}
}



//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here

	LED.flightStatus(ACTIVATE);

}
```



![Result](.gitbook/assets/ezgif.com-video-to-gif1.gif)

