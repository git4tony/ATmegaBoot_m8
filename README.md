ATmega8 internal-RC 8.000MHz
LFUSE 0xC4
HFUSE 0xCA

#program bootloader using usbasp
avrdude -p m8 -c usbasp -B 4 -U lfuse:w:0xc4:m -U hfuse:w:0xca:m -U flash:w:$(PROGRAM).hex:i

#program application using arduino
avrdude -p m8 -c arduino -P /dev/ttyUSB0 -b 19200 -U flash:w:main.hex:i
