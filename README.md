#Clock
```python
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
#GUI

```python

'''
Author : Tarik Alkanan

'''
from tkinter import *
from PIL import Image, ImageTk
from time import strftime
'''
from tkinter.ttk import *
from function import *
'''
#Create the window
window = Tk()
width = window.winfo_screenwidth()          ##get screen width
height= window.winfo_screenheight()         ##get screen height
window.geometry("%dx%d" % (width,height))   ##set screen size
window.title("Tarik is alive")
'''
Resize image 
'''
def resizeImage(image,width,height):
    resizedImage=image.resize((int(width/2),int(height/2)))
    newImage=ImageTk.PhotoImage(resizedImage)
    return newImage

'''
import images
'''
img_email=(Image.open("T:/Projekt/gui/email1.png"))       ##Email

img_close=(Image.open("T:/Projekt/gui/shutdown1.png"))    ##Shutdown

img_browser=(Image.open("T:/Projekt/gui/browser2.png"))   ##Browser

img_editor=(Image.open("T:/Projekt/gui/texteditor1.png")) ##Test editor


def time():         #clock
    string = strftime('%H:%M:%S %p')
    lbl.config(text = string)
    lbl.after(1000, time)
def newWindowEd():
    new_window = Toplevel()
    new_window.geometry("500x500")
    new_window.title("Editor")
    lab_new_window=Label(new_window, text=("Editor"))
    lab_new_window.pack(pady=30)

def newWindowEm():
    new_window = Toplevel()
    new_window.geometry("500x500")
    new_window.title("Email")
    lab=Label(new_window ,text=("Email"),fg="red",font=("Helvetica",25))
    lab.pack(pady=30)



def resizeIcon(image): ## size for confirm Icon
    resizedImage=image.resize((50,50))
    newIcon=ImageTk.PhotoImage(resizedImage)

    return newIcon
def check_root_user():
    check_root_win = Toplevel(window)
    check_root_win.title('Permission only for Root')
    check_root_win.geometry("400x150")
    usernameLabel = Label(check_root_win, text="User Name").grid(row=0, column=0)
    username = StringVar()
    usernameEntry = Entry(check_root_win, textvariable=username).grid(row=0, column=1)

    #password label and password entry box
    passwordLabel = Label(check_root_win,text="Password").grid(row=1, column=0)
    password = StringVar()
    passwordEntry = Entry(check_root_win, textvariable=password, show='*').grid(row=1, column=1)
    e=password.get()
    print(e)
    #login button
    loginButton = Button(check_root_win, text="Login").grid(row=4, column=0)

def messageWindow():
    confirm_win = Toplevel(window)
    confirm_win.title('Shut down')
    confirm_win.geometry("550x200")
    message = "Are you sure that you want to shutdown the Computer "
    shutdown_img= (Image.open("T:/Projekt/gui/shutdown1.png"))
    war_img= (Image.open("T:/Projekt/gui/warning.png"))
    shutdown_img1=resizeIcon(shutdown_img)
    image_warning=resizeIcon(war_img)
    '''
    Add a label to ask for confirm
    '''
    confirm_text_lbl=Label(confirm_win, text=message,
                           font=("Times",15,"bold"),
                           image=image_warning,
                           compound=RIGHT)
    confirm_text_lbl.image=image_warning
    confirm_text_lbl.pack()
    '''
    Add a ok button
    '''
    ok_btn =Button(confirm_win, text='OK',font=('Times', 20),
                   fg="#7d2811",bd=5,
                   image=shutdown_img1,
                   activebackground="#D6252A",
                   compound=LEFT,
                   command=window.destroy)
    ok_btn.image=shutdown_img1
    ok_btn.pack(side=LEFT,padx=40)
    '''
    Add a Cancel button
    '''
    cancel_btn =Button(confirm_win, text='Cancel',
                       font=('Times', 20),
                       fg="#7d2811",bd=5,
                       activebackground="#53B4DA",
                       command=confirm_win.destroy)
    cancel_btn.pack(side=RIGHT,padx= 50)
    '''
    Add a root button 
    '''
    root_button=Button(confirm_win, text='Super user',
                       font=('Times', 5),
                       fg="#7d2811",bd=1,
                       activebackground="#560000",
                       command=check_root_user)
    root_button.pack(side=BOTTOM)

'''
Resize the imported images 
'''
img_close_resized=resizeImage(img_close,width,height)
img_email_resized=resizeImage(img_email,width,height)
img_browser_resized=resizeImage(img_browser,width,height)
img_editor_resized=resizeImage(img_editor,width,height)

'''
Exit button on desktop 
'''
exitButton =Button(window,image =img_close_resized,
                   bd=7,command=messageWindow)
exitButton.place(x=width/2,y=0)
'''
Editor button on desktop 
'''
editorButton=Button(window,text="Editor",image = img_editor_resized,
                    bd=7,command=newWindowEd)
editorButton.place(x=0,y=0)
'''
Browser button on desktop 
'''
browserButton=Button(window,text="Browser",image = img_browser_resized,
                     bd=7,command=newWindowEd)
browserButton.place(x=width/2,y=height/2)
'''
Email button on desktop 
'''
emailButton=Button(window,text="Email",image =img_email_resized,
                   bd=7,command=newWindowEm)
emailButton.place(x=0,y=height/2)

lbl = Label(window, font = ('calibri', 40, 'bold'),
                            background = '#6a8c93',
                            foreground = '#fffbd3')
lab_width = width-300
lab_height = height-150
lbl.place(x= lab_width,y=lab_height)
time()

window.mainloop()

```
