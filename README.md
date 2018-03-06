from tkinter import *
import random
import time
import datetime
from tkinter import messagebox

root=Tk()
root.geometry("1350x750+0+0")
root.title("Cafe Management System")
root.configure(background='black')

tops=Frame(root,width=1350, height=100,bd=14,relief='raise')
tops.pack(side=TOP)

f1=Frame(root,width=900, height=650,bd=8,relief='raise')
f1.pack(side=LEFT)

f2=Frame(root,width=440, height=650,bd=8,relief='raise')
f2.pack(side=RIGHT)

f1a=Frame(f1,width=900, height=330,bd=8,relief='raise')
f1a.pack(side=TOP)

f2a=Frame(f1,width=900, height=320,bd=6,relief='raise')
f2a.pack(side=BOTTOM)

ft2=Frame(f2,width=440, height=650,bd=12,relief='raise')
ft2.pack(side=TOP)

fb2=Frame(f2,width=440, height=250,bd=16,relief='raise')
fb2.pack(side=BOTTOM)

f1aa=Frame(f1a ,width=400, height=330,bd=16,relief='raise')
f1aa.pack(side=LEFT)

f1ab=Frame(f1a,width=400, height=330,bd=16,relief='raise')
f1ab.pack(side=RIGHT)

f2aa=Frame(f2a,width=450, height=330,bd=14,relief='raise')
f2aa.pack(side=LEFT)

f2ab=Frame(f2a,width=450, height=330,bd=14,relief='raise')
f2ab.pack(side=RIGHT)

tops.configure(background='black')
f1.configure(background='black')
f2.configure(background='black')


#---------------Methods--------------
def CostofItem():
    item1 = float(E_Panipuri.get())
    item2 = float(E_Bhel.get())
    item3 = float(E_Samosa.get())
    item4 = float(E_Vadapav.get())
    item5 = float(E_masalapapad.get())
    item6 = float(E_Alootikki.get())
    item7 = float(E_Kachori.get())
    item8 = float(E_pavbhaji.get())

    item9 = float(E_Coldcoffee.get())
    item10 = float(E_Mosambi.get())
    item11 = float(E_Apple.get())
    item12 = float(E_Mango.get())
    item13 = float(E_Pmogranate.get())
    item14 = float(E_Grape.get())
    item15 = float(E_Orange.get())
    item16 = float(E_Tea.get())

    priceofchats = (item1 * 1.26) + (item2 * 1.99) + (item3 * 2.05)  + (item4 * 1.89) \
             +(item5 * 1.99) +(item6 * 2.99) + (item7 * 2.39) + (item8 * 1.29)

    priceofjuices = (item9 * 1.35)+(item10 * 2.55)+(item11 * 5.58)+(item12 * 7.9)+(item13 * 5.4)\
               +(item14 * 7.59)+(item15 * 8.45)+(item16 * 6.78)

    chatsprice = "Rs" , str("%.2f"%(priceofchats))
    juicesprice= "Rs",str("%.2f"%(priceofjuices))
    costofchats.set(chatsprice)
    costofjuices.set(juicesprice)
    SC="Rs", str("%.2f"%(5.59))
    Servicecharges.set(SC)

    SubTotalofitems="Rs",str("%.2f"%(priceofchats + priceofjuices+5.59))
    SubTotal.set(SubTotalofitems)

    Tax="Rs",str('%.2f'%((priceofchats+priceofjuices+5.59)*0.15))
    paidTax.set(Tax)
    TT=((priceofchats+priceofjuices+5.59)*0.15)
    TC="Rs",str('%.2f'%(priceofchats+priceofjuices+5.59+TT))
    Totalcost.set(TC)


def qExit():
    qExit=messagebox.askyesno("QuitSystem","Do you want to quite")
    if qExit > 0:
        root.destroy()
        return

