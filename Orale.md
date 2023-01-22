Orale di Laboratorio
======================
***Laboratorio di Meccanica e Termodinamica: domande e risposte plausibili***

**Autore:** *Lorenzo Cazzoli*

# Elenco delle domande

* [Sensori](#sensori)
* [Teorema di Nyquist](#teorema-di-nyquist)
* [Discrepanza](#discrepanza-tra-misure-della-stessa-um)
* [Propagazione delle incertezze (anche binomiale)](#propagazione-delle-incertezze-anche-binomiale)
* [Distribuzioni multivariate](#distribuzioni-multivariate)
* [Covarianza (distribuzione bivariata)](#covarianza-distribuzione-bivariata)
* [Descrivere la probabilità](#descrivere-la-probabilità)
* [Probabilità di somma e intersezione di due eventi](#probabilità-di-somma-e-intersezione-di-due-eventi)
* [Formula di bayes](#formula-di-bayes)
* [Regressione lineare(tutti i casi)](#regressione-linearetutti-i-casi)
* [Coefficiente di correlazione lineare](#coefficiente-di-correlazione-lineare)
* [Gaussiana con criterio di massima verosimiglianza](#gaussiana-con-criterio-di-massima-verosimiglianza)
* [Errore sulla media e miglior stima (massima verosimiglianza)](#errore-sulla-media-e-miglior-stima-massima-verosimiglianza)
* [Formula della varianza](#formula-della-varianza)
* [Compatibilità tra due misure(+media pesata)](#compatibilità-tra-due-misuremedia-pesata)
* [Metodo del rigetto](#metodo-del-rigetto)
* [Distribuzione binomiale (contatori di particelle)](#distribuzione-binomiale-contatori-di-particelle)
* [Distribuzione di poisson](#distribuzione-di-poisson)
* [Poissoniana come limite della binomiale](#poissoniana-come-limite-della-binomiale)
* [Chi quadrato](#chi-quadrato)
* [Random walk](#random-walk)
* [Teorema del limite centrale (+variabili non continue)](#teorema-del-limite-centrale-variabili-non-continue)
* [Somma di due variabili uniformi](#somma-di-due-variabili-uniformi)
* [Fattore di copertura](#fattore-di-copertura)
* [Esperimenti](#esperimenti)

# Sensori

Un `sensore` è un dispositivo capace di restituire una Differenza Di Potenziale in risposta al rilevamento di una grandezza fisica.
Nel tempo genera una curva `Y = f(x)` dove `Y = d.d.p.` e  `x = input`.

Un sensore è caratterizzato da:

$$ Sensibilità: \ f'(x) = \frac{dy}{dx} $$

$$ Accuratezza: \ max|f(x) - f(x)_{standard}| $$

### Catena di misura

$$ Sensore \rarr Amplificatore \rarr Digitalizzatore \ (Analog \ to \ Digital \ Converter \ = ADC) \rarr Computer \ e \ software $$

1. [`Sensore`](#sensori): restituisce un responso in d.d.p. in base alla grandezza rilevata
2. [`Amplificazione`](#amplificazione): moltiplica il segnale per il fattore di amplificazione opportuno (f amp)
3. [`Digitalizzatore ADC`](#digitalizzazione): converte il segnale amplificato in un segnale digitale
4. [`Computer + Software`](#portata): riceve il segnale e lo elabora

#### Amplificazione
Il DAQ (Amplificazione + Digitalizzazione) permette di selezionare un valore di amplificazione f amp, applicato prima della digitalizzazione.

#### Digitalizzazione
L'`ADC` trasforma il segnale da d.d.p. in binario.
L'`ADC` è caratterizzato dal numero di bit assegnati alla conversione di ciascun segnale ricevuto.
Un `ADC` a `x bit` divide il segnale in $2^{x}$ livelli.

#### Portata
La portata è il range di valori accettati a seguito dell'elaborazione del segnale da parte dell'`ADC`.
È caratterizzata da un valore `ADC min` ed uno `ADC max`.
Il fattore di amplificazione è calibrato in modo tale da poter leggere entro i valori della portata quelli riportati dal sensore, secondo la formula:

$$ f_{amp} * Y_{min} > ADC_{min} $$

$$ f_{amp} * Y_{max} \leq ADC_{max} $$

Ricordando che `Y = f(x)` è il valore di d.d.p. riportato dal sensore e $f_{amp}$ il fattore di amplificazione


# Teorema di Nyquist

Data una funzione periodica `s(t)` caratterizzata da una frequenza `fm`, il teorema di Nyquist ci dice che:

$$ Per \ ottenere \ informazioni \ sulla \ frequenza \ fm \ la \ frequenza \ di \ campionamento \ dev'essere \ due \ volte \ fm $$

$$ Per \ ottenere \ informazioni \ sulla \ forma \ di \ s(t) \ la \ frequenza \ di \ campionamento \ dev'essere \ dalle \ cinque \ alle \ dieci \ volte \ fm $$

![Grafico](Screenshot_2023-01-19_18-03-23.png "Grafico Effetto Aliasing")

Immagine sopra:
Sopra: campionamento con frequenza adeguatamente impostata (notare che i punti rossi sono i campionamenti fatti ogni dt)
Sotto: campionamento con frequenza insufficiente. Sia la frequenza della funzione che la sua forma non sono deducibili dai dati ottenuti.

![Grafico2](Screenshot_2023-01-19_18-20-26.png "Grafico esempi aliasing")

Immagine sopra:
Esempi di effetti di aliasing.


# Discrepanza tra misure della stessa u.m.

Date due misure dello stesso valore, la discrepanza è la differenza tra di esse.
Date due misure, `X` ed `Y`, con relativi errori $\sigma_{x}$ e $\sigma_{y}$, le misure sono compatibili, ovvero hanno *discrepanza non significativa* se:

$$ max|X+$\sigma_{x}$, Y+\sigma_{y}| \geq min|X-$\sigma_{x}$, Y-\sigma_{y}| $$

Lo stesso procedimento può essere applicato anche per misure appurate, o per misure il cui sigma è ottenuto per propagazione degli errori.

# Propagazione delle incertezze (anche binomiale)

## Prime approssimazioni

Per la propagazione delle incertezze si può passare per diverse approssimazioni, nel Taylor spiegate in ordine.
Come prima approssimazione possiamo considerare il valore `Z` ottenuto dalla somma di altri due come appartenente al range [$Z-(\sigma_{x}+\sigma_{y}); Z+(\sigma_{x}+\sigma_{y})$], e perciò l'incertezza come la somma delle incertezze.

$$ Z = X \pm Y ; \ \sigma_{Z} = \sigma_{X} + \sigma_{Y} $$

Mentre per valori `Z` ottenuti per prodotto di altre misure si utilizza l'incertezza relativa, secondo la formula:

$$ Z = X * Y ; \ \frac{\sigma_{Z}}{Z} = \frac{\sigma_{X}}{X} + \frac{\sigma_{Y}}{Y}  $$

Queste formule ci permettono di ricavare una formula per `Z` ottenuta come prodotto di fattori elevati ad un esponente:

$$ Z = c * X^{\alpha} * Y^{\beta} * W^{\gamma} ; \frac{\sigma_{Z}}{Z} = |\alpha|*\frac{\sigma_{X}}{X} + |\beta|*\frac{\sigma_{Y}}{Y} + |\gamma|*\frac{\sigma_{W}}{W} $$

## Somma in quadratura

### Esposizione

Ma le formule di cui sopra sono in fin dei conti approssimazioni per ottenere il valore dell'errore *massimo*, non del più probabile. Per ottenere l'errore più *probabile*, invece, si usa un altro processo, adesso esposto e poi giustificato.

$$ Z = X + Y ; \ \sigma_{Z} = \sqrt{\sigma_{X}^2 + \sigma_{Y}^2} $$

Questa è la **somma in quadratura**, e rappresenta più precisamente l'errore più probabile ottenuto dalla somma di misure.
Perché la somma in quadratura dovrebbe essere più precisamente in grado di rappresentare l'errore più probabile?
Perché, se sia `X` che `Y` sono misure *indipendenti* e dotate di sole incertezze *casuali*, si ha una probabilità del 50% di avere una *sovrastima* di `X` sia associata ad una *sottostima* di `Y`. Nel caso invece le misure di `X` ed `Y` fossero correlate in qualche modo (effettuate con lo stesso strumento, o sono correlate da qualunque tipo di fattore), sarebbe probabile che ad una *sovrastima* di `X` sia associata una *sovrastima* di `Y`, e perciò l'errore sarebbe più simile a quello descritto nel paragrafo precedente.
Di seguito la dimostrazione matematica di quanto appena detto:

### Dimostrazione

La dimostrazione richiede la comprensione della [probabilità](#descrivere-la-probabilità) e della funzione di distribuzione di probabilità standard, la [Gaussiana](#gaussiana-con-criterio-di-massima-verosimiglianza).
Detto cio, suddividiamo il problema in `4` casi distinti:

1. *Grandezza misurata con somma di costante numerica*

$$ q = x + A $$

con A fissato e senza incertezza, ed `x` distribuito normalmente attorno ad un valore vero `X`, con una larghezza $\sigma_{x}$.
La probabilità di ottenere un qualunque valore `x` sarà:

$$ P(x) \propto G_{X,\sigma}(x)dx \ proporzionale \ a \ e^{\frac{-(x-X)^{2}}{2\sigma^2}} $$

$$ q = x + A \rarr x = q - A \rarr e^{\frac{-(q-A-X)^{2}}{2\sigma^2}} = e^{\frac{-(x-(X+A))^{2}}{2\sigma^2}} $$

da cui, per la forma della Gaussiana, essendo $ \sigma_{q} = \sigma_{x} $, l'errore rimane invariato in `q`.

2. *Grandezza misurata moltiplicata per una costante numerica*

$$ q = x*B $$

con B fissato e senza incertezza, ed `x` distribuito normalmente attorno ad un valore vero `X`, con una larghezza $\sigma_{x}$.
Seguendo un processo simile al 1., possiamo dire che la probabilità di ottenere un valore `q` sarà proporzionale a:

$$ P(q) \propto e^{\frac{-(\frac{q}{B}-X)^{2}}{2\sigma^2}} = e^{\frac{-(q-BX)^{2}}{2B^{2}\sigma^2}} $$

ovvero, secondo la forma della Gaussiana, i valori di `q` saranno distribuiti normalmente attorno ad un valore medio `q=B` e con larghezza `B`$*\sigma_{x}$.
Da cui l'incertezza su `q` è `B` volte quella in `x`

3. *Somma di due grandezze misurate*

$$ q = x + y $$

con sia `x` che `y` indipendenti e distribuiti secondo due rispettive distribuzioni normali con medie `X` ed `Y` e larghezze $\sigma_{x}$ e $\sigma_{y}$.
Avremo che le probabilità di ottenere un `x` ed un `y` saranno proporzionali alle seguenti:

$$ P(x) \propto e^{\frac{-(x-X)^{2}}{2\sigma_{x}^2}} $$

$$ P(y) \propto e^{\frac{-(y-Y)^{2}}{2\sigma_{y}^2}} $$

Essendo `x` ed `y` indipendenti la probabilità di ottenere un `x` ed un `y` dati sarà il prodotto delle due probabilità.
Per facilitare la dimostrazione svolgiamo i calcoli con `X` ed `Y` uguali a `0`.

$$ P(x,y) \propto exp(-\frac{1}{2}*(\frac{x^2}{\sigma_{x}^2} + \frac{x^2}{\sigma_{y}^2})) $$

Secondo l'identità qui sotto dimostrata:

$$ \frac{x^2}{A} + \frac{y^2}{B} = \frac{(x+y)^2}{A+B} + \frac{(Bx-Ay)^2}{AB(A+B)} = \frac{(x+y)^2}{A+B}+z^2 $$

(ponendo z^2 al posto del secondo termine). DIMOSTRAZIONE IDENTITÀ:

$$ \frac{x^2}{A} + \frac{y^2}{B} = \frac{Bx^2 + Ay^2}{AB} = \frac{(A+B)B*x^2 + (A+B)A*y^2}{AB(A+B)} = \frac{(AB + B^2)x^2 + (AB + A^2)y^2}{AB(A+B)} = \frac{ABx^2 + B^2x^2 + ABy^2 + A^2y^2 +2ABxy -2ABxy}{AB(A+B)} =  $$

$$ = \frac{AB(x^2+2xy+y^2) + B^2x^2 -2ABxy +A^2y^2}{AB(A+B)} = \frac{AB(x+y)^2 + (Bx - Ay)^2}{AB(A+B)} = \frac{(x+y)^2}{A+B} + \frac{(Bx-Ay)^2}{AB(A+B)} $$

Sostituendo secondo l'identità appena dimostrata la somma di $\frac{x^2}{\sigma_{x}^2} + \frac{y^2}{\sigma_{y}^2}$ otteniamo:

$$ P(x,y) \propto exp(-\frac{(x+y)^2}{2(\sigma_{x}^2+\sigma_{y}^2)} -\frac{z^2}{2}) $$

che però può essere considerata come la probabilità di ottenere valori di `x + y` e `z`, e riscritta come:

$$ P(x+y,z) \propto exp(-\frac{(x+y)^2}{2(\sigma_{x}^2+\sigma_{y}^2)}) exp(-\frac{z^2}{2}) $$

per ottenere una probabilità di `x + y` a prescindere da `z` si integra su `z`:

$$ \int_{-\infty}^{+\infty} P(x+y,z)\ dz = P(x+y)*\sqrt{2\pi}  $$

Da cui i valori di `x+y` sono distribuiti normalmente con larghezza:

$$ \sigma_{x+y} = \sqrt{\sigma_{x}^2 + \sigma_{y}^2} $$

che è la stima dell'errore che avevamo preventivato come somma in quadratura.
Se `X` ed `Y` sono diversi da `0` abbiamo che:

$$ x+y = (x-X)+(y-Y)+(X+Y) $$

i termini `x-X` ed `y-Y` sono centrati in `0` con larghezza $\sigma_{x}$ e $\sigma_{y}$, come ottenuto in 1, perciò la loro somma, come appena dimostrato, è distribuita uniformemente con larghezza $\sigma_{x+y}$ in `0`.
Il termine `X+Y` è un valore fisso senza errore, da per cui, come secondo il punto 1., sposta solamente la media in `X+Y`, senza influire sulla larghezza della distribuzione. Da cui:

$$ q = x + y \ ; \ \sigma_{q} = \sqrt{\sigma_{x}^2 + \sigma_{y}^2} $$

4. *Caso generale*

Supponendo di avere una `q` ottenuta da un `x` ed un `y`, non come semplice somma ma come qualunque tipo di funzione.
Ipotizzando di avere $\sigma_{x}$ e $\sigma_{y}$ sufficientemente piccole da poter fare un'approssimazione lineare della funzione `q`, otteniamo:

$$ q(x,y) \approx q(X,Y) + \frac{\partial{q}}{\partial{x}}(x-X) + \frac{\partial{q}}{\partial{y}}(y-Y)  $$

l'approssimazione può essere detta valida in quanto essendo normalmente distribuiti, `x` ed `y` appaiono significativamente solo se relativamente vicini a `X` o `Y`.
Adesso, analizzando la distribuzione di `q(x,y)`, possiamo osservare che è composta dalla somma di tre termini:
1. `q(X,Y)`, che essendo un valore fissato sposta solamente la media, senza influire sulla larghezza
2. la derivata parziale di `q` (un valore fisso in X), moltiplicata per `(x-X)` ha distribuzione normale attorno allo zero con larghezza pari a "derivata di q in x * $\sigma_{x}$"
3. analoga a 2.
Sommando i tre componenti di `q(x,y)`, come visto nei punti 1.-4. otteniamo una distribuzione normale di centro e larghezza seguenti:

$$ q(X,Y) \ ; \ \sigma_{q} = \sqrt{(\frac{\partial{q}}{\partial{x}}\sigma_{x})^2 + (\frac{\partial{q}}{\partial{y}}\sigma_{y})^2} $$

**Questa sopra è la formula generale per il calcolo della propagazione delle incertezze**

# Distribuzioni multivariate

Funzioni dipendenti da più di una variabile casuale sono dette *multivariate*.
Nel corso di Laboratorio di Meccanica e Termodinamica ci si è concentrati sulle funzioni dipendenti da **due** variabili casuali, dette anche *bivariate*.
Per funzioni bivariate è possibile disporre i dati ottenuti in un grafico bidimensionale, con lungo ogni asse una variabile casuale, detto **scatter plot**, o **grafico di dispersione**, ed estrapolarne un grafico "tridimensionale", più accuratamente un istogramma bidimensionale, detto **LEGO plot**.
Il LEGO plot rappresenta sulla terza dimensione il numero di eventi per ogni coordinata degli altri due assi.
Analogamente per il caso monodimensionale, un istogramma bidimensionale i cui bin tendono ad un numero infinito permette la definizione di una funzione di distribuzione di probabilità (PDF bidimensionale)
Al fine di trattare come indipendenti le due variabili abbiamo però la necessità di uno strumento che ci permetta di quantificare la correlazione tra le due. Questo sarà detto covarianza, e definito nel prossimo paragrafo.

# Covarianza (distribuzione bivariata)

Data una funzione multivariata, `f(x,y)`, dalla formula della propagazione delle incertezze (comunque sarà riportata la dimostrazione a seguito) possiamo ricavare che la [**varianza**](#formula-della-varianza) di `f(x,y)` sarà:

$$ \sigma_{f(x,y)}^2 = (\frac{\partial{q}}{\partial{x}}\sigma_{x})^2 + (\frac{\partial{q}}{\partial{y}}\sigma_{y})^2 + 2(\frac{\partial{q}}{\partial{x}}\frac{\partial{q}}{\partial{y}})\sigma_{xy} $$

Con $\sigma_{xy}$ come valore di **covarianza**, ovvero:

$$ \sigma_{xy} = \frac{1}{N} \sum_{i}(x_{i}-\bar{x})(y_{i}-\bar{y}) $$

Se i valori `x` ed `y` sono indipendenti, per `N` tendenti ad $\infty$, la covarianza tenderà a 0, se **non** sono indipendenti avrà un valore che ci dà informazioni riguardo il tipo di correlazione.
Se $\sigma_{xy} > 0 \rarr x \propto y$, mentre se $\sigma_{xy} < 0 \rarr x \propto y^{-1}$  

## Due possibili dimostrazioni della Covarianza

### Taylor (con la varianza, p.213)
 
$$ Varianza \ = \sigma_{q}^2 = \frac{1}{N} \sum (q_{i}-\bar{q})^2 $$
$$ q_{i} = q(x_{i},y_{i}) \ che \ per \ approssimazione \ lineare \ di \ q \ per \ (x_{i}-\bar{x}) \ piccoli: \ 
q_{i} \approx q(\bar{x}, \bar{y}) + \frac{\partial{q}}{\partial{x}}(x_{i}-\bar{x}) + \frac{\partial{q}}{\partial{y}}(y_{i}-\bar{y}) $$
$$ \bar{q} = \frac{1}{N}\sum_{i}^{N}q_{i}, \ sostituendo \ la \ formula \ sopra: \ \bar{q} = q(\bar{x}, \bar{y}), \ siccome \ gli \ altri \ termini \ si \ annullano. \ (dalla \ def. \ di \ \bar{x} \ segue \ che: \ \sum(x_{i} - \bar{x}) = 0) $$

Sostituendo le ultime due equazioni nella formula della varianza otteniamo che:

$$ \sigma_{q}^2 = \frac{1}{N}\sum[\frac{\partial{q}}{\partial{x}}(x_{i}-\bar{x}) + \frac{\partial{q}}{\partial{y}}(y_{i}-\bar{y}]^2 $$
$$ = (\frac{\partial{q}}{\partial{x}})^2 \frac{1}{N} \sum(x_{i}-\bar{x})^2 + (\frac{\partial{q}}{\partial{y}})^2 \frac{1}{N} \sum(y_{i}-\bar{y})^2 + 2\frac{\partial{q}}{\partial{x}}\frac{\partial{q}}{\partial{y}}\sum(x_{i}-\bar{x})(y_{i}-\bar{y}) $$

Adesso, i primi due termini sono per definizione i valori $\sigma_{x}$ e $\sigma_{y}$, mentre il terzo è proprio il valore della covarianza.

### Con deviazione standard massima

Considerando i risultati ottenuti nella dimostrazione della somma in quadratura, possiamo dire che il valore massimo della deviazione standard sia = alla somma degli errori, ovvero alla somma delle derivate parziali della nostra `q`, ognuna di esse moltiplicata per il valore dell'errore sulla variabile di derivazione:

$$ \sigma_{q} \leq \frac{\partial{q}}{\partial{x}}\sigma_{x} + \frac{\partial{q}}{\partial{y}}\sigma_{y} $$

Non ci rimane che elevare al quadrato per ottenere la varianza:

$$ \sigma_{q}^2 \leq (\frac{\partial{q}}{\partial{x}}\sigma_{x})^2 + (\frac{\partial{q}}{\partial{y}}\sigma_{y})^2 + 2\frac{\partial{q}}{\partial{x}}\frac{\partial{q}}{\partial{y}}\sigma_{x}\sigma_{y} $$

Adesso, per la **Disuguaglianza di Schwartz**, $\sigma_{x}\sigma_{y}$ è proprio il valore massimo di $|\sigma_{xy}|$, se questa è definita come abbiamo detto all'inizio del paragrafo.
Possiamo sostituirla ed abbiamo il nostro risultato, come per la [dimostrazione del Taylor](#taylor-con-la-varianza-p213).

# Coefficiente di correlazione lineare

Il **coefficiente di correlazione lineare**, `r`, è un valore adimensionale compreso tra -1 ed 1, che indica quanto due valori sono correlati da una relazione funzionale (in particolare lineare). 
`r` è definito come:

$$ r = \frac{\sigma_{xy}}{\sigma{x}\sigma_{y}} = \frac{\sum(x_{i}-\bar{x})(y_{i}-\bar{y})}{\sqrt{\sum(x_{i}-\bar{x})^2*\sum(y_{i}-\bar{y})^2}} $$

## dimostrazione del dominio di r

essendo $|\sigma_{xy}| \leq \sigma_{x}\sigma_{y}$ il loro rapporto è al massimo 1 ed al minimo -1.

In alternativa, considerando una `y` ottenuta in funzione di `x` secondo una correlazione lineare possiamo ottenere che `r` sarà = $\pm 1$:

$$ y_{i} = A + Bx_{i} \rarr \bar{y} = A + B\bar{x} $$

$$ r = \frac{\sum(x_{i}-\bar{x})(A+Bx_{i}-A+B\bar{x})}{\sqrt{\sum(x_{i}-\bar{x})^2*\sum(A+Bx_{i}-A+B\bar{x})^2}} = 
\frac{B\sum(x_{i}-\bar{x})^2}{|B|\sqrt{\sum(x_{i}-\bar{x})^2}} = \frac{B}{|B|} = \pm 1 $$

Per decretare la significatività di una correlazione lineare, si può studiare la probabilità che un `r` sia maggiore di `|r|` dato `N`, secondo una distribuzione particolare data dalla formula (non richiesta nell'orale):

$$ P_{N}(|r|>|r_{0}|) = \frac{2\Gamma[(N-1)/2]}{\sqrt{\pi}\Gamma[(N-2)/2]}\int_{|r_{0}|}^{1} (1-r^2)^{(N-4)/2} dr $$

Se la probabilità di `r` maggiori è minore del `5%` la correlazione è **significativa**, se è minore dell'`1%` è **altamente significativa**. 

# Metodo del rigetto

È possibile, in un campione di dati distribuiti normalmente (secondo una distribuzione Gaussiana), rigettare dati altamente improbabili secondo il **Criterio di Chauvenet**, che dice:

> Se il numero atteso di misure improbabili, cioè misure che distano dalla media più di z variazioni standard (con z = (Xsospetta - Xbest)/sigma) è minore di 0.5, la misura può essere rigettata

Per ottenere il numero di misure attese data la probabilità di $z > z_{0}$ moltiplicare tale probabilità per il numero di campioni. 

# Descrivere la probabilità



# Probabilità di somma e intersezione di due eventi

# Formula di bayes

$$ Formula \ di \ Bayes:$$

$$ P(Hi|E) = \frac{P(E|Hi)*P(Hi)}{P(E)} $$

$$ Con: P(E)=\sum_{i=0}^{N}{P(E|Hi)*P(Hi)} $$

La formula è ricavata sempicemente, data la definizione di probabilità condizionata ed il teorema della probabilità composta, il tutto portato al caso in cui, essendo presenti più eventi, la combinazione totale sia una sommatoria:

$$ Per \ definizione \ di \ probabilità \ combinata: \ P(Hi|E) = \frac{P(E\cap Hi)}{P(E)} $$ 

$$ Per \ il \ teorema \ della \ probabilità \ composta: \ P(E \cap Hi)=P(E|Hi)*P(Hi) $$

Ora non resta che dire che, se la probabilità complessiva che avvenga E sia la sommatoria di più probabilità, ognuna di esse data dalla probabilità composta di un evento *Hi-esimo*, ed abbiamo ottenuto la Formula di Bayes.

# Regressione lineare(tutti i casi)
# Gaussiana con criterio di massima verosimiglianza
# Errore sulla media e miglior stima (massima verosimiglianza)
# Formula della varianza
# Compatibilità tra due misure(+media pesata)
# Distribuzione binomiale (contatori di particelle)
# Distribuzione di poisson
# Poissoniana come limite della binomiale
# Chi quadrato
# Random walk
# Teorema del limite centrale (+variabili non continue)
# Somma di due variabili uniformi
# Fattore di copertura
# Esperimenti
