# Calculator and Unit Converter
This is a project was made with Vue. It consists of a calculator and a unit converters.

## Calculator 
This is a simple calculators where you can use basic operators (+ - * /). My goal was to be able to write out multiple calculation at the same time, where a typical calculator does one calculation at the time. Example of multiple calculations: 2 + 2 * 8 - 1. It does the calculation from left to right.

### Features  
- The user input is pushed into an array and it's calculation is done with the array-method reduce(). 
- If you try to calculate an invalid calculation you get an 'Error'-message. Example: 8 * - / // 'Error'
- When the calculation is 0 or you've gotten an 'Error'-message and you start inputting new numbers, the 0 / 'Error'-message is removed automatically.   

## Converter 
I've made a converter consisting of two, one for length and another for weight. 

### Features  
- Input both sides.
- When you change units it will update the conversion.
