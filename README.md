# NAME:SOUNDARYA J
# REG NO:212223220108
# DATE: 29.8.2025


# Experiment: Binary Counter using Switch, Seven Segment and Arduino Uno
# Aim:
To design and simulate a binary counter using an Arduino Uno, push button switch, and seven-segment display. The counter should increment its value on each button press and display the count (0–9) on the seven-segment display.
# Components Required:
Arduino Uno,Proteus
# Procedure:
1.Connect Arduino Uno, push button, and seven-segment display in Proteus as per connection diagram.<br>
2.Upload the Arduino program in Arduino IDE and compile.<br>
3.Load the generated .hex file into the Arduino Uno in Proteus.<br>
4.Run simulation → Press the push button → Observe the count increments (0 → 9).
# Program:
```
int segPins[] = {13,12,11,10,9,8,7}; 
int buttonPin = 2;
int count = 0;
bool lastButtonState = HIGH;
byte digits[10][7] = {
  {1,1,1,1,1,1,0}, 
  {0,1,1,0,0,0,0}, 
  {1,1,0,1,1,0,1}, 
  {1,1,1,1,0,0,1}, 
  {0,1,1,0,0,1,1}, 
  {1,0,1,1,0,1,1}, 
  {1,0,1,1,1,1,1}, 
  {1,1,1,0,0,0,0}, 
  {1,1,1,1,1,1,1}, 
  {1,1,1,1,0,1,1}  
};

void setup() {
  for(int i=0; i<7; i++) {
    pinMode(segPins[i], OUTPUT);
  }
  pinMode(buttonPin, INPUT_PULLUP); 
  displayDigit(count);
}

void loop() {
  bool buttonState = digitalRead(buttonPin);

  if (lastButtonState == HIGH && buttonState == LOW) {
    count++;
    if (count > 9) count = 0;
    displayDigit(count);
    delay(200); // debounce
  }
  lastButtonState = buttonState;
}

void displayDigit(int num) {
  for (int i=0; i<7; i++) {
    digitalWrite(segPins[i], digits[num][i]);
    }
}
```
# Circuit diagram:
<img width="1036" height="615" alt="image" src="https://github.com/user-attachments/assets/13a62b8c-e57f-4a95-822f-cdc6c674598f" />

# Output:
<img width="812" height="562" alt="Screenshot 2025-08-29 104249" src="https://github.com/user-attachments/assets/be43aa6b-c9e3-4b99-8cbd-0478e3de57ea" />

<img width="1059" height="589" alt="Screenshot 2025-08-29 104215" src="https://github.com/user-attachments/assets/fdc4c84c-4e03-4a4a-aa23-3232d40eab7a" />

<img width="893" height="603" alt="Screenshot 2025-08-29 104236" src="https://github.com/user-attachments/assets/94356499-020f-425a-8234-fbf88b28c116" />


# Result:
Thus,Binary Counter using Switch, Seven Segment and Arduino Uno is done successfully.





