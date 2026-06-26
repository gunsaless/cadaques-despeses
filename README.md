# 🏖️ Despeses Cadaqués 2026

Web senzilla per repartir les despeses d'un viatge entre amics quan **cadascú ve i marxa en moments diferents**.

## Com funciona

1. **Àpats** — una graella tipus full de càlcul on marques quins àpats fa cada persona a Cadaqués (sopar de divendres, dinar de dissabte…). Aquesta taula és la base de tots els repartiments.
2. **Despeses** — qualsevol pot afegir una despesa indicant import, qui ha pagat i com s'ha de repartir:
   - **Tot el viatge** — es divideix entre tothom de forma justa, *segons quants àpats fa cadascú* (qui ve menys dies paga menys).
   - **Àpats concrets** — es divideix només entre els qui hi són en aquells àpats.
3. **Comptes** — balanç per persona i la llista mínima de pagaments per quedar en paus.

## Model de repartiment

Cada parella *(àpat × persona present)* és una **unitat**. El cost d'una despesa es divideix pel total d'unitats, i cada persona paga segons quantes unitats li toquen. Així, tant les despeses generals com les d'un àpat concret són proporcionals a la presència real.

## Ús

És un sol fitxer `index.html`. Obre'l al navegador — no cal servidor.

- **Sense configurar res:** funciona en mode local (les dades es guarden només en aquest dispositiu, a localStorage).
- **Amb sincronització (recomanat):** configura Firebase i tots els dispositius veuen i editen les mateixes dades en temps real.

## Sincronització entre dispositius (Firebase)

1. Ves a [console.firebase.google.com](https://console.firebase.google.com) i crea un projecte (gratuït).
2. Menú **Build → Realtime Database → Crear base de dades**. Tria una regió (ex: `europe-west1`) i comença en **mode de prova** (test mode).
3. Activa l'**autenticació anònima**: *Build → Authentication → Sign-in method → Anonymous → Activar*. (L'app inicia sessió sola, sense que ningú faci res.)
4. A **Regles** de la Realtime Database, exigeix estar autenticat (així la BBDD no és pública):
   ```json
   { "rules": { ".read": "auth != null", ".write": "auth != null" } }
   ```
4. **⚙️ → Configuració del projecte → Les teves apps → Web (</>)**: registra una app i copia l'objecte `firebaseConfig`.
5. Enganxa'l dins de `FIREBASE_CONFIG` a `index.html` (a dalt del primer `<script>`), descomentant les línies.
6. Puja-ho i obre la web. Hauria de sortir **🟢 Sincronitzat** a dalt.

### Sales (URL secreta)

Per defecte tothom comparteix la sala `cadaques2026`. Pots fer servir una sala diferent/secreta afegint-ho al final de la URL:

```
…/index.html#room=la-meva-clau-secreta
```

Comparteix exactament aquesta URL amb el grup.
