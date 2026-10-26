# Your 1952 Champion Owner's Guide: DITA 2.0 sample (complete)

Source: Project Gutenberg eBook 62925 (public domain). Converted as a test and training sample for DITA 2.0.
Processor: DITA-OT 4.4.1 (DITA 2.0 preview support).

## Contents
- `champion.ditamap`: full DITA 2.0 bookmap, all topicrefs by @keyref except the three children of the chunk="combine" branch (build this map directly)
- `champion-build.ditamap`: generated copy listing only the topics that exist
- `keystore.ditamap` / `keystore-build.ditamap`: keydefs for topics and for names (company-name, company-name-short, product-name, product-name-full, top-motor-breaker), referenced from the bookmap via mapresources
- `topics/`: all 84 topic files (79 from the original plus multimedia-demo, interior-and-body-fittings, driving-through-the-seasons, markdown-showcase and before-a-long-trip (Markdown)) (topic, concept, reference, task, troubleshooting)
- `topics/glossary/`: 31 glossentry files (DITA 2.0 techcomm), listed in the bookmap glossarylist and keyed in the keystore
- `multimedia/`: awooga-car-horn.mp3 and .ogg, studebaker-awooga.mp4 and .webm, a poster jpg and a captions .vtt, used by topics/multimedia-demo.dita
- `includes/`: text files pulled in with the 2.0 include element (wiring-diagram-desc.txt; the captions file in multimedia/ is also included)
- `seasons-scheme.ditamap`: DITA 2.0 subject scheme for @otherprops (fall, spring)
- `cascade-demo.ditamap`: small test map for cascading @otherprops
- `images/`, `ditaval/` (fall and spring filters), `topic-list.md` (approved topic list)
- `out/`: html5 and pdf output, plus fall, spring and no-seasons variants of the html5 output (and a no-seasons PDF)

## DITA 2.0 comments
Every topic, glossary entry, map, keystore and DITAVAL file has a comment headed "DITA 2.0 FEATURES IN THIS FILE" after the DOCTYPE, listing the 2.0-specific features it uses. The comments in the generated maps come from genmap.py; the ones in the topics were added by annotating the finished files.

## Multimedia and chunking (added)
- `topics/multimedia-demo.dita` shows `audio` and `video` with a primary file (mp3, mp4) and a backup `media-source` (ogg, webm), `video-poster` and `fallback`. Formats are given as MIME types because html5 copies @format into the HTML `type` attribute.
- `champion.ditamap` has `chunk="combine"` on the interior-and-body-fittings topicref: the parent topic and its three children render as one page (out/html5/topics/interior-and-body-fittings.html). The children use @href, not keys, because DITA-OT 4.4.1 loses keydefs and link targets for chunked topics.
- DITA-OT 4.4.1 limits are listed at the end of topic-list.md.
- hwcontrol: control names (clutch pedal, gearshift lever and so on) are marked up with the 2.0 hardware domain element, keyed through keystore.ditamap.
- partno: the part numbers in technical-reference-data are keys (part-*) in keystore.ditamap, each with a comment describing its use.
- titlehint and titlealt: alternative titles in the prologs of 22 topics (symptom hints on the troubleshooting topics, custom title-roles modern-term and british). Not rendered by DITA-OT 4.4.1.
- linktitle on 12 topics (not used by DITA-OT 4.4.1), and an external xref to Project Gutenberg through the key source-gutenberg (foreword, About this edition).
- subtitle on all 12 chapters (generated from genmap.py SUBTITLES; not output by DITA-OT 4.4.1), and include in wiring-diagram.dita (parse="text", text kept in includes/).
- chunk="split" (driving-through-the-seasons, four html5 pages), include line ranges (multimedia-demo), resourceid with @appid-role on the troubleshooting topics, and @add-outputclass in the two DITAVAL files.
- keyscope (fall, spring) in keystore.ditamap, conref ranges in driving-through-the-seasons, a subject scheme with ditaval/no-seasons.ditaval, a cascade test map, Markdown (before-a-long-trip.md plus include in markdown-showcase). The learning domain is not used.
- Lubrication chart check marks are the inline image images/checkmark.png (a text check mark does not print in the PDF font). The only hwcontrol key is hw-ignition-switch.
