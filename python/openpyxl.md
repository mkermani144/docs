openpyxl: working with excel files
====


```python
# import
import openpyxl
# Load workbook
wb = openpyxl.load_workbook('sample.xlsx')
# Get active sheet
sheet = wb.active
# Get maximum row/column number
max = sheet.max_row
# Get value of a cell
val = sheet.cell(row=1, column=1).value
```


Resources
----
Book: [Automate the boring stuff with python](https://www.amazon.com/Automate-Boring-Stuff-Python-Programming/dp/1593275994)