def Reset():
    paidTax.set("")
    SubTotal.set("")
    Totalcost.set("")
    costofchats.set("")
    costofjuices.set("")
    Servicecharges.set("")
    txtReceipt.delete("1.0",END)

    E_Panipuri.set("0")
    E_Bhel.set("0")
    E_Samosa.set("0")
    E_Vadapav.set("0")
    E_masalapapad.set("0")
    E_Alootikki.set("0")
    E_Kachori.set("0")
    E_pavbhaji.set("0")

    E_Coldcoffee.set("0")
    E_Mosambi.set("0")
    E_Apple.set("0")
    E_Mango.set("0")
    E_Pmogranate.set("0")
    E_Grape.set("0")
    E_Orange.set("0")
    E_Tea.set("0")

    var1.set(0)
    var2.set(0)
    var3.set(0)
    var4.set(0)
    var5.set(0)
    var6.set(0)
    var7.set(0)
    var8.set(0)
    var9.set(0)
    var10.set(0)
    var11.set(0)
    var12.set(0)
    var13.set(0)
    var14.set(0)
    var15.set(0)
    var16.set(0)

    txtPanipuri.configure(state=DISABLED)
    txtBhel.configure(state=DISABLED)
    txtSamosa.configure(state=DISABLED)
    txtVadapav.configure(state=DISABLED)
    txtmasalapapad.configure(state=DISABLED)
    txtAlootikki.configure(state=DISABLED)
    txtKachori.configure(state=DISABLED)
    txtpavbhaji.configure(state=DISABLED)

    txtColdcoffee.configure(state=DISABLED)
    txtMosambi.configure(state=DISABLED)
    txtApple.configure(state=DISABLED)
    txtMango.configure(state=DISABLED)
    txtPomogranate.configure(state=DISABLED)
    txtGrape.configure(state=DISABLED)
    txtOrange.configure(state=DISABLED)
    txtTea.configure(state=DISABLED)

def Receipt():
    txtReceipt.delete("1.0",END)
    x=random.randint(10908,500876)
    randomRef = str(x)
    Receipt_Ref.set("BILL"+randomRef)

    txtReceipt.insert(END,'Receipt Ref:\t\t\t'+Receipt_Ref.get()+'\t\t'+Dateoforder.get()+'\n')
    txtReceipt.insert(END,"Items\t\t\t\t"+"CostofItems\n\n")
    txtReceipt.insert(END, 'Panipuri\t\t\t'+E_Panipuri.get()+'\n')
    txtReceipt.insert(END,'Bhel\t\t\t'+E_Bhel.get()+'\n')
    txtReceipt.insert(END,'Samosa\t\t\t' +E_Samosa.get()+'\n')
    txtReceipt.insert(END,'Vadapav\t\t\t'+E_Vadapav.get()+'\n')
    txtReceipt.insert(END,'Masalapapad\t\t\t'+E_masalapapad.get()+'\n')
    txtReceipt.insert(END,'Alootikki\t\t\t'+E_Alootikki.get()+'\n')
    txtReceipt.insert(END,'Kachori\t\t\t'+E_Kachori.get()+'\n')
    txtReceipt.insert(END,'Pavbhaji\t\t\t'+ E_pavbhaji.get()+'\n')
    txtReceipt.insert(END,'Coldcoffee\t\t\t'+E_Coldcoffee.get()+'\n')
    txtReceipt.insert(END,'Mosambi\t\t\t' +E_Mosambi.get()+'\n')
    txtReceipt.insert(END,'Apple\t\t\t'+E_Apple.get()+'\n')
    txtReceipt.insert(END,'Mango\t\t\t'+ E_Mango.get()+'\n')
    txtReceipt.insert(END,'Pomogranate\t\t\t'+ E_Pmogranate.get()+'\n')
    txtReceipt.insert(END,'Grape\t\t\t'+ E_Grape.get()+'\n')
    txtReceipt.insert(END,'Orange\t\t\t' + E_Orange.get()+'\n')
    txtReceipt.insert(END,'Tea\t\t\t' + E_Tea.get()+'\n')
    txtReceipt.insert(END,'cost of chats\t\t' + costofchats.get() + '\tTax paid:\t'+paidTax.get()+'\n')
    txtReceipt.insert(END,'costofjuices\t\t'+ costofjuices.get() +'\tSubTotal:\t' +SubTotal.get()+'\n')
    txtReceipt.insert(END,'Service charge\t\t' + Servicecharges.get()+'\tTotalcost:\t'+Totalcost.get()+'\n')


#==================Heading==============================

lblInfo = Label(tops,font=('arial',50,'bold'),text="\t Cafe Management System \t",bd=10)
lblInfo.grid(row=0,column=0)

