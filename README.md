¨SUPSI 2026  
Corso d’interaction design, CV429.01  
Docenti: A. Gysin, G. Profeta  

Progetto 1: Un piccolo passo per un uomo, un grande balzo per l'umanità

# NASA70
Autore: Laura Pantani \
[NASA70](https://laura-pantani.github.io/NASA-P2/)


## Intenzioni progetto
la mia intenzione per questo progetto e di creare un archivio nello spazio dove i progetti orbitano attorno al Logo di NASA70. 
L'intenzione del progetto è creare un archivio digitale ispirato allo spazio, in cui i progetti della classe orbitano attorno al titolo NASA70. L'interfaccia non è pensata come una semplice lista, ma come un sistema visivo in movimento: ogni progetto diventa una piccola card nello spazio, simile a un satellite o a un corpo celeste.
L'idea principale è rendere l'esplorazione dei progetti più libera e curiosa. L'utente può osservare l'orbita generale, filtrare i contenuti attraverso i tag e aprire le card per scoprire maggiori informazioni sul singolo progetto.

## Riferimenti, Tag e animazioni
I tag sono stati pensati come un modo per dare ordine all'archivio, ma anche per modificare il comportamento visivo della pagina. Quando si seleziona un tag, cambiano sia i progetti mostrati sia il tipo di movimento orbitale. 
Per alcuni tag l'animazione è collegata al significato del tag stesso. Ad esempio, il tag 2D genera un'orbita più piatta e frontale, mentre il tag 3D crea un movimento con maggiore profondità e prospettiva. Altri tag più generici, come history, Apollo o space, mantengono invece l'animazione classica di NASA70, perché non hanno una forma visiva specifica abbastanza forte da richiedere un movimento dedicato.
Anche il testo centrale cambia in base al tag selezionato, con un effetto "matrix" che rende il passaggio da una categoria all'altra più dinamico. Le card laterali nella modale seguono il tag attivo, così l'utente vede progetti collegati al contesto che sta esplorando.

**Riferimento video per le animazioni:**  
[Guarda il video di riferimento su Instagram](https://www.instagram.com/p/C755CmDif_q/)

## Design dell’interfaccia e modalità di interazione
Il progetto è nato dalla volontà di trasformare un semplice elenco in un'esperienza immersiva. I primi schizzi si sono concentrati sulla meccanica dell'orbita: come tradurre i dati dei progetti in variabili matematiche (raggio, inclinazione e velocità) per creare un sistema che sembrasse vivo e dinamico.

![Schizzo 1 - Concetto di Orbita](p2/schizzo_01.jpeg)
*Studio iniziale delle traiettorie ellittiche: definizione della prospettiva 3D e della gerarchia visiva tra il nucleo centrale e i progetti orbitanti.*

![Schizzo 2 - Layout e Navigazione](p2/schizzo_03.jpeg)
*Progettazione dell'interfaccia: studio del posizionamento dei filtri laterali e della transizione verso la modalità Timeline per garantire un'usabilità chiara.*

## Interfaccia e Schermate
L'esperienza utente si articola in tre momenti principali, ognuno con una funzione specifica nella navigazione dell'archivio.

![Schermata 1 - Visualizzazione Orbitale](p2/screen_01.png)


![Schermata 2 - Visualizzazione Timeline](p2/screen_03.png)


![Schermata 3 - Dettaglio Progetto](p2/screen_02.png)



https://github.com/user-attachments/assets/2d2ed76d-7fe2-4432-98f8-29d80f78015b
ps. il video é velocizzato e tagliato


## Tecnologia usata
Il progetto è stato sviluppato utilizzando le tecnologie web standard per creare un'esperienza interattiva fluida e immersiva. La struttura portante è realizzata in **HTML5**, mentre lo stile e le transizioni visive sono gestite tramite **CSS3**. La logica di interazione, il filtraggio dinamico e la gestione dei dati sono scritti in **JavaScript (ES6)**. Per la visualizzazione delle orbite e degli elementi nello spazio, viene utilizzato il **Canvas 2D** per il tracciamento delle rotte e una logica di proiezione prospettica applicata al DOM per le card. Tutti i contenuti e i metadati dei progetti sono caricati dinamicamente da un file **JSON**.

### Esempio di proiezione orbitale
La funzione principale calcola la posizione $X, Y$ e la scala di profondità ($Z$) per simulare uno spazio tridimensionale partendo da coordinate polari:

```JavaScript
function projectOrbitPoint(angle, radiusX, radiusY, tiltXDeg, tiltZDeg) {
  const x = Math.cos(angle) * radiusX;
  const y = Math.sin(angle) * radiusY;
  
  // Calcolo delle rotazioni sugli assi X e Z per l'inclinazione dell'orbita
  const px = x;
  const py = -y * Math.sin(degToRad(tiltXDeg));
  const pz = y * Math.cos(degToRad(tiltXDeg));

  // Applicazione della prospettiva
  const persp = 900;
  const scale = persp / (persp + pz);
  
  return {
    x: fx * scale,
    y: fy * scale,
    z: pz,
    scale: scale
  };
}
```
## Logo e animazione
Per il logo ho scelto di seguire il manuale grafico della NASA del 1976, in cui il font del logotipo non viene mai utilizzato per altri testi; per questi viene invece impiegato l'Helvetica.
Per l'animazione, invece, ho pensato a una sorta di countdown al contrario, ovvero un count-up che va da 0 a 70, a rappresentare i 70 anni di attività della NASA.

![logo statico](p2/logo.png)
![logo animato](p2/Logo_animato.gif)

## Target
Il progetto è pensato principalmente per studenti, docenti e visitatori interessati a scoprire i lavori realizzati per NASA70. Il target include persone che vogliono esplorare i progetti in modo rapido, ma anche utenti curiosi che preferiscono un'esperienza più immersiva e visiva rispetto a un archivio tradizionale.
L'obiettivo è rendere la consultazione accessibile, ma allo stesso tempo coerente con l'immaginario NASA: orbite, movimento, profondità e navigazione nello spazio diventano il linguaggio con cui raccontare i progetti.
