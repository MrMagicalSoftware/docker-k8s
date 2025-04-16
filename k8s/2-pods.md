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

 


