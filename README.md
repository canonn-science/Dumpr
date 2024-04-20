# Dumpr
Python Script for dumping database tables out to google cloud storage from the database

# About 
Dumpr is used to generate csv extracts of codex data to google cloud storage. These extracts will be used by the Canonn 3D maps to display locations of the various biological, geological and interstellar phenomena around the galaxy.

They may also be used by third party developers in their own tools. 

The dumpr will be updated daily.

The storage bucket is cors enabled so the files can be accessed directly from another website.

# Prerequisites

A mysql database containing the source data
A google storage bucket and associated secrets for access.
Optional: A webhook for discord updates

# usage

```dumpr [-c codex_keywords] [-d database_secrets] [-s storage_secrets] [-w discord_secrets] [-h --hyperdictions]```

if called with no parameters dumpr will extract and upload all of the dumps

-c You can supply a keyword that will be used to identify which entryids to extract e.g. "Yellow" Would extract all entries with Yellow in the name.

-d database_secrets is a file containing details of the database connection. If not supplied it will look in the local directory for a file called [database_secrets.json](database_secrets.md)

-s drive_secrets is a file containing details of the google storage connection. If not supplied it will look in the local directory for a file called [storage_secrets.json](storage_secrets.md)

-w discord_secrets is a file containing details of the discord webhooks to send update information. If not supplied it will look in the local directory for a file called [discord_secrets.json](discord_secrets.md)

-hd if present will only dump the hyperdiction data 

# The dump contents

## Codex Items

| Column Name | Description |
| ------------------ |-----------------------------------------------------------------------|
| System Name | This is the system name |
| X | The galactic X coordinate |
| Y | Like X but Y |
| Z | You get the picture |
| entryid | This is the unique identifier for the codex item |