#-------------------------Calculator----------------------

def chkbutton_value():
    if(var1.get()==1):
        txtPanipuri.configure(state=NORMAL)
    elif var1.get()== 0:
        txtPanipuri.configure(state=DISABLED)
        E_Panipuri.set("0")
    if(var2.get()==1):
         txtBhel.configure(state=NORMAL)
    elif var2.get()==0:
         txtBhel.configure(sate=DISABLED)
         E_Bhel.set("0")
    if(var3.get()==1):
        txtSamosa.configure(state=NORMAL)
    elif var3.get()==0:
        txtSamosa.configure(state=DISABLED)
        E_Samosa.set("0")
    if (var4.get() == 1):
        txtVadapav.configure(state=NORMAL)
    elif var4.get() == 0:
        txtVadapav.configure(state=DISABLED)
        E_Vadapav.set("0")
    if (var5.get() == 1):
        txtmasalapapad.configure(state=NORMAL)
    elif var5.get() == 0:
        txtmasalapapad.configure(state=DISABLED)
        E_masalapapad.set("0")
    if (var6.get() == 1):
        txtAlootikki.configure(state=NORMAL)
    elif var6.get() == 0:
        txtAlootikki.configure(state=DISABLED)
        E_Alootikki.set("0")
    if (var7.get() == 1):
        txtKachori.configure(state=NORMAL)
    elif var7.get() == 0:
        txtKachori.configure(state=DISABLED)
        E_Kachori.set("0")
    if (var8.get() == 1):
        txtpavbhaji.configure(state=NORMAL)
    elif var8.get() == 0:
        txtpavbhaji.configure(state=DISABLED)
        E_pavbhaji.set("0")
    if (var9.get() == 1):
        txtColdcoffee.configure(state=NORMAL)
    elif var9.get() == 0:
        txtColdcoffee.configure(state=DISABLED)
        E_Coldcoffee.set("0")
    if (var10.get() == 1):
        txtMosambi.configure(state=NORMAL)
    elif var10.get() == 0:
        txtMosambi.configure(state=DISABLED)
        E_Mosambi.set("0")
    if (var11.get() == 1):
        txtApple.configure(state=NORMAL)
    elif var11.get() == 0:
        txtApple.configure(state=DISABLED)
        E_Apple.set("0")
    if (var12.get() == 1):
        txtMango.configure(state=NORMAL)
    elif var12.get() == 0:
        txtMango.configure(state=DISABLED)
        E_Mango.set("0")
    if (var13.get() == 1):
        txtPomogranate.configure(state=NORMAL)
    elif var13.get() == 0:
        txtPomogranate.configure(state=DISABLED)
        E_Pmogranate.set("0")

    if (var14.get() == 1):
        txtGrape.configure(state=NORMAL)
    elif var14.get() == 0:
        txtGrape.configure(state=DISABLED)
        E_Grape.set("0")
    if (var15.get() == 1):
        txtOrange.configure(state=NORMAL)
    elif var15.get() == 0:
        txtOrange.configure(state=DISABLED)
        E_Orange.set("0")
    if (var16.get() == 1):
        txtTea.configure(state=NORMAL)
    elif var16.get() == 0:
        txtTea.configure(state=DISABLED)
        E_Tea.set("0")


# ---------------Variables--------------
var1=IntVar()
var2=IntVar()
var3=IntVar()
var4=IntVar()
var5=IntVar()
var6=IntVar()
var7=IntVar()
var8=IntVar()
var9=IntVar()
var10=IntVar()
var11=IntVar()
var12=IntVar()
var13=IntVar()
var14=IntVar()
var15=IntVar()
var16=IntVar()

Dateoforder=StringVar()
Receipt_Ref=StringVar()
paidTax=StringVar()
SubTotal=StringVar()
Totalcost=StringVar()
costofchats=StringVar()
costofjuices=StringVar()
Servicecharges=StringVar()

E_Panipuri=StringVar()
E_Bhel=StringVar()
E_Samosa=StringVar()
E_Vadapav=StringVar()
E_masalapapad=StringVar()
E_Alootikki=StringVar()
E_Kachori=StringVar()
E_pavbhaji=StringVar()

