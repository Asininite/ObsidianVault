```python
from tkinter import *
def F_to_C():
    f = float(e1.get())
    c = (f-32)*5/9
    e2.delete(0,END)
    e2.insert(END,str(c))
  
def C_to_F():
    c = int(e2.get())
    f=c*9/5.0+32
    e1.delete(0,END)
    e1.insert(END,str(f))

root = Tk()
Label(root,text="Fahrenheir").grid(row=0,column=0,sticky="W")
Label(root,text="Celscius").grid(row=0,column=1,sticky="W")

e1 = Entry(root)
e2 = Entry(root)
  
e1.grid(row=1, column=0)
e2.grid(row=1,column=1)

e1.insert(END,"32.0")
e2.insert(END,"0.0")

b1 = Button(root,text=">>>",command=F_to_C).grid(row=3,column=0,padx=5,pady=5)
b2 = Button(root,text="<<<<",command=C_to_F).grid(row=3,column=1,padx=5,pady=5)

mainloop()
```