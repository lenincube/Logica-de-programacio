import random

def juego_piedra_papel_tijera_hasta_dos():
    opciones = ["piedra", "papel", "tijera"]
    jugador_score = 0
    computadora_score = 0

    # Se jugarán hasta 3 rondas (best of 3),
    # pero el bucle se interrumpe si alguien llega a 2 victorias antes.
    for ronda in range(1, 4):
        print(f"\n--- Ronda {ronda} ---")

        # Bucle para validar la elección del jugador
        while True:
            jugador = input("Elige piedra, papel o tijera: ").lower()
            if jugador in opciones:
                break
            else:
                print("Elección inválida. Por favor elige entre piedra, papel o tijera.")

        computadora = random.choice(opciones)
        print(f"La computadora elige: {computadora}")

        # Determinar el resultado de la ronda
        if jugador == computadora:
            print("¡Es un empate!")
        elif (jugador == "piedra" and computadora == "tijera") \
             or (jugador == "papel" and computadora == "piedra") \
             or (jugador == "tijera" and computadora == "papel"):
            print("¡Ganaste esta ronda!")
            jugador_score += 1
        else:
            print("La computadora ganó esta ronda.")
            computadora_score += 1

        # Mostrar la puntuación acumulada
        print(f"Puntuación: Jugador {jugador_score} - Computadora {computadora_score}")

        # Verificar si alguien ha alcanzado las 2 victorias
        if jugador_score == 2:
            print("\n¡Felicidades, ganaste la partida!")
            break
        elif computadora_score == 2:
            print("\nLa computadora ganó la partida.")
            break
    else:
        # Si se completaron las 3 rondas sin que nadie alcance 2 victorias,
        # revisamos quién tiene más puntos o si hubo empate.
        if jugador_score > computadora_score:
            print("\n¡Felicidades, ganaste la partida!")
        elif computadora_score > jugador_score:
            print("\nLa computadora ganó la partida.")
        else:
            print("\nLa partida terminó en empate.")

# Llamar a la función para iniciar el juego
juego_piedra_papel_tijera_hasta_dos()