E_Coldcoffee=StringVar()
E_Mosambi=StringVar()
E_Apple=StringVar()
E_Mango=StringVar()
E_Pmogranate=StringVar()
E_Grape=StringVar()
E_Orange=StringVar()
E_Tea=StringVar()

E_Panipuri.set("0")
E_Bhel.set("0")
E_Samosa.set("0")
E_Vadapav.set("0")
E_masalapapad.set("0")
E_Alootikki.set("0")
E_Kachori.set("0")
E_pavbhaji.set("0")

E_Coldcoffee.set("0")
E_Mosambi.set("0")
E_Apple.set("0")
E_Mango.set("0")
E_Pmogranate.set("0")
E_Grape.set("0")
E_Orange.set("0")
E_Tea.set("0")

Dateoforder.set(time.strftime("%d/%m/%y"))

#---------------------CHATS----------------------------------

Panipuri = Checkbutton(f1aa, text="Panipuri \t", variable=var1, onvalue= 1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=0,sticky=W)
Bhel = Checkbutton(f1aa, text="Bhel\t", variable=var2, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=1,sticky=W)
Samosa = Checkbutton(f1aa, text="Samosa\t", variable=var3, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=2,sticky=W)
Vadapav = Checkbutton(f1aa, text="Vadapav \t", variable=var4, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=3,sticky=W)
masalapapad = Checkbutton (f1aa, text="masalapapad \t", variable=var5, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=4,sticky=W)
Alootikki = Checkbutton(f1aa, text="Alootikki \t", variable=var6, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=5,sticky=W)
Kachori = Checkbutton(f1aa, text="Kachori \t", variable=var7, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=6,sticky=W)
pavbhaji = Checkbutton(f1aa, text="pavbhaji \t", variable=var8, onvalue=1, offvalue=0,
                            font=('arial',18,'bold'),command=chkbutton_value).grid(row=7,sticky=W)

#-----------------------------Juices-------------------------------------

Coldcoffee = Checkbutton(f1ab, text="Coldcoffee \t", variable=var9, onvalue= 1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=0,sticky=W)
Mosambi = Checkbutton(f1ab, text="Mosambi", variable=var10, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=1,sticky=W)
Apple = Checkbutton(f1ab, text="Apple", variable=var11, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=2,sticky=W)
Mango = Checkbutton(f1ab, text="Mango \t", variable=var12, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=3,sticky=W)
Pomogranate = Checkbutton (f1ab, text="Pomogranate\t", variable=var13, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=4,sticky=W)
Grape = Checkbutton(f1ab, text="Grape \t", variable=var14, onvalue=1, offvalue=0,  font=('arial',18,'bold'),command=chkbutton_value).grid(row=5,sticky=W)
Orange = Checkbutton(f1ab, text="Orange \t", variable=var15, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=6,sticky=W)
Tea = Checkbutton(f1ab, text="Tea \t", variable=var16, onvalue=1, offvalue=0, font=('arial',18,'bold'),command=chkbutton_value).grid(row=7,sticky=W)


#-----------Enter widget for chats-----------------------

txtPanipuri= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Panipuri, state=DISABLED)
txtPanipuri.grid(row=0,column=1)
txtBhel= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Bhel,state=DISABLED)
txtBhel.grid(row=1,column=1)
txtSamosa= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Samosa,state=DISABLED)
txtSamosa.grid(row=2,column=1)
txtVadapav= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Vadapav,state=DISABLED)
txtVadapav.grid(row=3,column=1)
txtmasalapapad= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_masalapapad,state=DISABLED)
txtmasalapapad.grid(row=4,column=1)
txtAlootikki= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Alootikki,state=DISABLED)
txtAlootikki.grid(row=5,column=1)
txtKachori= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Kachori,state=DISABLED)
txtKachori.grid(row=6,column=1)
txtpavbhaji= Entry(f1aa,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_pavbhaji,state=DISABLED)
txtpavbhaji.grid(row=7,column=1)

#-----------Enter widget for Juices-----------------------

