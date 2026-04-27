# Machine-Learning-1
M259 Machine Learning in BBB. Here I will be making an unsupervised clustering model

## Projektübersicht
Dieses Projekt konzentriert sich auf die Identifizierung von "musikalischen Vibes" innerhalb eines umfangreichen Datensatzes mittels **K-Means-Clustering**. Durch die Analyse mathematischer Audio-Eigenschaften (z. B. Energy, Tempo, Acousticness) gruppiert das Modell ähnliche Tracks, ohne auf vordefinierte Genre-Labels angewiesen zu sein.

## Teil 1: Datenbeschaffung
* **Quelle:** Spotify Tracks Dataset (Kaggle)
* **Umfang:** ca. 114.000 Zeilen
* **Merkmale:** 22 Spalten (u. a. Danceability, Energy, Loudness, etc.)

## Data Engineering & Bereinigung (Sanitizing)
Um die Rohdaten für ein Machine-Learning-Modell vorzubereiten, wurden folgende Schritte mit Python und der `Pandas`-Bibliothek durchgeführt:

1.  **Deduplizierung:** Entfernung doppelter Einträge basierend auf `track_name` und `artists`. Dies verhindert eine Verzerrung des Modells durch populäre Tracks, die auf mehreren Alben erscheinen.
2.  **Feature-Selektion:** Ausschluss nicht-numerischer Metadaten (IDs, Namen, Albumtitel), um ausschließlich die klangbasierten, numerischen Merkmale zu isolieren.
    * *Ausgewählte Merkmale:* `danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`.
3.  **Bereinigung von Fehlwerten:** Durchführung einer `dropna()`-Operation, um die mathematische Konsistenz des Datensatzes sicherzustellen.
4.  **Skalierung (Standardisierung):** Einsatz des `StandardScaler`, um die Daten zu normalisieren. Dies stellt sicher, dass Merkmale mit großen Wertebereichen (wie `tempo`) die Berechnung der euklidischen Distanz im K-Means-Algorithmus nicht unverhältnismäßig stark beeinflussen.

Der verwendete Spotify Datensatz enthält ausschliesslich oeffentlich verfuegbare Metadaten zu Musikstuecken, wie z. B. Titel, Kuenstler, Genre sowie akustische Merkmale (z. B. Tanzbarkeit oder Energie). Es sind keine personenbezogenen Daten oder identifizierbaren Informationen (PII) enthalten. Die Daten wurden von Spotify bzw. ueber die Kaggle Plattform bereits anonymisiert und aggregiert bereitgestellt. Dadurch besteht kein direkter Bezug zu einzelnen Nutzern und Datenschutzrichtlinien werden nicht verletzt. Zusaetzliche Massnahmen zur Anonymisierung sind daher nicht erforderlich.


## Verwendete Technologien
* **Python 3**
* **Jupyter Notebook**
* **Pandas:** Datenmanipulation
* **Scikit-Learn:** Vorverarbeitung und Skalierung
