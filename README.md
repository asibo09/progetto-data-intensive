# 🏎️ Analisi Telemetrica e Classificazione Stile di Guida in Formula 1 🏎️
*Progetto per il corso di Tecnologie Web (A.A. 2025/2026), Ingegneria e Scienze Informatiche, Università di Bologna - Cesena.*

---

## 🎯 Descrizione del problema e Obiettivi
Il progetto va ad applicare tecniche di Machine Learning all'ecosistema della Formula 1, sfruttando dati telemetrici e dati meteorologici. Il progetto si divide in due task principali:

1. **Task di Regressione:** Predizione del tempo sul giro in base all'usura degli pneumatici e alle condizioni ambientali.
2. **Task di Classificazione:** Riconoscimento multiclasse tra 6 piloti basato sulle telemetrie di ciascuno. L'analisi evolve da una baseline lineare a modelli non lineari, andando ad analizzare nel dettaglio 10 circuiti differenti per validare l'impatto della topologia del tracciato sull'accuratezza del modello.

**Fonte dei dati:** I dati sono estratti dalle API ufficiali fornite dalla libreria `FastF1`, che garantisce l'accesso a telemetria, cronometraggio, meteo, ecc..

---

## 🕜 TASK 1: Predizione Tempo sul Giro
### Caricamento della Sessione e Analisi della Struttura dei Dati

L'evento selezionato è il Gran Premio d'Italia, Monza 2025 - Gara. Tramite la libreria `FastF1` è stata caricata l'intera sessione, questa ci dà accesso a diversi DataFrame contenenti i tempi sul giro, i dati meteorologici e la telemetria delle singole vetture.

Estratto il dataset relativo ai giri completati (`Lap Data`) per i due piloti in analisi: Charles Leclerc (LEC) e Lewis Hamilton (HAM). <br>

Algoritmi utilizzati per il training: **Linear Regression** e **Random Forest**.

---
## 🧑‍🔧 TASK 2: Classificazione dello Stile di Guida tramite Telemetria
### Contesto e Obiettivo del Task Multi-Classe (6 Piloti)

L'obiettivo di questo task è costruire un modello di Classificazione Multi-Classe capace di riconoscere quale pilota si trova alla guida basandosi esclusivamente sulle azioni telemetriche.
Per rendere l'esperimento estremamente robusto ed esplorare il peso della variabile "telaio/scuderia" rispetto alla variabile "umana", sono stati analizzati 6 top driver appartenenti a 4 scuderie differenti:
* **Ferrari:** Charles Leclerc (LEC) e Lewis Hamilton (HAM)
* **McLaren:** Lando Norris (NOR) e Oscar Piastri (PIA)
* **Mercedes:** George Russell (RUS)
* **Red Bull:** Max Verstappen (VER)

Si sono analizzate come feature i seguenti dati telemetrici: `Speed`, `Brake`, `Throttle`, `RPM`, `nGear`, `Distance`, `DRS`.

Algoritmi utilizzati per il training: **Logistic Regression**, **Decision Tree Classifier** e **Random Forest Classifier**.

Dopo che i modelli hanno imparato le firme telemetriche di ciascun pilota si è fatta una valutazione attraverso una matrice di confusione 6x6 e si è notato che l'algoritmo tende a confondere maggiormente i compagni di squadra, suggerendo che la meccanica dell'auto domina, o piloti di scuderie diverse con stili di guida affini.
