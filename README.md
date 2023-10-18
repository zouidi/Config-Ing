Documentation détaillée pour les utilisateurs de Windows

Ce guide vous montrera comment configurer un environnement de test pour les projets Aries Mobile et Aries Agent sur Windows. Suivez ces étapes pour mettre en place votre environnement de développement.

**Étape 1 : Cloner les projets Aries**

1.1. Ouvrez Git Bash.

1.2. Clonez le projet Aries Mobile Test Harness en utilisant la commande suivante :
   ```bash
   git clone https://github.com/MCN-ING/aries-mobile-test-harness
   ```

1.3. Clonez le projet Aries Agent Test Harness avec la commande :
   ```bash
   git clone https://github.com/hyperledger/aries-agent-test-harness
   ```

**Étape 2 : Installation de Rancher Desktop**

2.1. Pour utiliser Rancher Desktop, vous devez d'abord activer la virtualisation WSL (Windows Subsystem for Linux). Ouvrez l'invite de commandes (cmd) en tant qu'administrateur et exécutez :
   ```bash
   wsl --install
   ```

2.2. Téléchargez Rancher Desktop à partir du lien suivant : [Télécharger Rancher Desktop](https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.10.0/Rancher.Desktop.Setup.1.10.0.msi)

**Étape 3 : Configuration de Rancher Desktop**

3.1. Ouvrez Rancher Desktop.

3.2. Dans l'onglet WSL (version 1.9.x), assurez-vous de cocher l'option "Enable networking tunnel".

**Étape 4 : Cloner le projet von-network**

4.1. Ouvrez Git Bash.

4.2. Clonez le projet von-network avec la commande :
   ```bash
   git clone https://github.com/bcgov/von-network
   ```

**Étape 5 : Configuration du projet von-network**

5.1. Ouvrez Git Bash dans le répertoire du projet "von-network".

5.2. Exécutez les commandes suivantes pour créer une image et la redémarrer :
   ```bash
   ./manage build            # Crée l'image
   ./manage start --logs     # Redémarre l'image
   ```

**Étape 6 : Configuration du projet Agent**

6.1. Ouvrez Git Bash dans le répertoire du projet Agent.

6.2. Exécutez les commandes suivantes pour construire le projet et définir des variables :
   ```bash
   ./manage build -a acapy-main

   # Définissez les variables
   $LEDGER_URL_CONFIG="http://test.bcovrin.vonx.io"
   $TAILS_SERVER_URL_CONFIG="https://tails.vonx.io"
   $AGENT_CONFIG_FILE="/aries-backchannels/acapy/auto_issuer_config.yaml"

   ./manage start -a acapy-main -b acapy-main -n
   ```

**Étape 7 : Installation de jq**

7.1. Installez l'outil jq à l'aide de Winget. Ouvrez votre terminal et exécutez la commande suivante :
   ```bash
   winget install jq
   ```

**Étape 8 : Configuration du projet Aries Mobile Test Harness**

8.1. Ouvrez Git Bash, puis naviguez vers le répertoire "aries-mobile-test-harness" en utilisant la commande "cd".

8.2. Exécutez les commandes suivantes pour construire le projet et le configurer :
   ```bash
   ./manage build -w qc_wallet

   LEDGER_URL_CONFIG=http://test.bcovrin.vonx.io ./manage run -d LambdaTest -u sylvain.rousseau -k 3nWogJYioE3aW7EwVO5b1xSqLdcALtfjTQOXt1wYLxg7UUo5tr -p Android -a lt://APP1016026831697124316551595 -b QCWallet-182-Android-Fetch-Upstream -i "AATH;http://0.0.0.0:9020" -v "AATH;http:0.0.0.0:9030" -t @bc_wallet -t @T002.1-Proof
   ```

Félicitations ! Vous avez maintenant configuré votre environnement pour travailler avec les projets Aries Mobile et Aries Agent sur Windows. Assurez-vous de suivre ces étapes attentivement pour une configuration réussie.
