# Practicas-Python
import random

def jugar():
    print("🎮 Bienvenido al juego de Adivina el Número")
    print("Estoy pensando en un número entre 1 y 100...")

    nivel = input("Elige dificultad (facil / medio / dificil): ").lower()

    if nivel == "facil":
        intentos = 10
    elif nivel == "medio":
        intentos = 7
    elif nivel == "dificil":
        intentos = 5
    else:
        print("Nivel inválido, usando modo medio por defecto.")
        intentos = 7

    numero_secreto = random.randint(1, 100)

    while intentos > 0:
        try:
            print(f"\nTe quedan {intentos} intentos")
            adivina = int(input("Ingresa tu número: "))

            if adivina == numero_secreto:
                print("🎉 ¡Correcto! Adivinaste el número.")
                return
            elif adivina < numero_secreto:
                print("📉 Muy bajo")
            else:
                print("📈 Muy alto")

            intentos -= 1

        except ValueError:
            print("⚠️ Debes ingresar un número válido")

    print(f"💀 Perdiste. El número era: {numero_secreto}")

if __name__ == "__main__":
    jugar()
