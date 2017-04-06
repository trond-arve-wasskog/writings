I forbindelse med slippet av skattemeldingen svarer avdelingsdirektør Cat Holten på spørsmål om hvordan Altinn håndterer den store pågangen; "skal vi bygge firefeltsvei til Holmenkollen på grunn av Holmenkollsøndag?"<sup>1</sup>. Metaforen er trolig riktig i denne sammenhengen, men den bryter sammen i møtet med elastiske nettskyplattformer.

Først og fremst; dette er ingen kritikk av Altinn, BankID eller ID-porten. Jeg har stor respekt for kompleksiteten og kostnaden ved å bygge og vedlikeholde IT-løsninger. Selv har jeg ikke jobbet med disse systemene, men vet av erfaring at alle IT-systemer er preget av sin historikk og varierende rammebetingelser over tid. Altinn-portalen ble eksemplevis lansert 4. desember 2003<sup>2</sup>, og er en hjørnestein i offentlige virksomheters kommunikasjon med næringslivet og privatpersoner.

Cat Holten refererer i intervjuet til en uttalelse av skattedirektør Hans Christian Holte i 2016. Ved nærmere undersøkelse ser det ut til at opprinnelsen er daværende informasjonsansvarlig i Altinn, Jørgen Ferkingstad, fra et intervju i mars 2012<sup>3</sup>:
> _Men det går fint an å bygge løsninger som tåler all verdens belastning. Men det blir litt som å bygge en seksfelts motorvei til Holmenkollen for å unngå kø opp dit på Kollensøndag._ 

Oversatt til IT-området; anskaffelse av maskinvare for å håndtere sporadisk topplast og la systemet gå på tomgang resten av året, er å skyte spurv med kanon.

_Elastisitet_ er en av de mest tilgjengelige gevinstene i nettskyen. Framfor å etablere infrastruktur i egen datahall, kan konsum av datakraft reguleres i takt med den faktiske pågangen. Skaleringen overlates til nettskyplattformen slik at behovet for å håndtere topplasten på egen maskinvare faller bort. Serverless-plattformer og driftede nettskytjenester er (foreløpig) siste evolusjonsnivå i frikoblingen fra fysiske servere og infrastruktur <sup>4</sup>. Holmenkollen er hard vare, servere og infrastruktur har blitt mjukvare<sup>5</sup>.

Forutsetningen er at applikasjonene er laget for å skalere og dermed kan utnytte nettskyplattformens elastisitet. Applikasjoner som ble unnfanget for 10 eller 20 år siden er med stor sannsynlighet ikke i denne kategorien. Spørsmålene som melder seg er om det er mulig å oppnå elastisitetsgevinsten ved å ta i bruk nettskyen, om det er hensiktsmessig, og hvordan man eventuelt går fram. Det finnes flere alternative strategier når man flytter eksisterende applikasjoner til nettskyen, og valget av strategi vil påvirke hvilke gevinster man kan oppnå<sup>6</sup>. Kort fortalt vil valget variere for ulike applikasjoner, teknologier og organisasjoner, men sannsynligvis vil man måtte gjøre endringer på applikasjonen for å dra nytte av nettskyplattformens elastisitet. Helt overordnet vil vi gi følgende anbefalinger:
* Det å bruke nettskyen som en forlengelse av egen datahall på IaaS-nivå kan virke naturlig, men viser seg ofte å være komplekst og utfordrende. Man vidererfører i mange tilfeller en kompleks infrastruktur på en ny plattform og man blir stående i spagat mellom to komplekse infrastrukturplattformer. Samtidig begrenser infrastruktur, arkitektur og applikasjonsdesign muligheten til å ta ut gevinster som skalerbarhet, forvaltbarhet og driftbarhet.
* Ved å starte i motsatt ende og designe for nettskyen fra starten av får man erfaring med hvordan arkitektur og applikasjoner best bør realiseres for å ta ut gevinster i nettskyen. Mikrotjenester, API-design, DevOps og kontinuerlig leveranse kan være naturlige områder å å starte med. Målet bør være å komme seg så langt opp i verdikjeden som mulig ved å ta i bruk serverless-plattformer og driftede skytjenester som overlater så mye som mulig av infrastrukturen til nettskyleverandøren. PaaS og CaaS gir større fleksibilitet og flyttbarhet, på bekostning av mer kompleksitet og større forvaltningskostnad. For en eldre monolittisk applikasjon må man lete etter områder som kan rives løs og gradvis migreres over på en skyplattformen. 
* Lokalisering av masterdata blir fort en problemstilling når man tar i bruk nettskyen. Generelt bør data ligge nært applikasjoner som aksesserer dataene i sanntid. Når applikasjonsdomenet ligger i skyen bør også data lever i skyen. Dedikerte nettverkskoblinger mellom nettskyen og egen datahall, speiling og replikering av data er sannsynligvis nødvendig ved migrering eller når applikasjonsporteføljen er splittet mellom intern og ekstern infrastruktur.
* Det kan virke skummelt å gå "all in" og satste på omfattende migrering til en enkelt skyleverandør. Samtidig er det først når du tar i bruk et større spekter av tjenestene på en plattform og bruker de tjenestene som er unike for plattformen at man får de største gevinstene. Vår anbefaling er derfor å ta i bruk en nettskyplattform for det den er verdt, men samtidig ha en tydelig exit-strategi og migreringsplaner som skisserer hvordan man eventuelt skal bytte plattform hvis det blir aktuelt.

TODO wrap it up:
Altinn bør fortsatt ha en rolle i offentlig IT, og Lars Peder Brekk trekker frem mange gode grunner til at man skal satse på statlige digitale plattformer<sup>7</sup>. Selv om etableringen av disse plattformene ikke overlates til markedet, så betyr ikke dette at staten selv bør bygge plattformene "sten for sten" fra bunnen av. En alternativ realiseringsstrategi for neste versjon av Altinn kan være å bygge den på en offentlig tilgjengelig skyplattform og etablere Altinn som en API-plattform som benytter moderne teknologier som AWS Lambda, blockchain, med mer. Ved å gjøre dette kan man dra nytte av de egenskapene og gevinstene som allerede eksisterer på plattformene fremfor å måtte lage disse selv, og man lager en digital plattform på toppen som gir ytterligere gevinster.

* Kommentar om Altinn og eventuell hensiktsmessighet av å flytte til skyen. Altinn som API-plattform med komponenter på AWS Lambda. Blockchain...
* Men alle nye IT-systemer i det offentlige.....! 
* Blest om frokostseminaret

* [1] https://radio.nrk.no/serie/nyhetsmorgen/NPUB50006717/04-04-2017#t=8m53s
* [2] TODO: Wikipedia
* [3] http://e24.no/makro-og-politikk/mange-faar-ikke-sjekket-selvangivelsen/20176100
* [4] TODO: Ekte datakraft i nettskyen
* [5] TODO: Alle vil til himmelen
* [6] http://open.bekk.no/hva-koster-det-a-drifte-i-skyen
* [7] http://www.cw.no/artikkel/hva-andre-mener/hva-andre-mener-tre-grunner-til-satse-pa-statlige-digitale-plattformer

Bilde: http://www.aftenposten.no/100Sport/mesterskap/Det-blir-ikke-OL-i-Oslo-i-2022-179680b.html
