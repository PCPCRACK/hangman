# ahorcado

```python

import random

animacion = ['''

  +---+
  |   |
      |
      |
      |
      |
=========''', '''

  +---+
  |   |
  O   |
      |
      |
      |
=========''', '''

  +---+
  |   |
  O   |
  |   |
      |
      |
=========''', '''

  +---+
  |   |
  O   |
 /|   |
      |
      |
=========''', '''

  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========''', '''

  +---+
  |   |
  O   |
 /|\  |
 /    |
      |
=========''', '''

  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |
=========''']
palabras = 'hormiga babuino tejón murciélago oso castor camello gato almeja cobra puma coyote cuervo ciervo perro burro pato águila hurón zorro rana cabra ganso halcón león lagarto llama topo mono alce ratón mula tritón nutria búho panda loro paloma pitón conejo carnero rata cuervo rinoceronte salmón foca tiburón oveja zorrillo perezoso serpiente araña cigüeña cisne tigre sapo trucha pavo tortuga comadreja ballena lobo wombat cebra'.split()

def Palabra_aleatoria(lista_palabras):
    # This function returns a random string from the passed list of strings.
    indice = random.randint(0, len(lista_palabras) - 1)
    return lista_palabras[indice]

def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):
    print(animacion[len(letras_incorrectas)])
    print()

    print('letras perdidas:', end=' ')
    for palabra in letras_incorrectas:
        print(palabra, end=' ')
    print()

    PL_adivinada = ''
    for i in range(len(palabra_secreta)): # replace PL_adivinada with correctly guessed letters
        if palabra_secreta[i] in letras_correctas:
            PL_adivinada += palabra_secreta[i]
        else:
            PL_adivinada += '_'

    for palabra in PL_adivinada: # show the secret word with spaces in between each palabra
        print(palabra, end=' ')
    print()

def adivina(adivinado):
    # Returns the palabra the player entered. This function makes sure the player entered a single palabra, and not something else.
    while True:
        print('Guess a palabra.')
        supongo = input().lower()
        if len(supongo) != 1:
            print('Please enter a single palabra.')
        elif supongo in adivinado:
            print('You have already guessed that palabra. Choose again.')
        elif supongo not in 'abcdefghijklmnopqrstuvwxyz':
            print('Please enter a LETTER.')
        else:
            return supongo

def volver_a_jugar():
    # This function returns True if the player wants to play again, otherwise it returns False.
    print('Do you want to play again? (yes or no)')
    return input().lower().startswith('y')

# Mira si el jugador adivino la palabra
def palabrometro(letras_correctas, palabra_secreta):
    letras_encontradas = True
    for i in range(len(palabra_secreta)):
        if palabra_secreta[i] not in letras_correctas:
            letras_encontradas = False
            break
    return letras_encontradas

# mira si el jugador perdio
def contador(letras_incorrectas, palabra_secreta):
    # Check if player has guessed too many times and lost
    if len(letras_incorrectas) == len(animacion) - 1:
        return True
    return False
            
def iniciador():
    """iniciador application entry point."""
    letras_incorrectas = ''
    letras_correctas = ''
    G_completado = False
    G_perdido = False
    palabra_secreta = Palabra_aleatoria(palabras)

    while True:
        pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta)

        if G_completado or G_perdido:
            if G_completado:
                print('Yes! The secret word is "' + palabra_secreta + '"! You have won!')
            else:
                print('You have run out of guesses!\nAfter ' + str(len(letras_incorrectas)) + ' missed guesses and ' + str(len(letras_correctas)) + ' correct guesses, the word was "' + palabra_secreta + '"')

            # Ask the player if they want to play again (but only if the game is done).
            if volver_a_jugar():
                letras_incorrectas = ''
                letras_correctas = ''
                G_completado = False
                G_perdido = False
                palabra_secreta = Palabra_aleatoria(palabras)
                continue 
            else: 
                break

        # Let the player type in a palabra.
        supongo = adivina(letras_incorrectas + letras_correctas)
        if supongo in palabra_secreta:
            letras_correctas = letras_correctas + supongo
            G_completado = palabrometro(letras_correctas, palabra_secreta)
        else:
            letras_incorrectas = letras_incorrectas + supongo
            G_perdido = contador(letras_incorrectas, palabra_secreta)


if __name__ == "__main__":
    iniciador()
```
