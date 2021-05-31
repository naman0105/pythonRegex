# pythonRegex

import re

txt = "Th.rain.d.DF and.thou.will an"
expr = "\w+\.\w+\.\w+(\.\w*)*"

def modified(str):
    print(str.group())
    x = re.split(r"\.", str.group())
    newstr = "json_value(" + x[0] + "." + x[1] + ", '$"
    for i in range(2, len(x)):
        newstr = newstr + "." + x[i]
    newstr = newstr + "')"
    return newstr
    

x = re.sub(expr, modified(re.search(expr, txt)), txt, 1)
print(x)
while re.search(expr, x):
    x = re.sub(expr, modified(re.search(expr, x)), x, 1)

print(x)
