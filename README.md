
import tkinter as tk
from tkinter import filedialog
from tkinter import ttk
from tkinter import messagebox
import random
from PIL import ImageTk, Image

# from tkinter import *
# from ttk import *
def click_calcular(label, num1, num2, operador):
    # Conversion de valores
    valor1 =float(num1)
    valor2 =float(num2)

    # Calculo dados los valores y el operador
    res =calculadora(valor1 ,valor2 ,operador)

    # Actualización del texto en la etiqueta
    label.configure(text='resultado:  ' +str(res))
def abrirventana():
    win=tk.Toplevel()
    win.geometry('380x300')
    win.configure(background='blue')
    txto=tk.Label(win,text='ERROR, está dividiendo en 0(cero)',bg='black',fg='white')
    txto.pack(padx=5,pady=5,ipadx=5,ipady=5,fill=tk.X)


def calculadora(num1 ,num2 ,operador):
    if operador =='+':
        resultado = num1 + num2
    elif operador =='-':
        resultado = num1 - num2
    elif operador =='*':
        resultado = num1 * num2
    elif operador =='/':
        if num2==0:
            error=1
            resultado ='ERRRORRR'
            if error==1:
                abrirventana()
        else:
            resultado = round(num1 /num2 ,2)
    else:
        resultado =num1**num2
    return resultado


def init_window():

    window = tk.Tk(  )  # crear pantalla
    window.title('Mi primera aplicacion'  )  # agragar titulo a la pantalla
    # Establece el tamaño de la pantalla (ancho:400px y largo: 250px)
    window.geometry('400x250')

    def changeBG():
        colors=['green','black','white','red','blue','purple']
        r_color=random.choice(colors)
        window.config(background=r_color)
    def icono():
        window.iconbitmap(r'C:\Users\edwar\Downloads\CODIGO.ico')



    def imagen():
        ventana=Tk()
        imagen=ImageTk.PhotoImage(Image.open(r'C:\Users\edwar\Downloads\COD.PNG'))
        #window.config(Label= imagen)
        label=Label(Image=imagen)
        label.pack()
        ventana.mainloop()


    label = tk.Label(window, text='Calculadora' ,font=('Arial bold', 15))
    label.grid(column=0, row=0)

    label_entrada1 = tk.Label(window, text='Ingrese primer numero' ,font=('Arial bold', 10))
    label_entrada1.grid(column=0, row=1)

    label_entrada2 = tk.Label(window, text='Ingrese segundo numero' ,font=('Arial bold', 10))
    label_entrada2.grid(column=0, row=2)



    main_btm=tk.Button(window, text='Cambia color', command=changeBG)
    main_btm.place(x=300,y=210)


    main_dibu=tk.Button(window, text='Traer ícono', command=icono)
    main_dibu.place(x=200,y=210)

    main_dibu=tk.Button(window, text='Traer imagen', command=imagen)
    main_dibu.place(x=100,y=210)

    entrada1 =tk.Entry(window, width=10)
    entrada2 =tk.Entry(window, width=10)

    entrada1.focus()
    entrada2.focus()

    entrada1.grid(column=1 ,row=1)
    entrada2.grid(column=1 ,row=2)



    label_operador =tk.Label(window, text= 'Escoja un operador', font=('Arial bold' ,10))
    label_operador.grid(column = 0, row = 3)

    combo_operadores =ttk.Combobox(window)
    combo_operadores['values' ] =('+' ,'-' ,'*' ,'/' ,'pow')
    combo_operadores.current(0  )  # set the select item
    combo_operadores.grid(column=1 ,row=3)
    # agregar etiqueta para mostar el resultado de la operación

    label_resultado =tk.Label(window ,text='Resultado', font=('Arial bold', 15))
    label_resultado.grid(column=0 ,row=5)


    # Boton calcular
    boton =tk.Button(window,
                    command= lambda: click_calcular(
                        label_resultado,
                        entrada1.get(),
                        entrada2.get(),
                        combo_operadores.get()),
                    text='Calcular',
                    bg='purple',
                    fg='white')
    boton.grid(column=1 ,row=4)

    window.mainloop()
def main():
    init_window()
main()
