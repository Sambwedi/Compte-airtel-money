# Compte-airtel-money
    def __init__(self, nom_utilisateur, mot_de_passe):
        self.nom_utilisateur = nom_utilisateur
        self.mot_de_passe = mot_de_passe
        self.solde = 0.0

    def deposer(self, montant):
        if montant > 0:
            self.solde += montant
            print(f"Dépot de {montant}€ effectué. Nouveau solde : {self.solde}€")
        else:
            print("Le montant du dépôt doit être supérieur à 0.")

    def retirer(self, montant):
        if montant > 0 and montant <= self.solde:
            self.solde -= montant
            print(f"Retrait de {montant}€ effectué. Nouveau solde : {self.solde}€")
        elif montant > self.solde:
            print("Fonds insuffisants.")
        else:
            print("Le montant du retrait doit être supérieur à 0.")

    def afficher_solde(self):
        print(f"Votre solde actuel est de {self.solde}€.")

def main():
    # Demander à l'utilisateur de se connecter
    nom_utilisateur = input("Entrez votre nom : ")
    mot_de_passe = input("Entrez votre mot de passe : ")

    # Créer un compte avec le nom et mot de passe
    compte = CompteBancaire(nom_utilisateur, mot_de_passe)

    # Validation du mot de passe
    mot_de_passe_utilisateur = input("Entrez votre mot de passe pour accéder à votre compte : ")
    if mot_de_passe_utilisateur != mot_de_passe:
        print("Mot de passe incorrect. Accès refusé.")
        return

    while True:
        print("\n1. Déposer de l'argent")
        print("2. Retirer de l'argent")
        print("3. Afficher le solde")
        print("4. Quitter")
        choix = input("Que voulez-vous faire ? (1/2/3/4) : ")

        if choix == '1':
            try:
                montant = float(input("Entrez le montant à déposer : "))
                compte.deposer(montant)
            except ValueError:
                print("Veuillez entrer un montant valide.")
        elif choix == '2':
            try:
                montant = float(input("Entrez le montant à retirer : "))
                compte.retirer(montant)
            except ValueError:
                print("Veuillez entrer un montant valide.")
        elif choix == '3':
            compte.afficher_solde()
        elif choix == '4':
            print("Merci d'avoir utilisé notre service.")
            break
        else:
            print("Choix invalide. Essayez à nouveau.")

if __name__ == "__main__":
    main()
