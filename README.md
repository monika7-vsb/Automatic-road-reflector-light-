# Automatic-road-reflector-light-#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <wiringPi.h>


#define

void setup() {
    wiringPiSetup();
    pinMode(LDR_PIN, INPUT);
    pinMode(RELAY_PIN, OUTPUT);
}

int getLightLevel() {
    // Read analog value from LDR sensor (0-1023)
    return analogRead(LDR_PIN);
}

void loop() {
    int lightLevel = getLightLevel();
    printf("Light Level: %d\n", lightLevel);

    if (lightLevel < LIGHT_THRESHOLD) {
        // Turn LED lights on
        digitalWrite(RELAY_PIN, HIGH);
        printf("LEDs On\n");
    } else {
        // Turn LED lights off
        digitalWrite(RELAY_PIN, LOW);
        printf("LEDs Off\n");
    }

    delay(1000); // Check light level every 1 second
}

int main() {
    setup();
    while (1) {
        loop();
    }
    return 0;
}
