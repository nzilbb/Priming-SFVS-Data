# Priming-SFVS-Data

Dan Villarreal (University of Pittsburgh)

This repository contains data for the under-review paper "Intraspeaker priming across the New Zealand English short front vowel shift." The data consists of 91,146 tokens of short front vowels (TRAP, DRESS, KIT) from New Zealand English, from the [QuakeBox corpus](https://doi.org/10.1016/j.amper.2016.01.001). Of these, the final model was modeled on 59,824 tokens due to various exclusions (e.g., outliers were excluded); information on which tokens were analyzed in the final model is encoded in the column `In_Mod`. To ensure anonymity, the Word column has been replaced with anonymous codes, and the SpkrCode column uses anonymized QuakeBox codes.

The data is in two formats: .Rds (for use in the R statistical computing environment) and .csv (with blanks for what are called `NA`s in R parlance).

If you have any questions, please do not hesitate to email me (d.vill atsign pitt.edu) or create a GitHub issue.

## Columns

In these columns, the _target_ is the current instance of a short front vowel (TRAP, DRESS, KIT), and the _prime_ is the preceding instance (which may or may not be of the same lexical set as the target). Prime columns have missing values if the target is the speaker's first token in the data.

* `SpkrCode`: Speaker code
* `FirstRow`: (Boolean) Is this the speaker's first token in the data?
* `Gender`, `AgeCategory`: Speaker attributes
* `MatchId`: Internal [LaBB-CAT](http://labbcat.sourceforge.net/) code for each token
* `SpeechRate`: Articulation rate (syllables per second) of the line in which the token is found
* `SpeechRateDev`: Speech rate deviance (`SpeechRate` of current line divided by speaker's mean `SpeechRate`)
* `Word`: Anonymized word code
* `WordStart`, `WordEnd`: Word timepoints within transcript
* `TargetCorpusFreq`: Frequency of the target word within QuakeBox
* `WordMentions30s`: Mentions of the same word within the preceding 30 seconds
* `VowelStart`, `VowelEnd`, `VowelMid`: Vowel timepoints within transcript
* `PrecSegment`: The previous segment before the token, in [Wells lexical set notation](https://en.wikipedia.org/wiki/Lexical_set#Wells_Standard_Lexical_Sets_for_English) for vowels, [two-letter ARPABET](https://en.wikipedia.org/wiki/ARPABET#Symbols) notation for consonants, or "WordBound" for word-initial tokens
* `PrecSegmentStart`, `PrecSegmentEnd`: Preceding segment timepoints
* `PrecSegmentVoice`, `PrecSegmentPlace`, `PrecSegmentManner`: Preceding segment features
* `FollSegment`: The next segment after the token, with the same notation as `PrecSegment`
* `FollSegmentStart`, `FollSegmentEnd`: Following segment timepoints
* `FollSegmentVoice`, `FollSegmentPlace`, `FollSegmentManner`: Following segment features
* `F1_50`, `F2_50`, `F3_50`: Raw (un-normalized) formant measurements at `VowelMid`
* `F1_norm`, `F2_norm`, `F3_norm`: Normalized formant measurements, using the Atlas of North American English method (default G value)
* `TargetShiftIndex`: _Shift index_ for target/prime, a measure of advancement with respect to the NZE short front vowel shift (SFVS) calculated as a linear combination of `F1_norm` and `F2_norm`. Greater shift index means more advanced with respect to NZE SFVS (i.e., higher & fronter TRAP, higher & fronter DRESS, lower & backer KIT), lesser shift index means more conservative. Missing values indicate that target formant measurements were outliers.
* `PrimeShiftIndex`: Shift index for prime, calculated the same as for target. Missing values indicate that either prime formant measurements were outliers, or the target is the speaker's first token in the data.
* `PrimeCorpusFreq`: Frequency of the prime word within QuakeBox
* `TargetStopword`/`PrimeStopword`: (Boolean) Is the target/prime word a stopword (a high-frequency and/or function word excluded from the data)?
* `TargetNumSyll`/`PrimeNumSyll`: Number of syllables in the target/prime word
* `PrimeMorpheme`/`TargetMorpheme`: Morphological class (grammatical vs. lexical) for the prime/target morpheme
* `TargetStress`/`PrimeStress`: Syllable stress: ' for primary, " for secondary, 0 for unstressed, _ for single-syllable words that are usually unstressed
* `TargetVowelCategory`/`PrimeVowelCategory`: Lexical set of target/prime in [Wells lexical set notation](https://en.wikipedia.org/wiki/Lexical_set#Wells_Standard_Lexical_Sets_for_English)
* `TargetVowelDur`/`PrimeVowelDur`: Duration of target/prime vowel
* `TargetOutlier`/`PrimeOutlier`: (Boolean) Are target/prime formant measurements outliers?
* `PrimeTargetSameExactWord`: (Boolean) Is target in the same word as its prime (e.g., the target TRAP vowel in _liquefaction_ has its prime, a KIT vowel, in the same word)?
* `PrimeTargetPauseBetween`: (Boolean) Is there an intervening pause between target and its prime?
* `PrimeTargetTimeDiff`: Difference in seconds between onset of target and offset of prime
* `PrimeTargetSameWord`: (Boolean) Is target in a different instance of the same word as its prime?
* `In_Mod`: (Boolean) Was this token included in the model reported in the paper?
