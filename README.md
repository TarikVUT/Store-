#Clock
```
from tkinter import *
from tkinter.ttk import *
from time import strftime




window = Tk()       #create window
#window.state('zoomed')

window.title("Tarik is here")
width = window.winfo_screenwidth()
height = window.winfo_screenheight()
window.geometry("%dx%d" % (width,height))

def time():
    string = strftime('%H:%M:%S %p')
    lbl.config(text = string)
    lbl.after(1000, time)

lbl = Label(window, font = ('calibri', 40, 'bold'),
            background = '#6a8c93',
            foreground = '#fffbd3')

lab_width = width-300
lab_height = height-150
lbl.place(x=lab_width,y=lab_height)
time()

closeButton = Button(window,text ="Close",command=window.destroy)
closeButton.pack(pady=200)


window.mainloop()


```
