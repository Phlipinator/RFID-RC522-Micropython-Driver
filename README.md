# RFID with a Raspberry Pi Pico

This library can be used to interface with the RC522 RFID module using Micropython.
This is a fork from <https://github.com/kevinmcaleer/pico-rfid>, so all credit belongs there.
I changed the code slightly ro make the read, create and erase functions usable as importable libraries.

## Wiring

The Raspberry Pi Pico connects to the RC522 module via the SPI interface. The default PinOut are provided below:

| RFID Reader | Raspberry Pi Pico Pin |
| ----------- | --------------------- |
| SDA         | GP1                   |
| SCK         | GP2                   |
| MOSI        | GP3                   |
| MISO        | GP4                   |
| RST         | GP0                   |

---

The Pins can be changed to work with other microcontrollers. Just look for this line in the three files read, create and erase:

```python
reader = MFRC522(spi_id=0, sck=2, miso=4, mosi=3, cs=1, rst=0)
```

## Example Usage

```python
import read
import erase
import create

# Erase a card
erase.main()

# Create a new Card
create.main()

# Read a Card and have the ID returned
print(str(read.main()))
```

## STL files for 3d printing the case

There are two files: [`Top.stl`](Top.stl) and [`Bottom.stl`](bottom.stl) that you can print out to encase the RC522 module.
