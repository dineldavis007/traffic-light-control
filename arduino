#define RED_LED 3
#define YELLOW_LED 4
#define GREEN_LED 5
#define BUZZER 6

String command = "";

void setup() {

  Serial.begin(9600);

  pinMode(RED_LED, OUTPUT);
  pinMode(YELLOW_LED, OUTPUT);
  pinMode(GREEN_LED, OUTPUT);
  pinMode(BUZZER, OUTPUT);

  allOff();

  Serial.println("SYSTEM READY");
}

void loop() {

  if (Serial.available()) {

    command = Serial.readStringUntil('\n');

    command.trim();

    // RED
    if (command == "RED") {

      trafficLight(RED_LED);

      Serial.println("ACK:RED");
    }

    // YELLOW
    else if (command == "YELLOW") {

      trafficLight(YELLOW_LED);

      Serial.println("ACK:YELLOW");
    }

    // GREEN
    else if (command == "GREEN") {

      trafficLight(GREEN_LED);

      Serial.println("ACK:GREEN");
    }

    // STANDARD CHECK
    else if (command == "CHECK") {

      standardCheck();

      Serial.println("ACK:CHECK_COMPLETED");
    }

    else {

      Serial.println("ERROR:INVALID_COMMAND");
    }
  }
}

// =========================
// STANDARD CHECK
// =========================
void standardCheck() {

  trafficLight(RED_LED);

  delay(500);

  trafficLight(YELLOW_LED);

  delay(500);

  trafficLight(GREEN_LED);

  delay(500);
}

// =========================
// TRAFFIC LIGHT FUNCTION
// =========================
void trafficLight(int ledPin) {

  allOff();

  digitalWrite(ledPin, HIGH);

  // Buzzer sounds 2 times
  for (int i = 0; i < 2; i++) {

    tone(BUZZER, 1000);

    delay(300);

    noTone(BUZZER);

    delay(300);
  }

  delay(1000);

  digitalWrite(ledPin, LOW);
}

// =========================
// TURN EVERYTHING OFF
// =========================
void allOff() {

  digitalWrite(RED_LED, LOW);
  digitalWrite(YELLOW_LED, LOW);
  digitalWrite(GREEN_LED, LOW);

  noTone(BUZZER);
}
