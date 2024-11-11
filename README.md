# Temperature-Control-Library

Task 1:
Create a PLC program for Temperature Control in any PLC programming language of your choice. The system consist of Heater and Temp. sensor. The Program should work as follows:
If Heater is ON (TRUE), the temperature (Float variable) increases linearly at the rate of 0.5°C/second
If Heater is OFF (FALSE), the temperature (Float variable) decreases linearly at the rate of 0.25°C/second
The Temperature should stay within the limit of 0 ~ 100°C

Task 2:
Create a PLC program for Liquid level Control in any PLC programming language of your choice. The system consist of Fill valve, drain valve and liquid level sensor. The Program should work as follows:
If Fill valve is ACTIVATED (0 ~ 10V), the Level (Float variable) increases proportional to the opening of Fill valve.
If Drain valve is ACTIVATED (0 ~ 10V), the Level (Float variable) decreases proportional to the opening of Drain valve.
The Level should stay within the limit of 0 ~ 100%
When the Level is more than 80%, there should be HIGH LEVEL alarm (bool variable) and if the Level is less than 20%, there should be LOW LEVEL alarm (bool variable) 
Case 1: If Fill valve is 100% open and Drain valve is 100% closed. The level should increases with the rate of 10% per second
Case 2: If Fill valve is 0% open and Drain valve is 100% open. The level should decreases with the rate of 10% per second
Case 3: If Fill valve is 50% open and Drain valve is 50% open. The level should not change
Case 4: If Fill valve is 25% open and Drain valve is 50% open.  The level should decreases with the rate of 2.5% per second
Case 5: If Fill valve is 50% open and Drain valve is 25% open.  The level should increases with the rate of 2.5% per second
and so on...
