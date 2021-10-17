
  Data is the stuff you put into an individual cell in Excel. Data can take many different forms, but in Excel it only comes in five different types. That means that regardless of what you type, paste, or otherwise enter into a cell in Excel, the data you put in that cell can be classified as belonging to one of five distinct data types. These data types are:
  
* A Number
* Text
* A Boolean value (TRUE/FALSE)
* The Error Data Type

  This section is a quick crash course and a link to a short blog post that goes into a little more depth. Being able to understand and identify what kind of a datatype you are working with in any given cell is crucial to understanding how your actions with cutting and pasting data between spreadsheets or manipulating things with formulas works. If you take anything from learning how to clean and process raw data it should be a working knowledge of the concept of datatypes.

* Excel has five data types - Number, Date, Text, Logical or Boolean value, and the Error data type

* A Number data type is just what it says, a number that has been entered into a cell
  * All numbers are represented by a Double-Precision Floating Point value (a really big decimal number with lots of digits after the decimal place).
  * Numbers may contain up to 15 significant digits (exclude zeros on either side of the number).
  * Numbers may be as large as 1.79768 X 10^308 or as small as 2.2250 X 10^-308.
  * The number value is stored in the cell but may not be visible to you as a user. Formatting determines how the number is displayed not what is stored in the cell. You can change the formatting to alter the level of precision of the displayed number. The actual value stored in the cell is not affected by the display format.

* Dates and times are stored as number values. Think of them as a number datatype with a gloss applied on top.
    * Cell entries that look like dates (formatted like 1/1/1900 or Jan, 1900 or 1-1-1900) are automatically converted to a number by excel when entered into a cell, and a formatting is then automatically applied over the number to make it appear as a date
    * Times are stored as fractional parts of days. 1/4 = 1/4th of one day = 24/4 = 6 hours from the beginning of the day, or 6:00 AM
    * The date 1/1/1900 is represented by the number 1, and successive dates are numbered as days since that date.

* Text values are stored as literal "strings" of characters that are specifically designated as text. A "Text" value may consist of numbers, letters, or other characters and is not limited to just letters.
  * To specifically designate a cell as containing Text data rather than a number you would place an apostrophe in front of the value
    * For example '012345 would store the characters 012345 as a text value. Without the apostrophe Excel would interpret this as a number and would drop the leading zero.
  * You can also designate a cell, row, column, or range as containing text by applying formatting to those cells

* Logical Values - A TRUE or FALSE. Logical values can be entered directly into a cell by typing TRUE or FALSE. However, these are most often returned by a formula. For example the formula =ISBLANK(#Ref) will return a logical value of TRUE or FALSE depending on whether the #Ref cell contains a value or does not contain a value

* Error type - Error data types occur when you have an issue with a formula or Excel does not understand what you are trying to enter into a cell. The different error codes Excel returns can help you troubleshoot what problem you are experiencing.

For a more in depth discussion of datatypes you can visit:

http://johnatten.com/2011/10/03/microsoft-excel-basics-part-ii-data-types-in-excel/
