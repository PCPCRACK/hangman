# ahorcado

```python
import random
import os


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


# Esta funcion devuelve un string aleatorio de la lista de strings
def Palabra_aleatoria(lista_palabras):

    # Indice es igual al valor de un numero aleatorio entero
    indice = random.randint(0, len(lista_palabras) - 1)

    # Retorna la palabra que esta en lista_palabras con valor de indice
    return lista_palabras[indice]

# Esta funcion muestra el dibujo del hangman y la interface
def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):

    # Limpia el terminal
    os.system('cls')
    print(animacion[len(letras_incorrectas)])
    print()

    print('letras perdidas:', end=' ')
    for palabra in letras_incorrectas:
        print(palabra, end=' ')
    print()
    PL_adivinada = ''

    # Remplaza PL_adivinada con las letras correctas
    for i in range(len(palabra_secreta)): 
        if palabra_secreta[i] in letras_correctas:
            PL_adivinada += palabra_secreta[i]
        else:
            PL_adivinada += '_'

    # Muestra la palabra secreta con espacios entre cada palabra
    for palabra in PL_adivinada: 
        print(palabra, end=' ')
    print()


# Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
def adivina(adivinado):    
    while True:
        print('adivina la palabra.')
        supongo = input().lower()
        if len(supongo) != 1:
            print('porfavor ingresa una sola letra.')
        elif supongo in adivinado:
            print('Haz adivinado la paralabra. intenta de nuevo.')
        elif supongo not in 'abcdefghijklmnopqrstuvwxyz':
            print('porfavor una letra.')
        else:
            return supongo


# Esta funcion retorna verdadero si el jugador quiere jugar otra vez sino retorna falso
def volver_a_jugar():
    print('Quieres jugar otra vez? (si o no)')
    return input().lower().startswith('s')


# Mira si el jugador adivino la palabra
def palabrometro(letras_correctas, palabra_secreta):
    letras_encontradas = True
    for i in range(len(palabra_secreta)):
        if palabra_secreta[i] not in letras_correctas:
            letras_encontradas = False
            break
    return letras_encontradas


# mira si adivino muchas veces y perdio
def contador(letras_incorrectas, palabra_secreta):
    if len(letras_incorrectas) == len(animacion) - 1:
        return True
    return False


def iniciador():
    """Iniciador es el punto de partida de el codigo"""

    # Define parametros
    letras_incorrectas = ''
    letras_correctas = ''
    G_completado = False
    G_perdido = False

    # Llama la funcion Palabra_aleatoria
    palabra_secreta = Palabra_aleatoria(palabras)

    #Llama la funcion pantalla
    while True:
        pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta)

        if G_completado or G_perdido:
            if G_completado:
                print('Si la palabra secreta es "' + palabra_secreta + '" !ganaste!')
            else:
                print('haz adivinado demaciadas veces!\ndepues de ' + str(len(letras_incorrectas)) + ' intentos fallaste adivinando, la palabra correcta era "' + palabra_secreta + '"')

            # Pregunta si el jugador quiere volver a jugar, pero solo si el juego acabo
            if volver_a_jugar():

                # Vuelve a definir los parametros 
                letras_incorrectas = ''
                letras_correctas = ''
                G_completado = False
                G_perdido = False

                # Llama la funcion Palabra_aleatoria
                palabra_secreta = Palabra_aleatoria(palabras)
                continue 
            else: 
                break


        # Llama la funcion adivina
        supongo = adivina(letras_incorrectas + letras_correctas)

        # Si supongo esta en palabra_secreta 
        if supongo in palabra_secreta:

            # # letras_correctas es igual a su valor anterior mas el valor de supongo
            letras_correctas = letras_correctas + supongo

            # Llama la funcion palabrometro
            G_completado = palabrometro(letras_correctas, palabra_secreta)
        else:

            # letras_incorrectas es igual a su valor anterior mas el valor de supongo
            letras_incorrectas = letras_incorrectas + supongo

            # Llama la funcion contador
            G_perdido = contador(letras_incorrectas, palabra_secreta)


if __name__ == "__main__":
    iniciador()
```
