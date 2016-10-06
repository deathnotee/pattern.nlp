# pattern.nlp
R package to perform sentiment analysis and Parts of Speech tagging for Dutch/French/English/German

The  **pattern.nlp** package allows to do the following text mining tasks based on the pattern library

- POS tagging: Parts of Speech tagging for Dutch, French, English, German
- Sentiment analysis: Sentiment + subjectivity scoring for Dutch, French, English

![](http://www.clips.ua.ac.be/media/pattern_schema.gif)

## Examples

The following shows how to use the package

### Sentiment analysis

```
library(pattern.nlp)

## Sentiment analysis
x <- pattern_sentiment("i really really hate iphones", language = "english")
y <- pattern_sentiment("de wereld is een mooie plaats, nietwaar sherlock", language = "dutch")
z <- pattern_sentiment("j'aime Paris, c'est super", language = "french")
rbind(x, y, z)

polarity subjectivity                                               id
   -0.80         0.90                     i really really hate iphones
    0.70         1.00 de wereld is een mooie plaats, nietwaar sherlock
    0.65         0.75                        j'aime Paris, c'est super
```

### Parts of Speech tagging

```
x <- "Mevrouw wenst zich aan te sluiten bij onze dienst, kan dat wel zomaar?"
pattern_pos(x = x, language = 'dutch')

x <- "Il pleure dans mon coeur comme il pleut sur la ville.
 Quelle est cette langueur qui penetre mon coeur?"
pattern_pos(x = x, language = 'french')

x <- "BNOSAC provides consultancy in open source analytical intelligence. 
 We gather dedicated open source software engineers with a focus on data mining, 
 business intelligence, statistical engineering and advanced artificial intelligence."
pattern_pos(x = x, language = 'english')

x <- "Der Turmer, der schaut zu Mitten der Nacht. 	
 Hinab auf die Graber in Lage
 Der Mond, der hat alles ins Helle gebracht.
 Der Kirchhof, er liegt wie am Tage.
 Da regt sich ein Grab und ein anderes dann."
pattern_pos(x = x, language = 'german')
```

The output of the POS tagging shows at least the following elements:
```
sentence.id sentence.language chunk.id chunk.type chunk.pnp chunk.relation word.id     word word.type word.lemma
         9                fr        1         NP      <NA>            SBJ       1       Il       PRP         il
         9                fr        2         VP      <NA>           <NA>       2   pleure        VB    pleurer
         9                fr        3        PNP       PNP           <NA>       3     dans        IN       dans
         9                fr        3        PNP       PNP           <NA>       4      mon      PRP$        mon
         9                fr        3        PNP       PNP           <NA>       5    coeur        NN      coeur
         9                fr        4        PNP       PNP           <NA>       6    comme        IN      comme
         9                fr        4        PNP       PNP           <NA>       7       il       PRP         il
         9                fr        5         VP      <NA>           <NA>       8    pleut        VB   pleuvoir
         9                fr        6        PNP       PNP           <NA>       9      sur        IN        sur
         9                fr        6        PNP       PNP           <NA>      10       la        DT         la
         9                fr        6        PNP       PNP           <NA>      11    ville        NN      ville
         9                fr        7       <NA>      <NA>           <NA>      12        .         .          .
        10                fr        1         NP      <NA>            SBJ      13   Quelle       PRP     quelle
        10                fr        2         VP      <NA>           <NA>      14      est        VB       être
        10                fr        3         NP      <NA>            OBJ      15    cette       PRP      cette
        10                fr        3         NP      <NA>            OBJ      16 langueur        NN   langueur
        10                fr        4       <NA>      <NA>           <NA>      17      qui        WP        qui
        10                fr        5         VP      <NA>           <NA>      18  penetre        VB    penetre
        10                fr        6         NP      <NA>            OBJ      19      mon      PRP$        mon
        10                fr        6         NP      <NA>            OBJ      20    coeur        NN      coeur
        10                fr        7       <NA>      <NA>           <NA>      21        ?         .          ?
```

## Installation

First install Python version 2.5+ (not version 3) and the pattern package (http://www.clips.ua.ac.be/pages/pattern). 

```
pip install pattern
```

Make sure the location of Python is into the PATH and proceed by installing the R package as follows:

```
devtools::install_github("bnosac/pattern.nlp", args = "--no-multiarch")
```

Make sure your when you run the R version (64/32 bit) it is the same as the Python version you installed (64/32 bit).
Advise: don't use RStudio, but just plain R when executing the code. 


## Support in text mining

Need support in text mining. 
Contact BNOSAC: http://www.bnosac.be