# Lightpets-flashpets
Demonstration of the system assembled on an Arduino and programmed with the Christmas tree blinker
 
    // C++ code
    //
    #include <Adafruit_LiquidCrystal.h>
    Adafruit_LiquidCrystal lcd_1(0);
    int pir = 3;
    int LEDbranco = 2;
    int readpir = 0;
    int ledvermelho = 4;
    int ledamarelo = 5;
    int ledazul = 6;
    int ledverde = 7;
    int ledvermelho2 = 8;
    int randomnumber = 0;
    int som = 8;
    bool felizNatalExibida = false;
    
    
    void setup()
    {
      pinMode(pir, INPUT);
      pinMode (LEDbranco, OUTPUT);
      pinMode(ledvermelho, OUTPUT);
      pinMode(ledamarelo, OUTPUT);
      pinMode(ledazul, OUTPUT);
      pinMode(ledverde, OUTPUT);
      pinMode(ledvermelho2, OUTPUT);
      pinMode(som, OUTPUT);
      lcd_1.begin(16, 2);
    }
    void loop()
    {
     if (!felizNatalExibida){
         lcd_1.clear();
         lcd_1.print("Feliz Natal");
         felizNatalExibida = true;
      }
      randomnumber = random(0, 500);
        if (randomnumber == 4) {
           digitalWrite(ledvermelho, HIGH);
           digitalWrite(ledamarelo, LOW);
           digitalWrite(ledazul, LOW);
           digitalWrite(ledverde, LOW);
      }
      else if (randomnumber == 1) {
          digitalWrite(ledazul, HIGH);
          digitalWrite(ledvermelho, LOW);
          digitalWrite(ledamarelo, LOW);
          digitalWrite(ledverde, LOW);
      }
      else if (randomnumber == 2) {
      
      digitalWrite(ledverde, HIGH);
           digitalWrite(ledvermelho, LOW);
         digitalWrite(ledamarelo, LOW);
            digitalWrite(ledazul, LOW);
    }
    else if (randomnumber == 3) {
         digitalWrite(ledamarelo, HIGH);
          digitalWrite(ledvermelho, LOW);
          digitalWrite(ledazul, LOW);
       digitalWrite(ledverde, LOW);
    }
    //digitalWrite(ledazul, HIGH);
    //digitalWrite(ledvermelho, HIGH);
    //digitalWrite(ledamarelo, HIGH);
    //digitalWrite(ledverde, HIGH);
    readpir = digitalRead(pir);
    if (readpir == HIGH){
      digitalWrite(som, HIGH);
      felizNatalExibida = false;
      randomnumber = 0;
      lcd_1.clear();
      lcd_1.print("Animal");
      lcd_1.setCursor(0, 1);
      lcd_1.print("Detectado!");
      digitalWrite(LEDbranco, HIGH);
      digitalWrite(ledvermelho, LOW);
      digitalWrite(ledamarelo, LOW);
      digitalWrite(ledazul, LOW);
      digitalWrite(ledverde, LOW);
      digitalWrite(ledvermelho2, LOW);
      delay(500);
    }
    else{
     digitalWrite(LEDbranco, LOW);
    }
  }
