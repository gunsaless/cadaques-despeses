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

És un sol fitxer `index.html`. Obre'l al navegador — no cal servidor. Les dades es guarden al teu dispositiu (localStorage).

> ⚠️ De moment cada dispositiu té la seva còpia local; encara no se sincronitza automàticament entre mòbils.