txtColdcoffee= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Coldcoffee,state=DISABLED)
txtColdcoffee.grid(row=0,column=1)
txtMosambi= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Mosambi,state=DISABLED)
txtMosambi.grid(row=1,column=1)
txtApple= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Apple,state=DISABLED)
txtApple.grid(row=2,column=1)
txtMango= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Mango,state=DISABLED)
txtMango.grid(row=3,column=1)
txtPomogranate= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Pmogranate,state=DISABLED)
txtPomogranate.grid(row=4,column=1)
txtGrape= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Grape,state=DISABLED)
txtGrape.grid(row=5,column=1)
txtOrange= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Orange,state=DISABLED)
txtOrange.grid(row=6,column=1)
txtTea= Entry(f1ab,font=('airal',16,'bold'),bd=8,width=6,justify='left',textvariable=E_Tea,state=DISABLED)
txtTea.grid(row=7,column=1)



#------------------ cost Items information------------------------
lblcostofchats=Label(f2aa,font=('airal',16,'bold'),text='cost of chats',bd=8,anchor='w')
lblcostofchats.grid(row=2,column=0,sticky=W)
txtcostofchats=Entry(f2aa,font=('airal',16,'bold'),bd=8,insertwidth=2,justify='left',textvariable=costofchats)
txtcostofchats.grid(row=2,column=1,sticky=W)

lblcostofjuices=Label(f2aa,font=('airal',16,'bold'),text='cost of juices',bd=8,anchor='w')
lblcostofjuices.grid(row=3,column=0,sticky=W)
txtcostofjuices=Entry(f2aa,font=('airal',16,'bold'),bd=8,insertwidth=2,justify='left',textvariable=costofjuices)
txtcostofjuices.grid(row=3,column=1,sticky=W)

lblServicecharge=Label(f2aa,font=('airal',16,'bold'),text='Service charge',bd=8,anchor='w')
lblServicecharge.grid(row=4,column=0,sticky=W)
txtServicecharge=Entry(f2aa,font=('airal',16,'bold'),bd=8,insertwidth=2,justify='left',textvariable=Servicecharges)
txtServicecharge.grid(row=4,column=1,sticky=W)



#------------------Payment Information------------------------

lblpaidTax=Label(f2ab,font=('airal',16,'bold'),text='paid Tax',bd=8)
lblpaidTax.grid(row=2,column=0,sticky=W)
txtpaidTax= Entry(f2ab,font=('airal',16,'bold'),textvariable=paidTax,bd=8,insertwidth=2,justify="left")
txtpaidTax.grid(row=2,column=1)

lblSubTotal=Label(f2ab,font=('airal',16,'bold'),text='Sub Total',bd=8)
lblSubTotal.grid(row= 3,column=0,sticky=W)
txtSubTotal=Entry(f2ab,font=('airal',16,'bold'),textvariable=SubTotal,bd=8,insertwidth=2,justify='left')
txtSubTotal.grid(row=3,column=1)

lblTotalcost=Label(f2ab ,font=('airal',16,'bold'),text='Total',bd=8)
lblTotalcost.grid(row=4,column=0,sticky=W)
txtTotalcost=Entry(f2ab,font=('airal',16,'bold'),textvariable=Totalcost,bd=8,insertwidth=2,justify='left')
txtTotalcost.grid(row=4,column=1)

#------------------information------------------------

lblReceipt = Label (ft2,font=('airal',12,'bold'),text="Receipt",bd=2,anchor='w')
lblReceipt.grid(row=0,column=0,sticky=W)
txtReceipt= Text(ft2,font=('airal',11,'bold'),bd=8,width=59,height=22,bg="white")
txtReceipt.grid(row=1,column=0)

# ------------------Button------------------------

btnTotal=Button(fb2,padx=16,pady=1,bd=4,fg="black",font=('airal',16,'bold'),width=5,text="Total", command=CostofItem).grid(row=0, column=0)

btnReceipt=Button(fb2,padx=16,pady=1,bd=4,font=('airal',16,'bold'),width=5,text="Receipt",command=Receipt).grid(row=0,column=1)

btnReset=Button(fb2,padx=16,pady=1,bd=4,font=('airal',16,'bold'),width=5,text="Reset",command=Reset).grid(row=0,column=2)

btnExit=Button(fb2,padx=16,pady=1,bd=4,font=('airal',16,'bold'),width=5,text="Exit",command=qExit).grid(row=0,column=3)


root.mainloop()


cafe1.py

Open with Google Docs





# cafe-mangement-system
Taking number items orderd, displaying amount of each items and with receipt 
https://drive.google.com/drive/my-drive
