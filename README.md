# Projekat iz mašinskog učenja
## Klasifikacija muzičkih žanrova na osnovu audio ulaza
Cilj projekta je kreirati model koji na osnovu samog zvuka određuje kom muzičkom žanru pripada. Pristup izradi projekta se sastoji iz dva dela. Prvi deo podrazumeva samostalno treniranje konvolutivne mreže sa 1D kovolucijom, a drugi deo korišćenje pretreniranog transformera.  

## Skup podataka
Za izradu projekta korišćen je skup podataka [GTZAN](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification).

Skup sadrži 1000 instanci ravnomerno podeljenih u 10 foldera koji predstavljaju različite žanrove:
- blues
- classical
- country
- disco
- hiphop
- jazz
- metal
- pop
- reggae
- rock

Svaka pesma traje tačno 30 sekundi, a za potrebe projekta izvršena je podela na pet jednakih delova, kako bi veličina ulaza bila manja, a količina podataka veća.

## Model sa 1D konvolucijom

Prva Jupyter sveska obuhvata analizu i preprocesiranje podataka, kao i treniranje konvolutivne neuronske mreže sa različitim vrednostima learning rate-a. U drugoj Jupyter svesci se nalazi detaljnija analiza dobijenih modela, kao i evaluacija modela koji je odabran kao najbolji. Tu se takođe mogu videti i reprodukovati primeri instanci na kojima model greši. Za izradu ovog modela korišćena je biblioteka Keras.

## Transformer

Ovaj model predstavlja prilagođavanje (fine-tuning) pretreniranog modela [Wav2Vec2](https://huggingface.co/docs/transformers/model_doc/wav2vec2) na našem skupu podataka. Ovaj Transformer je bio treniran na skupu glasovnih komandi i koristi se za audio klasifikaciju, ali zahteva dodatno treniranje na željenom tipu ulaza, što je u ovom slučaju deo pesme.  Uz njega dolazi i odgovarajući Feature Extractor za preprocesiranje, koji se može dohvatiti automatski. Model i feature extractor se mogu naći u biblioteci [Transformer](https://huggingface.co/docs/transformers/index). Ova biblioteka pruža interfejs za fine-tuning dostupnih modela kroz klase Trainer i TrainingArguments, pomoću kojih se postavljaju različiti parametri. 

## Demo

Za kreiranje demo aplikacija (Jupyter sveske 4 i 5) korišćena je biblioteka [gradio](https://www.gradio.app/) koja omogućava jednostavno kreiranje GUI. Potrebno je da korisnik samo odabere audio fajl i aplikacija će prikazati procenat pripadanja te pesme svakom od muzičkih žanrova.

## Instalacije

Za pokretanje priloženih Jupyter svezaka potrebno je instalirati korišćene biblioteke:
- tensorflow
- datasets
- transformers==4.28.0
- evaluate
- torch
- soundfile
- gradio

Sve biblioteke se mogu instalirati kroz komandnu liniju:
  ```
pip install [ime-biblioteke]
  ```
ili direktno iz Jupyter sveske

```
!pip install [ime-biblioteke]
```

## Članovi tima
- Aleksandra Pešić
- Lucija Miličić
