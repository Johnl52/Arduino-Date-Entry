The original sketch I started with I got off ofthe Arduino forum as a way to read serial data.

The keybord goes to Serial port 1 "Serial1", I leave port 0 for the serial monitor.

Those are the two functions
		recvWithEndMarker();
    		showNewData();

The original loop just just kept call those. you typed on the keyboard, hit enter and it would print in the serial monitor

What I want to do is have several fields on a screen, you touch the field you want to update, type in the value, press enter, and it displays.
I want to use the recvWithEndMarker() with each field, date. name, ID Number and so on.

This sketch only has one field "Date" The touch area is defined with the statement 
	// Detect Date pressed
	if ((p.x>=387) && (p.x<=475) && (p.y>=158) && (p.y<=318)) 

What happens now is if I type something before touching the date field, then touch the date, what I had type is displayed
So I need to clear the serial buffer. I tried putting the statement "Serial1.read()" when it first goes into the fuction but that didn't seem to work
or it may have but the rest of the funtion didn't. I tried adding another while loop to wait for something to be typed
		while (Serial.available==0) 
then when a key is pressed it should have dropped out of that and into the existing while
		while (Serial1.available > 0)

I think my while loops were fighting each other

That's what needs to happen
	clear the buffer
	wait for a key to be pressed
	read what was typed until the enter key is pressed

Maybe that logic needs to come out of the while loop and in a if/else. I know what I want it to do I'm just having troubles figuring out how to.

A couple of other questions

1. do I declare the variable "CurrentDate" as a char or a char array?
2. to have the function put the value into that variable would I use this statement ?CurrentDate = recvWithEndMarker()"? 

The funtion "showNewData()" is just to see what is going on, after I get the function and call working it wont be needed




