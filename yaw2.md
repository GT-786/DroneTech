# Yaw2

```text
// Do not remove the include below
#include "PlutoPilot.h"
#include "Estimate.h" //gives access to drone rates, angles,velocities, positions
#include "utils.h"
#include "User.h"
#include "Control.h"
int16_t x=0;

//The setup function is called once at Pluto's hardware startup
void plutoInit()
{
// Add your hardware initialization code here
}


//The function is called once before plutoLoop when you activate Developer Mode
void onLoopStart()
{
  // do your one time stuff here

	LED.flightStatus(DEACTIVATE); //disable LED function

}


// The loop function is called in an endless loop
void plutoLoop()
{

//Add your repeated code here
x=App.getAppHeading();
Monitor.println("Yaw Readings are=",x);

//doing +100 bcz the variation is coming for my phone, for different phones the reading is different
x+=100; //error correction to find difference between phone and drone heading

int16_t reading=Angle.get(AG_YAW);
Monitor.println(" Readings are=",reading);

int16_t Diff=reading-x;
Monitor.println("Difference in Readings are=",Diff);


if(x>360)
x-=360;

LED.set(BLUE,ON);
LED.set(RED,ON);

DesiredAngle.set(AG_YAW,x); //set drone heading same as that of phone

}


//The function is called once after plutoLoop when you deactivate Developer Mode
void onLoopFinish()
{

// do your cleanup stuffs here

	LED.flightStatus(ACTIVATE);
}
```

