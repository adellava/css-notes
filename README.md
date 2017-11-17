# Checklist Buona Salute CSS/SCSS di SPA


### uso delle variabili

* E' molto importante avere un file variabili principale con un numero finito di variabili da cui tutte le altre variabili derivano. Stanno di solti in questo set:
    - palette di colori (5/../10)
    - palette di grigi (5/../10)
    - padding e margin di base per griglia e tipografia
    - font(s): (regular, italic, pre sono quelli che di solito ci sono)
    - icofont
    - path agli assets
    - scatti delle media query
* E' molto importante che tutte le variabili di sizing e di colore che si usano per tutti i componenti siano una f(x) del primo set, limitato di variabili, in questo modo tramite poche modifiche si potrà ottenere un effetto consistente su tutta l'app
* per le variabili commensurabili o appartenenti ad uno stesso tipo fare una collections in modo da poter lavorare coi cicli su componenti simili che cambiano solo nel colore

```scss
$palette: ( 
    primary: $brand-primary, 
    secondary: $brand-secondary, 
    neutral: $brand-neutral, 
    calm: $brand-calm, 
    success: $brand-success, 
    info: $brand-info, 
    warning: $brand-warning, 
    danger: $brand-danger
);
```
* è importante avere un set di mixins per media query, animazioni, border radius, shadows da importare sui componenti in modo che questi dettagli siano consistenti tra loro

### files

* Avere un unico file di scss compilato in css da importare che include anche il css di eventuali stili
* Creare un file di modulo per ogni tipo di componente, evitare i file con tropper righe di codice, quando non sai rispondere alla domando "cosa c'è dentro questo file?" è ora di refattorizzarlo
* dividere chiaramente i componenti dai file interni (variabili, operations, mixins)

### Dipendenze

* se si usa bootstrap non importarlo come compilato la importare solo i moduli scss necessari al progetto, es:

```scss
@import "../../../vendor/bootstrap-sass/assets/stylesheets/bootstrap/grid";
```

* I file di stile di eventuali widget o plugin grafici è consigliabile duplicare il css in un modulo proprio scss dell'app e sostituire tutti i valori critici con le variabili base dell'app colori, tipografia, mixins. Questo evita l'effetto Frankenstein.
* evitare il più possibile dipendenze che aggiungono stile lato js di cui non si ha il controllo


### Animazioni

* le animazioni hanno un valore semantico molto importante ma essere effettive dentro l'app devono essere:
    - un numero finito
    - applicate allo stesso modo: uguale "causa -> effetto" sono legati sempre dalla stessa animazione
    - coerenti fra loro, easing e tutte le "qualità" dell'animazione devono sembrare far parte di un'unica library


### Componenti

* stabilire un numero finito di componenti riutilizzabili e componibili.. impossibile scrivere tutto ma esistono diversi validi esempi. Un qualsisi tema acquistato rispetta questo requisito.

### Layout

* Stabilire un numero finito di layout pagina inferiore a 10 per comporre le pagine, i layout devono essere
    - componibili
    - privi di style
    - ismorfi rispetto agli ingombri dei componenti di navigazione
    - espressi tramite posizionamenti absolute


### Design Patterns

* i componenti e i layout vanno documentati in pattern e spiegati, questo un esempio di spiegazione:

```
Pattern: table-style1

Super-patterns: layout1 (nel *__body), layout6, layout7 (nel *__body)

Problema: Elencare dati ordinabili e/o paginati ma omogenei fra loro. Utilie anche in una navigazione lista > dettaglio.

Sub-patterns: buttons, icons
```


