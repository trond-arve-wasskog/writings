I forbindelse med slippet av skattemeldingen svarer avdelingsdirektør Cat Holten på spørsmål om hvordan Altinn håndterer den store pågangen; "skal vi bygge firefeltsvei til Holmenkollen på grunn av Holmenkollsøndag?"<sup>1</sup>. Metaforen er trolig riktig i denne sammenhengen, men den bryter sammen i møtet med elastiske nettskyplattformer.

Først og fremst; dette er ingen kritikk av Altinn, BankID eller ID-porten. Jeg har stor respekt for kompleksiteten og kostnaden ved å bygge og vedlikeholde IT-løsninger. Selv har jeg ikke jobbet med disse systemene, men vet av erfaring at alle IT-systemer er preget av sin historikk og varierende rammebetingelser over tid. Altinn-portalen ble eksemplevis lansert 4. desember 2003<sup>2</sup>, og er en hjørnestein i offentlige virksomheters kommunikasjon med næringslivet og privatpersoner.

Cat Holten refererer i intervjuet til en uttalelse av skattedirektør Hans Christian Holte i 2016. Ved nærmere undersøkelse ser det ut til at opprinnelsen er daværende informasjonsansvarlig i Altinn, Jørgen Ferkingstad, fra et intervju i mars 2012<sup>3</sup>:
> _Men det går fint an å bygge løsninger som tåler all verdens belastning. Men det blir litt som å bygge en seksfelts motorvei til Holmenkollen for å unngå kø opp dit på Kollensøndag._ 

Oversatt til IT-området; anskaffelse av maskinvare for å håndtere sporadisk topplast og la systemet gå på tomgang resten av året, er å skyte spurv med kanon.

_Elastisitet_ er en av de mest tilgjengelige gevinstene i nettskyen. Framfor å etablere infrastruktur i egen datahall, kan konsum av datakraft reguleres i takt med den faktiske pågangen. Skaleringen overlates til nettskyplattformen slik at behovet for å håndtere topplasten på egen maskinvare faller bort. Serverless-plattformer og driftede nettskytjenester er (foreløpig) siste evolusjonsnivå i frikoblingen fra fysiske servere og infrastruktur <sup>4</sup>. Holmenkollen er hard vare, servere og infrastruktur har blitt mjukvare<sup>5</sup>.

Forutsetningen er at applikasjonene er laget for å skalere og dermed kan utnytte nettskyplattformens elastisitet. Applikasjoner som ble unnfanget for 10 eller 20 år siden er med stor sannsynlighet ikke i denne kategorien. Spørsmålene som melder seg er om det er mulig å oppnå elastisitetsgevinsten ved å ta i bruk nettskyen, om det er hensiktsmessig, og hvordan man eventuelt går fram. TODO: Vegards migreringsalternativer. Svarene vil variere for ulike applikasjoner, teknologier og organisasjoner. Helt overordnet vil vi gi følgende anbefalinger:
* Å bruke nettskyen som en forlengelse av egen datahall på IaaS-nivå kan være feil ende å starte. Man kan bli stående i spagat mellom to komplekse plattformer, mens applikasjonsdesignet begrenser skalerbarhet, forvaltbarhet og driftbarhet.
* Design for nettskyen, mikrotjenester, data
* => PaaS, Serverless
* Gå all inn, men ha en migreringsplan

TODO wrap it up:
* Kommentar om Altinn og eventuell hensiktsmessighet av å flytte til skyen. Altinn som API-plattform med komponenter på AWS Lambda. Blockchain...
* Men alle nye IT-systemer i det offentlige.....! 
* Blest om frokostseminaret

[1] https://radio.nrk.no/serie/nyhetsmorgen/NPUB50006717/04-04-2017#t=8m53s
[2] TODO: Wikipedia
[3] http://e24.no/makro-og-politikk/mange-faar-ikke-sjekket-selvangivelsen/20176100
[4] TODO: Ekte datakraft i nettskyen
[5] TODO: Alle vil til himmelen

Bilde: http://www.aftenposten.no/100Sport/mesterskap/Det-blir-ikke-OL-i-Oslo-i-2022-179680b.html
