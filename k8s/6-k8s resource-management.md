# Kubernetes resource Management


<img width="1432" alt="Screenshot 2025-04-19 alle 14 10 33" src="https://github.com/user-attachments/assets/72c6ec24-7fe1-4231-b501-ef9a6eaa4e14" />

<img width="1342" alt="Screenshot 2025-04-19 alle 14 11 07" src="https://github.com/user-attachments/assets/f520a362-9223-43d5-bd2e-0e44dc445a68" />


<img width="923" alt="Screenshot 2025-04-19 alle 14 26 22" src="https://github.com/user-attachments/assets/e8ddd2c9-85ee-450e-87d4-0a718e8bb5dd" />


In Kubernetes, le **labels** e i **selectors** sono concetti fondamentali utilizzati per organizzare, gestire e selezionare risorse nel cluster. Questi strumenti consentono di raggruppare e filtrare le risorse in modo efficiente, facilitando la gestione delle applicazioni e delle loro configurazioni.

### Labels

#### Cosa sono le Labels?

Le **labels** sono coppie chiave-valore associate a risorse Kubernetes (come Pod, Service, Deployment, ReplicaSet, ecc.). Le labels forniscono un modo per identificare e categorizzare le risorse in base a criteri specifici.

#### Caratteristiche delle Labels:

1. **Flessibilità:** Le labels possono essere utilizzate per qualsiasi scopo, come identificare l'ambiente (sviluppo, test, produzione), il team responsabile, la versione dell'applicazione, ecc.
  
2. **Multi-Valore:** Una risorsa può avere più labels, consentendo di categorizzarla in diversi modi.

3. **Non Uniche:** Le labels non devono essere uniche. Più risorse possono avere la stessa label.

#### Esempio di Labels:

Ecco un esempio di come definire le labels in un manifesto YAML per un Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
    environment: production
    version: v1
spec:
  containers:
  - name: nginx
    image: nginx
```

In questo esempio, il Pod `my-pod` ha tre labels: `app`, `environment` e `version`.

### Selectors

#### Cosa sono i Selectors?

I **selectors** sono utilizzati per filtrare e selezionare risorse in base alle labels. I selectors consentono di specificare criteri per identificare un insieme di risorse che corrispondono a determinate labels.

#### Tipi di Selectors:

1. **Equality-based Selectors:** Permettono di selezionare risorse in base all'uguaglianza delle labels. Ad esempio, `app=my-app` selezionerà tutte le risorse con la label `app` impostata su `my-app`.

2. **Set-based Selectors:** Permettono di selezionare risorse in base a un insieme di valori. Ad esempio, `environment in (production, staging)` selezionerà tutte le risorse con la label `environment` impostata su `production` o `staging`.

#### Esempio di Selectors:

I selectors sono comunemente utilizzati nei manifesti di risorse come i Service e i Deployment. Ecco un esempio di un Service che utilizza un selector per selezionare i Pod:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
    environment: production
  ports:
    - port: 80
      targetPort: 80
```

In questo esempio, il Service `my-service` utilizza un selector per selezionare tutti i Pod che hanno le labels `app=my-app` e `environment=production`. Il Service inoltrerà il traffico a questi Pod.

### Vantaggi di Labels e Selectors

1. **Organizzazione:** Le labels consentono di organizzare le risorse in modo logico, facilitando la gestione delle applicazioni.

2. **Selezione Dinamica:** I selectors consentono di selezionare dinamicamente le risorse in base a criteri specifici, rendendo più facile il bilanciamento del carico, la gestione delle versioni e l'implementazione di strategie di rollout.

3. **Flessibilità:** Puoi modificare le labels delle risorse senza dover cambiare la configurazione delle applicazioni, consentendo una gestione più agile delle risorse.

<img width="1441" alt="Screenshot 2025-04-19 alle 14 30 50" src="https://github.com/user-attachments/assets/930b32c5-5804-47db-997d-541a5624d522" />

<img width="1427" alt="Screenshot 2025-04-19 alle 14 31 55" src="https://github.com/user-attachments/assets/a6ccf105-0781-4567-8ba4-676e8a9f50ba" />

<img width="1436" alt="Screenshot 2025-04-19 alle 14 33 46" src="https://github.com/user-attachments/assets/b3f18a6f-b4ee-4c9f-810a-0a847cd0b1d0" />



___________


## esempio  Hands-On Labels and Selectors in Kubectl 

le etichette (labels) e i selettori (selectors) sono strumenti fondamentali per organizzare e gestire le risorse. Le etichette sono coppie chiave-valore associate a risorse come pod, servizi e deployment, mentre i selettori vengono utilizzati per filtrare le risorse in base a queste etichette.

Ecco alcuni esempi pratici di come utilizzare le etichette e i selettori con `kubectl`.

### 1. Creare un Pod con Etichette

Puoi creare un pod e assegnargli delle etichette utilizzando un file YAML. Ecco un esempio:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
    env: production
spec:
  containers:
  - name: my-container
    image: nginx
