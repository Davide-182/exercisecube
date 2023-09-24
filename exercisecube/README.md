# Guida alla Ricreazione della Struttura Cloud su AWS

Questo repository contiene un file YAML che descrive un'infrastruttura cloud su Amazon Web Services (AWS). Segui i passaggi seguenti per ricreare questa struttura nel tuo account AWS.

![PNG Struttura](/images/Structure_diagram.png)

## Prerequisiti

- Un account AWS attivo.
- AWS CLI installato e configurato con le tue credenziali.

## Passaggi

1. **Clonare il repository:**

   Clona questo repository in una nuova cartella sul tuo computer con questi comandi:
```
$ git clone https://github.com/Davide-182/exercisecube.git
$ cd exercisecube
```
   O se preferisci, scarica il file .zip cliccando sul bottone verde "code"
   al seguente link: https://github.com/Davide-182/exercisecube.git

!["Code" button](/images/green_button.png)

2. **Accedi al tuo account AWS:**

Assicurati di essere connesso al tuo account AWS tramite AWS CLI:

```
$ aws configure
```

Inserisci le credenziali necessarie...
- Access-Key
- Secret-Key
- per "default region" puoi lasciare "None", definiremo in seguito la region in cui creare le nostre risorse. 

Altrimenti digita: eu-west-1
ed evita di inserire più avanti il comando "--region eu-west-1"

## Attenzione
Le AMI per le risorse in questo file .yaml sono configurate per questa region.
---

3. **Esegui il provisioning delle risorse:**

Utilizza AWS CLI e il file YAML per creare le risorse specificate:

```
$ aws cloudformation create-stack --stack-name NomeStack --template-body file://cf_v1.4.yaml --region eu-west-1
```
- Modifica "NomeStack" col nome che preferisci assegnare al tuo stack.
- modifica "/cf_v1.4.yaml" inserendo il path per il file, se non sei nella stessa directory.

4. **Monitora lo stato dello stack:**

Puoi monitorare lo stato dello stack in CloudFormation nella console AWS o utilizzando il seguente comando:

```
$ aws cloudformation describe-stacks --stack-name NomeStack --region eu-west-1
```

   A questo punto, aspetta qualche minuto e rilancia l'ultimo comando finché non vedrai "StackStatus": "CREATE_COMPLETE".

![Screenshot dello Stack](/images/stack__create_complete.png)


5. **Rimuovi le risorse:**

Quando hai finito con le risorse, puoi rimuovere lo stack:

```
$ aws cloudformation delete-stack --stack-name NomeStack --region eu-west-1
```

## Risorse Aggiuntive

- [Documentazione AWS CloudFormation](https://docs.aws.amazon.com/cloudformation/index.html)

---

