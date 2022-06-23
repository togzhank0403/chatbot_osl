from array import *
inport csv
from operator import itemgetter

# INDEX A=1, not 0

lines = [] 

people= { 

“A” : ”89”, 

“B” : ”44”, 

“C” : ”152”, 

“D” : ”53”, 

“E” : ”141”, 

“F” : “230”, 

“G” : “131”, 

“H” : “103”, 

“J” : “145”, 

“L” : “982”, 

“M” : “194”, 

“N” : “124”, 

“P” : “175”, 

“Q” : “228”, 

“R” : “206”,  

“S” : “91”,  

“T” : “144”,  

“U” : “61”, 

“V” : “312”,  

“VA” : “1021”,  

“VS” : “54”,  

“W” : “169”,  

“X” : “20”,  

“Y” : “263”,  

“Z” : “152”,  

“Communal Building” : “800” 
} 

  

# FILE NAME DECLARATION 

with open (‘EcoX.csv’, newline = ‘ ‘) as f: 

         lines = csv.reader(f) 

         lines = list(lines) 

indices = lines[0] 

  

def SumFinder(current_bin,bin2,bin3): 

         sum = 0 

         for core in lines[0][1:]: # a to commu 

                   if core == current_bin or core == bin2 or core == bin3; 

                            continue 

  

                   indices = list(people) 

                   curr_x = indices.index(current_bin)+1 

                   core_y = indices.index(core)+1 

                   temp = float(lines[curr_x][core_y]) * float(people[core]) 

                   sum += temp 

  

         return sum 

  

combinations= { } 

for c1 in lines[0][1:]: # a - Com 

         for c2 in lines[0][1:]: # a 

                   for c3 in lines[0][1:]: # a to cmp 

                            if c1 == c2 or c1 == c3 or c2==c3 : 

                                     continue 

  

                            d1 = SumFinder(c1, c2, c3) 

                            d2 = SumFinder(c2, c1, c3) 

                            d3 = SumFinder(c3, c1, c2) 

                            combinations[c1 + c2 + c3]= d1 + d2 + d3 

  

res = dict(sorted(combinations.items(), key = itemgetter(1))[:60]) 

print(“\nTop 10 places to place bin!”) 

  

count=0 

for items in res: 

         if count%6==0: 

                   print (items, “:”,res[items]) 

         count += 1 

  

  

Top 10 places to place bin! 

LVACommunal Building : 1550543.04 

LCommunal BuildingM : 1775580.1331999996 

LVSCommunal Building : 1784735.89 

VACommunal Building M : 1787637.6931999999 

LMVA : 1822701.4232 

LRVA : 1841803.1668 

VAVSCommunal Building : 1841941.6099999999 

LVAVS : 1851426.6400000001 

LVCommunal Building : 1856237.6799999997 
