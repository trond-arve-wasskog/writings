I boka [The Big Switch: Rewiring the World, from Edison to Google](http://www.computerworld.com/article/2534133/infrastructure-management/q-a--nicholas-carr-on--the-big-switch--to-cloud-computing.html) fra 2008 hevdet Nicholas Carr at dataindustrien var inne i en tilsvarende transformasjom som ved etablering av strømnettet for 100 år siden, da industrien faset ut egen energiproduksjon til fordel for elektrisk kraft fra nettet. Mer en ti år etter at AWS lanserte EC2 og S3 som Infrastructure-as-a-Service, er tilgangen på ekte datakraft nå en realitet. _#Serverless_ tjenester i nettskyen er frikoblet fra servere og infrastruktur. Når man ikke lenger forholder seg til infrastruktur elimineres den tradisjonelle basisdriften; _#NoOps_. Dataindustrien går igjen bananas! Og det med god grunn!

# Serverless?
Aller først, to kjernepunkter:
* **_Serverless_-applikasjoner kjører fortsatt på datamaskiner**. Poenget er at hele infrastrukturen er usynlig for applikasjonen; den forholder seg kun til _serverless_-plattformen for å kjøre. Skalering og oppetid håndteres uten at man selv må legge til eller fjerne servere. Betaling baseres på faktisk bruk av tjenesten, eksempelvis tiden den bruker, antall kjøringer eller datavolum. 
* **_Serverless_ er kun mulig i nettskyen** . Joda, store virksomheter med sterke driftsmiljøer vil etablere interne "_serverless_"-plattformer. _Men de må fortsatt håndtere infrastrukturen!!_ Dessuten er vanskelig å se for seg hvordan interne driftsorganisasjoner skal konkurrere med de store nettskyplattformene; [Hvem kan konkurrere med AWS?](https://open.bekk.no/hvem-kan-konkurrere-med-amazon-web-services)?

## Function-as-a-Service (FaaS)
[AWS Lambda](https://aws.amazon.com/lambda/) er den mest kjente _serverless_-plattformen i kategorien _Function-as-a-Service (FaaS)_. Lambda-funksjonen er kun forretningslogikk implementert i Java, Node.js, C# eller Python. Den kan kjøres som resultat av hendelser i AWS-økosystemet, som svar på en forespørsel i en webapplikasjon eller utgjøre kjernefunksjonaliteten i _stream computing_ med Kinesis:
* [Jakten på fem tusen skatteberegninger i sekundet](https://open.bekk.no/jakten-pa-fem-tusen-skatteberegninger-i-sekundet) illustrerer sistnevnte variant med AWS DynamoDB, Kinesis og Lambda for skatteberegning.
* [Jakten på fem tusen KRYPTERTE skatteberegninger](https://open.bekk.no/jakten-pa-5000-krypterte-skatteberegninger) viser hvordan kryptering kan integreres med denne plattformen.
* [Referansearkitektur](https://github.com/awslabs/lambda-refarch-webapp) for en _Single Page App_ lastet fra AWS S3 med som spør direkte mot Lambda-funksjoner via API Gateway ([illustrasjon](https://s3.amazonaws.com/awslambda-serverless-web-refarch/RefArch_BlogApp_Serverless.png)).  

[Google Cloud Functions](https://cloud.google.com/functions/), [Azure Functions](https://azure.microsoft.com/nb-no/services/functions/), [IBM OpenWhisk](https://developer.ibm.com/openwhisk/) og [Auth0 Webtask](https://webtask.io/) er eksempler på FaaS-plattformer fra andre nettskyleverandører. [Fission](http://blog.kubernetes.io/2017/01/fission-serverless-functions-as-service-for-kubernetes.html) ble nylig lansert som en FaaS-plattform på toppen av Kubernetes.

OpenWhisk og Fission er eksempler på FaaS-plattformer man kan kjøre på egen infrastruktur. Dette kan gi mening i en overgangsperiode der man eksperimenterer med og bygger kompetanse på plattformene eller har data og eksisterende systemer man integrerer med som ikke kan flyttes ut i skyen på kort sikt. Imidlertid bør dette benyttes som et steg på veien mot å ta i bruk skyen, ikke som en endestasjon for FaaS i virksomheten.

TODO
* Utvikling, debugging, innsyn, migrering osv. Generelt eller for FaaS?

## Driftede skytjenester (Managed cloud services)
En annen type _serverless_-plattformer er _driftede skytjenester_ eller _managed cloud services_. Dette er tjenester som støtter et spesifikt behov, der skyleverandøren står for basisdriften. Et utmerket eksempel er [Google BigQuery](https://cloud.google.com/bigquery/), som tilbyr et moderne datavarehus i nettskyen med et SQL-API for analyse. Som bruker av BigQuery har du ikke noe forhold til den underliggende infrastrukturen; Google Cloud Platform sørger for skalerbarhet og tilgjengelighet, og du betaler for bruk i form av lagring, _streaming inserts_ og spørringer. En slik driftet skytjeneste passer som hånd i hanske når Skatteetaten ønsker seg en plattform for analyse og scoring; [Skatteetatens analyseplattform i Google Cloud](https://open.bekk.no/skatteetatens-analyseplattform-i-google-cloud).

Et annet illustrerende eksempel er fra [Datainn](https://open.bekk.no/trafikkmeldinger-og-datainn) hos Statens Vegvesen. Her benyttes Elasticsearch for lagring, søk og aggregering av mange milliarder hendelser som representerer kjøretøy som passerer målestasjoner på veinettet i Norge. Sommeren 2016 testet to sommervikarer BigQuery som alternativ til Elasticsearch-clusteret som kjøres på intern infrastruktur. Konklusjonen ble at de samme aggregeringene og rapportene kunne kjøres på litt kortere tid i BigQuery. Og selv om det ikke er det sentrale poenget, havnet disse kjøringene på gratiskvoten i BigQuery; stordata i norsk sammenheng er gjerne ikke store for globale aktører som Google.

TODO: Flere eksempler, S3, GCP, AWS, Azure. En nøkkel er at skalering og betaling ikke skjer på infrastrukturnivå.

## FaaS, BaaS, AaaS, XaaS...
BaaS
Fowler-artikkelen

# NoOps, LessOps, DifferentOps, DevOps?

NoOps - LessOps, DifferentOps
DevOps-gjengen skjelver i buksene

# En titt i krystallkula
Noen spådommer, muligheter
Wardley - recovering management consultant - fra oppfinnelse til industristandard - map
Disruptive - på mange plan
10-15 år
* Serverless er kun mulig i nettskyen.
* Store selskaper vil lage sine egne serverless-plattformer
* DevOps-folka vil tviholde på sin investerte kompetanse
* Serverless tar over verden
* Amazon tar over verden
