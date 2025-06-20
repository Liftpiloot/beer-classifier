# The Perfect Pour 🍻
Een machine learning-project om te bepalen of een pilsje correct is ingeschonken

## Overzicht
Dit project ontwikkelt een machine learning-model dat automatisch herkent of een glas bier correct is ingeschonken, met een focus op de juiste schuimkraag en hoeveelheid. Het model kan gebruikt worden voor kwaliteitscontrole in de horeca of als educatief voorbeeld van beeldclassificatie.

## Inhoud
- [Beschrijving](#beschrijving)
- [Dataset](#dataset)
- [Data preprocessing & augmentatie](#data-preprocessing--augmentatie)
- [Feature extractie](#feature-extractie)
- [Gebruikte modellen](#gebruikte-modellen)
- [Resultaten](#resultaten)
- [Uitlegbare AI (Explainable AI)](#uitlegbare-ai-explainable-ai)
- [Conclusie & Advies](#conclusie--advies)
- [Installatie & Gebruik](#installatie--gebruik)

## Beschrijving
Het doel van dit project is te onderzoeken of een machine learning-model kan bepalen of een pilsje correct is ingeschonken. Hiervoor is een dataset samengesteld van afbeeldingen van glazen bier, handmatig gelabeld als ‘correct’ of ‘incorrect’ ingeschonken. Het model wordt getraind om deze classificatie automatisch uit te voeren.

## Dataset
De dataset bestaat uit afbeeldingen van correct en incorrect ingeschonken bier, afkomstig van [images.cv](https://images.cv/dataset/beer-glass-image-classification-dataset) en handmatig aangevuld. 
- Correcte afbeeldingen staan in de map `correct_beer`
- Incorrecte afbeeldingen staan in de map `incorrect_beer`
Alle afbeeldingen zijn `.jpg`-bestanden, gecropt en gelabeld met behulp van YOLOv8.

## Data preprocessing & augmentatie
Omdat de dataset scheef verdeeld is (meer incorrect dan correct), wordt data augmentatie toegepast op de minderheidsklasse. Methoden als flippen, roteren en helderheid aanpassen zorgen voor een gebalanceerde dataset zonder informatieverlies.

## Feature extractie
Er worden verschillende soorten features uit de afbeeldingen gehaald:
- **Region-based color statistics**: Wit-percentage in de bovenste derde van het glas (schuimherkenning)
- **Kleurstatistieken (HSV)**: Gemiddelde kleurwaarden in het middengedeelte
- **Histogram of Oriented Gradients (HOG)**: Herkent randen en vormen, bijvoorbeeld de scheiding tussen schuim en bier

## Gebruikte modellen
Het project vergelijkt meerdere classificatiemodellen:
- Logistic Regression (met cross-validatie)
- Support Vector Machine (SVM, met cross-validatie)
- Random Forest (met cross-validatie)

## Resultaten
De prestaties van de modellen worden geëvalueerd aan de hand van accuracy, confusion matrix en explainable AI technieken. Uit de analyses blijkt dat bepaalde features, zoals het wit-percentage bovenaan, goed onderscheidend zijn. Door data augmentatie presteert het model significant beter.

## Uitlegbare AI (Explainable AI)
Met behulp van SHAP en feature importance analyses worden de belangrijkste kenmerken inzichtelijk gemaakt die bijdragen aan een correcte classificatie.

## Conclusie & Advies
Het model kan met redelijke nauwkeurigheid bepalen of een pilsje correct is ingeschonken. Vooral de schuimlaag en de kleur in het midden van het glas zijn belangrijk. Voor verdere verbetering is uitbreiding van de dataset aan te raden.

## Installatie & Gebruik

1. **Clone de repository**
    ```bash
    git clone https://github.com/Liftpiloot/beer-classifier.git
    cd beer-classifier
    ```

2. **Installeer de vereiste packages**
    - Gebruik bij voorkeur een virtual environment of conda:
    ```bash
    pip install -r requirements.txt
    ```
    of
    ```bash
    conda env create -f environment.yml
    conda activate beerClassifier
    ```
    (Zie de notebook voor een overzicht van gebruikte libraries.)

3. **Dataset**
    - Plaats de afbeeldingen in de juiste mappen: `correct_beer/` en `incorrect_beer/`.

4. **Notebook uitvoeren**
    - Open `Beer_classifier.ipynb` in Jupyter Notebook of JupyterLab en volg de stappen in het notebook.

## Auteur
- Abel van Dijk  
- Fontys ICT & AI, semester 4  
- Juni 2025
