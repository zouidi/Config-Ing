Documentation détaillée pour les utilisateurs Windows

Ce guide vous aidera à configurer un environnement de développement pour les projets Aries Mobile et Aries Agent sur Windows. Suivez les étapes ci-dessous pour mettre en place cet environnement.

**Étape 1 : Clonage des projets Aries avec Git**

Avant de commencer, assurez-vous d'avoir Git installé sur votre système. Si ce n'est pas déjà fait, vous pouvez le télécharger à partir de https://git-scm.com/downloads et l'installer.

1.1. Ouvrez votre terminal Git Bash.

1.2. Clonez le projet Aries Mobile Test Harness en utilisant la commande suivante :
```bash
git clone https://github.com/MCN-ING/aries-mobile-test-harness
```

1.3. Clonez le projet Aries Agent Test Harness en utilisant la commande suivante :
```bash
git clone https://github.com/hyperledger/aries-agent-test-harness
```

**Étape 2 : Installation de Rancher Desktop**

2.1. Pour utiliser Rancher Desktop, vous devez d'abord activer la virtualisation WSL (Windows Subsystem for Linux). Ouvrez l'invite de commandes (cmd) et exécutez la commande suivante :
```bash
wsl --install
```

2.2. Téléchargez et installez Rancher Desktop à partir de https://github.com/rancher-sandbox/rancher-desktop/releases/download/v1.10.0/Rancher.Desktop.Setup.1.10.0.msi

**Étape 3 : Configuration de Rancher Desktop**

3.1. Ouvrez Rancher Desktop.

3.2. Dans l'onglet WSL (version 1.9.x), assurez-vous de cocher l'option "Enable networking tunnel".

**Étape 4 : Clonage du projet von-network**

4.1. Dans votre terminal Git Bash, exécutez la commande suivante pour cloner le projet von-network :
```bash
git clone https://github.com/bcgov/von-network
```

**Étape 5 : Configuration du projet von-network**

5.1. Ouvrez Git Bash dans le répertoire du projet "von-network".

5.2. Exécutez les commandes suivantes pour créer une image et la redémarrer :
```bash
./manage build                    # Créer l'image   
./manage start --logs            # Redémarrer l'image
```

**Étape 6 : Configuration du projet Agent**

6.1. Ouvrez Git Bash dans le répertoire du projet Agent.

6.2. Exécutez les commandes suivantes pour construire le projet et définir des variables :
```bash
./manage build -a acapy-main 

export LEDGER_URL_CONFIG="http://test.bcovrin.vonx.io"
export TAILS_SERVER_URL_CONFIG="https://tails.vonx.io"
export AGENT_CONFIG_FILE="/aries-backchannels/acapy/auto_issuer_config.yaml"

./manage start -a acapy-main -b acapy-main -n
```

**Étape 7 : Installation de jq**

7.1. Installez l'outil jq en utilisant Winget. Ouvrez votre terminal et exécutez la commande suivante :
```bash
winget install jq
```

**Étape 8 : Configuration du projet Aries Mobile Test Harness**

8.1. Ouvrez Git Bash, puis naviguez vers le répertoire "aries-mobile-test-harness" en utilisant la commande "cd".

8.2. Exécutez les commandes suivantes pour construire le projet et le configurer :
```bash
./manage build -w qc_wallet

LEDGER_URL_CONFIG=http://test.bcovrin.vonx.io ./manage run -d LambdaTest -u YOUR_USER_NAME -k YOUR_API_KEY -p Android -a lt://DEVICE_ID -b QCWallet-182-Android-Fetch-Upstream -i "AATH;http://0.0.0.0:9020" -v "AATH;http: //0.0.0.0:9030" -t @bc_wallet -t @T002.1-Proof
```

Vous avez maintenant configuré l'environnement pour les projets Aries Mobile et Aries Agent sur Windows. Suivez attentivement chaque étape pour une configuration réussie.
