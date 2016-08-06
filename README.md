# Pelco D and Pelco P Telemetry Decoder (node-pelcod-decoder)

This module reads Pelco D and Pelco D CCTV Camera Pan/Tilt/Zoom data, validates each command and decodes its meaning.
The descripion of each command is written to the console. The Pelco D and Pelco P commands decoded include  
  * Camera Number
  * Pan  (direction and speed)
  * Tilt (direction and speed)
  * Zoom (Tele/In and Wide/Out)
  * Manual Focus (Near and Far)
  * Manual Iris (Open and Close)
  * Store Preset / Goto Preset / Clear Preset
  * Set Auxiliary (Turn On) / Clear Auxiliary (Turn Off)
  * Start Learning Pattern (Tour) / Stop Learning Pattern (Tour) / Run Pattern (Tour)
  * Set Zoom Speed

# Baud Rates
Pelco D telemery is always 7 bytes long and always starts with 0xFF. On a Pelco KBD300A Pelco D runs at 2400 baud 8-N-1 with 4800 and 9600 also common on other installations.

Pelco P telemetry is always 8 bytes long and starts with 0xA0. Pelco P often runs at 4800 baud 8-N-1 with 2400 and 9600 also common on other installations.

# Stream Sources
The module processes data from a NodeJS Buffer object. A small example program, read_from_serial.js, will read from a Serial Port / COM Port (using node-serial) and pass data into the Pelco D and Pelco P Decoder.

# Future Enhancements
A future enhancement would be to use an I/O module to drive motors or relays.
Another enhancement would be to output a new Pan/Tilt/Zoom telemetry command in a different protocol format to drive other makes of camera (ie a protocol converter)
Another would be to formally support BBV Telemetry. This is identical to Pelco P but the STX and ETX are 0xB0 and 0xBF but have no test hardware.

# Pelco D Testing
The code has been tested with Pelco D telemetry generated by
 * Official Pelco KBD300A Keyboard (Rev A0, Ver 5.7)in Direct D mode 2400 baud 8-N-1 SW1-SW8: UP-UP-UP-UP-down-UP-down-UP
 * Bosch Universal Camset CCTV Engineer Tool
 * NodeJS Pelco D Generator https://github.com/Scoup/node-pelcod
 * ISpyConnect http://www.ispyconnect.com/

# Pelco P Testing
The code has been tested with Pelco P telemetry generated by
 * Official Pelco KBD300A Keyboard (Rev A0, Ver 5.7)in Direct P mode 4800 baud 8-N-1 SW1-SW8: UP-UP-UP-UP-down-UP-UP-UP
 * Bosch Universal Camset CCTV Engineer Tool
 * Sample byte strings from Commfront

