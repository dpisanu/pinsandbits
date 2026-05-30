# Notes: Waveshare ESP32-S3-Matrix

## Interrupt pin notes

Online documentation often mentions GPIO13 instead of GPIO10 as the QMI8658 interrupt pin. 

## LED brightness warning

⚠️ Do not run the 8×8 LED matrix at high brightness for long periods. ⚠️

Waveshare **explicitly** warns that excessive LED brightness can cause the board temperature 🌡️ to rise rapidly and may damage the board.

Current tests use relatively limited brightness values:

- Red test: 40%
- White test: 30%
- RGB sweep: 5%
