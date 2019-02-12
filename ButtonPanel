#include <Joystick.h> //libary: https://github.com/MHeironimus/ArduinoJoystickLibrary

Joystick_ Joystick;

class Button
{
  int pin;
  bool currentState;
  bool lastState;
  public:

    Button(int pin)
    {
      this -> pin = pin;
      pinMode(pin, INPUT);
    }

    void update() //update the states of the button
    {
      lastState = currentState;
      currentState = digitalRead(pin);
    }

    bool getCurrentState()
    {
      return currentState;
    }

    bool getLastState()
    {
      return lastState;
    }
 
};
void setup() 
{

  // Initialize Joystick Library
  Joystick.begin();
}


//List the buttons to be used
const int numberOfButtons = 9;

Button buttons[numberOfButtons] = { //initizilze buttons to corisponding pins
  Button(13),
  Button(12),
  Button(11),
  Button(10),
  Button(9),
  Button(8),
  Button(7),
  Button(6),
  Button(5)
};

void loop() 
{
  // Read pin values the check if the value of the button has chnage if it has pass it trough the joystick api
  
  for (int index = 0; index < numberOfButtons ; index++)
  {
    buttons[index].update();
    if (buttons[index].getCurrentState() != buttons[index].getLastState())
    {
      Joystick.setButton(index, buttons[index].getCurrentState()); //pass the value of the button to the joystick
    }
  }

  delay(20); //teleop periodic is called every 20ms so might as well wait
}
