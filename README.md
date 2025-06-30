
def menu():
    print("\nSuper cool calculatrice qui n'a pas de nom officiel!! 👾”)
    print("------------------------------------------------")
    print("\n1. Calculer un pourboire 💰 \n2. Convertir des unités 🏋️\n3. Effectuer un calcul mathématique ➕ \n4. Convertir des devises 💱\n5. Générer un nombre aléatoire 🔢\n6. Quitter ✌️") 
    while True:
        choix = input("\nVeuillez choisir une option (1-6) : ")
        print("--------------------------------------------")
        if choix == "1":
            calcul_pourboire()
            menu()
        elif choix == "2":
            conversion_unites()
            menu()
        elif choix == "3":
            calcul_math()
            menu()
        elif choix == "4":
            conversion_monetaire()
            menu()
        elif choix == "5":
            generateur_aleatoire()
            menu()
        elif choix == "6":
            print("Merci de votre visite ! A la prochaine !")
            break
        else:
            print("Option invalide! Veuillez choisir un option entre 1-6")
            menu()

def calcul_pourboire():
        # Demander à l'utilisateur de choisir l'option de pourcentage
    print("\nChoisissez un pourcentage pour le pourboire: \n1. 15% \n2. 18% \n3. 20% \n4. Pourcentage personnalisé")
    
    choix = int(input("Entrez votre choix (1-3): "))
    
    if choix == 4:
        pourcent = float(input("Entrez votre pourcentage personnalisé : "))
    else:
        if choix == 1:
            pourcent = 15
        elif choix == 2:
            pourcent = 18
        elif choix == 3:
            pourcent = 20
        else:
            print("Choix invalide.")
            exit()
    
    # Saisie du sous-total
    sousT = float(input("Sous-total : "))
    
    # Calcul du pourboire
    pourboire = sousT * (pourcent / 100)
    
    # Demander à l'utilisateur s'il veut diviser la facture
    diviser = input("Souhaitez-vous diviser la facture entre plusieurs personnes ? (O/N) : ").lower()
    
    # Si oui, demander combien de personnes
    if diviser == "o":
        nombre_personnes = int(input("Combien de personnes ? "))
        montant_par_personne = (sousT + pourboire) / nombre_personnes
        print(f"Montant par personne : {montant_par_personne:.2f}$")
    else:
        print(f"Pourboire : {pourboire:.2f}$")
    
    # Calcul du montant total (sous-total + pourboire)
    t_final = sousT + pourboire
    print(f"Montant total : {t_final:.2f}$")


def conversion_unites():
    while True: 
        print("Type de conversion :")
        print("1. Longueur (km, m, cm, mm, miles, feet, inches) \n2. Température (Celsius, Fahrenheit, Kelvin \n3. Poids (lb, kg, oz, etc.) \n4. Quitte ")
        choix_type = int(input("Votre choix (1-4) : "))
        
        if choix_type == 4:  # Quit
            menu()
    
    
        elif choix_type == 1:  # Longueur
            print("\nUnités disponibles : \n1. km \n2. m \n3. cm \n4. mm \n5. miles \n6. feet \n7. inches")
            source = int(input("Unité de départ (1-7) : "))
            if source not in range(1, 8):
                print("Unité source invalide!")
                continue
    
            cible = int(input("Unité cible (1-7) : "))
            if cible not in range(1, 8):
                print("Unité cible invalide!")
                continue
    
            valeur = float(input("Valeur à convertir : "))
    
            # Convert source to meters
            if source == 1:
                valeur_m = valeur * 1000
                usource = "km"
            elif source == 2:
                valeur_m = valeur
                usource = "m"
            elif source == 3:
                valeur_m = valeur / 100
                usource = "cm"
            elif source == 4:
                valeur_m = valeur / 1000
                usource = "mm"
            elif source == 5:
                valeur_m = valeur * 1609.34
                usource = "miles"
            elif source == 6:
                valeur_m = valeur * 0.3048
                usource = "feet"
            elif source == 7:
                valeur_m = valeur * 0.0254
                usource = "inches"
    
            # Convert meters to target
            if cible == 1:
                result = valeur_m / 1000
                ucible = "km"
            elif cible == 2:
                result = valeur_m
                ucible = "m"
            elif cible == 3:
                result = valeur_m * 100
                ucible = "cm"
            elif cible == 4:
                result = valeur_m * 1000
                ucible = "mm"
            elif cible == 5:
                result = valeur_m / 1609.34
                ucible = "miles"
            elif cible == 6:
                result = valeur_m / 0.3048
                ucible = "feet"
            elif cible == 7:
                result = valeur_m / 0.0254
                ucible = "inches"
    
            print(f"Résultat : {valeur} {usource} = {result:.2f} {ucible}\n")
    
        elif choix_type == 2:  # Température
            print("\nUnités disponibles : \n1. Celsius (C) \n2. Fahrenheit (F) \n3. Kelvin (K)")
            source = int(input("Unité de départ (1-3) : "))
            if source not in range(1, 4):
                print("Unité source invalide!")
                continue
    
            cible = int(input("Unité cible (1-3) : "))
            if cible not in range(1, 4):
                print("Unité cible invalide!")
                continue
    
            valeur = float(input("Valeur à convertir : "))
    
            if source == 1:  # Celsius
                usource = "C"
                if cible == 2:
                    result = (valeur * 9 / 5) + 32
                    ucible = "F"
                elif cible == 3:
                    result = valeur + 273.15
                    ucible = "K"
                else:
                    result = valeur
                    ucible = "C"
            elif source == 2:  # Fahrenheit
                usource = "F"
                if cible == 1:
                    result = (valeur - 32) * 5 / 9
                    ucible = "C"
                elif cible == 3:
                    result = (valeur - 32) * 5 / 9 + 273.15
                    ucible = "K"
                else:
                    result = valeur
                    ucible = "F"
            elif source == 3:  # Kelvin
                usource = "K"
                if cible == 1:
                    result = valeur - 273.15
                    ucible = "C"
                elif cible == 2:
                    result = (valeur - 273.15) * 9 / 5 + 32
                    ucible = "F"
                else:
                    result = valeur
                    ucible = "K"
            elif source == 4:
                menu()
    
            print(f"Résultat : {valeur} {usource} = {result:.2f} {ucible}\n")
    
        elif choix_type == 3:  # Poids
            print("\nUnités disponibles :\n1. kg \n2. g \n3. lbs \n4. oz")
            source = int(input("Unité de départ (1-5) : "))
            cible = int(input("Unité cible (1-5) : "))
            valeur = float(input("Valeur à convertir : "))
    
            if source == 1:
                valeur_kg = valeur
                usource = "kg"
            elif source == 2:
                usource = "g"
                valeur_kg = valeur / 1000
            elif source == 3:
                usource = "lbs"
                valeur_kg = valeur * 0.453592
            elif source == 4:
                usource = "oz"
                valeur_kg = valeur * 0.0283495
            else:
                print("Unité source invalide!")
                continue
    
            if cible == 1:
                ucible = "kg"
                result = valeur_kg
            elif cible == 2:
                ucible = "g"
                result = valeur_kg * 1000
            elif cible == 3:
                ucible = "lbs"
                result = valeur_kg / 0.453592
            elif cible == 4:
                ucible = "oz"
                result = valeur_kg / 0.0283495
            else:
                print("Unité cible invalide!")
                continue
    
            print(f"Résultat : {valeur} {usource} = {result:.2f} {ucible}\n")
    
        else:
            print("Choix invalide. Veuillez entrer 1, 2, 3, ou 4.")
    
def calcul_math():
    #options 
    print("\nCalcul disponible : \n1. Addition (+) \n2. Soustraction (-) \n3. Multiplication (x) \n4. Division (÷)\n5. Racine Carrée \n6. Sin, Cos, Tan")
    choix = int(input("\nChoisissez le calcul que vous souhaitez effectuer (1-7): "))
    print("------------------------------------------------")
    
    
    if choix == 1:
        while True:
            v1 = int(input("Valeur 1 : "))
            v2 = int(input("Valeur 2 : "))
            rep = v1 + v2
            print(f"{v1} + {v2} = {rep}")
            quit = input("quit? (Oui/Non) : ")
            if quit == ("oui").lower():
                break
            else:
                choix == 1
    if choix == 2:
        while True:
            v1 = int(input("Valeur 1 : "))
            v2 = int(input("Valeur 2 : "))
            rep = v1 - v2
            print(f"{v1} - {v2} = {rep}")
            quit = input("quit? (Oui/Non) : ")
            if quit == ("oui").lower():
                break
            else:
                choix == 2
    if choix == 3:
        while True:
            v1 = int(input("Valeur 1 : "))
            v2 = int(input("Valeur 2 : "))
            rep = v1 * v2
            print(f"{v1} x {v2} = {rep}")
            quit = input("quit? (Oui/Non) : ")
            if quit == ("oui").lower():
                break
            else:
                choix == 3
    
    if choix == 4:
        while True:
            v1 = int(input("Valeur 1 : "))
            v2 = int(input("Valeur 2 : "))
            rep = v1 / v2
            print(f"{v1} ÷ {v2} = {rep}")
            quit = input("quit? (Oui/Non) : ")
            if quit == ("oui").lower():
                break
            else:
                choix == 4
    if choix == 5:
        while True:
            import math
            v1 = int(input("Valeur : "))
            print(f" La racine carrée de {v1} est {math.sqrt(v1)}")
            quit = input("quit? (Oui/Non) : ")
            if quit == ("oui").lower():
                break
            else:
                choix == 5
    if choix == 6:
        print("\n1. Sin \n2. Cos \n3. Tan")
        choix2 = int(input("(1-3): "))
        print("------------------------------------------------")
        if choix2 == 1:
            while True:
                import math
                v1 = int(input("Valeur : "))
                print(f"\nsin{v1}º = {round(math.sin(v1),3)}")
                quit = input("quit? (Oui/Non) : ")
                if quit == ("oui").lower():
                    break
                else:
                    choix2 == 2
        elif choix2 == 2:
            while True:
                import math
                v1 = int(input("Valeur : "))
                print(f"\nCos{v1}º = {round(math.cos(v1),3)}")
                quit = input("quit? (Oui/Non) : ")
                if quit == ("oui").lower():
                    break
                else:
                    choix2 == 2
        elif choix2 == 3:
            while True:
                import math
                v1 = int(input("Valeur : "))
                print(f"\ntan{v1}º = {round(math.tan(v1),3)}")
                quit = input("quit? (Oui/Non) : ")
                if quit == ("oui").lower():
                    break
                else:
                    choix2 == 2
    
def conversion_monetaire():
    while True:
        print("Type de conversion monétaire : \n1. CAD (Canadian Dollar) \n2. USD (US Dollar) \n3. EUR (Euro) \n4. PESOS \n5. FRANC \n6. British Pound \n7. Quitte")
        
        source = int(input("Choisissez votre devise source (1-6) : "))
    
        cible = int(input("Devise cible (1-6) : "))
     
        
        montant = float(input("Entrez le montant à convertir : "))
        
        if source == 1:
            rate_to_CAD = 1      # CAD to CAD
        elif source == 2:
            rate_to_CAD = 1.35   # USD to CAD
        elif source == 3:
            rate_to_CAD = 1.45   # EUR to CAD
        elif source == 4:
            rate_to_CAD = 0.067  # PESOS to CAD
        elif source == 5:
            rate_to_CAD = 1.59   # FRANC to CAD
        elif source == 6:
            rate_to_CAD = 1.75   # British Pound to CAD
    
        montant_CAD = montant * rate_to_CAD
        
        if cible == 1:
            rate_CAD = 1      # CAD to CAD
        elif cible == 2:
            rate_CAD = 0.74   # CAD to USD
        elif cible == 3:
            rate_CAD = 0.69   # CAD to EUR
        elif cible == 4:
            rate_CAD = 14.99  # CAD to PESOS
        elif cible == 5:
            rate_CAD = 0.63   # CAD to FRANC
        elif cible == 6:
            rate_CAD = 0.57   # CAD to British Pound
    
        result = montant_CAD * rate_CAD
        
        devise = ["CAD", "USD", "EUR", "PESOS", "FRANC", "British Pound"]
        print(f"Résultat: {montant} {devise[source-1]} = {result:.2f} {devise[cible-1]}")
        
        cont = input("\nSouhaitez-vous faire une autre conversion? (O/N) : ")
            
def generateur_aleatoire():
    import random
    vmin = int(input("Entrez la valeur minimal : "))
    vmax = int(input("Entrez la valeur maximale : "))
    print(f"Nombre aléatoire généré : {random.randint(vmin, vmax)}") 
    
menu()
