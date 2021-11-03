import tkinter as tk
from tkinter import scrolledtext as st
import sys
from tkinter import filedialog as fd
from tkinter import messagebox as mb
tk

class buscar:

    def __init__(self):
        self.ventana1=tk.Tk()
        self.agregar_menu()
        self.scrolledtext1=st.ScrolledText(self.ventana1, width=80, height=20, font=("Roboto Cn",14))
        self.scrolledtext1.grid(column=0,row=0,padx=10,pady=10)
        self.ventana1.mainloop()

    def agregar_menu(self):
        menu2 = tk.Menu(self.ventana1)
        self.ventana1.config(menu=menu2)
        opci1 = tk.Menu(menu2, tearoff=0)
        opci1.add_command(label="Crear Archivo", command=self.guardar, font=("Roboto Cn",10))
        opci1.add_command(label="abrir archivo", command=self.recuperar, font=("Roboto Cn",10))
        opci1.add_command(label="Guardar Cambios", command=self.guardar, font=("Roboto Cn",10))
        opci1.add_separator()
        opci1.add_command(label="Datos", command=self.datos, font=("Roboto Cn",10))
        opci1.add_command(label="Salir", command=self.salir, font=("Roboto Cn",10))
        menu2.add_cascade(label="Opciones", menu=opci1, font=("Roboto Cn",14))  

    def salir(self):
        sys.exit(0)

    def guardar(self):
        NomArchi=fd.asksaveasfilename(initialdir = "c:/pythonya",title = "Guardar Archivo como",filetypes = (("txt files","*.txt"),("todos los archivos","*.*")))
        if NomArchi!='':
            Archivonuevo=open(NomArchi, "w", encoding="utf-8")
            Archivonuevo.write(self.scrolledtext1.get("1.0", tk.END))
            Archivonuevo.close()
            mb.showinfo("Información", "Los datos fueron guardados con exito en el archivo.")

    def recuperar(self):
        NomArchi=fd.askopenfilename(initialdir = "c:/pythonya",title = "Seleccione Archivo",filetypes = (("txt files","*.txt"),("todos los archivos","*.*")))
        if NomArchi!='':
            Archivonuevo=open(NomArchi, "r", encoding="utf-8")
            contenido=Archivonuevo.read()
            Archivonuevo.close()
            self.scrolledtext1.delete("1.0", tk.END) 
            self.scrolledtext1.insert("1.0", contenido)

    def datos(self):
            mb.showinfo("Datos", "Carlos Andres Ramirez Garcia.")
                
aplicacion1=buscar()


