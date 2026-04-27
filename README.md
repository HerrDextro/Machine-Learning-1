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

LB1.3
Der verwendete Spotify Datensatz enthält ausschliesslich oeffentlich verfuegbare Metadaten zu Musikstuecken, wie z. B. Titel, Kuenstler, Genre sowie akustische Merkmale (z. B. Tanzbarkeit oder Energie). Es sind keine personenbezogenen Daten oder identifizierbaren Informationen (PII) enthalten. Die Daten wurden von Spotify bzw. ueber die Kaggle Plattform bereits anonymisiert und aggregiert bereitgestellt. Dadurch besteht kein direkter Bezug zu einzelnen Nutzern und Datenschutzrichtlinien werden nicht verletzt. Zusaetzliche Massnahmen zur Anonymisierung sind daher nicht erforderlich.

## Teil 2: Datenvorbereitung und Zielsetzung
LB2.1
Da es sich um ein unüberwachtes Lernmodell (K-Means Clustering) handelt, wird kein existierendes Feld vorhergesagt. Stattdessen ist das Ziel die Vorhersage der Cluster-Zugehörigkeit (Vibe-Label) basierend auf den Audio-Merkmalen. Das Modell generiert somit eine neue kategorische Variable, die Tracks mit ähnlichen klanglichen Eigenschaften gruppiert.


LB2.2 & 2.3 Stats & Graphics: Provide the median/standard deviation for your audio features (Energy, Tempo, etc.) and a histogram or correlation heatmap.
LB2.4 Skalierung:
Für dieses Modell ist eine Skalierung (Standardisierung) zwingend erforderlich. K-Means basiert auf der Berechnung der euklidischen Distanz zwischen Datenpunkten. Da Merkmale wie 'Tempo' (Werte bis 200+) und 'Danceability' (Werte zwischen 0 und 1) völlig unterschiedliche Skalen haben, würde das Tempo die Distanzberechnung dominieren. Durch den StandardScaler werden alle Merkmale auf einen Mittelwert von 0 und eine Standardabweichung von 1 gebracht, sodass jedes Attribut das gleiche Gewicht erhält.

## Teil 3: Modell trainieren und Auswerten

LB3.1 Sorry aber K means also nicht sehr Sinnvoll
LB3.2
K-Means ist für dieses Projekt ideal, da es effizient große Datensätze wie diesen mit über 100.000 Einträgen verarbeiten kann. Da das Ziel die Identifizierung von "Vibes" ohne vordefinierte Labels ist, ermöglicht K-Means die Gruppierung von Tracks allein basierend auf der mathematischen Ähnlichkeit ihrer Audio-Features. Wir nutzen die euklidische Distanz, um Schwerpunkte zu finden, die typische Kombinationen aus Tempo, Energie und Stimmung repräsentieren. Die Wahl von scikit-learn bietet zudem robuste Implementierungen für die Cluster-Zuweisung neuer Datenpunkte aus dem Test-Set.

LB3.3

## Verwendete Technologien
* **Python 3**
* **Jupyter Notebook**
* **Pandas:** Datenmanipulation
* **Scikit-Learn:** Vorverarbeitung und Skalierung
