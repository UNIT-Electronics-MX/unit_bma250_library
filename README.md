# UBMA250 library

Arduino library for the **Bosch BMA250 Accelerometer**, maintained by [Unit Electronics](https://www.uelectronics.com/).

## UBMA250 Class

### Initialization

* **int begin(uint8_t range, uint8_t bandwidth)** Legacy I2C initialization (backward compatible). Input the *range* (±2/±4/±8/±16g) and low-pass filter *bandwidth*.
* **int beginI2C(uint8_t range, uint8_t bandwidth, uint8_t i2c_addr = 0x18)** I2C initialization with optional custom address.
* **int beginSPI(uint8_t range, uint8_t bandwidth, uint8_t cs_pin, SPIClass\* spi = &SPI)** SPI initialization with chip-select pin and optional SPI instance.

```cpp
#include "BMA250.h"

UBMA250 accel;

void setup() {
    accel.beginI2C(BMA250_range_2g, BMA250_update_time_64ms);
}

void loop() {
    accel.read();
    Serial.println(accel.X);
}
```

### Public Variables

| Variable | Type | Description |
|----------|------|-------------|
| `X` | int16_t | X-axis acceleration |
| `Y` | int16_t | Y-axis acceleration |
| `Z` | int16_t | Z-axis acceleration |
| `tempC` | int8_t | Temperature in degrees Celsius |
| `rawTemp` | int8_t | Raw temperature register value |
| `I2Caddress` | uint8_t | Detected I2C address |

## Range Constants

`BMA250_range_2g`, `BMA250_range_4g`, `BMA250_range_8g`, `BMA250_range_16g`

## Bandwidth Constants

`BMA250_update_time_64ms`, `BMA250_update_time_32ms`, `BMA250_update_time_16ms`, `BMA250_update_time_8ms`, `BMA250_update_time_4ms`, `BMA250_update_time_2ms`, `BMA250_update_time_1ms`, `BMA250_update_time_05ms`

## License

See [License.h](License.h) for license information.
