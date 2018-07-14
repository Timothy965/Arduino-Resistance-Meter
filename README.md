# Arduino-Resistance-Meter

1)Introduction:
1.1)Resistors are important electronic components that are used to oppose the flow of current. And hence, Resistance is the property of a material which opposes the flow of current through it. Resistors are of different values and hence to find the value we use device like Multimeter. But this repository shows how to build an Arduino Resistance Meter.

2)Harware/ Components Needed:

2.1)       *Arduino Uno
           *Breadboard
           *3x Jumper Wires(Male-Male)
           *2x different Value Resistors
 
2.2) For the Resistors, we must know the value of either 1 of the resistor, and unknown value of the other resistor.

3)Connection/Wiring:

3.1) For this device, we will be using the pins 5V, GND and one of the Analog pins of arduino.

3.2)Connect the Jumper Wires from Arduino Analog Pin 3 to breadboard, 5v from Arduino to breadboard and GND from Arduino to breadboard.

3.3)Connect the known value resistor between Analog Pin 3 and GND, and the unknown value resistor between Analog Pin 3 and 5V (Look In fig 1.1 for connecting resistors to breadboard).

4)Programming and Code

4.1)For this repository, I am going to use 100Ω resistor, and therefore my float R1= 100[instead of 100, enter the value of your resistor in digits, for example a 10KΩ will be 10000]

4.2)Let the value of our unknown resistor[R2] be 0.

4.3)Code: Copy the code to Arduino IDE and upload it.

     int analogPin= 3; //read Analog pin 3
     int raw= 0;
		 int Vin= 5;
     float Vout= 0;
     float R1= 100;   //Value of Known Resistor
     float R2= 0;     //Unknown Value constant
     float buffer= 0;
    void setup()
    {
    Serial.begin(9600);
    }
    void loop()
		{
    raw= analogRead(analogPin);
    if(raw) 
		{
    buffer= raw * Vin;
    Vout= (buffer)/1024.0;
    buffer= (Vin/Vout) -1;
    R2= R1 * buffer;
    Serial.print("Vout: ");
    Serial.println(Vout);
    Serial.print("R2: ");
    Serial.println(R2);
    delay(10000);
    }
    }

5) Output/Readings:

5.1) The program sets up analog pin A0 to read the voltage between the known resistor and the unknown resistor. You can use any other analog pin though, just change the pin number in line 31, and wire the circuit accordingly.

5.2)After uploading the code to Arduino, open the serial monitor[top right] of your Arduino IDE software. When you open up the serial monitor you’ll see the resistance values printed once per 10 seconds. There will be two values, R2 and Vout.
       
    R2: is the resistance of your unknown resistor in Ohms.
    Vout: is the voltage drop across your unknown resistor.
