---
title: "HTS221 Sensor"
permalink: /docs/apis/hts221/
excerpt: "Library for HTS221 humidity and temperature sensor on AZ3166"
last_modified_at: 2017-06-28T00:01:52-04:00
---

The [ST HTS221](http://www.st.com/en/mems-and-sensors/hts221.html){:target="_blank"} is a sensor for relative humidity and temperature.

The `HTS221Sensor` class provides methods to read and write data, set configuration of HTS221 sensor.

## Assembly

HTS221Sensor.h

## Summary

| Types |
| :---- |
| [DevI2C](#devi2c) |
| [PinName](#pinname) |

| Constructors |
| :----------- |
| [HTS221Sensor](#hts221sensor) - `HTS221Sensor(DevI2C &i2c)` |
| [HTS221Sensor](#hts221sensor-1) - `HTS221Sensor(DevI2C &i2c, unsigned char address)` |

| Methods |
| :------ |
| [init](#init) - `int init(void *init)` |
| [enable](#enable) - `int enable(void)` |
| [disable](#disable) - `int disable(void)` |
| [readId](#readid) - `int readId(unsigned char *id)` |
| [reset](#reset) - `int reset(void)` |
| [getHumidity](#gethumidity) - `int getHumidity(float* pfData)` |
| [getTemperature](#gettemperature) - `int getTemperature(float* pfData)` |
| [getOdr](#getodr) - `int getOdr(float* odr)` |
| [setOdr](#setodr) - `int setOdr(float odr)` |

## Types

### DevI2C

> Provides functions for multi-register I2C communication.

### PinName

> Provides the mapping of mbed DIP and LPC Pin Names.

## Constructors

### HTS221Sensor

```cpp
HTS221Sensor(DevI2C &i2c)
```

> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | DevI2C & | i2c | The object of an helper class which handles the I2C peripheral. |

### HTS221Sensor

```cpp
HTS221Sensor(DevI2C &i2c, unsigned char address)
```

> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | DevI2C & | i2c | The object of an helper class which handles the I2C peripheral. |
> | unsigned char | address | The address of the component's instance. |

## Methods

### init

```cpp
int init(void *init)
```

> Initializing the component.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | void * | init | Pointer to device specific initalization structure. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### enable

```cpp
int enable(void)
```

> Enable HTS221.
> 
> #### Parameters
> 
> None.
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### disable

```cpp
int disable(void)
```

> Disable HTS221.
> 
> #### Parameters
> 
> None.
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### readId

```cpp
int readId(unsigned char *id)
```

> Read ID address of HTS221.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | unsigned char * | id | The pointer where the ID of the device is stored. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### reset

```cpp
int reset(void)
```

> Reboot memory content of HTS221.
> 
> #### Parameters
> 
> None.
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### getHumidity

```cpp
int getHumidity(float *pfData)
```

> Read HTS221 output register, and calculate the humidity.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | float * | pfData | The pointer to data output. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### getTemperature

```cpp
int getTemperature(float *pfData)
```

> Read HTS221 output register, and calculate the temperature.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | float * | pfData | The pointer to data output. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### getOdr

```cpp
int getOdr(float *odr)
```

> Read HTS221 output register, and calculate the humidity.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | float * | odr | The pointer to the output data rate. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

### setOdr

```cpp
int setOdr(float odr)
```

> Set ODR.
> 
> #### Parameters
> 
> | Type | Name | Description |
> | :--- | :--- | :---------- |
> | float | odr | The output data rate to be set. |
> 
> #### Return value
> 
> | Type | Description |
> | :--- | :---------- |
> | int | Result code, 0 in case of success, an error code otherwise. |

## Sample code

```cpp
#include "HTS221Sensor.h"
DevI2C *i2c;
HTS221Sensor *sensor;
float humidity = 0;
float temperature = 0;
unsigned char id;
void setup() {
    i2c = new DevI2C(D14, D15);
    sensor = new HTS221Sensor(*i2c);
    // init the sensor
    sensor -> init(NULL);
}
void loop() {
    // enable
    sensor -> enable();
    // read id
    sensor -> readId(&id);
    Serial.printf("ID: %d\r\n", id);
    // get humidity
    sensor -> getHumidity(&humidity);
    Serial.print("Humidity: ");
    Serial.println(humidity);
    // get temperature
    sensor -> getTemperature(&temperature);
    Serial.print("Temperature: ");
    Serial.println(temperature);
    // disable the sensor
    sensor -> disable();
    // reset
    sensor -> reset();
    delay(1000);
}
```
