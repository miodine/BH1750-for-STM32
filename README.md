# BH1750 for STM32 (yet-another)
Simple library for handling the communication with the BH1750 sensor for STM32 microcontrollers. 
Intended to use within the STM32Cube IDE. 

## Examplary usage
In the appropriate section of the code, initialise the sensor in the following way:
```c

/* USER CODE BEGIN 2 */
BH1750_Data sensor = BH1750_Init(CONT_HI_RES, ADDR_0V, &hi2c1);
/* USER CODE END 2 */

```

BH1750_Data holds the information about sensor operating mode, status flag, and a pointer 
to the I2C handle responsible for communication with the sensor (hi2c1 in this case). The middle
argument is the addres of the sensor (adjust accordingly to the connection of the ADDR pin on the 
module - if it's connected to the ground - its addres is 0x23, otherwise its address is 0x5c")

Then, read out the data transmitted by the sensor through I2C in the following way ( in this example - each 2 seconds, in the 
program loop):

```c

/* USER CODE BEGIN WHILE */
while (1)
{
HAL_Delay(200);
result = BH1750_Read(&sensor);
/* USER CODE END WHILE */
```

the 'result' variable is predefined, and of float type.
