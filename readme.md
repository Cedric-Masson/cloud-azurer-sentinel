
# Infrastructure Labo Cloud - Azure Sentinel
Ce document décrit l'infrastructure déployée dans Microsoft Azure à l'aide de Terraform. L'infrastructure comprend les éléments suivants :

[![](https://mermaid.ink/img/pako:eNqVVduO2jAQ_RXL-8otgbJLHipxa7tqd4tK24eSFTLOhFgkduQLW4r49zoJmyU0VEteYk_OmRmfmYz3mIoAsIfXkqQR-j7xObKPMqvC8IWsBBrHwgSoiYZ_jAQ0B64Zh7hAZg_J7DJZyvXiGyhhJAX0UQqTPv2L2XLQi59MakNi9Aj6WchNDcwmkAHn-avme2pWMaNLli5m-Qrdz2pQXK0Xxxg2bWok07uLmXFGS_A91yBDQqHuBEmZ_wOhkZWiLn8tJFnDklAqDLcHKfZoWOyPDOCBz4vlq4ao2URjwTVhXNn1-4p0VXBmuQgvJKwS7BmPeA5UV_FWrFrwDwVvdjxUSlBG9BmjrNZZ-kmtf-urDpdJaJFf52jC1AYxXk2qKvjFQJ9hh2aESRRKkRw9kJQtlYqWG9i98E5Mi_n8U0l7eqmX0rsYTqsWsjj2bsbO1Jn0GkpLsQHvpjccdKZuHSMv3ZWcQvhrWaX41xJtQ1xNsW1wrRDJ1TJUS_12-klR_0-q655yzuRNs02y2ePcui1n4LS6nZbT7571Rg45xvkwmI5GbhlnOhj1euPjtvnMAh15bvrb57iBExuSsMCO5H3mzcc6ggR87NllACExsfaxzw8WSowW8x2n2NPSQAObNLC_3oQRO7sT7IUkVqV1GjArW2mMBQnAbvdY79J8_jOlrUsqeMjWmd3I2JojrVPltdvZ59aa6cisWlQkbcWCiEgdbQf9dt_t3xG3C_3bLnnX7QZ05QzuQrfnhMFtx3EJPhwaOCX8lxCvWUGez0Nx-eR30OEv52AuHQ?type=png)](https://mermaid.live/edit#pako:eNqVVduO2jAQ_RXL-8otgbJLHipxa7tqd4tK24eSFTLOhFgkduQLW4r49zoJmyU0VEteYk_OmRmfmYz3mIoAsIfXkqQR-j7xObKPMqvC8IWsBBrHwgSoiYZ_jAQ0B64Zh7hAZg_J7DJZyvXiGyhhJAX0UQqTPv2L2XLQi59MakNi9Aj6WchNDcwmkAHn-avme2pWMaNLli5m-Qrdz2pQXK0Xxxg2bWok07uLmXFGS_A91yBDQqHuBEmZ_wOhkZWiLn8tJFnDklAqDLcHKfZoWOyPDOCBz4vlq4ao2URjwTVhXNn1-4p0VXBmuQgvJKwS7BmPeA5UV_FWrFrwDwVvdjxUSlBG9BmjrNZZ-kmtf-urDpdJaJFf52jC1AYxXk2qKvjFQJ9hh2aESRRKkRw9kJQtlYqWG9i98E5Mi_n8U0l7eqmX0rsYTqsWsjj2bsbO1Jn0GkpLsQHvpjccdKZuHSMv3ZWcQvhrWaX41xJtQ1xNsW1wrRDJ1TJUS_12-klR_0-q655yzuRNs02y2ePcui1n4LS6nZbT7571Rg45xvkwmI5GbhlnOhj1euPjtvnMAh15bvrb57iBExuSsMCO5H3mzcc6ggR87NllACExsfaxzw8WSowW8x2n2NPSQAObNLC_3oQRO7sT7IUkVqV1GjArW2mMBQnAbvdY79J8_jOlrUsqeMjWmd3I2JojrVPltdvZ59aa6cisWlQkbcWCiEgdbQf9dt_t3xG3C_3bLnnX7QZ05QzuQrfnhMFtx3EJPhwaOCX8lxCvWUGez0Nx-eR30OEv52AuHQ)

## Resource Group

- Nom : rg-chief-locust (généré dynamiquement)
- Emplacement : eastus

## Virtual Network

- Nom : myVnet
- Espace d'adressage : 10.0.0.0/16

## Subnet

- Nom : mySubnet
- Espace d'adressage : 10.0.1.0/24

## Public IP

- Nom : myPublicIP
- IP : 172.191.30.163 (généré dynamiquement)

## Network Security Group

- Nom : myNetworkSecurityGroup

### Règle de sécurité

- Nom : SSH
- Priorité : 1001
- Direction : Inbound
- Accès : Allow
- Protocole : Tcp
- Port source : *
- Port destination : 22
- Adresse IP source : *
- Adresse IP destination : *

## Network Interface

- Nom : myNIC

### Configuration IP

- Nom de la configuration : my_nic_configuration
- Allocation d'adresse IP privée : Dynamic
- ID de l'adresse IP publique : myPublicIP

## Clé SSH

- Nom d'utilisateur : azureadmin
- Clé publique : Voir lors de la création avec terraform

## Stockage

- Nom du compte de stockage : (génére dynamiquement)

## Machine virtuelle

- Nom : myVM
- Taille : Standard_DS1_v2

### Disque du système d'exploitation

- Nom : myOsDisk
- Mise en cache : ReadWrite
- Type de compte de stockage : Premium_LRS

### Image source

- Éditeur : Canonical
- Offre : 0001-com-ubuntu-server-jammy
- SKU : 22_04-lts-gen2
- Version : latest
