#AHORCADO

 
CODEBABES
 
 [![1.png](https://i.postimg.cc/v8JsrSC7/1.png)](https://postimg.cc/vDtkMXYD)


```python
import random
import os


if __name__ == "__main__":
    Idioma = int(input("!Hola Bienvenido!\nSelecciona el idioma del juego con el numero que tiene\n1.Español\n2.English\n3.Deutsch\n4.Français\n"))
    
    # Limpia el terminal
    os.system('clear')
    
    if Idioma == 1:
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
        
        
        palabras = 'café crema estrella explosión guitarra plástico navaja martillo libros lápiz lapicero aluminio embarcación letra agujeta ventana librería sonido universidad rueda perro llaves camisa pelo papá sillón felicidad catre teclado servilleta escuela pantalla sol codo tenedor estadística mapa agua mensaje lima cohete rey edificio césped presidencia hojas parlante colegio granizo pestaña lámpara mano monitor flor música hombre tornillo habitación velero abuela abuelo palo satélite templo lentes bolígrafo plato nube gobierno botella castillo enano casa libro persona planeta televisor guantes metal teléfono proyector mono muela petróleo remate debate anillo cuaderno ruido pared taladro herramienta cartas chocolate anteojos impresora caramelos luces angustia zapato bomba lluvia ojo corbata periódico diente planta buzo oficina persiana puerta tío silla ensalada pradera zoológico candidato deporte recipiente diarios fotografía ave hierro refugio pantalón barco carne nieve tecla humedad pistola departamento celular tristeza hipopótamo sofá cama árbol mesada discurso auto cinturón famoso madera lentejas piso maletín reloj diputado cuchillo desodorante candado luz montañas computadora radio moño cuadro calor partido teatro fiesta bala auriculares hormiga babuino tejón murciélago oso castor camello gato almeja cobra puma coyote cuervo ciervo perro burro pato águila hurón zorro rana cabra ganso halcón león lagarto llama topo mono alce ratón mula tritón nutria búho panda loro paloma pitón conejo carnero rata cuervo rinoceronte salmón foca tiburón oveja zorrillo perezoso serpiente araña cigüeña cisne tigre sapo trucha pavo tortuga comadreja ballena lobo wombat cebra'.split()
        
        
        # Esta funcion devuelve un string aleatorio de la lista de strings
        def Palabra_aleatoria(lista_palabras):
        
            # Indice es igual al valor de un numero aleatorio entero
            indice = random.randint(0, len(lista_palabras) - 1)
            
            # comprueba el tamaño de la palabra de acuerdo a la Dificultad
            n = len(lista_palabras[indice])
            if Dificultad == 1 :
                if n <= 5:
                    return lista_palabras[indice]
                    
            elif Dificultad == 2 :
                if n > 5 and 8 > n :
                    return lista_palabras[indice]
                    
            elif Dificultad == 3 :
                if 8 <= n :
                    return lista_palabras[indice]
                    
            # Si no se cumplen las condiciones se vuelve a llamar a ella misma
            return Palabra_aleatoria(lista_palabras)
        
        # Esta funcion muestra el dibujo del hangman y la interface
        def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):
        
            # Limpia el terminal
            os.system('clear')
            
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
            
            # muestra el contador al jugador
            print(f"te quedan {len(animacion)-len(letras_incorrectas)-1} intentos")
        
        
        # Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
        def adivina(adivinado):    
            while True:
                print('adivina la palabra.')
                supongo = input().lower()
                if len(supongo) != 1:
                    print('porfavor ingresa una sola letra.')
                elif supongo in adivinado:
                    print('Ya haz adivinado esta letra. intenta de nuevo.')
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
        
        Dificultad = int(input("Selecciona una dificulatad\n1.Facil\n2.Normal\n3.Dificil\n"))
        
        #inicia el codigo llamando la funcion iniciador
        iniciador()
            
    elif Idioma == 2:
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
        
        
        palabras = 'coffee cream star explosion guitar plastic razor hammer book pencil pen aluminum boat letter shoelace window bookstore sound college wheel dog keys shirt hair dad chair happiness cot keyboard napkin school screen sun elbow fork statistics map water message lime rocket king building lawn chair leaf talking school hail tab lamp hand monitor flower music man screw room sailboat grandmother grandfather stick satellite temple glasses pen plate cloud government bottle castle dwarf house book person planet television gloves metal phone projector mono grinder oil auction debate ring notebook noise wall drill tool letter chocolate glasses printer candy lights anguish shoe bomb rain eye tie newspaper tooth plant diver office blind door uncle chair salad prairie zoo applicant sport container diary photography bird iron shelter pants boat meat snow key humidity gun department cell phone sadness hippo sofa bed tree allowance speech car belt famous wood lentil floor briefcase watch deputy knife deodorant padlock light mountain computer radio bun picture heat party theater party bullet headphones ant baboon badger bat bear beaver camel cat clam cobra cougar coyote crow deer dog donkey duck eagle ferret fox frog goat goose hawk lion lizard llama mole monkey moose mouse mule newt otter owl panda parrot pigeon python rabbit ram rat crow rhino salmon seal shark sheep skunk sloth snake spider stork swan tiger toad trout turkey turtle weasel whale wolf wombat zebra'.split()
        
        
        # Esta funcion devuelve un string aleatorio de la lista de strings
        def Palabra_aleatoria(lista_palabras):
        
            # Indice es igual al valor de un numero aleatorio entero
            indice = random.randint(0, len(lista_palabras) - 1)
            
            # comprueba el tamaño de la palabra de acuerdo a la Dificultad
            n = len(lista_palabras[indice])
            if Dificultad == 1 :
                if n <= 5:
                    return lista_palabras[indice]
                    
            elif Dificultad == 2 :
                if n > 5 and 8 > n :
                    return lista_palabras[indice]
                    
            elif Dificultad == 3 :
                if 8 <= n :
                    return lista_palabras[indice]
                    
            # Si no se cumplen las condiciones se vuelve a llamar a ella misma
            return Palabra_aleatoria(lista_palabras)
        
        # Esta funcion muestra el dibujo del hangman y la interface
        def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):
        
            # Limpia el terminal
            os.system('clear')
            
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
            
            # muestra el contador al jugador
            print(f"te quedan {len(animacion)-len(letras_incorrectas)-1} intentos")
        
        
        # Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
        def adivina(adivinado):    
            while True:
                print('adivina la palabra.')
                supongo = input().lower()
                if len(supongo) != 1:
                    print('porfavor ingresa una sola letra.')
                elif supongo in adivinado:
                    print('Ya haz adivinado esta letra. intenta de nuevo.')
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
        
        Dificultad = int(input("Selecciona una dificulatad\n1.Facil\n2.Normal\n3.Dificil\n"))
        
        #inicia el codigo llamando la funcion iniciador
        iniciador()
            
        
    elif Idioma == 3:
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
        
        
        palabras = 'Kaffee, Sahne, Stern, Explosion, Gitarre, Kunststoff, Rasiermesser, Hammer, Buch, Bleistift, Stift, Aluminium, Boot, Buchstabe, Schnürsenkel, Fenster, Buchladen, Ton, Hochschule, Rad, Hund, Schlüssel, Hemd, Haar, Papa, Stuhl, Glück, Kinderbett, Tastatur, Serviette, Schule, Bildschirm, Sonne, Ellenbogen, Gabel, Statistiken, Karte, Wasser, Nachricht, Limette, Rakete, König, Gebäude, Rasen, Stuhl, Blatt, Reden, Schule, Hagel, Tab Lampe Hand Monitor Blume Musik Mann Schraube Zimmer Segelboot Großmutter Großvater Stock Satellit Tempel Brille Stift Teller Wolke Regierung Flasche Schloss Zwerg Haus Buch Person Planet Fernsehen Handschuhe Metall Telefon Projektor Mono Mühle Öl Auktion Debatte Ring Notizbuch Lärm Wand Bohrer Werkzeug Brief Schokolade Gläser Drucker Süßigkeiten Lichter Angst Schuh Bombe Regen Auge Krawatte Zeitung Zahn Pflanze Taucher Büro blind Tür Onkel Stuhl Salat Prärie Zoo Bewerber Sport Container Tagebuch Fotografie Vogel Eisen Unterschlupf Hose Boot Fleisch Schnee Schlüssel Feuchtigkeit Pistole Abteilung Handy Traurigkeit Nilpferd Schlafsofa Baum Zulage Rede Auto Gürtel berühmt Holz Linse Boden Aktentasche Uhr Stellvertreter Messer Deodorant Vorhängeschloss Licht Berg Computer Radio Brötchen Bild Hitze Party Theater Party Kugel Kopfhörer Ameise Pavian Dachs Fledermaus Bär Biber Kamel Katze Muschel Kobra Puma Kojote Krähe Hirsch Hund Esel Ente Adler Frettchen Fuchs Frosch Ziege Gans Falke Löwe Eidechse Lama Maulwurf Affe Elch Maus Maultier Molch Otter Eule Panda Papagei Taube Python Kaninchen Widder Ratte Krähe Nashorn Lachs Robbe Hai Schaf Stinktier Faultier Schlange Spinne Storch Schwan Tiger Kröte Forelle Truthahn Schildkröte Wiesel Wal Wolf Wombat Zebra'.split()
        
        
        # Esta funcion devuelve un string aleatorio de la lista de strings
        def Palabra_aleatoria(lista_palabras):
        
            # Indice es igual al valor de un numero aleatorio entero
            indice = random.randint(0, len(lista_palabras) - 1)
            
            # comprueba el tamaño de la palabra de acuerdo a la Dificultad
            n = len(lista_palabras[indice])
            if Dificultad == 1 :
                if n <= 5:
                    return lista_palabras[indice]
                    
            elif Dificultad == 2 :
                if n > 5 and 8 > n :
                    return lista_palabras[indice]
                    
            elif Dificultad == 3 :
                if 8 <= n :
                    return lista_palabras[indice]
                    
            # Si no se cumplen las condiciones se vuelve a llamar a ella misma
            return Palabra_aleatoria(lista_palabras)
        
        # Esta funcion muestra el dibujo del hangman y la interface
        def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):
        
            # Limpia el terminal
            os.system('clear')
            
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
            
            # muestra el contador al jugador
            print(f"te quedan {len(animacion)-len(letras_incorrectas)-1} intentos")
        
        
        # Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
        def adivina(adivinado):    
            while True:
                print('adivina la palabra.')
                supongo = input().lower()
                if len(supongo) != 1:
                    print('porfavor ingresa una sola letra.')
                elif supongo in adivinado:
                    print('Ya haz adivinado esta letra. intenta de nuevo.')
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
        
        Dificultad = int(input("Selecciona una dificulatad\n1.Facil\n2.Normal\n3.Dificil\n"))
        
        #inicia el codigo llamando la funcion iniciador
        iniciador()
            
    
    else:
        
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
        
        
        palabras = 'café crème étoile explosions guitare plastique rasoir marteau livre crayon stylo aluminium bateau lettre lacet fenêtre librairie son collège roue chien clés chemise cheveux papa chaise bonheur lit bébé clavier serviette école écran soleil coude fourchette statistiques carte eau messages citron vert fusée roi bâtiment chaise de jardin feuille parler école grêle languette lampe main varan fleur musique homme vis salle voilier grand-mère grand-père bâton satellite temple verres stylo assiette nuage gouvernement bouteille château nain maison livre personne planète télévision gants métal téléphone projecteur mono meuleuse huile vente aux enchères débat anneau carnets bruit mur perceuse outil lettre chocolat verres imprimante bonbon lumière angoisse chaussure bombe pluie œil attacher journal dent plante plongeur bureau aveugle porte oncle chaise salade prairie zoo demandeur sport récipient journal intime photographie oiseau fer abri pantalon bateau viande neige clé humidité pistolet département téléphone portable tristesse hippopotame canapé lit arbre allocation parole voiture ceinture célèbre bois lentille étage mallette regarder député couteau déodorant cadenas lumière montagne ordinateur radio chignon image chaleur fête théâtre fête balle écouteurs fourmi babouin blaireau chauve-souris ours castor chameau chat palourde cobra couguar coyote corbeau cerf chien âne canard aigle furet renard grenouille chèvre oie faucon lion lézard lama taupe singe orignal souris mule triton loutre chouette panda perroquet pigeon python lapin bélier rat corbeau rhinocéros saumon phoque requin mouton mouffette paresse serpent araignée cigogne cygne tigre crapaud truite dinde tortue belette baleine loup wombat zèbre'.split()
        
        
        # Esta funcion devuelve un string aleatorio de la lista de strings
        def Palabra_aleatoria(lista_palabras):
        
            # Indice es igual al valor de un numero aleatorio entero
            indice = random.randint(0, len(lista_palabras) - 1)
            
            # comprueba el tamaño de la palabra de acuerdo a la Dificultad
            n = len(lista_palabras[indice])
            if Dificultad == 1 :
                if n <= 5:
                    return lista_palabras[indice]
                    
            elif Dificultad == 2 :
                if n > 5 and 8 > n :
                    return lista_palabras[indice]
                    
            elif Dificultad == 3 :
                if 8 <= n :
                    return lista_palabras[indice]
                    
            # Si no se cumplen las condiciones se vuelve a llamar a ella misma
            return Palabra_aleatoria(lista_palabras)
        
        # Esta funcion muestra el dibujo del hangman y la interface
        def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):
        
            # Limpia el terminal
            os.system('clear')
            
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
            
            # muestra el contador al jugador
            print(f"te quedan {len(animacion)-len(letras_incorrectas)-1} intentos")
        
        
        # Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
        def adivina(adivinado):    
            while True:
                print('adivina la palabra.')
                supongo = input().lower()
                if len(supongo) != 1:
                    print('porfavor ingresa una sola letra.')
                elif supongo in adivinado:
                    print('Ya haz adivinado esta letra. intenta de nuevo.')
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
        
        Dificultad = int(input("Selecciona una dificulatad\n1.Facil\n2.Normal\n3.Dificil\n"))
        
        #inicia el codigo llamando la funcion iniciador
        iniciador()
            
        
        
    
    
    
    
```

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


palabras = 'café crema estrella explosión guitarra plástico navaja martillo libros lápiz lapicero aluminio embarcación letra agujeta ventana librería sonido universidad rueda perro llaves camisa pelo papá sillón felicidad catre teclado servilleta escuela pantalla sol codo tenedor estadística mapa agua mensaje lima cohete rey edificio césped presidencia hojas parlante colegio granizo pestaña lámpara mano monitor flor música hombre tornillo habitación velero abuela abuelo palo satélite templo lentes bolígrafo plato nube gobierno botella castillo enano casa libro persona planeta televisor guantes metal teléfono proyector mono muela petróleo remate debate anillo cuaderno ruido pared taladro herramienta cartas chocolate anteojos impresora caramelos luces angustia zapato bomba lluvia ojo corbata periódico diente planta buzo oficina persiana puerta tío silla ensalada pradera zoológico candidato deporte recipiente diarios fotografía ave hierro refugio pantalón barco carne nieve tecla humedad pistola departamento celular tristeza hipopótamo sofá cama árbol mesada discurso auto cinturón famoso madera lentejas piso maletín reloj diputado cuchillo desodorante candado luz montañas computadora radio moño cuadro calor partido teatro fiesta bala auriculares hormiga babuino tejón murciélago oso castor camello gato almeja cobra puma coyote cuervo ciervo perro burro pato águila hurón zorro rana cabra ganso halcón león lagarto llama topo mono alce ratón mula tritón nutria búho panda loro paloma pitón conejo carnero rata cuervo rinoceronte salmón foca tiburón oveja zorrillo perezoso serpiente araña cigüeña cisne tigre sapo trucha pavo tortuga comadreja ballena lobo wombat cebra'.split()


# Esta funcion devuelve un string aleatorio de la lista de strings
def Palabra_aleatoria(lista_palabras):

    # Indice es igual al valor de un numero aleatorio entero
    indice = random.randint(0, len(lista_palabras) - 1)

    # Retorna la palabra que esta en lista_palabras con valor de indice
    return lista_palabras[indice]

# Esta funcion muestra el dibujo del hangman y la interface
def pantalla(animacion, letras_incorrectas, letras_correctas, palabra_secreta):

    # Limpia el terminal
    os.system('clear')
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
    
    # muestra el contador al jugador
    print(f"te quedan {len(animacion)-len(letras_incorrectas)-1} intentos")


# Retorna la letra que el jugador ingreso. Esta funcion se asegura de que el jugador ingrese solo una letra y no otra cosa
def adivina(adivinado):    
    while True:
        print('adivina la palabra.')
        supongo = input().lower()
        if len(supongo) != 1:
            print('porfavor ingresa una sola letra.')
        elif supongo in adivinado:
            print('Ya haz adivinado esta letra. intenta de nuevo.')
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
