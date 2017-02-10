I boka [The Big Switch: Rewiring the World, from Edison to Google](http://www.computerworld.com/article/2534133/infrastructure-management/q-a--nicholas-carr-on--the-big-switch--to-cloud-computing.html) fra 2008 hevdet Nicholas Carr at dataindustrien var inne i en tilsvarende transformasjom som ved etablering av strømnettet for 100 år siden, da industrien faset ut egen energiproduksjon til fordel for elektrisk kraft fra nettet. Mer en ti år etter at AWS lanserte Infrastructure-as-a-Service er tilgangen på foredlet datakraft nå en realitet. _#Serverless_ tjenester i nettskyen er frikoblet fra servere og infrastruktur. Når man ikke lenger forholder seg til infrastruktur elimineres den tradisjonelle basisdriften; _#NoOps_. Dataindustrien går igjen bananas! Og det med god grunn!

# Serverless?
Aller først, to banale poenger (TODO):
* **_Serverless_-applikasjoner kjører fortsatt på datamaskiner**. Poenget er at hele infrastrukturen er usynlig for applikasjonen; den forholder seg kun til _serverless_-plattformen for å kjøre. Skalering og oppetid håndteres uten at man selv må legge til eller fjerne servere. Betaling baseres på faktisk bruk av tjenesten, eksempelvis tiden den bruker, antall kjøringer eller datavolum. 
* ** Serverless er kun mulig i nettskyen** . Joda, store virksomheter med sterke driftsmiljøer vil etablere interne "_serverless_"-plattformer. _Men de må fortsatt håndtere infrastrukturen!!_ Dessuten er det umulig for interne driftsorganisasjoner å konkurrere med de store nettskyplattformene; [Hvem kan konkurrere med AWS](https://open.bekk.no/hvem-kan-konkurrere-med-amazon-web-services)?

[AWS Lambda](https://aws.amazon.com/lambda/) er den mest kjente _serverless_-plattformen i kategorien _Function-as-a-Service (FaaS)_. Lambda-funksjonen kan være ren forretningslogikk implementert i Java, Node.js, C# eller Python. Den kan kjøres som resultat av hendelser i AWS-økosystemet, som svar på en forespørsel i en webapplikasjon eller utgjøre hjernen i _stream computing_ med Kinesis:
* [Jakten på fem tusen skatteberegninger i sekundet](https://open.bekk.no/jakten-pa-fem-tusen-skatteberegninger-i-sekundet) illustrerer sistnevnte variant med AWS DynamoDB, Kinesis og Lambda for skatteberegning.
* [Jakten på fem tusen KRYPTERTE skatteberegninger](https://open.bekk.no/jakten-pa-5000-krypterte-skatteberegninger) viser hvordan kryptering kan integreres med denne plattformen.
* [Referansearkitektur](https://github.com/awslabs/lambda-refarch-webapp) for en _Single Page App_ lastet fra AWS S3 med som spør direkte mot Lambda-funksjoner via API Gateway ([illustrasjon](https://s3.amazonaws.com/awslambda-serverless-web-refarch/RefArch_BlogApp_Serverless.png)).  

[Google Cloud Functions](https://cloud.google.com/functions/), [Azure Functions](https://azure.microsoft.com/nb-no/services/functions/), [IBM OpenWhisk](https://developer.ibm.com/openwhisk/) og [Auth0 Webtask](https://webtask.io/) er eksempler på FaaS-plattformer fra andre skytjenester.

## Driftede skytjenester - Managed services
DataInn

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
