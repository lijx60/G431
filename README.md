# G431
Examples based on G431 development
This project is about driving HC_RS04,it is a Ultrasonic ranging module.

We need to add these codes in the main.c after generating code by STM32CubeMx:
#include "stdio.h"

while (1)
  {
		
		HAL_GPIO_WritePin(GPIOA, trig_Pin, GPIO_PIN_SET);
		delay_us(15);
		HAL_GPIO_WritePin(GPIOA, trig_Pin, GPIO_PIN_RESET);
		while(!(HAL_GPIO_ReadPin(echo_GPIO_Port,echo_Pin)));
		count=0;
		while(HAL_GPIO_ReadPin(echo_GPIO_Port,echo_Pin))
		{
		   count ++ ;			
		}
		printf("count=%d\r\n",(count*17)/10000 );
		HAL_GPIO_TogglePin(GPIOA, LD2_Pin);
    HAL_Delay(1500);
  }
  
