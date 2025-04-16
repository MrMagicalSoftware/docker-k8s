# pods



<img width="1441" alt="Screenshot 2025-04-16 alle 19 10 05" src="https://github.com/user-attachments/assets/b95f1337-7891-42a9-8c16-15370ca6f530" />
<img width="1458" alt="Screenshot 2025-04-16 alle 19 14 57" src="https://github.com/user-attachments/assets/8273c6c6-f5de-4196-8fcb-68261d842318" />
<img width="706" alt="Screenshot 2025-04-16 alle 19 16 15" src="https://github.com/user-attachments/assets/e0cebd52-e931-41c9-995d-758fafffe1dd" />
<img width="1439" alt="Screenshot 2025-04-16 alle 19 25 17" src="https://github.com/user-attachments/assets/22ad1d42-fc6a-45f9-8fa5-80fa109d5084" />
<img width="1428" alt="Screenshot 2025-04-16 alle 19 28 26" src="https://github.com/user-attachments/assets/ffbb573c-cc66-489c-91a7-98ab75aa3f61" />


___________________



![Screenshot 2025-04-16 alle 20 25 22](https://github.com/user-attachments/assets/d10f64f6-4705-459a-8ef9-fe7aca1ef4e7)
![Screenshot 2025-04-16 alle 20 26 27](https://github.com/user-attachments/assets/11f60f1c-69b1-491b-8fee-3144b07d9fc5)


```
kubectl run --help
```



`kubectl run` è un comando utilizzato nella CLI di Kubernetes per creare e avviare un nuovo pod. Questo comando è spesso utilizzato per eseguire rapidamente un container in un cluster Kubernetes. Ecco una spiegazione più dettagliata delle sue funzionalità e opzioni:

### Funzionalità di `kubectl run`

1. **Creazione di un Pod**: `kubectl run` crea un nuovo pod che esegue un container specificato. Puoi specificare l'immagine del container che desideri utilizzare.

2. **Esecuzione Interattiva**: Puoi eseguire un container in modo interattivo, ad esempio per eseguire comandi di debug o testare un'applicazione.

3. **Specifiche del Container**: Puoi specificare vari parametri per il container, come le variabili d'ambiente, le porte da esporre e le risorse richieste.

### Sintassi di Base

La sintassi di base per il comando è:

```bash
kubectl run <nome-del-pod> --image=<nome-dell-immagine> [opzioni]
```

### Esempi

1. **Eseguire un Pod con un'immagine**:

   ```bash
   kubectl run my-pod --image=nginx
   ```

   Questo comando crea un pod chiamato `my-pod` che esegue un container basato sull'immagine `nginx`.

2. **Eseguire un Pod in modo interattivo**:

   ```bash
   kubectl run my-shell --image=ubuntu --stdin --tty -- /bin/bash
   ```

   Questo comando crea un pod chiamato `my-shell` che esegue un container Ubuntu e apre una shell interattiva.

3. **Specificare variabili d'ambiente**:

   ```bash
   kubectl run my-app --image=my-image --env="ENV_VAR=value"
   ```

   Questo comando crea un pod con una variabile d'ambiente chiamata `ENV_VAR`.

### Opzioni Comuni

- `--env`: Specifica le variabili d'ambiente per il container.
- `--port`: Espone una porta specifica del container.
- `--restart`: Specifica la politica di riavvio (ad esempio, `Never` o `OnFailure`).
- `--stdin` e `--tty`: Utilizzati per eseguire un container in modo interattivo.

A partire dalle versioni più recenti di Kubernetes, l'uso di `kubectl run` per creare applicazioni complesse è stato deprecato in favore di manifesti YAML e comandi come `kubectl apply`. È consigliabile utilizzare i file di configurazione per gestire le risorse in modo più strutturato e ripetibile.


```
kubectl run nginx --image=nginx:1.27.0
```


![Screenshot 2025-04-16 alle 20 30 20](https://github.com/user-attachments/assets/a4489b1b-2ce4-4b64-9aa9-60fd1710b179)

![Screenshot 2025-04-16 alle 20 30 40](https://github.com/user-attachments/assets/4e8393e9-920d-4b7b-8dbd-d0a48998ddc9)

![Screenshot 2025-04-16 alle 20 48 44](https://github.com/user-attachments/assets/4f335f14-6ba1-4972-a86a-0aecff6d1ff2)

![Screenshot 2025-04-16 alle 20 49 25](https://github.com/user-attachments/assets/d2fe4e15-e6ae-452b-8262-5834056130a7)

![Screenshot 2025-04-16 alle 20 51 41](https://github.com/user-attachments/assets/71d70938-b9dd-4311-9aac-62f53afe7330)

 ![Screenshot 2025-04-16 alle 20 55 14](https://github.com/user-attachments/assets/685b07ca-177a-4458-ad48-a8cc0302cc78)



![Screenshot 2025-04-16 alle 20 56 17](https://github.com/user-attachments/assets/e67622f4-123f-4073-94f4-ac631c654683)


![Screenshot 2025-04-16 alle 20 56 37](https://github.com/user-attachments/assets/e16a89a9-56b6-41f1-9cdf-cce90362690e)

![Screenshot 2025-04-16 alle 20 58 08](https://github.com/user-attachments/assets/4cd9e37e-50d1-4f72-a3f9-5d179ab8d6b5)


![Screenshot 2025-04-16 alle 20 58 43](https://github.com/user-attachments/assets/53359aa8-976c-4e1f-9b83-9528d651d428)

  
![Screenshot 2025-04-16 alle 20 59 17](https://github.com/user-attachments/assets/a901ab99-437d-4b73-a8da-00901d984594)

![Screenshot 2025-04-16 alle 21 00 03](https://github.com/user-attachments/assets/01506b3a-2ef6-41cf-80d4-733aa284b5e4)

![Screenshot 2025-04-16 alle 21 00 23](https://github.com/user-attachments/assets/ac594c70-0826-4101-b22f-55022441d0a7)



_________________________________________________________________________



```
kubectl get pods
```

```
kubectl expose pods --help
```


```
kubectl expose pods
```
`kubectl expose` è un comando di Kubernetes utilizzato per creare un servizio (Service) che espone una risorsa, come un pod, un deployment o un replicaset, all'interno del cluster o all'esterno di esso. Quando si espone un pod, si crea un endpoint che consente ad altri servizi o a client esterni di comunicare con il pod.

### Sintassi di base

La sintassi generale per esporre un pod è la seguente:

```bash
kubectl expose pod <nome-del-pod> --port=<porta-esposta> --target-port=<porta-del-pod> --type=<tipo-di-servizio>
```

### Parametri principali

- `<nome-del-pod>`: il nome del pod che si desidera esporre.
- `--port`: la porta su cui il servizio sarà accessibile.
- `--target-port`: la porta sul pod a cui il servizio deve inoltrare il traffico. Se non specificato, di default è la stessa della porta esposta.
- `--type`: il tipo di servizio da creare. Può essere `ClusterIP` (default), `NodePort`, `LoadBalancer`, ecc.

### Esempio

Supponiamo di avere un pod chiamato `my-pod` che ascolta sulla porta `8080`. Per esporre questo pod, puoi utilizzare il seguente comando:

```bash
kubectl expose pod my-pod --port=80 --target-port=8080 --type=NodePort
```

In questo esempio:

- Il servizio sarà accessibile sulla porta `80`.
- Il traffico in entrata sulla porta `80` sarà inoltrato alla porta `8080` del pod `my-pod`.
- Il tipo di servizio è `NodePort`, il che significa che sarà accessibile anche all'esterno del cluster attraverso una porta assegnata su ogni nodo.

- È importante notare che esporre direttamente i pod non è sempre la pratica migliore, poiché i pod possono essere temporanei e soggetti a riavvii. È spesso preferibile esporre un deployment o un replicaset.
- Assicurati di avere i permessi necessari per eseguire il comando e che il tuo contesto Kubernetes sia configurato correttamente.

![Screenshot 2025-04-16 alle 21 06 11](https://github.com/user-attachments/assets/c0a079f1-2ee9-4b5e-9749-611eda6ae1ac)
![Screenshot 2025-04-16 alle 21 06 41](https://github.com/user-attachments/assets/1a962c82-71f4-4150-866b-69e422c2c94f)
![Screenshot 2025-04-16 alle 21 08 30](https://github.com/user-attachments/assets/169f6b33-e48d-432d-a0e4-f8a3c1f5e5d4)
![Screenshot 2025-04-16 alle 21 12 08](https://github.com/user-attachments/assets/9c4e9981-7a25-4c2a-abb6-22c07361a39f)



# Da codice Dockerfile a pods


![Screenshot 2025-04-16 alle 21 19 21](https://github.com/user-attachments/assets/426ebec6-be28-401b-aac4-558ca9903823)

![Screenshot 2025-04-16 alle 21 19 40](https://github.com/user-attachments/assets/90544c23-4914-43b4-b80b-f4a6770f48b6)
![Screenshot 2025-04-16 alle 21 21 14](https://github.com/user-attachments/assets/40b5dfae-6bc4-4496-ac78-3dc39609e5a2)

![Screenshot 2025-04-16 alle 21 21 34](https://github.com/user-attachments/assets/12f3ae53-3a5a-4375-bdf0-c68d4e4426f1)
![Screenshot 2025-04-16 alle 21 22 16](https://github.com/user-attachments/assets/3a72983c-2061-4875-a3f9-7baf2814325d)


![Screenshot 2025-04-16 alle 21 23 04](https://github.com/user-attachments/assets/e132b54b-fedc-4cf0-a36a-230fde431cab)
![Screenshot 2025-04-16 alle 21 23 43](https://github.com/user-attachments/assets/23a2a9ab-02eb-4184-b858-e366c6b0e3fc)
![Screenshot 2025-04-16 alle 21 24 42](https://github.com/user-attachments/assets/4309318d-82c6-43fb-a56b-c8aa63572157)

![Screenshot 2025-04-16 alle 21 25 11](https://github.com/user-attachments/assets/ab4d1d7b-ebd8-4631-a557-4d76716977fe)








