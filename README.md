# Tkinter
Taller/Edward V

import tkinter as tk
#from tkinter import filedialog
from tkinter import ttk



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


def calculadora(num1 ,num2 ,operador):
    if operador =='+':
        resultado = num1 + num2
    elif operador =='-':
        resultado = num1 - num2
    elif operador =='*':
        resultado = num1 * num2
    elif operador =='/':
        resultado = round(num1 /num2 ,2)
    else:
        resultado =num1**num2
    return resultado


def init_window():

    window = tk.Tk(  )  # crear pantalla
    window.title('Mi primera aplicacion'  )  # agragar titulo a la pantalla
    # Establece el tamaño de la pantalla (ancho:400px y largo: 250px)
    window.geometry('400x250')

    label = tk.Label(window, text='Calculadora' ,font=('Arial bold', 15))
    label.grid(column=0, row=0)

    label_entrada1 = tk.Label(window, text='Ingrese primer numero' ,font=('Arial bold', 10))
    label_entrada1.grid(column=0, row=1)

    label_entrada2 = tk.Label(window, text='Ingrese segundo numero' ,font=('Arial bold', 10))
    label_entrada2.grid(column=0, row=2)

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
