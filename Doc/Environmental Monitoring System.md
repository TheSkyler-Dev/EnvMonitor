This document outlines hardware requirements, characteristics and cost for this Project. Below you'll find said information.

## Stage 1: Environmental sensing node(s)

**This section aims to outline the hardware needed for this stage, its characteristics and potential cost.**

### 1. Required Hardware
Here, an outline of hardware components needed for this module are listed.

- Micro controller: [Arduino Nicla Sense ME](https://store.arduino.cc/products/nicla-sense-me?_pos=3&_psq=ABX00051+OR+ABX00050+OR+AFX00006+OR+AFX00005+OR+AFX00007&_ss=e&_v=1.0) (best option), ESP32 (cost effective)
- Display: OLED Display (such as [SSD1351](https://www.berrybase.de/waveshare-1-27-rgb-oled-displaymodul-128-96-aufloesung-262k-farben-spi-schnittstelle))
- Environmental sensor: seeed Grove [SCD41](https://www.berrybase.de/seeed-grove-co2-temperature-feuchtigkeits-sensor-scd41) (only if ESP32 is used)
- Loudness sensor: [seeed Loudness sensor](https://www.berrybase.de/seeed-grove-sensor-fuer-lautstaerke) (LM2904-based)
- OPTIONAL: [Adafruit STEMMA speaker](https://www.berrybase.de/adafruit-stemma-verstaerker-und-lautsprecher) (if audible alarm functionality is needed)

#### Further Hardware considerations
Considering its primary use in office environments, the necessity of a screen should be evaluated further. It is generally considered best practice to avoid the addition of screens to the nodes to ensure discreetness. Alternative output options should be explored, **such as LED indicators** (Green for good air quality, yellow for moderate air quality and red for poor air quality). This would **significantly reduce the footprint of the nodes and make it more discreet while still communicating data in a very simple way**. The omission of a display would also reduce overall cost of each node.

### 2. Hardware Characteristics
Here's an outline of hardware specs of the components named above:

- Micro controller: 
	- Nicla Sense ME:
		- ![[Screenshot 2025-06-27 102849.png]]
	- ESP32:
		- See ESP32 [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf#cd-peri-pin-config)
- Display (may not be needed):
	- Operational Voltage: 3.3V / 5V
	- Resolution: 128 x 96 Pixels
	- communication Interface: 3/4-pin SPI
	- Display Size: 25.708 x 19.28mm
	- Display Panel: OLED
	- Pixel Format: 0.047 x 0.185mm
	- Driver: SSD1351
	- Module Size: 42.2 x 29.0mm
	- [More information](http://www.waveshare.com/wiki/1.27inch_RGB_OLED_Module)
- Environmental Sensor (ony for ESP32, Nicla Sense ME has on-board environmental sensors)
	- Operational Voltage: 3.3V / 5V
	- Operational ranges: -10 - +60 °C / 0 - 100% Humidity / 400 - 5000 ppm CO2
	- SCL clock: 100 kHz
	- Communication interface: I2C (Address: 0x62)
	- Dimensions: 10.1 x 10.1 x 6.5mm
- Loudness Sensor:
	- Operational Voltage: 3.5 - 10VDC (external power likely needed)
	- Dimensions: 24 x 20 x 9.8mm
	- Operational Frequency range: 50 - 2000 Hz
	- Sensitivity: -48 up to -66 dB
	- Signal-to-Noise ratio: >58 dB
	- Output Signal: Analog
- (OPTIONAL) Speaker:
	- Operational Voltage: 3 - 5VDC

### 3. Cost Analysis
Here we evaluate the cost of aforementioned components. All prices include VAT.
- ESP32: 0.00 € (already owned, ~5.90 € - 23.30 € if bought new)
- Arduino Nicla Sense ME: 55.30 €
- Display (SSD1351): 21.40 € (may be omitted)
- Environmental sensor (SCD41): 55.60 € (Not needed with Nicla Sense ME)
- Loudness sensor (LM2904): 6.00 €
- (OPTIONAL) Speaker: 6.55 €

Total cost (ESP32 option, with speaker): **89.55 €**
Total cost (ESP32 option without speaker): **83.00 €**
Total cost (ESP32 option with speaker, no display): **68.15 €**
Total cost (ESP32 option without speaker, no display): **61.60 €**
Total cost (Nicla Sense ME option with speaker): **89.25€**
Total cost (Nicla Sense ME option without speaker): **82.70€**
Total cost (Nicla Sense ME option with speaker, no display): **67.85 €**
Total cost (Nicla Sense ME option without speaker, no display): **61.30 €**

As is visible above, the cost difference per node is 30 cents, which may seem minor, but can snowball into considerable savings at scale. with 8 such nodes, overall savings would amount to 2.40 €, 30.00 € with 100 nodes and 300 € with 1000 nodes. 

### 4. Further Considerations
**In this section, further considerations pertaining to the choice of micro controller are outlined.**

Assuming this project is intended to be production-ready or production adjacent, it is important to consider which of the two micro controller options (Nicla Sense ME or ESP32) is most suitable for this module. While ESP32 is decent for **rapid prototyping purposes** and offers decent performance for the scope of this module, it is not designed for production use and is more tailored to use in conjunction with breadboards and jumper wires, which do not provide a dependable or reliable architecture needed in such mission-critical applications. Jumper wires and breadboards are prone to connection instability over time, which can cause additional monetary or time cost due to more intensive maintenance needs. Even in an office environment, with the additional of a potentially larger footprint in volume due to the ends of jumper wires not being bendable. On the other hand, while more expensive, the Arduino Nicla Sense ME is a **production-ready** micro controller tailored for more permanent and robust applications. As outlined in its specs, it already integrates environmental sensors, eliminating the need of an external sensor. for its size, it provides a sufficiently comprehensive I/O, including SPI communication. Additionally, the more solder-focused design makes it more readily possible to bend cables as needed to achieve as lean of a device as possible.

**Break-even analysis**: The maintenance cost (in time commitment) for the ESP32 variant (no speaker, no display) would break-even after a total of **approximately 3 hours and 37 minutes of maintenance time, after roughly 5 hours and 17 minutes for the ESP32 variant with all listed additional components**. Assuming frequent maintenance due to connection weakness or other potential issues associated with rapid prototyping approaches, these break even times would likely be reached rather quickly. Please not that the break-even was calculated based on an hourly rate of 17 €. Since wire connections on the Nicla Sense ME are predominantly soldered, while the total break-even time would be similar, the necessity of maintenance would generally be much lower and more infrequent, leading to a much slower break-even due to the more infrequent servicing needs, especially considering reduced potential failure points.

**RECOMMENDATION**: Due to robustness concerns and the mission-critical nature of said module, it is advised to use production-ready hardware such as the Arduino Nicla Sense ME. Additionally, it is recommended to omit the display to ensure a smaller overall footstep of the nodes and make them more discreet, which is desirable in office environments, which is important to reduce distractions and potential surveillance anxiety among office workers, and foster better productivity and mental health. 

## Stage 2: The Master Node/Bridge Node
**Next, we evaluate what we need to build the master/bridge node to which the environmental sensing nodes described in Stage 1 connect for real time communication. We will explore which components are likely needed, take a look at technical specifications of those parts and evaluate the cost of the master/bridge node.

### 1. Hardware
Here, we evaluate what hardware would be needed for the master node.

- Main system: [Arduino Portenta X8](https://store.arduino.cc/products/portenta-x8?_pos=2&_psq=ABX00042+OR+ABX00049+OR+TPX00070+OR+TPX00075&_ss=e&_v=1.0) or [Raspberry Pi 5](https://www.berrybase.de/raspberry-pi-5-4gb-ram) (base spec + Micro SD Card and [27W Power supply](https://www.berrybase.de/raspberry-pi-27w-usb-c-power-supply-netzteil-schwarz)) or [Arduino Portenta H7](https://store.arduino.cc/products/portenta-h7?_pos=4&_psq=M000011+OR+ASX00026+OR+ABX00042+OR+ABX00045&_ss=e&_v=1.0]) or ESP32
- Optionally a display: SSD1351 or other (unless the master node is run in a web server configuration)
- Ethernet interface (Portenta X8/H7 only, already present on RPI5):  [Portenta Vision Shield - Ethernet](https://store.arduino.cc/products/portenta-vision-shield-ethernet?_pos=1&_psq=AVX00039+OR+ASX00031+OR+ASX00027+OR+ASX00021&_ss=e&_v=1.0) 
- Storage: [Raspberry Pi SSD Kit (256 GiB)](https://www.berrybase.de/raspberry-pi-ssd-kit-fuer-raspberry-pi-5-256gb) or [Portenta Max Carrier](https://store.arduino.cc/products/portenta-max-carrier) (includes Ethernet, eliminates need for Portenta vision shield) + mass storage media

#### Further Hardware considerations
The choice of the right core system and overall necessity of this system should be thoroughly evaluates, since this system is meant to receive data from the environmental Sensing Nodes and aggregate it. An existing server system may also be used, but would necessitate a bridge node that can pass the information from the nodes discussed in Stage 1 to the existing server system. It is not recommended to use an ESP32 due to its more rapid prototyping focus and exclusive support for BLE and WiFi, the latter of which is considered too unreliable for mission critical data transfer.

### 2. Hardware Characteristics
Here, we take a look at Hardware specs of the hardware listed above.

- Core System:
	- Arduino Portenta X8:
		- [See Arduino Portenta X8 Datasheet](https://docs.arduino.cc/resources/datasheets/ABX00049-datasheet.pdf)
	- Raspberry Pi 5:
		- 2.4 GHz Quad-core Arm Cortex A76 CPU (64 bit)
		- Dual-band 802.11ac WiFi support
		- Bluetooth 5.0/BLE
	- Arduino Portenta H7: 
		- ![[Screenshot 2025-07-01 092227.png]]
		- ESP32 See Hardware Characteristics in Stage 1 (Not recommended)
- Display (Optional):
	- See Hardware Characteristics in Stage 1
- Communication Module (only for Arduino Portenta, Raspberry Pi has on-board Ethernet)
	- Portenta Vision Shield - Ethernet:
		- Includes a camera and Microphone, Can be omitted in code
	- Portenta Max Carrier
		- ![[Screenshot 2025-07-01 094736.png]]
- Storage: (Portenta Max Carrier has that covered for the Portenta family)
	- Raspberry Pi SSD Kit:
		- Includes 256 GiB M.2 NVMe SSD
		- Has GPIO pass through
		- 16mm Stacking header

### 3. Cost Analysis
In this part, we take a look at the cost of the Master/Bridge node, and its components. all prices include VAT, exclude shipping cost

- Arduino Portenta X8: 223.00 €
- Arduino Portenta H7: 120.80 €
- Raspberry Pi 5 (Base spec: 4 GiB RAM): 62.90 €
- Portenta Vision Shield - Ethernet: 55.00 € (Vision Shield - LoRa: ~65.80 €)
- Portenta Max Carrier: 340.00 €
- Raspberry Pi SSD Kit: 44.90 €

#### Configurations
- Portenta X8 + Portenta Max Shield (web server configuration): **563.00 €**
- Portenta X8 + Vision Shield - Ethernet (BLE/WiFi to Ethernet brdge): **278.00 €**
- Raspberry Pi + SSD kit (web server configuration): **107.80 €**
- Portenta H7 + Vision Shield - Ethernet (BLE/WiFi to Ethernet bridge): **175.80 €**

#### Maintenance Considerations
In terms of maintenance, the configurations listed above all generally have rather low maintenance needs, however the type of maintenance would be different depending on the configuration. The BLE/WiFi bridge have minimum maintenance needs, since they only act as a simple relay between the Environmental Sensing Node(s) and the Data Aggregation Server (assumed already present), therefore virtually no additional maintenance needs would be added. On the other hand, the web server configurations may add a bit more maintenance needs in form of up-time assurance, but also rather minimal, beyond potential system updates.

#### Choice of Configuration
It is recommended to choose the BLE/WiFi to Ethernet bridge configurations, if existing server infrastructure will be used for data aggregation and visualization. If a standalone Master Node with web server capabilities is preferred, the web server configurations are recommended. It is generally recommended to use BLE for better reliability, especially if the WiFi connection in the environment is known to be less than optimal. The BLE/WiFi to Ethernet bridge configuration based on the Arduino Portenta H7 is the most cost effective if existing server infrastructure is used for data processing. Otherwise, the Raspberry Pi-based web server configuration is more cost effective (and most cost effective overall).

### 4. Additional Considerations
One downside of BLE is that it only supports up to 8 simultaneous incoming connections in BLE Central mode. It's worth considering using multiple BLE/WiFi bridge nodes to support more than 8 environmental Sensing Nodes. another option may be LoRa, depending on the desired scale of the system. However, using multiple BLE/WiFi to Ethernet bridges would also come with the benefit of spreading workload across multiple nodes, reducing strain on the individual Bridges, even if data is only sent every 30 - 60 minutes as key data points.