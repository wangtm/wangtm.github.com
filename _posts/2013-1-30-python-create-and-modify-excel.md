---

layout : post

category : manage

tags : [python   python  平板文件]

title : 创建并修改excel

---

# 创建并修改excel

import xlrd filename="D:/test.xls" 
data=xlrd.open_workbook(filename) 
sheet=data.sheet_by_index(0)
 rows=sheet.nrows 
cols=sheet.ncols for row in range(rows):     
value=sheet.row_values(row) 	
print value import time time.sleep(20)  
    #创建excel，并随机输入数据
 import xlwt import xlrd
 import random
 filename=xlwt.Workbook() 
sheet=filename.add_sheet("my_sheet") 
for row in range(0,10):     
for col in range(0,10):         
sheet.write(row,col,random.randrange(0,10)) filename.save("D:/test.xls") print "Done"  
    #判断每行的和，若>=40,则为“ok"，否则为”no“  
from xlrd import open_workbook 
from xlutils.copy import copy 
rb=open_workbook("D:test.xls") 
sheet=rb.sheet_by_index(0) 
rows=sheet.nrows 
cols=sheet.ncols 
wb=copy(rb) 
ws=wb.get_sheet(0) 
for row in range(rows): 	
value=sheet.row_values(row) 	
if sum(value)>=40: 		
ws.write(row,10,"ok") 	
else: 		
ws.write(row,10,"no") wb.save("D:/test.xls")
