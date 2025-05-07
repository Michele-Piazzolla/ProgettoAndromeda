```markdown
# ANDROMEDA CLUB - Documentazione del Progetto

#### Introduzione
Applicazione Java per la gestione di prenotazioni eventi in locale notturno, composta da:
- **Interfaccia Admin**: Creazione/modifica/eliminazione eventi (locandine)
- **Interfaccia Clienti**: Visualizzazione eventi e acquisto biglietti  
*Ispirato a sistemi come Xceed, semplificato per singolo locale*

#### Obiettivo
- **Amministratori**: Gestione eventi e monitoraggio prenotazioni
- **Clienti**: Consultazione eventi e acquisto biglietti intuitivo

#### Architettura
```plaintext
Andromeda.java (Classe principale)
├── Admin.java (GUI amministratore)
└── Clienti.java (GUI clienti)
```

#### Componenti Chiave
##### Classe Locandina
```java
public static class Locandina {
    public String titolo, data;
    public double prezzoStandard, prezzoSaltacoda, prezzoPrive;
    
    public void reset() {
        titolo = data = null;
        prezzoStandard = prezzoSaltacoda = prezzoPrive = 0;
    }
}
```
*Funzionalità*: Memorizza dettagli eventi con metodo `reset()` per cancellazione dati

##### Aggiorna Lista Clienti
```java
private void aggiornaListaClienti() {
    StringBuilder sb = new StringBuilder();
    for (String cliente : Andromeda.clientiRegistrati) {
        sb.append(cliente).append("\n");
    }
    AreaClientiRegistrati.setText(sb.toString());
}
```
*Perché StringBuilder*: Ottimizza memoria/prestazioni modificando un singolo oggetto invece di crearne multipli

##### Registrazione Cliente
```java
private void registraCliente(String tipoBiglietto) {
    if (nome.isEmpty() || cognome.isEmpty() /*...*/) {
        MessaggioVerifica.setText("️Compila tutti i campi!");
        return;
    }
    Andromeda.clientiRegistrati.add("Nome: " + nome + " " + cognome /*...*/);
}
```
*Funzionalità*: Validazione dati + registrazione clienti

##### Creazione Locandina
```java
private void jButton1ActionPerformed(...) {
    Andromeda.locandina1.titolo = jTextField2.getText();
    Andromeda.locandina1.data = jTextField1.getText();
    // ...
}
```
*Funzionalità*: Assegnazione dati campi testo alle locandine

#### Funzionalità Principali
##### Interfaccia Admin
- 🎟️ Crea Locandina (3 eventi)  
- 🗑️ Elimina Locandina  
- 👥 Visualizza/Svuota lista clienti  

##### Interfaccia Clienti
- 📅 Visualizza eventi (titolo/data/prezzi)  
- 💳 Acquista biglietti (3 tipologie)  
- ✅ Validazione automatica dati  

#### Screenshot
`Interfaccia Admin`  
![Admin Interface](path/to/admin_screenshot.png)  

`Interfaccia Clienti`  
![Client Interface](path/to/client_screenshot.png)  

#### Conclusione
Sistema intuitivo per gestione eventi con:
- Struttura codice espandibile  
- Interfacce utente semplificate  
- Gestione efficiente delle risorse (*es. StringBuilder*)
``` 

*Note per GitHub*:
1. Sostituire `path/to/` con percorsi reali delle immagini
2. Formattare i blocchi codice con sintassi Markdown corretta
3. Aggiungere eventuali badge di stato (es. `![Java Version](https://img.shields.io/badge/Java-17-blue)`)
