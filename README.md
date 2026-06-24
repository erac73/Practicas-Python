# Practicas-Python
import tkinter as tk
from tkinter import messagebox

# Crear ventana principal
ventana = tk.Tk()
ventana.title("📝 Mi Bloc de Notas")
ventana.geometry("500x400")

# Función para guardar texto
def guardar():
    texto = caja_texto.get("1.0", tk.END).strip()
    if texto:
        with open("notas.txt", "a", encoding="utf-8") as f:
            f.write(texto + "\n---\n")
        messagebox.showinfo("Guardado", "Nota guardada correctamente ✅")
        caja_texto.delete("1.0", tk.END)
    else:
        messagebox.showwarning("Error", "No hay texto para guardar ⚠️")

# Función para limpiar
def limpiar():
    caja_texto.delete("1.0", tk.END)

# Título
titulo = tk.Label(ventana, text="Bloc de Notas", font=("Arial", 18))
titulo.pack(pady=10)

# Caja de texto
caja_texto = tk.Text(ventana, height=12, width=50)
caja_texto.pack(pady=10)

# Botones
frame_botones = tk.Frame(ventana)
frame_botones.pack()

btn_guardar = tk.Button(frame_botones, text="💾 Guardar", command=guardar)
btn_guardar.grid(row=0, column=0, padx=10)

btn_limpiar = tk.Button(frame_botones, text="🧹 Limpiar", command=limpiar)
btn_limpiar.grid(row=0, column=1, padx=10)

btn_salir = tk.Button(frame_botones, text="❌ Salir", command=ventana.quit)
btn_salir.grid(row=0, column=2, padx=10)

# Ejecutar app
ventana.mainloop()
