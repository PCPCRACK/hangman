 # CODEBABES
 [![1.png](https://i.postimg.cc/v8JsrSC7/1.png)](https://postimg.cc/vDtkMXYD)
 
 Busquen el nombre del equipo en youtube si quieren aprender a programar
 ## Integrantes
 - ppssss yo mero

 # game
```python
import random
import os

def Español():
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
        else:
                    Español()
                    
        # Si no se cumplen las condiciones se vuelve a llamar a ella misma
        return Palabra_aleatoria(lista_palabras)
        
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

def English():
    animation = ['''
        
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
        
        
    words = 'coffee cream star explosion guitar plastic razor hammer book pencil pen aluminum boat letter shoelace window bookstore sound college wheel dog keys shirt hair dad chair happiness cot keyboard napkin school screen sun elbow fork statistics map water message lime rocket king building lawn chair leaf talking school hail tab lamp hand monitor flower music man screw room sailboat grandmother grandfather stick satellite temple glasses pen plate cloud government bottle castle dwarf house book person planet television gloves metal phone projector mono grinder oil auction debate ring notebook noise wall drill tool letter chocolate glasses printer candy lights anguish shoe bomb rain eye tie newspaper tooth plant diver office blind door uncle chair salad prairie zoo applicant sport container diary photography bird iron shelter pants boat meat snow key humidity gun department cell phone sadness hippo sofa bed tree allowance speech car belt famous wood lentil floor briefcase watch deputy knife deodorant padlock light mountain computer radio bun picture heat party theater party bullet headphones ant baboon badger bat bear beaver camel cat clam cobra cougar coyote crow deer dog donkey duck eagle ferret fox frog goat goose hawk lion lizard llama mole monkey moose mouse mule newt otter owl panda parrot pigeon python rabbit ram rat crow rhino salmon seal shark sheep skunk sloth snake spider stork swan tiger toad trout turkey turtle weasel whale wolf wombat zebra'.split()
        
        
    # This function returns a random string from the list of strings
    def Random_word(list_words):
    
        # index is equal to the value of an integer random number
        indice = random.randint(0, len(list_words) - 1)
        
        # Check the size of the word according to the Difficulty
        n = len(list_words[indice])
        if Dificulty == 1 :
            if n <= 5:
                return list_words[indice]
                
        elif Dificulty == 2 :
            if n > 5 and 8 > n :
                return list_words[indice]
                
        elif Dificulty == 3 :
            if 8 <= n :
                return list_words[indice]
        else:
                English()
                
        # If the conditions are not met, it calls itself again
        return Random_word(list_words)
    
    # This function shows the hangman's drawing and the interface
    def display(animation, wrong_letters, correct_letters, secret_word):
    
        # clean terminal
        os.system('cls')
        
        print(animation[len(wrong_letters)])
        print()
    
        print('missing letters:', end=' ')
        for palabra in wrong_letters:
            print(palabra, end=' ')
        print()
        PL_guesstda = ''
    
        # Replace PL_guesstda with the correct letters
        for i in range(len(secret_word)): 
            if secret_word[i] in correct_letters:
                PL_guesstda += secret_word[i]
            else:
                PL_guesstda += '_'
    
        # Shows the secret word with spaces between each word
        for palabra in PL_guesstda: 
            print(palabra, end=' ')
        print()
        
        # show the counter to the player
        print(f"you have left {len(animation)-len(wrong_letters)-1} Attempts")
    
    
    # Returns the letter the player entered. This function makes sure that the player enters only one letter and not something else.
    def guesst(guesstdo):    
        while True:
            print('guess the word.')
            guess = input().lower()
            if len(guess) != 1:
                print('please enter a single letter.')
            elif guess in guesstdo:
                print('You have already guessed this letter. try again.')
            elif guess not in 'abcdefghijklmnopqrstuvwxyz':
                print('please a letter')
            else:
                return guess
    
    
    # This function returns true if the player wants to play again, otherwise it returns false.
    def play_again():
        print('Do you want to play again? (yes or no)')
        return input().lower().startswith('y')
    
    
    # See if the player guessed the word
    def meter(correct_letters, secret_word):
        letras_encontradas = True
        for i in range(len(secret_word)):
            if secret_word[i] not in correct_letters:
                letras_encontradas = False
                break
        return letras_encontradas
    
    
    # Look if I guessed many times and lost
    def counter(wrong_letters, secret_word):
        if len(wrong_letters) == len(animation) - 1:
            return True
        return False
    
    
    def main():
        """main is the starting point of the code"""
    
        # Define parameters
        wrong_letters = ''
        correct_letters = ''
        G_completed = False
        G_lost = False
    
        # Call the Random_Word function
        secret_word = Random_word(words)
    
        # call the display function
        while True:
            display(animation, wrong_letters, correct_letters, secret_word)
    
            if G_completed or G_lost:
                if G_completed:
                    print('yeah, the secret word is "' + secret_word + '" !you win!')
                else:
                    print('you have guessed too many times!\nafter of ' + str(len(wrong_letters)) + ' attempts you failed guessing, the correct word was "' + secret_word + '"')
    
                # Asks if the player wants to play again, but only if the game is over
                if play_again():
    
                    # Redefine the parameters
                    wrong_letters = ''
                    correct_letters = ''
                    G_completed = False
                    G_lost = False
    
                    # Call the function Random_word
                    secret_word = Random_word(words)
                    continue 
                else: 
                    break
    
    
            # call the guesst function
            guess = guesst(wrong_letters + correct_letters)
    
            # Si guess esta en secret_word 
            if guess in secret_word:
    
                # correct letters is equal to its previous value plus the value of guess
                correct_letters = correct_letters + guess
    
                # call the function meter
                G_completed = meter(correct_letters, secret_word)
            else:
    
                # wrong letters is equal to its previous value plus the value of guess
                wrong_letters = wrong_letters + guess
    
                # Call the counter function
                G_lost = counter(wrong_letters, secret_word)
    
    Dificulty = int(input("Select a difficulty\n1.Easy\n2.Normal\n3.Hard\n"))
    
    # start the code by calling the main function
    main()

def Deutsch():
    Animation = ['''
        
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
        
        
    Wörter = 'Kaffee Sahne Stern Explosion Gitarre Kunststoff Rasiermesser Hammer Buch Bleistift Stift Aluminium Boot Buchstabe Schnürsenkel Fenster Buchladen Ton Hochschule Rad Hund Schlüssel Hemd Haar Papa Stuhl Glück Kinderbett Tastatur Serviette Schule Bildschirm Sonne Ellenbogen Gabel Statistiken Karte Wasser Nachricht Limette Rakete König Gebäude Rasen Stuhl Blatt Reden Schule Hagel Tab Lampe Hand Monitor Blume Musik Mann Schraube Zimmer Segelboot Großmutter Großvater Stock Satellit Tempel Brille Stift Teller Wolke Regierung Flasche Schloss Zwerg Haus Buch Person Planet Fernsehen Handschuhe Metall Telefon Projektor Mono Mühle Öl Auktion Debatte Ring Notizbuch Lärm Wand Bohrer Werkzeug Brief Schokolade Gläser Drucker Süßigkeiten Lichter Angst Schuh Bombe Regen Auge Krawatte Zeitung Zahn Pflanze Taucher Büro blind Tür Onkel Stuhl Salat Prärie Zoo Bewerber Sport Container Tagebuch Fotografie Vogel Eisen Unterschlupf Hose Boot Fleisch Schnee Schlüssel Feuchtigkeit Pistole Abteilung Handy Traurigkeit Nilpferd Schlafsofa Baum Zulage Rede Auto Gürtel berühmt Holz Linse Boden Aktentasche Uhr Stellvertreter Messer Deodorant Vorhängeschloss Licht Berg Computer Radio Brötchen Bild Hitze Party Theater Party Kugel Kopfhörer Ameise Pavian Dachs Fledermaus Bär Biber Kamel Katze Muschel Kobra Puma Kojote Krähe Hirsch Hund Esel Ente Adler Frettchen Fuchs Frosch Ziege Gans Falke Löwe Eidechse Lama Maulwurf Affe Elch Maus Maultier Molch Otter Eule Panda Papagei Taube Python Kaninchen Widder Ratte Krähe Nashorn Lachs Robbe Hai Schaf Stinktier Faultier Schlange Spinne Storch Schwan Tiger Kröte Forelle Truthahn Schildkröte Wiesel Wal Wolf Wombat Zebra'.split()
        
    
    # Diese Funktion gibt eine zufällige Zeichenfolge aus der Liste der Zeichenfolgen zurück
    def Zufalliges_Wort(Wortliste):
    
        # Der Index entspricht dem Wert einer zufälligen Ganzzahl
        Index = random.randint(0, len(Wortliste) - 1)
        
        # Überprüfen Sie die Größe des Wortes entsprechend der Schwierigkeit
        n = len(Wortliste[Index])
        if Schwierigkeit == 1 :
            if n <= 5:
                return Wortliste[Index]
                
        elif Schwierigkeit == 2 :
            if n > 5 and 8 > n :
                return Wortliste[Index]
                
        elif Schwierigkeit == 3 :
            if 8 <= n :
                return Wortliste[Index]
        else:
                Deutsch()
                
        # Wenn die Bedingungen nicht erfüllt sind, ruft es sich erneut auf
        return Zufalliges_Wort(Wortliste)
    
    # Diese Funktion zeigt die Zeichnung des Henkers und die Benutzeroberfläche
    def Bildschirm(Animation, falsche_Buchstaben, korrekte_Buchstaben, Geheimwort):
    
        # sauberes Terminal
        os.system('cls')
        
        print(Animation[len(falsche_Buchstaben)])
        print()
    
        print('fehlende Buchstaben:', end=' ')
        for palabra in falsche_Buchstaben:
            print(palabra, end=' ')
        print()
        PL_erratenda = ''
    
        # Ersetzen Sie PL_erratenda durch die richtigen Buchstaben
        for i in range(len(Geheimwort)): 
            if Geheimwort[i] in korrekte_Buchstaben:
                PL_erratenda += Geheimwort[i]
            else:
                PL_erratenda += '_'
    
        # Zeigt das geheime Wort mit Leerzeichen zwischen den einzelnen Wörtern an
        for palabra in PL_erratenda: 
            print(palabra, end=' ')
        print()
        
        # Zeigen Sie dem Spieler den Schalter
        print(f"Du bist gegangen {len(Animation)-len(falsche_Buchstaben)-1} Versuche")
    
    
    # Gibt den vom Spieler eingegebenen Buchstaben zurück. Diese Funktion stellt sicher, dass der Spieler nur einen Buchstaben eingibt und nichts anderes.
    def erraten(erratendo):    
        while True:
            print('vermisse das Wort')
            glauben = input().lower()
            if len(glauben) != 1:
                print('Bitte geben Sie einen einzelnen Buchstaben ein.')
            elif glauben in erratendo:
                print('Sie haben diesen Brief bereits verpasst. versuchen Sie es erneut.')
            elif glauben not in 'abcdefghijklmnopqrstuvwxyz':
                print('Bitte einen Brief')
            else:
                return glauben
    
    
    # Diese Funktion gibt true zurück, wenn der Spieler erneut spielen möchte, andernfalls gibt sie false zurück.
    def nochmal_abspielen():
        print('Willst du noch einmal spielen? (ja oder nein)')
        return input().lower().startswith('j')
    
    
    # Mira si el jugador adivino la palabra
    def Sprichwortometer(korrekte_Buchstaben, Geheimwort):
        letras_encontradas = True
        for i in range(len(Geheimwort)):
            if Geheimwort[i] not in korrekte_Buchstaben:
                letras_encontradas = False
                break
        return letras_encontradas
    
    
    # mira si adivino muchas veces y perdio
    def Schalter(falsche_Buchstaben, Geheimwort):
        if len(falsche_Buchstaben) == len(Animation) - 1:
            return True
        return False
    
    
    def Initiator():
        """Der Initiator ist der Ausgangspunkt des Codes"""
    
        # Parameter definieren
        falsche_Buchstaben = ''
        korrekte_Buchstaben = ''
        G_abgeschlossen = False
        G_verloren = False
    
        # Rufen Sie die Funktion Zufalliges_Wort auf
        Geheimwort = Zufalliges_Wort(Wörter)
    
        # Rufen Sie die Bildschirm-Funktion auf
        while True:
            Bildschirm(Animation, falsche_Buchstaben, korrekte_Buchstaben, Geheimwort)
    
            if G_abgeschlossen or G_verloren:
                if G_abgeschlossen:
                    print('Wenn das geheime Wort ist"' + Geheimwort + '" !Gewonnen!')
                else:
                    print('Du hast zu oft einen Fehler gemacht !\n danach' + str(len(falsche_Buchstaben)) + ' Versuche, die Sie gescheitert sind, erratenndo, das richtige Wort war "' + Geheimwort + '"')
    
                # Fragt, ob der Spieler noch einmal spielen möchte, aber nur, wenn das Spiel vorbei ist
                if nochmal_abspielen():
    
                    # Definieren Sie die Parameter neu
                    falsche_Buchstaben = ''
                    korrekte_Buchstaben = ''
                    G_abgeschlossen = False
                    G_verloren = False
    
                    # Rufen Sie die Funktion Zufalliges_Wort auf
                    Geheimwort = Zufalliges_Wort(Wörter)
                    continue 
                else: 
                    break
    
    
            # Rufen Sie die Funktion err auf
            glauben = erraten(falsche_Buchstaben + korrekte_Buchstaben)
    
            # Wenn glauben ist im Geheimwort
            if glauben in Geheimwort:
    
                # korrekte Buchstaben ist gleich seinem vorherigen Wert plus dem Wert von glauben
                korrekte_Buchstaben = korrekte_Buchstaben + glauben
    
                # Rufen Sie die Funktion Sprichwortometer auf
                G_abgeschlossen = Sprichwortometer(korrekte_Buchstaben, Geheimwort)
            else:
    
                # falsche Buchstaben ist gleich seinem vorherigen Wert plus dem Wert von glauben
                falsche_Buchstaben = falsche_Buchstaben + glauben
    
                # Rufen Sie die Zählerfunktion auf
                G_verloren = Schalter(falsche_Buchstaben, Geheimwort)
    
    Schwierigkeit = int(input("Wählen Sie einen Schwierigkeitsgrad\n1.Einfach\n2.Normal\n3.Schwer\n"))
    
    # Starten Sie den Code, indem Sie die Initiator-Funktion aufrufen
    Initiator()
            
def Français():
    animation = ['''
        
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
        
        
    mots = 'café crème étoile explosions guitare plastique rasoir marteau livre crayon stylo aluminium bateau lettre lacet fenêtre librairie son collège roue chien clés chemise cheveux papa chaise bonheur lit bébé clavier serviette école écran soleil coude fourchette statistiques carte eau messages citron vert fusée roi bâtiment chaise de jardin feuille parler école grêle languette lampe main varan fleur musique homme vis salle voilier grand-mère grand-père bâton satellite temple verres stylo assiette nuage gouvernement bouteille château nain maison livre personne planète télévision gants métal téléphone projecteur mono meuleuse huile vente aux enchères débat anneau carnets bruit mur perceuse outil lettre chocolat verres imprimante bonbon lumière angoisse chaussure bombe pluie œil attacher journal dent plante plongeur bureau aveugle porte oncle chaise salade prairie zoo demandeur sport récipient journal intime photographie oiseau fer abri pantalon bateau viande neige clé humidité pistolet département téléphone portable tristesse hippopotame canapé lit arbre allocation parole voiture ceinture célèbre bois lentille étage mallette regarder député couteau déodorant cadenas lumière montagne ordinateur radio chignon image chaleur fête théâtre fête balle écouteurs fourmi babouin blaireau chauve-souris ours castor chameau chat palourde cobra couguar coyote corbeau cerf chien âne canard aigle furet renard grenouille chèvre oie faucon lion lézard lama taupe singe orignal souris mule triton loutre chouette panda perroquet pigeon python lapin bélier rat corbeau rhinocéros saumon phoque requin mouton mouffette paresse serpent araignée cigogne cygne tigre crapaud truite dinde tortue belette baleine loup wombat zèbre'.split()
        
        
    # Cette fonction renvoie une chaîne aléatoire à partir de la liste des chaînes
    def Mot_aléatoire(liste_de_mots):
    
        # index est égal à la valeur d'un nombre entier aléatoire
        index = random.randint(0, len(liste_de_mots) - 1)
        
        # vérifier la taille du mot en fonction de la Difficulté
        n = len(liste_de_mots[index])
        if Difficulté == 1 :
            if n <= 5:
                return liste_de_mots[index]
                
        elif Difficulté == 2 :
            if n > 5 and 8 > n :
                return liste_de_mots[index]
                
        elif Difficulté == 3 :
            if 8 <= n :
                return liste_de_mots[index]
        else:
                Français()
                
        # Si les conditions ne sont pas remplies, il s'appelle à nouveau
        return Mot_aléatoire(liste_de_mots)
    
    # Cette fonction affiche le dessin du pendu et l'interface
    def filtrer(animation, fausses_lettres, lettres_correctes, mot_secret):
    
        # borne propre
        os.system('cls')
        
        print(animation[len(fausses_lettres)])
        print()
    
        print('lettres manquantes:', end=' ')
        for palabra in fausses_lettres:
            print(palabra, end=' ')
        print()
        PL_devinerda = ''
    
        # Remplacez PL_devinerda par les bonnes lettres
        for i in range(len(mot_secret)): 
            if mot_secret[i] in lettres_correctes:
                PL_devinerda += mot_secret[i]
            else:
                PL_devinerda += '_'
    
        # Affiche le mot secret avec des espaces entre chaque mot
        for palabra in PL_devinerda: 
            print(palabra, end=' ')
        print()
        
        # montrer le comptoir au joueur
        print(f"ils te donnent {len(animation)-len(fausses_lettres)-1} Tentatives")
    
    
    # Renvoie la lettre saisie par le joueur. Cette fonction garantit que le joueur n'entre qu'une seule lettre et pas autre chose.
    def deviner(devinerdo):    
        while True:
            print('devenir le mot')
            je_suppose = input().lower()
            if len(je_suppose) != 1:
                print('veuillez saisir une seule lettre.')
            elif je_suppose in devinerdo:
                print('Vous êtes venu à cette lettre. tente à nouveau.')
            elif je_suppose not in 'abcdefghijklmnopqrstuvwxyz':
                print('sil vous plaît une lettre.')
            else:
                return je_suppose
    
    
    # Cette fonction renvoie vrai si le joueur veut rejouer, sinon elle renvoie faux.
    def rejouer():
        print('Voulez-vous rejouer ? (Oui ou non)')
        return input().lower().startswith('o')
    
    
    # Voir si le joueur a deviné le mot
    def proverbomètre(lettres_correctes, mot_secret):
        lettres_trouvées = True
        for i in range(len(mot_secret)):
            if mot_secret[i] not in lettres_correctes:
                lettres_trouvées = False
                break
        return lettres_trouvées
    
    
    # Regarde si j'ai deviné plusieurs fois et perdu
    def comptoir(fausses_lettres, mot_secret):
        if len(fausses_lettres) == len(animation) - 1:
            return True
        return False
    
    
    def initiateur():
        """initiateur est le point de départ du code"""
    
        # Définir les paramètres
        fausses_lettres = ''
        lettres_correctes = ''
        G_terminé = False
        G_lost = False
    
        # Appelez la fonction Random Word
        mot_secret = Mot_aléatoire(mots)
    
        # appeler la fonction filtre
        while True:
            filtrer(animation, fausses_lettres, lettres_correctes, mot_secret)
    
            if G_terminé or G_lost:
                if G_terminé:
                    print('Si le mot secret est "' + mot_secret + '" !Gagné!')
                else:
                    print('faire devinerdo trop de fois ! \n après' + str(len(fausses_lettres)) + ' tentatives que vous avez échoué à devenir, le bon mot était "' + mot_secret + '"')
    
                # Demande si le joueur veut rejouer, mais seulement si la partie est terminée
                if rejouer():
    
                    # Redéfinir les paramètres
                    fausses_lettres = ''
                    lettres_correctes = ''
                    G_terminé = False
                    G_lost = False
    
                    # Appelez la fonction Random Word
                    mot_secret = Mot_aléatoire(mots)
                    continue 
                else: 
                    break
    
    
            # appeler la fonction deviner
            je_suppose = deviner(fausses_lettres + lettres_correctes)
    
            # Si je_suppose est dans mot_secret
            if je_suppose in mot_secret:
    
                # lettres_correctes est égal à sa valeur précédente plus la valeur de je_suppose
                lettres_correctes = lettres_correctes + je_suppose
    
                # Appelez la fonction wordword
                G_terminé = proverbomètre(lettres_correctes, mot_secret)
            else:
    
                # fausses_lettres est égal à sa valeur précédente plus la valeur de je_suppose
                fausses_lettres = fausses_lettres + je_suppose
    
                # Appelez la fonction comptoir
                G_lost = comptoir(fausses_lettres, mot_secret)
    
    Difficulté = int(input("Sélectionnez une difficulté\n1.Facile\n2.Normal\n3.Difficile\n"))
    
    # initier le code en appelant la fonction initiateur
    initiateur()
            


if __name__ == "__main__":

    # Pregunta el idioma para llamar la funcion
    Idioma = int(input("!Hola Bienvenido!\nSelecciona el idioma del juego con el numero que tiene\n1.Español\n2.English\n3.Deutsch\n4.Français\n"))

    # Limpia el terminal
    os.system('cls')

    # compara el valor de Idioma
    if Idioma == 1:
        Español()
    elif Idioma == 2:
        English()
    elif Idioma == 3:
        Deutsch()

    elif Idioma == 4:
        Français()
    else:
        print("numero invalido")
```