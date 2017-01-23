# Phoneme Model

- [Manner of Articulation](#manner-of-articulation)
  - [Air Flow](#air-flow)
  - [Initiator](#initiator)
  - [Target](#target)
  - [Manner](#manner)
- [References](#references)

----------

Evan Kirshenbaum's feature set used in his ASCII transcription of the
International Phonetic Alphabet (IPA)<sup>\[<a href="#ref1">1</a>\],
\[<a href="#ref2">2</a>\]</sup> describes the phonemes in a way consistent with
how the phonemes are organised in the IPA code chart. That is the approach used
in the [Phonemes](phonemes.md) document to describe the phonemes in a phoneme
definition file.

Those phoneme features often represent the action of more than one articulatory
mechanism used to produce speech, or affect the same area. Internally, espeak-ng
makes use of the articulatory model, not the IPA descriptions. This document
describes how the feature-based IPA model is mapped to the articulatory model.

People working on adding new voices or languages do not need to read this
document, but should instead read the [Phonemes](phonemes.md) document. This is
intended for people working on the espeak-ng codebase, or people interested in
how espeak-ng works internally.

__NOTE:__ This model is in the process of being implemented. As such, the
current implementation does not reflect this document.

## Manner of Articulation

The manner of articulation is described in terms of several distinct feature
types. The possible manners of articulation are:

| Manner of Articulation | Feature   | Phoneme Model         |
|------------------------|-----------|-----------------------|
| nasal                  | `nas`     | `pmc egs nsl occ`     |
| plosive (stop)         | `stp`     | `pmc egs orl occ`     |
| affricate              | `afr`     | `pmc egs orl occ frr` |
| fricative              | `frc`     | `pmc egs orl frv`     |
| tap/flap               | `flp`     | `pmc egs orl fla`     |
| trill                  | `trl`     | `pmc egs orl tri`     |
| approximant            | `apr`     | `pmc egs orl app`     |
| click                  | `clk`     | `vlc igs orl`         |
| ejective               | `ejc`     | `vlc igs orl occ`     |
| implosive              | `imp`     | `gtc igs`             |
| vowel                  | `vwl`     | `pmc egs orl vow`     |

For `imp` consonants, they use the features of the base phoneme except for
the `pmc` and `egs` features. Thus, a `nas imp` is a `gtc igs nsl occ`.

The `vwl` phonemes are described using vowel height and backness features,
while consonants (the other manners of articulation) are described using
place of articulation features.

Additionally, the manner of articulation can be refined using the following
features:

| Feature | Name     | Description                                                 |
|---------|----------|-------------------------------------------------------------|
| `lat`   | lateral  | The air flow is directed along the sides of the tongue.     |
| `sib`   | sibilant | The air flow is directed through the teeth with the tongue. |

### Air Flow

| Feature | Name       | Description                                                       |
|---------|------------|-------------------------------------------------------------------|
| `egs`   | egressive  | The air flow is moving outwards from the initiator to the target. |
| `igs`   | ingressive | The air flow is moving inwards from the target to the initiator.  |

### Initiator

| Feature | Name       | Description                                                           |
|---------|------------|-----------------------------------------------------------------------|
| `pmc`   | pulmonic   | The diaphragm and lungs are used to generate the airstream.           |
| `gtc`   | glottalic  | The glottis is used to generate the airstream.                        |
| `vlc`   | velaric    | The velum is closed and the tongue is used to generate the airstream. |
| `pcv`   | percussive | There is no airstream used to produce this sound.                     |

### Target

| Feature | Name       | Description                                     |
|---------|------------|-------------------------------------------------|
| `nsl`   | nasal      | The air flows through the nose.                 |
| `orl`   | oral       | The air flows through the mouth.                |

### Manner

| Feature | Name        | Description                                                                       |
|---------|-------------|-----------------------------------------------------------------------------------|
| `occ`   | occlusive   | The air flow is blocked within the vocal tract.                                   |
| `frv`   | fricative   | The air flow is constricted, causing turbulence.                                  |
| `fla`   | flap        | A single tap of the tongue against the secondary articulator.                     |
| `tri`   | trill       | A rapid vibration of the primary articulator against the secondary articulator.   |
| `app`   | approximant | The vocal tract is narrowed at the place of articulation without being turbulant. |
| `vow`   | vowel       | The phoneme is articulated as a vowel instead of a consonant.                     |

## References

1. <a name="ref1"></a> Kirshenbaum, Evan,
   [Representing IPA phonetics in ASCII](http://www.kirshenbaum.net/IPA/faq.html) (HTML). 1993.

2. <a name="ref2"></a> Kirshenbaum, Evan,
   [Representing IPA phonetics in ASCII](http://www.kirshenbaum.net/IPA/ascii-ipa.pdf) (PDF). 2001.

3. <a name="ref3"></a> International Phonetic Association,
   [The International Phonetic Alphabet and the IPA Chart](https://www.internationalphoneticassociation.org/content/ipa-chart). 2015.
   Creative Commons Attribution-Sharealike 3.0 Unported License (CC-BY-SA).

4. <a name="ref4"></a> Wikipedia.
   [International Phonetic Alphabet](https://en.wikipedia.org/wiki/International_Phonetic_Alphabet). 2017.
   Creative Commons Attribution-Sharealike 3.0 Unported License (CC-BY-SA).

5. <a name="ref7"></a> Wikipedia.
   [Extensions to the International Phonetic Alphabet](https://en.wikipedia.org/wiki/Extensions_to_the_International_Phonetic_Alphabet). 2017,
   Creative Commons Attribution-Sharealike 3.0 Unported License (CC-BY-SA).