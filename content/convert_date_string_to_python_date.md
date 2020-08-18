title: Convert a date string into Python date
Slug: convert-date-string-to-python-date
Date: 2020-08-16 20:14
Category: python
Tags: python convert date string date object
author: Ashutosh Gupta
Summary: Python provides datetime class which has function strptime which convert a date string into date object.

Very often we store dates in string format in our database. It is very easy and convenient to store date in varchar and text datatype. 
But when we use date for manupulation in backend we can not use date in string format, we need to convert it into date object.

To convert date string into date object python has datetime class, which has function strptime. 
Strtptime function takes date string and the format in which the date string is stored, and it converts the string into date object.

```python
### Example 1
from datetime import datetime as dt
date_obj = dt.strptime("16/08/2020", "%d/%m/%Y")

Line 1 imports the datetime class
Line2 converts date string "16/08/2020" given in format "%d/%m/%Y" into date object and stores into variable date_obj

"%d" is for date
"%m" is for month 
"%Y" is for Year in 2020 format

output : datetime.datetime(2020, 8, 16, 0, 0)

### Example 2
from datetime import datetime as dt
date_obj = dt.strptime("16/08/20", "%d/%m/%y")

output : datetime.datetime(2020, 8, 16, 0, 0)

"%d" is for date
"%m" is for month 
"%y" is for Year in 20 format

### Example 3
from datetime import datetime as dt
date_obj = dt.strptime("16 August 2020", "%d %B %Y")

output : datetime.datetime(2020, 8, 16, 0, 0)

"%d" is for date
"%B" is for month in full text format 
"%Y" is for Year in 2020 format

### Example 4
from datetime import datetime as dt
date_obj = dt.strptime("16 Aug 2020", "%d %b %Y")

output : datetime.datetime(2020, 8, 16, 0, 0)

"%d" is for date
"%b" is for month in short text format 
"%Y" is for Year in 2020 format

### Example 5
from datetime import datetime as dt
date_obj = dt.strptime("16 Aug 2020 20:30:30", "%d %b %Y %H:%M:%S")

output : datetime.datetime(2020, 8, 16, 20, 30, 30)

"%d" is for date
"%b" is for month in short text format 
"%Y" is for Year in 2020 format
"%H" is for Hour in 24hour format
"%M" is for Minute
"%S" is for Seconds

### Example 6
from datetime import datetime as dt
date_obj = dt.strptime("16 Aug 2020 8:30:30 pm", "%d %b %Y %I:%M:%S %p")

output : datetime.datetime(2020, 8, 16, 20, 30, 30)

"%d" is for date
"%b" is for month in short text format 
"%Y" is for Year in 2020 format
"%I" is for Hour in 12hour format
"%M" is for Minute
"%S" is for Seconds
"%p" is for AM/PM

In above example since the 8:30 is evening time, the strptime function <br/> while converting it to object will convert it to 24 hour format and make the time as 20:30


All the format are listed below:
|-------------|-------------------------------------------------------------|---------------------------|
| Directive   |	Meaning 								                    | Example                   |
|-------------|-------------------------------------------------------------|---------------------------|
| %a	      | Abbreviated weekday name.									| Sun, Mon                  |
| %A	      | Full weekday name.											| Sunday, Monday 	        |
| %w	      | Weekday as a decimal number.								| 0, 1, ..., 6		        |
| %d	      | Day of the month as a zero-padded decimal.					| 01, 02, ..., 31	        |
| %-d	      | Day of the month as a decimal number.						| 1, 2, ..., 30		        |
| %b	      | Abbreviated month name.										| Jan, Feb, ..., Dec        |
| %B	      | Full month name.											| January, February	        |
| %m	      | Month as a zero-padded decimal number.						| 01, 02, ..., 12	        |
| %-m	      | Month as a decimal number.									| 1, 2, ..., 12		        | 
| %y	      | Year without century as a zero-padded decimal number.		| 00, 01, ..., 99	        | 
| %-y	      | Year without century as a decimal number.					| 0, 1, ..., 99		        |
| %Y	      | Year with century as a decimal number.						| 2013, 2019 etc.	        | 
| %H	      | Hour (24-hour clock) as a zero-padded decimal number.		| 00, 01, ..., 23	        |
| %-H	      | Hour (24-hour clock) as a decimal number.					| 0, 1, ..., 23		        |
| %I	      | Hour (12-hour clock) as a zero-padded decimal number.		| 01, 02, ..., 12	        |
| %-I	      | Hour (12-hour clock) as a decimal number.					| 1, 2, ... 12		        |
| %p	      | Locale’s AM or PM.											| AM, PM			        |
| %M	      | Minute as a zero-padded decimal number.						| 00, 01, ..., 59	        |
| %-M	      | Minute as a decimal number.	 								| 0, 1, ..., 59		        |
| %S	      | Second as a zero-padded decimal number.						| 00, 01, ..., 59	        |
| %-S	      | Second as a decimal number.									| 0, 1, ..., 59		        |
| %f	      | Microsecond as a decimal number, zero-padded on the left	| 000000 - 999999           |
| %z	      | UTC offset in the form +HHMM or -HHMM.						| 				            |
| %Z	      | Time zone name.	 											|				            |
| %j	      | Day of the year as a zero-padded decimal number.			| 001, 002, ..., 366        |
| %-j	      | Day of the year as a decimal number.						| 1, 2, ..., 366            |
| %U	      | Week number of the year (Sunday as the first day of the 
				week). All days in a new year preceding the first Sunday 
				are considered to be in week 0.							    | 00, 01, ..., 53           |
| %W		  | Week number of the year (Monday as the first day of the 
				week). All days in a new year preceding the first Monday 
				are considered to be in week 0.							    | 00, 01, ..., 53           | 
| %c		  | Locales appropriate date and time representation.			| Mon Sep 30 07:06:05 2013  |
| %x		  | Locales appropriate date representation.					| 09/30/13                  |
| %X		  | Locales appropriate time representation.					| 07:06:05                  |
| %%		  | A literal '%' character.									| %                         |
--------------|-------------------------------------------------------------|---------------------------|


Important to note if the date string provided and formate doesn't match the function will return error.

date_obj = dt.strptime("16/08/2020", "%d-%m-%Y")

Output : ValueError: time data '16/08/2020' does not match format '%d-%m-%Y'



```
