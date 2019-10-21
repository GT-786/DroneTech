# Code Structure Of Pluto X

* void plutoInit\(\)

The setup function is called once at Pluto's hardware startup. 

Add your hardware initialization code here.

* void onLoopStart\(\)

The function is called once before plutoLoop when you activate Developer Mode.

One should do their one time stuff here. 

* void plutoLoop\(\)

The loop function is called in an endless loop.

 Add your repeated code here.

* void onLoopFinish\(\)

The function is called once after plutoLoop when you deactivate Developer Mode.

Do your cleanup stuffs here.



