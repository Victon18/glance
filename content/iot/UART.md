# UART
- Universal Asynchronous Receiver/Transmitter
- Hardware that translates between parallel and serial forms
-  Commonly used in conjunction with communication standards such as EIA, RS-232, RS-422 or RS-485

# Protocol
- Each character is sent as
    -  a logic low start bit
    - a configurable number of data bits (usually 7 or 8, sometimes 5)
    - an optional parity bit
    - one or more logic high stop bits
    - with a particular bit timing (“baud”)

# UART Character Reception
- Receiver also verifies that stop bit is ‘1’
    - If not, reports “framing error” to host system
- New start bit can appear immediately after stop bit
    - Receiver will resynchronize on each start bit

# Transmitter/System Handshaking
- System asserts Send and holds it high when it wants to send a byte
- UART asserts Busy signal in response
- When UART has finished transfer, UART de-asserts Busy signal
- System de-asserts Send signal

# Serial Peripheral Interconnect (SPI)
- Another kind of serial protocol in embedded systems (proposed by Motorola)
- Four-wire protocol
    -  SCLK — Serial Clock
    - MOSI/SIMO — Master Output, Slave Input
    -  MISO/SOMI — Master Input, Slave Output
    - SS — Slave Select
    - Single master device and with one or more slave devices
    - Higher throughput than I2C and can do “stream transfers”
    - No arbitration required
- But
    -  Requires more pins
    -  Has no hardware flow control
    -  No slave acknowledgment (master could be talking to thin air and not even know it)
# SPI Basics
- A communication protocol using 4 wires
    - Also known as a 4 wire bus
- Used to communicate across small distances
- Multiple Slaves, Single Master
- Synchronized

# SPI cabpabilities
- Always Full Duplex
    - Communicating in two directions at the same time
    - Transmission need not be meaningful
- Multiple Mbps transmission speed
- Transfers data in 4 to 16 bit characters
- Multiple slaves
    -  Daisy-chaining possible

# SPI Protocol
- Wires:
    - Master Out Slave In (MOSI)-
    - Master In Slave Out (MISO)
    - System Clock (SCLK)
    - Slave Select 1…N
- Master Set Slave Select low
- Master Generates Clock
-  Shift registers shift in and out data

# SPI Wires in Detail
- MOSI – Carries data out of Master to Slave
- MISO – Carries data from Slave to Master
    - Both signals happen for every transmission
- SS_BAR – Unique line to select a slave
-  SCLK – Master produced clock to synchronize data transfer
