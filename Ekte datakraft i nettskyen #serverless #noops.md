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
En annen type _serverless_-plattformer er _driftede skytjenester_ eller _managed cloud services_. Dette er tjenester som støtter et spesifikt behov, der skyleverandøren står for basisdriften. Et utmerket eksempel er [Google BigQuery](https://cloud.google.com/bigquery/), som tilbyr et moderne datavarehus i nettskyen med et SQL-API for analyse. Som bruker av BigQuery har du ikke noe forhold til den underliggende infrastrukturen; Google Cloud Platform sørger for skalerbarhet og tilgjengelighet, og du betaler for bruk i form av lagring, _streaming inserts_ og spørringer. En slik driftet skytjeneste passer som hånd i hanske når Skatteetaten ønsker seg en plattform for analyse og scoring; [Skatteetatens analyseplattform i Google Cloud](https://open.bekk.no/[skatteetatDataflowens-analyseplattform-i-google-cloud).

Et annet illustrerende eksempel er fra [Datainn](https://open.bekk.no/trafikkmeldinger-og-datainn) hos Statens vegvesen. Her benyttes Elasticsearch for lagring, søk og aggregering av mange milliarder hendelser som representerer kjøretøy som passerer målestasjoner på veinettet i Norge. Sommeren 2016 testet to BEKK-sommervikarer BigQuery (som alternativ til internt Elasticsearch-cluster) for å generere en kompleks rapport med mye data i. Selve oppsettet av spørringene og rapporten var rimelig rett fram etter litt knot med overføring av relativt store datravolumer. Testen viste at de samme aggregeringene og rapporten kunne kjøres på litt kortere tid i BigQuery. Og selv om det ikke er poenget, havnet disse kjøringene på gratiskvoten i BigQuery; stordata i norsk sammenheng er ikke nødvendigvis store for de store nettskyplattformene. Den overordnede konklusjonen er at BigQuery sannsynligvis kan erstatte den interne Elasticsearch-riggen, i alle fall for rapportgenerering, og dermed la Google håndtere infrastruktur, skalering og oppetid.

[Amazon Simple Storage Service (S3)](https://aws.amazon.com/s3/) var kanskje det første eksemplet på en slik driftet skytjeneste, som tilbyr tilnærmet ubegrenset lagring med høy oppetid der man betaler for faktisk bruk. AWS tilbyr i dag en rekke driftede skytjenester, som [DynamoDB](https://aws.amazon.com/dynamodb/), [Kinesis](https://aws.amazon.com/kinesis) og [Rekognition](https://aws.amazon.com/rekognition/). En tjeneste som [Amazon Elasticsearch Service](https://aws.amazon.com/elasticsearch-service/) er en avart der man må forholde seg til CPU-instanser og minne for den driftede skytjenesten. De fleste tjenestene i Google Cloud Platform er også driftede skytjenester, eksempelvis [Cloud Dataflow]() og [Cloud Machine Learning](https://cloud.google.com/ml/). Ikke minst er det verdt å nevne [Cloud Spanner](https://cloud.google.com/spanner/); en relasjonsdatabase som tilbyr både sterk konsistens, horisontal skalerbarhet og høy oppetid (les gjerne [Spanner, TrueTime and the CAP Theorem](https://research.google.com/pubs/pub45855.html)). De andre nettskyplattformene som Azure og IBM tilbyr også en rekke slike skytjenester.

Kjennetegnene for driftede skytjenester er at man ikke forholder seg til infrastrukturen, at tilgjengelighet og skalering håndteres sømløst av skyplattformen, og man betaler for faktisk bruk. I lys av dette er Amazon Elasticsearch Service en umoden skytjeneste. _Platform-as-a-Service_-varianter som [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) og [Azure App Service](https://azure.microsoft.com/nb-no/services/app-service/) når heller ikke helt opp i denne kategorien ettersom man må forholde seg til infrastruktur som CPU og minne. Tilsvarende gjelder for [Google Container Engine (Kubernetes)](https://cloud.google.com/container-engine/) og [Heroku](https://www.heroku.com/). PaaS og CaaS kan imidlertid gi enorm verdi og være bra valg i mange tilfeller, men er ikke ekte _serverless_-plattformer.

## AaaS, BaaS, CaaS...
Gode, gamle IaaS, PaaS og SaaS har blitt supplert med _altmulig_-as-a-Service. _Software-as-a-Service (SaaS)_ som Salesforce og Office 365 er de mest kjente eksemplene på, er forsåvidt driftede skytjenester, men SaaS-begrepet betegner primært produkter. Etterhvert som [alt tilbys som driftede skytjenester](https://en.wikipedia.org/wiki/As_a_service) vil _aaS_-begrepene miste mening. Her er imidlertid noen mer eller mindre etablerte kategorier:
* _AaaS - Authentication as a Service_ omfatter autentisering av brukere, multifaktor-autentisering, _Single Sign-On (SSO)_ og liknende (også kjent som _Identity-as-a-Service_ eller _IDaaS_). BEKK har eksempelvis tatt i bruk [Auth0](https://auth0.com/) for autentisering.
* _BaaS - Backend-as-a-Service_ gir web- og mobilapper tjenester for å lagring og prosessering, i tillegg til funksjonalitet for brukerhåndtering, integrasjon med sosiale medier, push-notifikasjon og andre standard tjenester.
* _CaaS - Containers-as-a-Service_ betegner typisk Docker-containere som abstraksjon for utrulling av applikasjoner, og tilbyr gjerne orkestrering av clustere, tjenesteoppslag, lastbalansering, _fail-over_ og liknende funksjonalitet. _CaaS_ kan ses på som en mellomting mellom PaaS og virtualisering med IaaS. [Kubernetes](https://kubernetes.io/) er den mest kjente orkestreringsplattformen, og tre store nettskyleverandørene tilbyr [Google Container Engine](https://cloud.google.com/container-engine/), [Azure Container Service](https://azure.microsoft.com/en-us/services/container-service/) og [Amazon EC2 Container Service](https://aws.amazon.com/ecs/).

[Serverless Architectures av Mike Roberts/Martin Fowler](https://martinfowler.com/articles/serverless.html) er en grundig gjennomgang av konseptene. *TODO* Men vær oppmerksom på at den mangler litt perspektiv og visjon; serverless vil sannsynligvis bli mer dominerende enn artikkelforfatteren gir inntrykk av.

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
