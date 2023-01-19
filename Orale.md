Orale di Laboratorio
======================
***Laboratorio di Meccanica e Termodinamica: domande e risposte plausibili***

**Autore:** *Lorenzo Cazzoli*

# Elenco delle domande

* [Sensori](#sensori)
* [Teorema di Nyquist](#teorema-di-nyquist)
* [Campionamenti differenti della stessa grandezza](#campionamenti-differenti-della-stessa-grandezza)
* [Propagazione delle incertezze (anche binomiale)](#propagazione-delle-incertezze-anche-binomiale)
* [Distribuzioni multivariate](#distribuzioni-multivariate)
* [Descrivere la probabilità](#descrivere-la-probabilità)
* [Probabilità di somma e intersezione di due eventi](#probabilità-di-somma-e-intersezione-di-due-eventi)
* [Formula di bayes](#formula-di-bayes)
* [Regressione lineare(tutti i casi)](#regressione-linearetutti-i-casi)
* [Coefficiente di correlazione lineare](#coefficiente-di-correlazione-lineare)
* [Covarianza (distribuzione bivariata)](#covarianza-distribuzione-bivariata)
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
Un `ADC` a `x bit` divide il segnale in `2^(x)` livelli.

#### Portata
La portata è il range di valori accettati a seguito dell'elaborazione del segnale da parte dell'`ADC`.
È caratterizzata da un valore `ADC min` ed uno `ADC max`.
Il fattore di amplificazione è calibrato in modo tale da poter leggere entro i valori della portata quelli riportati dal sensore, secondo la formula:

$$ f_{amp} * Y_{min} > ADC_{min} $$

$$ f_{amp} * Y_{max} \leq ADC_{max} $$

Ricordando che `Y = f(x)` è il valore di d.d.p. riportato dal sensore e `f amp` il fattore di amplificazione


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


# Campionamenti differenti della stessa grandezza



# Propagazione delle incertezze (anche binomiale)

# Distribuzioni multivariate

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
# Coefficiente di correlazione lineare
# Covarianza (distribuzione bivariata)
# Gaussiana con criterio di massima verosimiglianza
# Errore sulla media e miglior stima (massima verosimiglianza)
# Formula della varianza
# Compatibilità tra due misure(+media pesata)
# Metodo del rigetto
# Distribuzione binomiale (contatori di particelle)
# Distribuzione di poisson
# Poissoniana come limite della binomiale
# Chi quadrato
# Random walk
# Teorema del limite centrale (+variabili non continue)
# Somma di due variabili uniformi
# Fattore di copertura
# Esperimenti