We do not supply the names of the items in the files. You are expected to look them up in a reference table. You can find the reference data [here](https://us-central1-canonn-api-236217.cloudfunctions.net/query/codex/ref)

## Hyperdictions

The dump replaces the get_hd_data cloud function for improved performance

| Column Name | Description |
| ------------------ |-----------------------------------------------------------------------|
| System Name | This is the system name |
| Year | The years the hyperdiction took place |
| X | The galactic X coordinate |
| Y | Like X but Y |
| Z | You get the picture |

# The dumps

## Hyperdictions

Can be downloaded from [hyperdictions.csv](https://storage.googleapis.com/canonn-downloads/dumpr/hyperdictions.csv)

## Codex Items

The filenames are base on the entryid from the journal CodexEntry event. The table below is based on what was available at time of writing. For up to date locations you should use the [codex/ref api](https://us-central1-canonn-api-236217.cloudfunctions.net/query/codex/ref) See the [documentation](https://github.com/canonn-science/Canonn-GCloud/tree/main/query#codexref)

| Category | Item  | Download |
| ------------- | ---------------- | --------------- | 
| Anomaly | E01-Type Anomaly | [2401013.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401013.csv) |
| Anomaly | E02-Type Anomaly | [2401014.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401014.csv) |
| Anomaly | E03-Type Anomaly | [2401015.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401015.csv) |
| Anomaly | E04-Type Anomaly | [2401007.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401007.csv) |
| Anomaly | K01-Type Anomaly | [2401001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401001.csv) |
| Anomaly | K02-Type Anomaly | [2401002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401002.csv) |
| Anomaly | K03-Type Anomaly | [2401003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401003.csv) |
| Anomaly | K04-Type Anomaly | [2401004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401004.csv) |
| Anomaly | K05-Type Anomaly | [2401005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401005.csv) |
| Anomaly | K06-Type Anomaly | [2401006.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401006.csv) |
| Anomaly | K07-Type Anomaly | [2401008.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401008.csv) |
| Anomaly | K08-Type Anomaly | [2401009.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401009.csv) |
| Anomaly | K09-Type Anomaly | [2401010.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401010.csv) |
| Anomaly | K10-Type Anomaly | [2401011.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401011.csv) |
| Anomaly | K11-Type Anomaly | [2401012.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401012.csv) |
| Anomaly | K12-Type Anomaly | [2401016.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401016.csv) |
| Anomaly | K13-Type Anomaly | [2401017.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2401017.csv) |
| Anomaly | L01-Type Anomaly | [2402003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402003.csv) |
| Anomaly | L03-Type Anomaly | [2402007.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402007.csv) |
| Anomaly | L04-Type Anomaly | [2402008.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402008.csv) |
| Anomaly | L05-Type Anomaly | [24020009.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/24020009.csv) |
| Anomaly | L06-Type Anomaly | [24020010.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/24020010.csv) |
| Anomaly | L07-Type Anomaly | [2402011.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402011.csv) |
| Anomaly | L08-Type Anomaly | [2402012.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402012.csv) |
| Anomaly | L09-Type Anomaly | [24020013.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/24020013.csv) |
| Anomaly | P01-Type Anomaly | [2403002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403002.csv) |
| Anomaly | P02-Type Anomaly | [2403003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403003.csv) |
| Anomaly | P03-Type Anomaly | [2403004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403004.csv) |
| Anomaly | P04-Type Anomaly | [2403005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403005.csv) |
| Anomaly | P05-Type Anomaly | [2403006.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403006.csv) |
| Anomaly | P06-Type Anomaly | [2403007.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403007.csv) |
| Anomaly | P07-Type Anomaly | [2403008.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403008.csv) |
| Anomaly | P08-Type Anomaly | [2403009.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403009.csv) |
| Anomaly | P09-Type Anomaly | [2403010.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403010.csv) |
| Anomaly | P10-Type Anomaly | [2403011.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403011.csv) |
| Anomaly | P11-Type Anomaly | [2403012.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403012.csv) |
| Anomaly | P12-Type Anomaly | [2403013.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403013.csv) |
| Anomaly | P13-Type Anomaly | [2403014.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403014.csv) |
| Anomaly | P14-Type Anomaly | [2403015.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403015.csv) |
| Anomaly | P15-Type Anomaly | [2403016.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2403016.csv) |
| Anomaly | Q01-Type Anomaly | [2406001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406001.csv) |
| Anomaly | Q02-Type Anomaly | [2406002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406002.csv) |
| Anomaly | Q03-Type Anomaly | [2406003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406003.csv) |
| Anomaly | Q04-Type Anomaly | [2406004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406004.csv) |
| Anomaly | Q05-Type Anomaly | [2406005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406005.csv) |
| Anomaly | Q06-Type Anomaly | [2406006.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406006.csv) |
| Anomaly | Q07-Type Anomaly | [2406007.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406007.csv) |
| Anomaly | Q08-Type Anomaly | [2406008.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406008.csv) |
| Anomaly | Q09-Type Anomaly | [2406009.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2406009.csv) |
| Anomaly | T01-Type Anomaly | [2402001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402001.csv) |
| Anomaly | T02-Type Anomaly | [2402002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402002.csv) |
| Anomaly | T03-Type Anomaly | [2402004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402004.csv) |
| Anomaly | T04-Type Anomaly | [2402005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Anomaly/2402005.csv) |
| Biology | Amphora Plant | [2101400.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2101400.csv) |
| Biology | Blatteum Bioluminescent Anemone | [2100405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100405.csv) |
| Biology | Croceum Anemone | [2100402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100402.csv) |
| Biology | Luteolum Anemone | [2100401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100401.csv) |
| Biology | Prasinum Bioluminescent Anemone | [2100407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100407.csv) |
| Biology | Puniceum Anemone | [2100403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100403.csv) |
| Biology | Roseum Anemone | [2100404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100404.csv) |
| Biology | Roseum Bioluminescent Anemone | [2100408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100408.csv) |
| Biology | Rubeum Bioluminescent Anemone | [2100406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100406.csv) |
| Biology | Bark Mounds | [2100301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100301.csv) |
| Biology | Aureum Brain Tree | [2100206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100206.csv) |
| Biology | Gypseeum Brain Tree | [2100202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100202.csv) |
| Biology | Lindigoticum Brain Tree | [2100208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100208.csv) |
| Biology | Lividum Brain Tree | [2100205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100205.csv) |
| Biology | Ostrinum Brain Tree | [2100203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100203.csv) |
| Biology | Puniceum Brain Tree | [2100207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100207.csv) |
| Biology | Roseum Brain Tree | [2100201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100201.csv) |
| Biology | Viride Brain Tree | [2100204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100204.csv) |
| Biology | Crystalline Shards | [2101500.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2101500.csv) |
| Biology | Albidum Sinuous Tubers | [2100503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100503.csv) |
| Biology | Blatteum Sinuous Tubers | [2100505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100505.csv) |
| Biology | Caeruleum Sinuous Tubers | [2100504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100504.csv) |
| Biology | Lindigoticum Sinuous Tubers | [2100506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100506.csv) |
| Biology | Prasinum Sinuous Tubers | [2100502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100502.csv) |
| Biology | Roseum Sinuous Tubers | [2100501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100501.csv) |
| Biology | Violaceum Sinuous Tubers | [2100507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100507.csv) |
| Biology | Viride Sinuous Tubers | [2100508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2100508.csv) |
| Biology | Aleoida Arcus - Amethyst | [2310110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310110.csv) |
| Biology | Aleoida Arcus - Emerald | [2310105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310105.csv) |
| Biology | Aleoida Arcus - Green | [2310102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310102.csv) |
| Biology | Aleoida Arcus - Grey | [2310111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310111.csv) |
| Biology | Aleoida Arcus - Indigo | [2310112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310112.csv) |
| Biology | Aleoida Arcus - Lime | [2310106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310106.csv) |
| Biology | Aleoida Arcus - Mauve | [2310108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310108.csv) |
| Biology | Aleoida Arcus - Ocher | [2310113.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310113.csv) |
| Biology | Aleoida Arcus - Sage | [2310107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310107.csv) |
| Biology | Aleoida Arcus - Teal | [2310103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310103.csv) |
| Biology | Aleoida Arcus - Turquoise | [2310104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310104.csv) |
| Biology | Aleoida Arcus - Yellow | [2310101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310101.csv) |
| Biology | Aleoida Coronamus - Amethyst | [2310210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310210.csv) |
| Biology | Aleoida Coronamus - Emerald | [2310205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310205.csv) |
| Biology | Aleoida Coronamus - Green | [2310202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310202.csv) |
| Biology | Aleoida Coronamus - Indigo | [2310212.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310212.csv) |
| Biology | Aleoida Coronamus - Lime | [2310206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310206.csv) |
| Biology | Aleoida Coronamus - Mauve | [2310208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310208.csv) |
| Biology | Aleoida Coronamus - Ocher | [2310213.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310213.csv) |
| Biology | Aleoida Coronamus - Sage | [2310207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310207.csv) |
| Biology | Aleoida Coronamus - Teal | [2310203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310203.csv) |
| Biology | Aleoida Coronamus - Turquoise | [2310204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310204.csv) |
| Biology | Aleoida Coronamus - Yellow | [2310201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310201.csv) |
| Biology | Aleoida Gravis - Amethyst | [2310510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310510.csv) |
| Biology | Aleoida Gravis - Emerald | [2310505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310505.csv) |
| Biology | Aleoida Gravis - Green | [2310502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310502.csv) |
| Biology | Aleoida Gravis - Lime | [2310506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310506.csv) |
| Biology | Aleoida Gravis - Mauve | [2310508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310508.csv) |
| Biology | Aleoida Gravis - Ocher | [2310513.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310513.csv) |
| Biology | Aleoida Gravis - Sage | [2310507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310507.csv) |
| Biology | Aleoida Gravis - Teal | [2310503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310503.csv) |
| Biology | Aleoida Gravis - Turquoise | [2310504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310504.csv) |
| Biology | Aleoida Gravis - Yellow | [2310501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310501.csv) |
| Biology | Aleoida Laminiae - Amethyst | [2310410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310410.csv) |
| Biology | Aleoida Laminiae - Emerald | [2310405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310405.csv) |
| Biology | Aleoida Laminiae - Green | [2310402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310402.csv) |
| Biology | Aleoida Laminiae - Grey | [2310411.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310411.csv) |
| Biology | Aleoida Laminiae - Indigo | [2310412.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310412.csv) |
| Biology | Aleoida Laminiae - Lime | [2310406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310406.csv) |
| Biology | Aleoida Laminiae - Mauve | [2310408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310408.csv) |
| Biology | Aleoida Laminiae - Ocher | [2310413.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310413.csv) |
| Biology | Aleoida Laminiae - Sage | [2310407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310407.csv) |
| Biology | Aleoida Laminiae - Teal | [2310403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310403.csv) |
| Biology | Aleoida Laminiae - Turquoise | [2310404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310404.csv) |
| Biology | Aleoida Laminiae - Yellow | [2310401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310401.csv) |
| Biology | Aleoida Spica - Emerald | [2310305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310305.csv) |
| Biology | Aleoida Spica - Green | [2310302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310302.csv) |
| Biology | Aleoida Spica - Indigo | [2310312.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310312.csv) |
| Biology | Aleoida Spica - Lime | [2310306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310306.csv) |
| Biology | Aleoida Spica - Mauve | [2310308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310308.csv) |
| Biology | Aleoida Spica - Ocher | [2310313.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310313.csv) |
| Biology | Aleoida Spica - Sage | [2310307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310307.csv) |
| Biology | Aleoida Spica - Teal | [2310303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310303.csv) |
| Biology | Aleoida Spica - Turquoise | [2310304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310304.csv) |
| Biology | Aleoida Spica - Yellow | [2310301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2310301.csv) |
| Biology | Bacterium Acies - Aquamarine | [2320406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320406.csv) |
| Biology | Bacterium Acies - Cobalt | [2320404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320404.csv) |
| Biology | Bacterium Acies - Cyan | [2320405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320405.csv) |
| Biology | Bacterium Acies - Lime | [2320401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320401.csv) |
| Biology | Bacterium Acies - Magenta | [2320403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320403.csv) |
| Biology | Bacterium Acies - White | [2320402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320402.csv) |
| Biology | Bacterium Alcyoneum - Amethyst | [2320613.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320613.csv) |
| Biology | Bacterium Alcyoneum - Emerald | [2320605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320605.csv) |
| Biology | Bacterium Alcyoneum - Green | [2320606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320606.csv) |
| Biology | Bacterium Alcyoneum - Grey | [2320602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320602.csv) |
| Biology | Bacterium Alcyoneum - Indigo | [2320615.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320615.csv) |
| Biology | Bacterium Alcyoneum - Lime | [2320604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320604.csv) |
| Biology | Bacterium Alcyoneum - Maroon | [2320610.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320610.csv) |
| Biology | Bacterium Alcyoneum - Mauve | [2320612.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320612.csv) |
| Biology | Bacterium Alcyoneum - Ocher | [2320614.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320614.csv) |
| Biology | Bacterium Alcyoneum - Red | [2320609.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320609.csv) |
| Biology | Bacterium Alcyoneum - Sage | [2320608.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320608.csv) |
| Biology | Bacterium Alcyoneum - Teal | [2320607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320607.csv) |
| Biology | Bacterium Alcyoneum - Turquoise | [2320601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320601.csv) |
| Biology | Bacterium Alcyoneum - Yellow | [2320603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320603.csv) |
| Biology | Bacterium Aurasus - Amethyst | [2320113.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320113.csv) |
| Biology | Bacterium Aurasus - Emerald | [2320105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320105.csv) |
| Biology | Bacterium Aurasus - Green | [2320106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320106.csv) |
| Biology | Bacterium Aurasus - Grey | [2320102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320102.csv) |
| Biology | Bacterium Aurasus - Indigo | [2320115.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320115.csv) |
| Biology | Bacterium Aurasus - Lime | [2320104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320104.csv) |
| Biology | Bacterium Aurasus - Maroon | [2320110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320110.csv) |
| Biology | Bacterium Aurasus - Mauve | [2320112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320112.csv) |
| Biology | Bacterium Aurasus - Ocher | [2320114.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320114.csv) |
| Biology | Bacterium Aurasus - Orange | [2320111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320111.csv) |
| Biology | Bacterium Aurasus - Red | [2320109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320109.csv) |
| Biology | Bacterium Aurasus - Sage | [2320108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320108.csv) |
| Biology | Bacterium Aurasus - Teal | [2320107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320107.csv) |
| Biology | Bacterium Aurasus - Turquoise | [2320101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320101.csv) |
| Biology | Bacterium Aurasus - Yellow | [2320103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320103.csv) |
| Biology | Bacterium Bullaris - Aquamarine | [2321004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321004.csv) |
| Biology | Bacterium Bullaris - Cobalt | [2321005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321005.csv) |
| Biology | Bacterium Bullaris - Gold | [2321001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321001.csv) |
| Biology | Bacterium Bullaris - Lime | [2321002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321002.csv) |
| Biology | Bacterium Bullaris - Red | [2321006.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321006.csv) |
| Biology | Bacterium Bullaris - Yellow | [2321003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321003.csv) |
| Biology | Bacterium Cerbrus - Amethyst | [2321213.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321213.csv) |
| Biology | Bacterium Cerbrus - Emerald | [2321205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321205.csv) |
| Biology | Bacterium Cerbrus - Green | [2321206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321206.csv) |
| Biology | Bacterium Cerbrus - Grey | [2321202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321202.csv) |
| Biology | Bacterium Cerbrus - Indigo | [2321215.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321215.csv) |
| Biology | Bacterium Cerbrus - Lime | [2321204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321204.csv) |
| Biology | Bacterium Cerbrus - Maroon | [2321210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321210.csv) |
| Biology | Bacterium Cerbrus - Mauve | [2321212.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321212.csv) |
| Biology | Bacterium Cerbrus - Ocher | [2321214.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321214.csv) |
| Biology | Bacterium Cerbrus - Orange | [2321211.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321211.csv) |
| Biology | Bacterium Cerbrus - Red | [2321209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321209.csv) |
| Biology | Bacterium Cerbrus - Sage | [2321208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321208.csv) |
| Biology | Bacterium Cerbrus - Teal | [2321207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321207.csv) |
| Biology | Bacterium Cerbrus - Turquoise | [2321201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321201.csv) |
| Biology | Bacterium Cerbrus - Yellow | [2321203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321203.csv) |
| Biology | Bacterium Informem - Aquamarine | [2320801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320801.csv) |
| Biology | Bacterium Informem - Cobalt | [2320806.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320806.csv) |
| Biology | Bacterium Informem - Gold | [2320804.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320804.csv) |
| Biology | Bacterium Informem - Lime | [2320803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320803.csv) |
| Biology | Bacterium Informem - Red | [2320805.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320805.csv) |
| Biology | Bacterium Informem - Yellow | [2320802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320802.csv) |
| Biology | Bacterium Nebulus - Cobalt | [2320206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320206.csv) |
| Biology | Bacterium Nebulus - Cyan | [2320201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320201.csv) |
| Biology | Bacterium Nebulus - Gold | [2320203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320203.csv) |
| Biology | Bacterium Nebulus - Green | [2320202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320202.csv) |
| Biology | Bacterium Nebulus - Magenta | [2320205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320205.csv) |
| Biology | Bacterium Nebulus - Orange | [2320204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320204.csv) |
| Biology | Bacterium Omentum - Aquamarine | [2321105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321105.csv) |
| Biology | Bacterium Omentum - Blue | [2321104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321104.csv) |
| Biology | Bacterium Omentum - Lime | [2321106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321106.csv) |
| Biology | Bacterium Omentum - Peach | [2321102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321102.csv) |
| Biology | Bacterium Omentum - Red | [2321103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321103.csv) |
| Biology | Bacterium Omentum - White | [2321101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321101.csv) |
| Biology | Bacterium Scopulum - Aquamarine | [2320304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320304.csv) |
| Biology | Bacterium Scopulum - Lime | [2320305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320305.csv) |
| Biology | Bacterium Scopulum - Mulberry | [2320303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320303.csv) |
| Biology | Bacterium Scopulum - Peach | [2320301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320301.csv) |
| Biology | Bacterium Scopulum - Red | [2320302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320302.csv) |
| Biology | Bacterium Scopulum - White | [2320306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320306.csv) |
| Biology | Bacterium Tela - Cobalt | [2320703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320703.csv) |
| Biology | Bacterium Tela - Gold | [2320706.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320706.csv) |
| Biology | Bacterium Tela - Green | [2320704.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320704.csv) |
| Biology | Bacterium Tela - Magenta | [2320702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320702.csv) |
| Biology | Bacterium Tela - Orange | [2320701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320701.csv) |
| Biology | Bacterium Tela - Yellow | [2320705.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320705.csv) |
| Biology | Bacterium Verrata - Blue | [2321303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321303.csv) |
| Biology | Bacterium Verrata - Lime | [2321304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321304.csv) |
| Biology | Bacterium Verrata - Mulberry | [2321302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321302.csv) |
| Biology | Bacterium Verrata - Peach | [2321306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321306.csv) |
| Biology | Bacterium Verrata - Red | [2321301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321301.csv) |
| Biology | Bacterium Verrata - White | [2321305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2321305.csv) |
| Biology | Bacterium Vesicula - Cyan | [2320505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320505.csv) |
| Biology | Bacterium Vesicula - Gold | [2320501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320501.csv) |
| Biology | Bacterium Vesicula - Lime | [2320506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320506.csv) |
| Biology | Bacterium Vesicula - Mulberry | [2320504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320504.csv) |
| Biology | Bacterium Vesicula - Orange | [2320503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320503.csv) |
| Biology | Bacterium Vesicula - Red | [2320502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320502.csv) |
| Biology | Bacterium Volu - Aquamarine | [2320903.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320903.csv) |
| Biology | Bacterium Volu - Cobalt | [2320904.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320904.csv) |
| Biology | Bacterium Volu - Cyan | [2320902.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320902.csv) |
| Biology | Bacterium Volu - Gold | [2320906.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320906.csv) |
| Biology | Bacterium Volu - Lime | [2320901.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320901.csv) |
| Biology | Bacterium Volu - Red | [2320905.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2320905.csv) |
| Biology | Cactoida Cortexum - Amethyst | [2330107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330107.csv) |
| Biology | Cactoida Cortexum - Green | [2330103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330103.csv) |
| Biology | Cactoida Cortexum - Mauve | [2330108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330108.csv) |
| Biology | Cactoida Cortexum - Ocher | [2330112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330112.csv) |
| Biology | Cactoida Cortexum - Orange | [2330109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330109.csv) |
| Biology | Cactoida Cortexum - Red | [2330110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330110.csv) |
| Biology | Cactoida Cortexum - Sage | [2330115.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330115.csv) |
| Biology | Cactoida Cortexum - Teal | [2330105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330105.csv) |
| Biology | Cactoida Cortexum - Turquoise | [2330114.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330114.csv) |
| Biology | Cactoida Cortexum - Yellow | [2330104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330104.csv) |
| Biology | Cactoida Lapis - Amethyst | [2330207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330207.csv) |
| Biology | Cactoida Lapis - Green | [2330203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330203.csv) |
| Biology | Cactoida Lapis - Grey | [2330201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330201.csv) |
| Biology | Cactoida Lapis - Indigo | [2330213.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330213.csv) |
| Biology | Cactoida Lapis - Mauve | [2330208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330208.csv) |
| Biology | Cactoida Lapis - Ocher | [2330212.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330212.csv) |
| Biology | Cactoida Lapis - Orange | [2330209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330209.csv) |
| Biology | Cactoida Lapis - Red | [2330210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330210.csv) |
| Biology | Cactoida Lapis - Sage | [2330215.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330215.csv) |
| Biology | Cactoida Lapis - Teal | [2330205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330205.csv) |
| Biology | Cactoida Lapis - Turquoise | [2330214.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330214.csv) |
| Biology | Cactoida Lapis - Yellow | [2330204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330204.csv) |
| Biology | Cactoida Peperatis - Amethyst | [2330507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330507.csv) |
| Biology | Cactoida Peperatis - Green | [2330503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330503.csv) |
| Biology | Cactoida Peperatis - Mauve | [2330508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330508.csv) |
| Biology | Cactoida Peperatis - Ocher | [2330512.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330512.csv) |
| Biology | Cactoida Peperatis - Orange | [2330509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330509.csv) |
| Biology | Cactoida Peperatis - Red | [2330510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330510.csv) |
| Biology | Cactoida Peperatis - Sage | [2330515.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330515.csv) |
| Biology | Cactoida Peperatis - Teal | [2330505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330505.csv) |
| Biology | Cactoida Peperatis - Turquoise | [2330514.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330514.csv) |
| Biology | Cactoida Peperatis - Yellow | [2330504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330504.csv) |
| Biology | Cactoida Pullulanta - Amethyst | [2330407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330407.csv) |
| Biology | Cactoida Pullulanta - Green | [2330403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330403.csv) |
| Biology | Cactoida Pullulanta - Mauve | [2330408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330408.csv) |
| Biology | Cactoida Pullulanta - Orange | [2330409.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330409.csv) |
| Biology | Cactoida Pullulanta - Red | [2330410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330410.csv) |
| Biology | Cactoida Pullulanta - Sage | [2330415.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330415.csv) |
| Biology | Cactoida Pullulanta - Teal | [2330405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330405.csv) |
| Biology | Cactoida Pullulanta - Turquoise | [2330414.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330414.csv) |
| Biology | Cactoida Pullulanta - Yellow | [2330404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330404.csv) |
| Biology | Cactoida Vermis - Amethyst | [2330307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330307.csv) |
| Biology | Cactoida Vermis - Green | [2330303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330303.csv) |
| Biology | Cactoida Vermis - Mauve | [2330308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330308.csv) |
| Biology | Cactoida Vermis - Ocher | [2330312.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330312.csv) |
| Biology | Cactoida Vermis - Orange | [2330309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330309.csv) |
| Biology | Cactoida Vermis - Red | [2330310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330310.csv) |
| Biology | Cactoida Vermis - Sage | [2330315.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330315.csv) |
| Biology | Cactoida Vermis - Teal | [2330305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330305.csv) |
| Biology | Cactoida Vermis - Yellow | [2330304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2330304.csv) |
| Biology | Clypeus Lacrimam - Amethyst | [2340105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340105.csv) |
| Biology | Clypeus Lacrimam - Green | [2340110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340110.csv) |
| Biology | Clypeus Lacrimam - Grey | [2340106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340106.csv) |
| Biology | Clypeus Lacrimam - Lime | [2340112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340112.csv) |
| Biology | Clypeus Lacrimam - Maroon | [2340102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340102.csv) |
| Biology | Clypeus Lacrimam - Mauve | [2340104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340104.csv) |
| Biology | Clypeus Lacrimam - Orange | [2340103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340103.csv) |
| Biology | Clypeus Lacrimam - Teal | [2340108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340108.csv) |
| Biology | Clypeus Lacrimam - Turquoise | [2340107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340107.csv) |
| Biology | Clypeus Lacrimam - Yellow | [2340113.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340113.csv) |
| Biology | Clypeus Margaritus - Amethyst | [2340205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340205.csv) |
| Biology | Clypeus Margaritus - Green | [2340210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340210.csv) |
| Biology | Clypeus Margaritus - Grey | [2340206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340206.csv) |
| Biology | Clypeus Margaritus - Maroon | [2340202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340202.csv) |
| Biology | Clypeus Margaritus - Mauve | [2340204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340204.csv) |
| Biology | Clypeus Margaritus - Orange | [2340203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340203.csv) |
| Biology | Clypeus Margaritus - Teal | [2340208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340208.csv) |
| Biology | Clypeus Margaritus - Turquoise | [2340207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340207.csv) |
| Biology | Clypeus Margaritus - Yellow | [2340213.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340213.csv) |
| Biology | Clypeus Speculumi - Amethyst | [2340305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340305.csv) |
| Biology | Clypeus Speculumi - Grey | [2340306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340306.csv) |
| Biology | Clypeus Speculumi - Maroon | [2340302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340302.csv) |
| Biology | Clypeus Speculumi - Mauve | [2340304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340304.csv) |
| Biology | Clypeus Speculumi - Orange | [2340303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340303.csv) |
| Biology | Clypeus Speculumi - Turquoise | [2340307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340307.csv) |
| Biology | Clypeus Speculumi - Yellow | [2340313.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2340313.csv) |
| Biology | Concha Aureolas - Emerald | [2350210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350210.csv) |
| Biology | Concha Aureolas - Green | [2350209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350209.csv) |
| Biology | Concha Aureolas - Grey | [2350203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350203.csv) |
| Biology | Concha Aureolas - Indigo | [2350201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350201.csv) |
| Biology | Concha Aureolas - Orange | [2350206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350206.csv) |
| Biology | Concha Aureolas - Red | [2350205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350205.csv) |
| Biology | Concha Aureolas - Teal | [2350202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350202.csv) |
| Biology | Concha Aureolas - Turquoise | [2350204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350204.csv) |
| Biology | Concha Aureolas - Yellow | [2350207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350207.csv) |
| Biology | Concha Biconcavis - Gold | [2350406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350406.csv) |
| Biology | Concha Biconcavis - Orange | [2350404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350404.csv) |
| Biology | Concha Biconcavis - Peach | [2350405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350405.csv) |
| Biology | Concha Biconcavis - Red | [2350403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350403.csv) |
| Biology | Concha Biconcavis - White | [2350401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350401.csv) |
| Biology | Concha Biconcavis - Yellow | [2350402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350402.csv) |
| Biology | Concha Labiata - Emerald | [2350310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350310.csv) |
| Biology | Concha Labiata - Green | [2350309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350309.csv) |
| Biology | Concha Labiata - Grey | [2350303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350303.csv) |
| Biology | Concha Labiata - Indigo | [2350301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350301.csv) |
| Biology | Concha Labiata - Lime | [2350308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350308.csv) |
| Biology | Concha Labiata - Orange | [2350306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350306.csv) |
| Biology | Concha Labiata - Red | [2350305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350305.csv) |
| Biology | Concha Labiata - Teal | [2350302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350302.csv) |
| Biology | Concha Labiata - Turquoise | [2350304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350304.csv) |
| Biology | Concha Labiata - Yellow | [2350307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350307.csv) |
| Biology | Concha Renibus - Aquamarine | [2350103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350103.csv) |
| Biology | Concha Renibus - Blue | [2350102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350102.csv) |
| Biology | Concha Renibus - Mulberry | [2350101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350101.csv) |
| Biology | Concha Renibus - Peach | [2350105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350105.csv) |
| Biology | Concha Renibus - Red | [2350106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350106.csv) |
| Biology | Concha Renibus - White | [2350104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2350104.csv) |
| Biology | Electricae Pluma - Blue | [2360104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360104.csv) |
| Biology | Electricae Pluma - Cobalt | [2360105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360105.csv) |
| Biology | Electricae Pluma - Cyan | [2360103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360103.csv) |
| Biology | Electricae Pluma - Magenta | [2360101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360101.csv) |
| Biology | Electricae Pluma - Mulberry | [2360106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360106.csv) |
| Biology | Electricae Pluma - Red | [2360102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360102.csv) |
| Biology | Electricae Radialem - Aquamarine | [2360201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360201.csv) |
| Biology | Electricae Radialem - Blue | [2360204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360204.csv) |
| Biology | Electricae Radialem - Cobalt | [2360203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360203.csv) |
| Biology | Electricae Radialem - Cyan | [2360205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360205.csv) |
| Biology | Electricae Radialem - Green | [2360206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360206.csv) |
| Biology | Electricae Radialem - Magenta | [2360202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2360202.csv) |
| Biology | Fonticulua Campestris - Amethyst | [2370207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370207.csv) |
| Biology | Fonticulua Campestris - Emerald | [2370206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370206.csv) |
| Biology | Fonticulua Campestris - Green | [2370203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370203.csv) |
| Biology | Fonticulua Campestris - Grey | [2370201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370201.csv) |
| Biology | Fonticulua Campestris - Lime | [2370202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370202.csv) |
| Biology | Fonticulua Campestris - Maroon | [2370211.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370211.csv) |
| Biology | Fonticulua Campestris - Mauve | [2370208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370208.csv) |
| Biology | Fonticulua Campestris - Ocher | [2370212.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370212.csv) |
| Biology | Fonticulua Campestris - Orange | [2370209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370209.csv) |
| Biology | Fonticulua Campestris - Red | [2370210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370210.csv) |
| Biology | Fonticulua Campestris - Sage | [2370215.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370215.csv) |
| Biology | Fonticulua Campestris - Teal | [2370205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370205.csv) |
| Biology | Fonticulua Campestris - Turquoise | [2370214.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370214.csv) |
| Biology | Fonticulua Campestris - Yellow | [2370204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370204.csv) |
| Biology | Fonticulua Digitos - Amethyst | [2370607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370607.csv) |
| Biology | Fonticulua Digitos - Emerald | [2370606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370606.csv) |
| Biology | Fonticulua Digitos - Green | [2370603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370603.csv) |
| Biology | Fonticulua Digitos - Lime | [2370602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370602.csv) |
| Biology | Fonticulua Digitos - Mauve | [2370608.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370608.csv) |
| Biology | Fonticulua Digitos - Ocher | [2370612.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370612.csv) |
| Biology | Fonticulua Digitos - Orange | [2370609.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370609.csv) |
| Biology | Fonticulua Digitos - Red | [2370610.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370610.csv) |
| Biology | Fonticulua Digitos - Sage | [2370615.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370615.csv) |
| Biology | Fonticulua Digitos - Teal | [2370605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370605.csv) |
| Biology | Fonticulua Digitos - Turquoise | [2370614.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370614.csv) |
| Biology | Fonticulua Digitos - Yellow | [2370604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370604.csv) |
| Biology | Fonticulua Fluctus - Amethyst | [2370507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370507.csv) |
| Biology | Fonticulua Fluctus - Emerald | [2370506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370506.csv) |
| Biology | Fonticulua Fluctus - Green | [2370503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370503.csv) |
| Biology | Fonticulua Fluctus - Lime | [2370502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370502.csv) |
| Biology | Fonticulua Fluctus - Mauve | [2370508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370508.csv) |
| Biology | Fonticulua Fluctus - Orange | [2370509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370509.csv) |
| Biology | Fonticulua Fluctus - Red | [2370510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370510.csv) |
| Biology | Fonticulua Fluctus - Sage | [2370515.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370515.csv) |
| Biology | Fonticulua Fluctus - Teal | [2370505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370505.csv) |
| Biology | Fonticulua Fluctus - Yellow | [2370504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370504.csv) |
| Biology | Fonticulua Lapida - Amethyst | [2370407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370407.csv) |
| Biology | Fonticulua Lapida - Emerald | [2370406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370406.csv) |
| Biology | Fonticulua Lapida - Green | [2370403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370403.csv) |
| Biology | Fonticulua Lapida - Grey | [2370401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370401.csv) |
| Biology | Fonticulua Lapida - Lime | [2370402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370402.csv) |
| Biology | Fonticulua Lapida - Maroon | [2370411.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370411.csv) |
| Biology | Fonticulua Lapida - Mauve | [2370408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370408.csv) |
| Biology | Fonticulua Lapida - Ocher | [2370412.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370412.csv) |
| Biology | Fonticulua Lapida - Orange | [2370409.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370409.csv) |
| Biology | Fonticulua Lapida - Red | [2370410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370410.csv) |
| Biology | Fonticulua Lapida - Sage | [2370415.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370415.csv) |
| Biology | Fonticulua Lapida - Teal | [2370405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370405.csv) |
| Biology | Fonticulua Lapida - Turquoise | [2370414.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370414.csv) |
| Biology | Fonticulua Lapida - Yellow | [2370404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370404.csv) |
| Biology | Fonticulua Segmentatus - Amethyst | [2370107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370107.csv) |
| Biology | Fonticulua Segmentatus - Emerald | [2370106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370106.csv) |
| Biology | Fonticulua Segmentatus - Green | [2370103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370103.csv) |
| Biology | Fonticulua Segmentatus - Lime | [2370102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370102.csv) |
| Biology | Fonticulua Segmentatus - Maroon | [2370111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370111.csv) |
| Biology | Fonticulua Segmentatus - Mauve | [2370108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370108.csv) |
| Biology | Fonticulua Segmentatus - Ocher | [2370112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370112.csv) |
| Biology | Fonticulua Segmentatus - Orange | [2370109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370109.csv) |
| Biology | Fonticulua Segmentatus - Red | [2370110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370110.csv) |
| Biology | Fonticulua Segmentatus - Sage | [2370115.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370115.csv) |
| Biology | Fonticulua Segmentatus - Teal | [2370105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370105.csv) |
| Biology | Fonticulua Segmentatus - Turquoise | [2370114.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370114.csv) |
| Biology | Fonticulua Segmentatus - Yellow | [2370104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370104.csv) |
| Biology | Fonticulua Upupam - Amethyst | [2370307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370307.csv) |
| Biology | Fonticulua Upupam - Emerald | [2370306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370306.csv) |
| Biology | Fonticulua Upupam - Green | [2370303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370303.csv) |
| Biology | Fonticulua Upupam - Indigo | [2370313.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370313.csv) |
| Biology | Fonticulua Upupam - Lime | [2370302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370302.csv) |
| Biology | Fonticulua Upupam - Maroon | [2370311.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370311.csv) |
| Biology | Fonticulua Upupam - Mauve | [2370308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370308.csv) |
| Biology | Fonticulua Upupam - Ocher | [2370312.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370312.csv) |
| Biology | Fonticulua Upupam - Orange | [2370309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370309.csv) |
| Biology | Fonticulua Upupam - Red | [2370310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370310.csv) |
| Biology | Fonticulua Upupam - Sage | [2370315.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370315.csv) |
| Biology | Fonticulua Upupam - Teal | [2370305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370305.csv) |
| Biology | Fonticulua Upupam - Turquoise | [2370314.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370314.csv) |
| Biology | Fonticulua Upupam - Yellow | [2370304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2370304.csv) |
| Biology | Fumerola Aquatis - Cobalt | [2380404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380404.csv) |
| Biology | Fumerola Aquatis - Cyan | [2380405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380405.csv) |
| Biology | Fumerola Aquatis - Gold | [2380402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380402.csv) |
| Biology | Fumerola Aquatis - Green | [2380406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380406.csv) |
| Biology | Fumerola Aquatis - Orange | [2380403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380403.csv) |
| Biology | Fumerola Aquatis - Yellow | [2380401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380401.csv) |
| Biology | Fumerola Carbosis - Cobalt | [2380102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380102.csv) |
| Biology | Fumerola Carbosis - Cyan | [2380103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380103.csv) |
| Biology | Fumerola Carbosis - Gold | [2380105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380105.csv) |
| Biology | Fumerola Carbosis - Magenta | [2380101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380101.csv) |
| Biology | Fumerola Carbosis - Orange | [2380106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380106.csv) |
| Biology | Fumerola Carbosis - Yellow | [2380104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380104.csv) |
| Biology | Fumerola Extremus - Aquamarine | [2380206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380206.csv) |
| Biology | Fumerola Extremus - Blue | [2380205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380205.csv) |
| Biology | Fumerola Extremus - Lime | [2380201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380201.csv) |
| Biology | Fumerola Extremus - Mulberry | [2380204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380204.csv) |
| Biology | Fumerola Extremus - Peach | [2380203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380203.csv) |
| Biology | Fumerola Extremus - White | [2380202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380202.csv) |
| Biology | Fumerola Nitris - Aquamarine | [2380304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380304.csv) |
| Biology | Fumerola Nitris - Lime | [2380305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380305.csv) |
| Biology | Fumerola Nitris - Mulberry | [2380303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380303.csv) |
| Biology | Fumerola Nitris - Peach | [2380301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380301.csv) |
| Biology | Fumerola Nitris - Red | [2380302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380302.csv) |
| Biology | Fumerola Nitris - White | [2380306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2380306.csv) |
| Biology | Fungoida Bullarum - Gold | [2390302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390302.csv) |
| Biology | Fungoida Bullarum - Magenta | [2390304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390304.csv) |
| Biology | Fungoida Bullarum - Mulberry | [2390303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390303.csv) |
| Biology | Fungoida Bullarum - Orange | [2390306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390306.csv) |
| Biology | Fungoida Bullarum - Peach | [2390301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390301.csv) |
| Biology | Fungoida Bullarum - Red | [2390305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390305.csv) |
| Biology | Fungoida Gelata - Cyan | [2390406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390406.csv) |
| Biology | Fungoida Gelata - Green | [2390402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390402.csv) |
| Biology | Fungoida Gelata - Lime | [2390401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390401.csv) |
| Biology | Fungoida Gelata - Mulberry | [2390405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390405.csv) |
| Biology | Fungoida Gelata - Orange | [2390404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390404.csv) |
| Biology | Fungoida Gelata - Red | [2390403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390403.csv) |
| Biology | Fungoida Setisis - Gold | [2390104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390104.csv) |
| Biology | Fungoida Setisis - Lime | [2390101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390101.csv) |
| Biology | Fungoida Setisis - Orange | [2390106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390106.csv) |
| Biology | Fungoida Setisis - Peach | [2390105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390105.csv) |
| Biology | Fungoida Setisis - White | [2390103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390103.csv) |
| Biology | Fungoida Setisis - Yellow | [2390102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390102.csv) |
| Biology | Fungoida Stabitis - Blue | [2390206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390206.csv) |
| Biology | Fungoida Stabitis - Green | [2390201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390201.csv) |
| Biology | Fungoida Stabitis - Magenta | [2390205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390205.csv) |
| Biology | Fungoida Stabitis - Orange | [2390203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390203.csv) |
| Biology | Fungoida Stabitis - Peach | [2390204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390204.csv) |
| Biology | Fungoida Stabitis - White | [2390202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2390202.csv) |
| Biology | Osseus Cornibus - Emerald | [2400506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400506.csv) |
| Biology | Osseus Cornibus - Green | [2400507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400507.csv) |
| Biology | Osseus Cornibus - Grey | [2400504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400504.csv) |
| Biology | Osseus Cornibus - Indigo | [2400505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400505.csv) |
| Biology | Osseus Cornibus - Lime | [2400502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400502.csv) |
| Biology | Osseus Cornibus - Maroon | [2400509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400509.csv) |
| Biology | Osseus Cornibus - Turquoise | [2400503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400503.csv) |
| Biology | Osseus Discus - Aquamarine | [2400202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400202.csv) |
| Biology | Osseus Discus - Blue | [2400203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400203.csv) |
| Biology | Osseus Discus - Lime | [2400201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400201.csv) |
| Biology | Osseus Discus - Peach | [2400205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400205.csv) |
| Biology | Osseus Discus - Red | [2400204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400204.csv) |
| Biology | Osseus Discus - White | [2400206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400206.csv) |
| Biology | Osseus Fractus - Emerald | [2400106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400106.csv) |
| Biology | Osseus Fractus - Green | [2400107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400107.csv) |
| Biology | Osseus Fractus - Grey | [2400104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400104.csv) |
| Biology | Osseus Fractus - Indigo | [2400105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400105.csv) |
| Biology | Osseus Fractus - Lime | [2400102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400102.csv) |
| Biology | Osseus Fractus - Maroon | [2400109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400109.csv) |
| Biology | Osseus Fractus - Turquoise | [2400103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400103.csv) |
| Biology | Osseus Pellebantus - Emerald | [2400606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400606.csv) |
| Biology | Osseus Pellebantus - Green | [2400607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400607.csv) |
| Biology | Osseus Pellebantus - Grey | [2400604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400604.csv) |
| Biology | Osseus Pellebantus - Indigo | [2400605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400605.csv) |
| Biology | Osseus Pellebantus - Lime | [2400602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400602.csv) |
| Biology | Osseus Pellebantus - Maroon | [2400609.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400609.csv) |
| Biology | Osseus Pellebantus - Turquoise | [2400603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400603.csv) |
| Biology | Osseus Pumice - Gold | [2400404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400404.csv) |
| Biology | Osseus Pumice - Green | [2400402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400402.csv) |
| Biology | Osseus Pumice - Lime | [2400401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400401.csv) |
| Biology | Osseus Pumice - Peach | [2400403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400403.csv) |
| Biology | Osseus Pumice - White | [2400405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400405.csv) |
| Biology | Osseus Pumice - Yellow | [2400406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400406.csv) |
| Biology | Osseus Spiralis - Emerald | [2400306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400306.csv) |
| Biology | Osseus Spiralis - Green | [2400307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400307.csv) |
| Biology | Osseus Spiralis - Grey | [2400304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400304.csv) |
| Biology | Osseus Spiralis - Indigo | [2400305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400305.csv) |
| Biology | Osseus Spiralis - Lime | [2400302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400302.csv) |
| Biology | Osseus Spiralis - Maroon | [2400309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400309.csv) |
| Biology | Osseus Spiralis - Turquoise | [2400303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400303.csv) |
| Biology | Osseus Spiralis - Yellow | [2400301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2400301.csv) |
| Biology | Recepta Conditivus - Aquamarine | [2410301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410301.csv) |
| Biology | Recepta Conditivus - Cyan | [2410302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410302.csv) |
| Biology | Recepta Conditivus - Green | [2410306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410306.csv) |
| Biology | Recepta Conditivus - Lime | [2410305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410305.csv) |
| Biology | Recepta Conditivus - White | [2410303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410303.csv) |
| Biology | Recepta Conditivus - Yellow | [2410304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410304.csv) |
| Biology | Recepta Deltahedronix - Cyan | [2410201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410201.csv) |
| Biology | Recepta Deltahedronix - Gold | [2410205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410205.csv) |
| Biology | Recepta Deltahedronix - Lime | [2410206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410206.csv) |
| Biology | Recepta Deltahedronix - Mulberry | [2410202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410202.csv) |
| Biology | Recepta Deltahedronix - Orange | [2410203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410203.csv) |
| Biology | Recepta Deltahedronix - Red | [2410204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410204.csv) |
| Biology | Recepta Umbrux - Amethyst | [2410103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410103.csv) |
| Biology | Recepta Umbrux - Emerald | [2410115.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410115.csv) |
| Biology | Recepta Umbrux - Grey | [2410111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410111.csv) |
| Biology | Recepta Umbrux - Lime | [2410112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410112.csv) |
| Biology | Recepta Umbrux - Maroon | [2410107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410107.csv) |
| Biology | Recepta Umbrux - Mauve | [2410104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410104.csv) |
| Biology | Recepta Umbrux - Ocher | [2410108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410108.csv) |
| Biology | Recepta Umbrux - Orange | [2410105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410105.csv) |
| Biology | Recepta Umbrux - Red | [2410106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410106.csv) |
| Biology | Recepta Umbrux - Sage | [2410110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410110.csv) |
| Biology | Recepta Umbrux - Teal | [2410109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410109.csv) |
| Biology | Recepta Umbrux - Turquoise | [2410102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410102.csv) |
| Biology | Recepta Umbrux - Yellow | [2410114.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2410114.csv) |
| Biology | Frutexa Acus - Emerald | [2440204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440204.csv) |
| Biology | Frutexa Acus - Green | [2440203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440203.csv) |
| Biology | Frutexa Acus - Grey | [2440205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440205.csv) |
| Biology | Frutexa Acus - Indigo | [2440210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440210.csv) |
| Biology | Frutexa Acus - Lime | [2440202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440202.csv) |
| Biology | Frutexa Acus - Mauve | [2440207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440207.csv) |
| Biology | Frutexa Acus - Orange | [2440209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440209.csv) |
| Biology | Frutexa Acus - Red | [2440211.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440211.csv) |
| Biology | Frutexa Acus - Teal | [2440206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440206.csv) |
| Biology | Frutexa Collum - Emerald | [2440704.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440704.csv) |
| Biology | Frutexa Collum - Green | [2440703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440703.csv) |
| Biology | Frutexa Collum - Grey | [2440705.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440705.csv) |
| Biology | Frutexa Collum - Indigo | [2440710.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440710.csv) |
| Biology | Frutexa Collum - Lime | [2440702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440702.csv) |
| Biology | Frutexa Collum - Mauve | [2440707.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440707.csv) |
| Biology | Frutexa Collum - Red | [2440711.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440711.csv) |
| Biology | Frutexa Collum - Teal | [2440706.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440706.csv) |
| Biology | Frutexa Fera - Emerald | [2440504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440504.csv) |
| Biology | Frutexa Fera - Green | [2440503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440503.csv) |
| Biology | Frutexa Fera - Grey | [2440505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440505.csv) |
| Biology | Frutexa Fera - Indigo | [2440510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440510.csv) |
| Biology | Frutexa Fera - Lime | [2440502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440502.csv) |
| Biology | Frutexa Fera - Mauve | [2440507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440507.csv) |
| Biology | Frutexa Fera - Red | [2440511.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440511.csv) |
| Biology | Frutexa Fera - Teal | [2440506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440506.csv) |
| Biology | Frutexa Flabellum - Emerald | [2440104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440104.csv) |
| Biology | Frutexa Flabellum - Green | [2440103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440103.csv) |
| Biology | Frutexa Flabellum - Grey | [2440105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440105.csv) |
| Biology | Frutexa Flabellum - Indigo | [2440110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440110.csv) |
| Biology | Frutexa Flabellum - Lime | [2440102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440102.csv) |
| Biology | Frutexa Flabellum - Mauve | [2440107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440107.csv) |
| Biology | Frutexa Flabellum - Orange | [2440109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440109.csv) |
| Biology | Frutexa Flabellum - Red | [2440111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440111.csv) |
| Biology | Frutexa Flabellum - Teal | [2440106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440106.csv) |
| Biology | Frutexa Flabellum - Yellow | [2440101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440101.csv) |
| Biology | Frutexa Flammasis - Emerald | [2440404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440404.csv) |
| Biology | Frutexa Flammasis - Green | [2440403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440403.csv) |
| Biology | Frutexa Flammasis - Grey | [2440405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440405.csv) |
| Biology | Frutexa Flammasis - Indigo | [2440410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440410.csv) |
| Biology | Frutexa Flammasis - Lime | [2440402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440402.csv) |
| Biology | Frutexa Flammasis - Mauve | [2440407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440407.csv) |
| Biology | Frutexa Flammasis - Red | [2440411.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440411.csv) |
| Biology | Frutexa Flammasis - Teal | [2440406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440406.csv) |
| Biology | Frutexa Metallicum - Emerald | [2440304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440304.csv) |
| Biology | Frutexa Metallicum - Green | [2440303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440303.csv) |
| Biology | Frutexa Metallicum - Grey | [2440305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440305.csv) |
| Biology | Frutexa Metallicum - Indigo | [2440310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440310.csv) |
| Biology | Frutexa Metallicum - Lime | [2440302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440302.csv) |
| Biology | Frutexa Metallicum - Mauve | [2440307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440307.csv) |
| Biology | Frutexa Metallicum - Red | [2440311.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440311.csv) |
| Biology | Frutexa Metallicum - Teal | [2440306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440306.csv) |
| Biology | Frutexa Sponsae - Emerald | [2440604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440604.csv) |
| Biology | Frutexa Sponsae - Green | [2440603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440603.csv) |
| Biology | Frutexa Sponsae - Grey | [2440605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440605.csv) |
| Biology | Frutexa Sponsae - Lime | [2440602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440602.csv) |
| Biology | Frutexa Sponsae - Mauve | [2440607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440607.csv) |
| Biology | Frutexa Sponsae - Red | [2440611.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440611.csv) |
| Biology | Frutexa Sponsae - Teal | [2440606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2440606.csv) |
| Biology | Stratum Araneamus - Emerald | [2420401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420401.csv) |
| Biology | Stratum Cucumisis - Amethyst | [2420606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420606.csv) |
| Biology | Stratum Cucumisis - Emerald | [2420601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420601.csv) |
| Biology | Stratum Cucumisis - Green | [2420603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420603.csv) |
| Biology | Stratum Cucumisis - Grey | [2420605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420605.csv) |
| Biology | Stratum Cucumisis - Indigo | [2420608.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420608.csv) |
| Biology | Stratum Cucumisis - Lime | [2420602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420602.csv) |
| Biology | Stratum Cucumisis - Mauve | [2420610.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420610.csv) |
| Biology | Stratum Cucumisis - Teal | [2420607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420607.csv) |
| Biology | Stratum Cucumisis - Turquoise | [2420604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420604.csv) |
| Biology | Stratum Excutitus - Amethyst | [2420106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420106.csv) |
| Biology | Stratum Excutitus - Emerald | [2420101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420101.csv) |
| Biology | Stratum Excutitus - Green | [2420103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420103.csv) |
| Biology | Stratum Excutitus - Grey | [2420105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420105.csv) |
| Biology | Stratum Excutitus - Indigo | [2420108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420108.csv) |
| Biology | Stratum Excutitus - Lime | [2420102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420102.csv) |
| Biology | Stratum Excutitus - Mauve | [2420110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420110.csv) |
| Biology | Stratum Excutitus - Red | [2420109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420109.csv) |
| Biology | Stratum Excutitus - Teal | [2420107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420107.csv) |
| Biology | Stratum Excutitus - Turquoise | [2420104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420104.csv) |
| Biology | Stratum Frigus - Amethyst | [2420806.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420806.csv) |
| Biology | Stratum Frigus - Emerald | [2420801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420801.csv) |
| Biology | Stratum Frigus - Green | [2420803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420803.csv) |
| Biology | Stratum Frigus - Grey | [2420805.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420805.csv) |
| Biology | Stratum Frigus - Indigo | [2420808.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420808.csv) |
| Biology | Stratum Frigus - Lime | [2420802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420802.csv) |
| Biology | Stratum Frigus - Teal | [2420807.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420807.csv) |
| Biology | Stratum Frigus - Turquoise | [2420804.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420804.csv) |
| Biology | Stratum Laminamus - Amethyst | [2420306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420306.csv) |
| Biology | Stratum Laminamus - Emerald | [2420301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420301.csv) |
| Biology | Stratum Laminamus - Green | [2420303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420303.csv) |
| Biology | Stratum Laminamus - Grey | [2420305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420305.csv) |
| Biology | Stratum Laminamus - Indigo | [2420308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420308.csv) |
| Biology | Stratum Laminamus - Lime | [2420302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420302.csv) |
| Biology | Stratum Laminamus - Mauve | [2420310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420310.csv) |
| Biology | Stratum Laminamus - Red | [2420309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420309.csv) |
| Biology | Stratum Laminamus - Turquoise | [2420304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420304.csv) |
| Biology | Stratum Limaxus - Amethyst | [2420506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420506.csv) |
| Biology | Stratum Limaxus - Emerald | [2420501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420501.csv) |
| Biology | Stratum Limaxus - Green | [2420503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420503.csv) |
| Biology | Stratum Limaxus - Grey | [2420505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420505.csv) |
| Biology | Stratum Limaxus - Indigo | [2420508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420508.csv) |
| Biology | Stratum Limaxus - Lime | [2420502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420502.csv) |
| Biology | Stratum Limaxus - Mauve | [2420510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420510.csv) |
| Biology | Stratum Limaxus - Teal | [2420507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420507.csv) |
| Biology | Stratum Limaxus - Turquoise | [2420504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420504.csv) |
| Biology | Stratum Paleas - Amethyst | [2420206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420206.csv) |
| Biology | Stratum Paleas - Emerald | [2420201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420201.csv) |
| Biology | Stratum Paleas - Green | [2420203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420203.csv) |
| Biology | Stratum Paleas - Grey | [2420205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420205.csv) |
| Biology | Stratum Paleas - Indigo | [2420208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420208.csv) |
| Biology | Stratum Paleas - Lime | [2420202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420202.csv) |
| Biology | Stratum Paleas - Mauve | [2420210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420210.csv) |
| Biology | Stratum Paleas - Red | [2420209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420209.csv) |
| Biology | Stratum Paleas - Teal | [2420207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420207.csv) |
| Biology | Stratum Paleas - Turquoise | [2420204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420204.csv) |
| Biology | Stratum Tectonicas - Amethyst | [2420706.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420706.csv) |
| Biology | Stratum Tectonicas - Emerald | [2420701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420701.csv) |
| Biology | Stratum Tectonicas - Green | [2420703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420703.csv) |
| Biology | Stratum Tectonicas - Grey | [2420705.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420705.csv) |
| Biology | Stratum Tectonicas - Indigo | [2420708.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420708.csv) |
| Biology | Stratum Tectonicas - Lime | [2420702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420702.csv) |
| Biology | Stratum Tectonicas - Mauve | [2420710.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420710.csv) |
| Biology | Stratum Tectonicas - Red | [2420709.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420709.csv) |
| Biology | Stratum Tectonicas - Turquoise | [2420704.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2420704.csv) |
| Biology | Tubus Cavas - Amethyst | [2430313.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430313.csv) |
| Biology | Tubus Cavas - Emerald | [2430302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430302.csv) |
| Biology | Tubus Cavas - Grey | [2430304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430304.csv) |
| Biology | Tubus Cavas - Indigo | [2430303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430303.csv) |
| Biology | Tubus Cavas - Maroon | [2430306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430306.csv) |
| Biology | Tubus Cavas - Mauve | [2430309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430309.csv) |
| Biology | Tubus Cavas - Ocher | [2430310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430310.csv) |
| Biology | Tubus Cavas - Red | [2430305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430305.csv) |
| Biology | Tubus Cavas - Teal | [2430307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430307.csv) |
| Biology | Tubus Cavas - Turquoise | [2430308.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430308.csv) |
| Biology | Tubus Cavas - Yellow | [2430312.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430312.csv) |
| Biology | Tubus Compagibus - Amethyst | [2430513.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430513.csv) |
| Biology | Tubus Compagibus - Emerald | [2430502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430502.csv) |
| Biology | Tubus Compagibus - Grey | [2430504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430504.csv) |
| Biology | Tubus Compagibus - Indigo | [2430503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430503.csv) |
| Biology | Tubus Compagibus - Lime | [2430511.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430511.csv) |
| Biology | Tubus Compagibus - Maroon | [2430506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430506.csv) |
| Biology | Tubus Compagibus - Mauve | [2430509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430509.csv) |
| Biology | Tubus Compagibus - Ocher | [2430510.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430510.csv) |
| Biology | Tubus Compagibus - Red | [2430505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430505.csv) |
| Biology | Tubus Compagibus - Teal | [2430507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430507.csv) |
| Biology | Tubus Compagibus - Turquoise | [2430508.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430508.csv) |
| Biology | Tubus Compagibus - Yellow | [2430512.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430512.csv) |
| Biology | Tubus Conifer - Amethyst | [2430113.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430113.csv) |
| Biology | Tubus Conifer - Emerald | [2430102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430102.csv) |
| Biology | Tubus Conifer - Grey | [2430104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430104.csv) |
| Biology | Tubus Conifer - Indigo | [2430103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430103.csv) |
| Biology | Tubus Conifer - Maroon | [2430106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430106.csv) |
| Biology | Tubus Conifer - Mauve | [2430109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430109.csv) |
| Biology | Tubus Conifer - Ocher | [2430110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430110.csv) |
| Biology | Tubus Conifer - Red | [2430105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430105.csv) |
| Biology | Tubus Conifer - Teal | [2430107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430107.csv) |
| Biology | Tubus Conifer - Turquoise | [2430108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430108.csv) |
| Biology | Tubus Conifer - Yellow | [2430112.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430112.csv) |
| Biology | Tubus Rosarium - Amethyst | [2430413.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430413.csv) |
| Biology | Tubus Rosarium - Emerald | [2430402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430402.csv) |
| Biology | Tubus Rosarium - Green | [2430401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430401.csv) |
| Biology | Tubus Rosarium - Grey | [2430404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430404.csv) |
| Biology | Tubus Rosarium - Indigo | [2430403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430403.csv) |
| Biology | Tubus Rosarium - Maroon | [2430406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430406.csv) |
| Biology | Tubus Rosarium - Mauve | [2430409.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430409.csv) |
| Biology | Tubus Rosarium - Ocher | [2430410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430410.csv) |
| Biology | Tubus Rosarium - Red | [2430405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430405.csv) |
| Biology | Tubus Rosarium - Teal | [2430407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430407.csv) |
| Biology | Tubus Rosarium - Turquoise | [2430408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430408.csv) |
| Biology | Tubus Rosarium - Yellow | [2430412.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430412.csv) |
| Biology | Tubus Sororibus - Amethyst | [2430213.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430213.csv) |
| Biology | Tubus Sororibus - Emerald | [2430202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430202.csv) |
| Biology | Tubus Sororibus - Grey | [2430204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430204.csv) |
| Biology | Tubus Sororibus - Indigo | [2430203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430203.csv) |
| Biology | Tubus Sororibus - Maroon | [2430206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430206.csv) |
| Biology | Tubus Sororibus - Mauve | [2430209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430209.csv) |
| Biology | Tubus Sororibus - Ocher | [2430210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430210.csv) |
| Biology | Tubus Sororibus - Red | [2430205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430205.csv) |
| Biology | Tubus Sororibus - Teal | [2430207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430207.csv) |
| Biology | Tubus Sororibus - Turquoise | [2430208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2430208.csv) |
| Biology | Tussock Albata - Emerald | [2450804.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450804.csv) |
| Biology | Tussock Albata - Green | [2450803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450803.csv) |
| Biology | Tussock Albata - Lime | [2450802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450802.csv) |
| Biology | Tussock Albata - Maroon | [2450811.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450811.csv) |
| Biology | Tussock Albata - Orange | [2450810.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450810.csv) |
| Biology | Tussock Albata - Red | [2450809.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450809.csv) |
| Biology | Tussock Albata - Sage | [2450805.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450805.csv) |
| Biology | Tussock Albata - Teal | [2450806.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450806.csv) |
| Biology | Tussock Albata - Yellow | [2450801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450801.csv) |
| Biology | Tussock Capillum - Emerald | [2451504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451504.csv) |
| Biology | Tussock Capillum - Green | [2451503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451503.csv) |
| Biology | Tussock Capillum - Lime | [2451502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451502.csv) |
| Biology | Tussock Capillum - Maroon | [2451511.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451511.csv) |
| Biology | Tussock Capillum - Red | [2451509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451509.csv) |
| Biology | Tussock Capillum - Sage | [2451505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451505.csv) |
| Biology | Tussock Capillum - Teal | [2451506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451506.csv) |
| Biology | Tussock Capillum - Yellow | [2451501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451501.csv) |
| Biology | Tussock Caputus - Emerald | [2451104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451104.csv) |
| Biology | Tussock Caputus - Green | [2451103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451103.csv) |
| Biology | Tussock Caputus - Lime | [2451102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451102.csv) |
| Biology | Tussock Caputus - Maroon | [2451111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451111.csv) |
| Biology | Tussock Caputus - Red | [2451109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451109.csv) |
| Biology | Tussock Caputus - Sage | [2451105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451105.csv) |
| Biology | Tussock Caputus - Teal | [2451106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451106.csv) |
| Biology | Tussock Caputus - Yellow | [2451101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451101.csv) |
| Biology | Tussock Catena - Emerald | [2450504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450504.csv) |
| Biology | Tussock Catena - Green | [2450503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450503.csv) |
| Biology | Tussock Catena - Lime | [2450502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450502.csv) |
| Biology | Tussock Catena - Maroon | [2450511.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450511.csv) |
| Biology | Tussock Catena - Red | [2450509.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450509.csv) |
| Biology | Tussock Catena - Sage | [2450505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450505.csv) |
| Biology | Tussock Catena - Teal | [2450506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450506.csv) |
| Biology | Tussock Catena - Yellow | [2450501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450501.csv) |
| Biology | Tussock Cultro - Emerald | [2450404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450404.csv) |
| Biology | Tussock Cultro - Green | [2450403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450403.csv) |
| Biology | Tussock Cultro - Lime | [2450402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450402.csv) |
| Biology | Tussock Cultro - Maroon | [2450411.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450411.csv) |
| Biology | Tussock Cultro - Orange | [2450410.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450410.csv) |
| Biology | Tussock Cultro - Red | [2450409.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450409.csv) |
| Biology | Tussock Cultro - Sage | [2450405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450405.csv) |
| Biology | Tussock Cultro - Teal | [2450406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450406.csv) |
| Biology | Tussock Cultro - Yellow | [2450401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450401.csv) |
| Biology | Tussock Divisa - Emerald | [2451004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451004.csv) |
| Biology | Tussock Divisa - Green | [2451003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451003.csv) |
| Biology | Tussock Divisa - Lime | [2451002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451002.csv) |
| Biology | Tussock Divisa - Maroon | [2451011.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451011.csv) |
| Biology | Tussock Divisa - Red | [2451009.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451009.csv) |
| Biology | Tussock Divisa - Sage | [2451005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451005.csv) |
| Biology | Tussock Divisa - Teal | [2451006.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451006.csv) |
| Biology | Tussock Divisa - Yellow | [2451001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451001.csv) |
| Biology | Tussock Ignis - Emerald | [2450304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450304.csv) |
| Biology | Tussock Ignis - Green | [2450303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450303.csv) |
| Biology | Tussock Ignis - Lime | [2450302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450302.csv) |
| Biology | Tussock Ignis - Maroon | [2450311.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450311.csv) |
| Biology | Tussock Ignis - Orange | [2450310.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450310.csv) |
| Biology | Tussock Ignis - Red | [2450309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450309.csv) |
| Biology | Tussock Ignis - Sage | [2450305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450305.csv) |
| Biology | Tussock Ignis - Teal | [2450306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450306.csv) |
| Biology | Tussock Ignis - Yellow | [2450301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450301.csv) |
| Biology | Tussock Pennata - Emerald | [2450104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450104.csv) |
| Biology | Tussock Pennata - Green | [2450103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450103.csv) |
| Biology | Tussock Pennata - Lime | [2450102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450102.csv) |
| Biology | Tussock Pennata - Maroon | [2450111.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450111.csv) |
| Biology | Tussock Pennata - Orange | [2450110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450110.csv) |
| Biology | Tussock Pennata - Red | [2450109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450109.csv) |
| Biology | Tussock Pennata - Sage | [2450105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450105.csv) |
| Biology | Tussock Pennata - Teal | [2450106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450106.csv) |
| Biology | Tussock Pennata - Yellow | [2450101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450101.csv) |
| Biology | Tussock Pennatis - Emerald | [2450604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450604.csv) |
| Biology | Tussock Pennatis - Green | [2450603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450603.csv) |
| Biology | Tussock Pennatis - Lime | [2450602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450602.csv) |
| Biology | Tussock Pennatis - Maroon | [2450611.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450611.csv) |
| Biology | Tussock Pennatis - Red | [2450609.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450609.csv) |
| Biology | Tussock Pennatis - Sage | [2450605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450605.csv) |
| Biology | Tussock Pennatis - Teal | [2450606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450606.csv) |
| Biology | Tussock Pennatis - Yellow | [2450601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450601.csv) |
| Biology | Tussock Propagito - Emerald | [2450904.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450904.csv) |
| Biology | Tussock Propagito - Green | [2450903.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450903.csv) |
| Biology | Tussock Propagito - Lime | [2450902.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450902.csv) |
| Biology | Tussock Propagito - Maroon | [2450911.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450911.csv) |
| Biology | Tussock Propagito - Red | [2450909.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450909.csv) |
| Biology | Tussock Propagito - Sage | [2450905.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450905.csv) |
| Biology | Tussock Propagito - Teal | [2450906.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450906.csv) |
| Biology | Tussock Propagito - Yellow | [2450901.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450901.csv) |
| Biology | Tussock Serrati - Emerald | [2450704.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450704.csv) |
| Biology | Tussock Serrati - Green | [2450703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450703.csv) |
| Biology | Tussock Serrati - Lime | [2450702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450702.csv) |
| Biology | Tussock Serrati - Maroon | [2450711.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450711.csv) |
| Biology | Tussock Serrati - Red | [2450709.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450709.csv) |
| Biology | Tussock Serrati - Sage | [2450705.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450705.csv) |
| Biology | Tussock Serrati - Teal | [2450706.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450706.csv) |
| Biology | Tussock Serrati - Yellow | [2450701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450701.csv) |
| Biology | Tussock Stigmasis - Emerald | [2451304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451304.csv) |
| Biology | Tussock Stigmasis - Green | [2451303.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451303.csv) |
| Biology | Tussock Stigmasis - Lime | [2451302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451302.csv) |
| Biology | Tussock Stigmasis - Maroon | [2451311.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451311.csv) |
| Biology | Tussock Stigmasis - Red | [2451309.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451309.csv) |
| Biology | Tussock Stigmasis - Sage | [2451305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451305.csv) |
| Biology | Tussock Stigmasis - Teal | [2451306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451306.csv) |
| Biology | Tussock Stigmasis - Yellow | [2451301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451301.csv) |
| Biology | Tussock Triticum - Emerald | [2451204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451204.csv) |
| Biology | Tussock Triticum - Green | [2451203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451203.csv) |
| Biology | Tussock Triticum - Lime | [2451202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451202.csv) |
| Biology | Tussock Triticum - Maroon | [2451211.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451211.csv) |
| Biology | Tussock Triticum - Red | [2451209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451209.csv) |
| Biology | Tussock Triticum - Sage | [2451205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451205.csv) |
| Biology | Tussock Triticum - Teal | [2451206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451206.csv) |
| Biology | Tussock Triticum - Yellow | [2451201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451201.csv) |
| Biology | Tussock Ventusa - Emerald | [2450204.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450204.csv) |
| Biology | Tussock Ventusa - Green | [2450203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450203.csv) |
| Biology | Tussock Ventusa - Lime | [2450202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450202.csv) |
| Biology | Tussock Ventusa - Maroon | [2450211.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450211.csv) |
| Biology | Tussock Ventusa - Orange | [2450210.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450210.csv) |
| Biology | Tussock Ventusa - Red | [2450209.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450209.csv) |
| Biology | Tussock Ventusa - Sage | [2450205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450205.csv) |
| Biology | Tussock Ventusa - Teal | [2450206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450206.csv) |
| Biology | Tussock Ventusa - Yellow | [2450201.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2450201.csv) |
| Biology | Tussock Virgam - Emerald | [2451404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451404.csv) |
| Biology | Tussock Virgam - Green | [2451403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451403.csv) |
| Biology | Tussock Virgam - Lime | [2451402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451402.csv) |
| Biology | Tussock Virgam - Sage | [2451405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451405.csv) |
| Biology | Tussock Virgam - Teal | [2451406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451406.csv) |
| Biology | Tussock Virgam - Yellow | [2451401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Biology/2451401.csv) |
| Cloud | Cereum Aster Pod | [2202001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2202001.csv) |
| Cloud | Cereum Aster Tree | [2208101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208101.csv) |
| Cloud | Lindigoticum Aster Pod | [2202002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2202002.csv) |
| Cloud | Prasinum Aster Pod | [2202003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2202003.csv) |
| Cloud | Prasinum Aster Tree | [2208103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208103.csv) |
| Cloud | Puniceum Aster Pod | [2202004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2202004.csv) |
| Cloud | Rubellum Aster Pod | [2202005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2202005.csv) |
| Cloud | Rubellum Aster Tree | [2208105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208105.csv) |
| Cloud | Lindigoticum Calcite Plates | [2101002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2101002.csv) |
| Cloud | Luteolum Calcite Plates | [2101001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2101001.csv) |
| Cloud | Rutulum Calcite Plates | [2101004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2101004.csv) |
| Cloud | Viride Calcite Plates | [2101003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2101003.csv) |
| Cloud | Albidum Chalice Pod | [2205001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2205001.csv) |
| Cloud | Caeruleum Chalice Pod | [2205002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2205002.csv) |
| Cloud | Ostrinum Chalice Pod | [2205004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2205004.csv) |
| Cloud | Rubellum Chalice Pod | [2205005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2205005.csv) |
| Cloud | Viride Chalice Pod | [2205003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2205003.csv) |
| Cloud | Albidum Collared Pod | [2204001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2204001.csv) |
| Cloud | Blatteum Collared Pod | [2204004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2204004.csv) |
| Cloud | Lividum Collared Pod | [2204002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2204002.csv) |
| Cloud | Rubicundum Collared Pod | [2204005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2204005.csv) |
| Cloud | Aurarium Gyre Pod | [2206002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2206002.csv) |
| Cloud | Aurarium Gyre Tree | [2210011.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2210011.csv) |
| Cloud | Roseum Gyre Pod | [2206001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2206001.csv) |
| Cloud | Viride Gyre Tree | [2210001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2210001.csv) |
| Cloud | Albidum Ice Crystals | [2100606.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100606.csv) |
| Cloud | Flavum Ice Crystals | [2100607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100607.csv) |
| Cloud | Lindigoticum Ice Crystals | [2100601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100601.csv) |
| Cloud | Prasinum Ice Crystals | [2100602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100602.csv) |
| Cloud | Purpureum Ice Crystals | [2100604.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100604.csv) |
| Cloud | Roseum Ice Crystals | [2100603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100603.csv) |
| Cloud | Rubeum Ice Crystals | [2100605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100605.csv) |
| Cloud | Caeruleum Lagrange Cloud | [1400601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400601.csv) |
| Cloud | Croceum Lagrange Cloud | [1401101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1401101.csv) |
| Cloud | Luteolum Lagrange Cloud | [1400801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400801.csv) |
| Cloud | Proto-Lagrange Cloud | [1401300.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1401300.csv) |
| Cloud | Roseum Lagrange Cloud | [1400901.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400901.csv) |
| Cloud | Rubicundum Lagrange Cloud | [1401001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1401001.csv) |
| Cloud | Viride Lagrange Cloud | [1400701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400701.csv) |
| Cloud | Flavum Metallic Crystals | [2100804.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100804.csv) |
| Cloud | Prasinum Metallic Crystals | [2100801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100801.csv) |
| Cloud | Purpureum Metallic Crystals | [2100802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100802.csv) |
| Cloud | Rubeum Metallic Crystals | [2100803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100803.csv) |
| Cloud | Lattice Mineral Spheres | [1410110.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1410110.csv) |
| Cloud | Solid Mineral Spheres | [1410100.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1410100.csv) |
| Cloud | Albens Bell Mollusc | [2300601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300601.csv) |
| Cloud | Albulum Gourd Mollusc | [2300101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300101.csv) |
| Cloud | Albulum Squid Mollusc | [2300301.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300301.csv) |
| Cloud | Blatteum Bell Mollusc | [2300605.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300605.csv) |
| Cloud | Blatteum Torus Mollusc | [2300205.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300205.csv) |
| Cloud | Caeruleum Gourd Mollusc | [2300102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300102.csv) |
| Cloud | Caeruleum Squid Mollusc | [2300302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300302.csv) |
| Cloud | Caeruleum Torus Mollusc | [2300202.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300202.csv) |
| Cloud | Cereum Bullet Mollusc | [2300401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300401.csv) |
| Cloud | Cobalteum Globe Mollusc | [2300502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300502.csv) |
| Cloud | Croceum Globe Mollusc | [2300507.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300507.csv) |
| Cloud | Croceum Gourd Mollusc | [2300107.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300107.csv) |
| Cloud | Flavum Bullet Mollusc | [2300407.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300407.csv) |
| Cloud | Flavum Torus Mollusc | [2300207.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300207.csv) |
| Cloud | Gypseeum Bell Mollusc | [2300603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300603.csv) |
| Cloud | Lindigoticum Bell Mollusc | [2300602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300602.csv) |
| Cloud | Lindigoticum Bulb Mollusc | [2301702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301702.csv) |
| Cloud | Lindigoticum Capsule Mollusc | [2301902.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301902.csv) |
| Cloud | Lindigoticum Parasol Mollusc | [2301602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301602.csv) |
| Cloud | Lindigoticum Reel Mollusc | [2302102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2302102.csv) |
| Cloud | Lindigoticum Umbrella Mollusc | [2301802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301802.csv) |
| Cloud | Lividum Bullet Mollusc | [2300402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300402.csv) |
| Cloud | Luteolum Bell Mollusc | [2300607.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300607.csv) |
| Cloud | Luteolum Bulb Mollusc | [2301701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301701.csv) |
| Cloud | Luteolum Capsule Mollusc | [2301901.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301901.csv) |
| Cloud | Luteolum Parasol Mollusc | [2301601.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301601.csv) |
| Cloud | Luteolum Reel Mollusc | [2302101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2302101.csv) |
| Cloud | Luteolum Umbrella Mollusc | [2301801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301801.csv) |
| Cloud | Niveum Globe Mollusc | [2300501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300501.csv) |
| Cloud | Ostrinum Globe Mollusc | [2300505.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300505.csv) |
| Cloud | Phoeniceum Gourd Mollusc | [2300104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300104.csv) |
| Cloud | Prasinum Globe Mollusc | [2300503.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300503.csv) |
| Cloud | Puniceum Squid Mollusc | [2300305.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300305.csv) |
| Cloud | Purpureum Gourd Mollusc | [2300105.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300105.csv) |
| Cloud | Roseum Globe Mollusc | [2300504.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300504.csv) |
| Cloud | Roseum Squid Mollusc | [2300304.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300304.csv) |
| Cloud | Rubellum Torus Mollusc | [2300206.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300206.csv) |
| Cloud | Rubeum Bullet Mollusc | [2300406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300406.csv) |
| Cloud | Rubeum Squid Mollusc | [2300306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300306.csv) |
| Cloud | Rufum Gourd Mollusc | [2300106.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300106.csv) |
| Cloud | Rutulum Globe Mollusc | [2300506.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300506.csv) |
| Cloud | Viride Bulb Mollusc | [2301703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301703.csv) |
| Cloud | Viride Bullet Mollusc | [2300403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300403.csv) |
| Cloud | Viride Capsule Mollusc | [2301903.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301903.csv) |
| Cloud | Viride Gourd Mollusc | [2300103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300103.csv) |
| Cloud | Viride Parasol Mollusc | [2301603.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301603.csv) |
| Cloud | Viride Reel Mollusc | [2302103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2302103.csv) |
| Cloud | Viride Torus Mollusc | [2300203.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2300203.csv) |
| Cloud | Viride Umbrella Mollusc | [2301803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2301803.csv) |
| Cloud | Albidum Peduncle Tree | [2208001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208001.csv) |
| Cloud | Caeruleum Peduncle Pod | [2201002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2201002.csv) |
| Cloud | Caeruleum Peduncle Tree | [2208002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208002.csv) |
| Cloud | Candidum Peduncle Pod | [2201001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2201001.csv) |
| Cloud | Gypseeum Peduncle Pod | [2201003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2201003.csv) |
| Cloud | Ostrinum Peduncle Tree | [2208004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208004.csv) |
| Cloud | Purpureum Peduncle Pod | [2201004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2201004.csv) |
| Cloud | Rubellum Peduncle Tree | [2208005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208005.csv) |
| Cloud | Rufum Peduncle Pod | [2201005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2201005.csv) |
| Cloud | Viride Peduncle Tree | [2208003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2208003.csv) |
| Cloud | Albidum Quadripartite Pod | [2207101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207101.csv) |
| Cloud | Blatteum Quadripartite Pod | [2207104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207104.csv) |
| Cloud | Caeruleum Quadripartite Pod | [2207102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207102.csv) |
| Cloud | Viride Quadripartite Pod | [2207103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207103.csv) |
| Cloud | Candidum Rhizome Pod | [2207001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207001.csv) |
| Cloud | Cobalteum Rhizome Pod | [2207002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207002.csv) |
| Cloud | Gypseeum Rhizome Pod | [2207003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207003.csv) |
| Cloud | Purpureum Rhizome Pod | [2207004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207004.csv) |
| Cloud | Rubeum Rhizome Pod | [2207005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207005.csv) |
| Cloud | Albidum Silicate Crystals | [2100706.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100706.csv) |
| Cloud | Flavum Silicate Crystals | [2100707.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100707.csv) |
| Cloud | Lindigoticum Silicate Crystals | [2100701.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100701.csv) |
| Cloud | Prasinum Silicate Crystals | [2100702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100702.csv) |
| Cloud | Purpureum Silicate Crystals | [2100704.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100704.csv) |
| Cloud | Roseum Silicate Crystals | [2100703.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100703.csv) |
| Cloud | Rubeum Silicate Crystals | [2100705.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2100705.csv) |
| Cloud | Stolon Pod | [2207200.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2207200.csv) |
| Cloud | Stolon Tree | [2209021.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2209021.csv) |
| Cloud | Croceum Lagrange Storm Cloud | [1401102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1401102.csv) |
| Cloud | Luteolum Lagrange Storm Cloud | [1400802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400802.csv) |
| Cloud | Roseum Lagrange Storm Cloud | [1400902.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400902.csv) |
| Cloud | Rubicundum Lagrange Storm Cloud | [1401002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1401002.csv) |
| Cloud | Viride Lagrange Storm Cloud | [1400702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/1400702.csv) |
| Cloud | Blatteum Octahedral Pod | [2203004.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2203004.csv) |
| Cloud | Caeruleum Octahedral Pod | [2203002.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2203002.csv) |
| Cloud | Chryseum Void Heart | [2210101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2210101.csv) |
| Cloud | Niveum Octahedral Pod | [2203001.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2203001.csv) |
| Cloud | Rubeum Octahedral Pod | [2203005.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2203005.csv) |
| Cloud | Viride Octahedral Pod | [2203003.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Cloud/2203003.csv) |
| Geology | Ammonia Ice Fumarole | [1400160.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400160.csv) |
| Geology | Carbon Dioxide Fumarole | [1400109.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400109.csv) |
| Geology | Carbon Dioxide Ice Fumarole | [1400159.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400159.csv) |
| Geology | Methane Ice Fumarole | [1400161.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400161.csv) |
| Geology | Nitrogen Ice Fumarole | [1400162.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400162.csv) |
| Geology | Silicate Vapour Fumarole | [1400114.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400114.csv) |
| Geology | Silicate Vapour Ice Fumarole | [1400164.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400164.csv) |
| Geology | Sulphur Dioxide Fumarole | [1400102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400102.csv) |
| Geology | Sulphur Dioxide Ice Fumarole | [1400152.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400152.csv) |
| Geology | Water Fumarole | [1400108.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400108.csv) |
| Geology | Water Ice Fumarole | [1400158.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400158.csv) |
| Geology | Carbon Dioxide Gas Vent | [1400409.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400409.csv) |
| Geology | Silicate Vapour Gas Vent | [1400414.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400414.csv) |
| Geology | Sulphur Dioxide Gas Vent | [1400402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400402.csv) |
| Geology | Water Gas Vent | [1400408.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400408.csv) |
| Geology | Ammonia Ice Geyser | [1400260.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400260.csv) |
| Geology | Carbon Dioxide Ice Geyser | [1400259.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400259.csv) |
| Geology | Methane Ice Geyser | [1400261.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400261.csv) |
| Geology | Nitrogen Ice Geyser | [1400262.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400262.csv) |
| Geology | Water Geyser | [1400208.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400208.csv) |
| Geology | Water Ice Geyser | [1400258.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400258.csv) |
| Geology | Iron Magma Lava Spout | [1400307.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400307.csv) |
| Geology | Silicate Magma Lava Spout | [1400306.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Geology/1400306.csv) |
| Guardian | Guardian Beacon | [3200800.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200800.csv) |
| Guardian | Guardian Codex | [3200200.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200200.csv) |
| Guardian | Guardian Data Terminal | [3200300.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200300.csv) |
| Guardian | Guardian Pylon | [3200400.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200400.csv) |
| Guardian | Guardian Relic Tower | [3200500.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200500.csv) |
| Guardian | Guardian Sentinel | [3200600.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Guardian/3200600.csv) |
| None | Thargoid Interceptor Basilisk | [3100402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100402.csv) |
| None | Thargoid Interceptor Cyclops | [3100401.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100401.csv) |
| None | Thargoid Interceptor Hydra | [3100404.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100404.csv) |
| None | Thargoid Interceptor Medusa | [3100403.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100403.csv) |
| None | Thargoid Scout Berserker | [3100802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100802.csv) |
| None | Thargoid Scout Inciter | [3100803.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100803.csv) |
| None | Thargoid Scout Marauder | [3100801.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100801.csv) |
| None | Thargoid Scout Regenerator | [3100804.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100804.csv) |
| None | Thargoid Hunter Glaive | [3100501.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100501.csv) |
| None | Thargoid Hunter Scythe | [3100502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100502.csv) |
| None | Thargoid Interceptor Orthrus | [3100406.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100406.csv) |
| None | Thargoid Revenants | [3100702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/None/3100702.csv) |
| Thargoid | Common Thargoid Barnacle | [2100101.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/2100101.csv) |
| Thargoid | Large Thargoid Barnacle | [2100102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/2100102.csv) |
| Thargoid | Thargoid Barnacle Barbs | [2100103.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/2100103.csv) |
| Thargoid | Thargoid Device | [3101200.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3101200.csv) |
| Thargoid | Thargoid Interceptor Shipwreck | [3100405.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3100405.csv) |
| Thargoid | Thargoid Pod | [3101100.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3101100.csv) |
| Thargoid | Thargoid Scavengers | [3100700.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3100700.csv) |
| Thargoid | Thargoid Scout Shipwreck | [3100805.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3100805.csv) |
| Thargoid | Thargoid Uplink Device | [3101000.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3101000.csv) |
| Thargoid | Coral Tree | [3100600.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3100600.csv) |
| Thargoid | Thargoid Caustic Generator | [3101300.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3101300.csv) |
| Thargoid | Thargoid Barnacle Matrix | [2100104.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/2100104.csv) |
| Thargoid | Toughened Spear Roots | [3100900.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Thargoid/3100900.csv) |
| Tourist | Green Class I Gas Giant | [1200502.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200502.csv) |
| Tourist | Green Class II Gas Giant | [1200602.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200602.csv) |
| Tourist | Green Class III Gas Giant | [1200702.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200702.csv) |
| Tourist | Green Class IV Gas Giant | [1200802.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200802.csv) |
| Tourist | Green Class V Gas Giant | [1200902.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200902.csv) |
| Tourist | Green Gas Giant | [1200402.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200402.csv) |
| Tourist | Green Gas Giant with Ammonia Life | [1200302.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200302.csv) |
| Tourist | Green Water Giant | [1200102.csv](https://storage.googleapis.com/canonn-downloads/dumpr/Tourist/1200102.csv) |