```

Puoi salvare questo file come `pod.yaml` e poi creare il pod con il comando:

```bash
kubectl apply -f pod.yaml
```

### 2. Visualizzare le Etichette di un Pod

Per visualizzare le etichette di un pod esistente, puoi usare il comando:

```bash
kubectl get pod my-pod --show-labels
```

### 3. Selezionare Pod con Selettori

Puoi utilizzare i selettori per filtrare i pod in base alle etichette. Ad esempio, per ottenere tutti i pod con l'etichetta `app=my-app`, puoi usare:

```bash
kubectl get pods -l app=my-app
```

### 4. Aggiornare le Etichette di un Pod

Puoi anche aggiornare le etichette di un pod esistente. Ad esempio, per aggiungere un'etichetta `version: v1` al pod `my-pod`, puoi usare:

```bash
kubectl label pod my-pod version=v1
```

### 5. Rimuovere un'Etichetta da un Pod

Per rimuovere un'etichetta, puoi usare il flag `-`:

```bash
kubectl label pod my-pod version-
```

### 6. Creare un Servizio con Selettori

creare un servizio che seleziona i pod in base alle etichette. Ecco un esempio di servizio che seleziona i pod con l'etichetta `app=my-app`:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

Salva questo file come `service.yaml` e crealo con:

```bash
kubectl apply -f service.yaml
```

### 7. Filtrare Risorse con Selettori Complessi

Puoi anche utilizzare selettori complessi. Ad esempio, per ottenere tutti i pod che hanno l'etichetta `app=my-app` e `env=production`

```bash
kubectl get pods -l app=my-app,env=production
```

### 8. Elencare Tutti i Pod con Etichette

Per elencare tutti i pod e le loro etichette

```bash
kubectl get pods --show-labels
```



_________


## Hands-On Selecting Objects with MatchLabels and MatchExpressions



In Kubernetes, i selettori di etichette possono essere utilizzati per filtrare oggetti in modo più sofisticato attraverso l'uso di `matchLabels` e `matchExpressions`. Questi strumenti ti permettono di definire criteri di selezione più complessi per le risorse.

### 1. Utilizzo di `matchLabels`

`matchLabels` è un modo semplice per selezionare oggetti in base a coppie chiave-valore. Ecco un esempio di come utilizzare `matchLabels` in un file YAML per un Deployment.

#### Esempio di Deployment con `matchLabels`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
      env: production
  template:
    metadata:
      labels:
        app: my-app
        env: production
    spec:
      containers:
      - name: my-container
        image: nginx
```

Puoi salvare questo file come `deployment.yaml` e applicarlo con:

```bash
kubectl apply -f deployment.yaml
```

### 2. Utilizzo di `matchExpressions`

`matchExpressions` consente di utilizzare operatori logici per definire criteri di selezione più complessi. Puoi utilizzare operatori come `In`, `NotIn`, `Exists`, e `DoesNotExist`.

#### Esempio di Deployment con `matchExpressions`

Ecco un esempio di un Deployment che utilizza `matchExpressions`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchExpressions:
      - key: app
        operator: In
        values:
          - my-app
      - key: env
        operator: NotIn
        values:
          - staging
  template:
    metadata:
      labels:
        app: my-app
        env: production
    spec:
      containers:
      - name: my-container
        image: nginx
```

In questo esempio, il Deployment selezionerà i pod che hanno l'etichetta `app=my-app` e che **non** hanno l'etichetta `env=staging`.

Puoi applicare questo file con:

```bash
kubectl apply -f deployment-with-expressions.yaml
```

### 3. Filtrare Risorse con Selettori Complessi

Puoi utilizzare `matchLabels` e `matchExpressions` anche per filtrare le risorse esistenti. Ad esempio, per ottenere tutti i pod che soddisfano i criteri di selezione definiti nel Deployment sopra, puoi usare:

```bash
kubectl get pods -l 'app=my-app,env!=staging'
```

### 4. Esempio di Selettore con `Exists` e `DoesNotExist`

Puoi anche utilizzare `Exists` e `DoesNotExist` per selezionare oggetti in base alla presenza o assenza di etichette.

#### Esempio di Deployment con `Exists`

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchExpressions:
      - key: app
        operator: Exists
  template:
    metadata:
      labels:
        app: my-app
        env: production
    spec:
      containers:
      - name: my-container
        image: nginx
```

In questo caso, il Deployment selezionerà tutti i pod che hanno l'etichetta `app`, indipendentemente dal valore.

### 5. Applicare e Verificare

Dopo aver creato i tuoi Deployment, puoi verificare i pod creati con:

```bash
kubectl get pods -l app=my-app
```

E per controllare le etichette di un pod specifico:

```bash
kubectl get pod <pod-name> --show-labels
```

### Conclusione

Utilizzando `matchLabels` e `matchExpressions`, puoi creare selettori di etichette più complessi e flessibili in Kubernetes. Questi strumenti ti permettono di gestire le tue risorse in modo più efficace, consentendo una maggiore granularità nella selezione degli oggetti.








