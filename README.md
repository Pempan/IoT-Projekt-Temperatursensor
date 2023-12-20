# IoT-Projekt-Temperatursensor

- Projekt beskrivning
  - Detta projekt syftar till att skapa en IoT-lösning för att mäta och övervaka fuktighetsnivåer med hjälp av en ESP8266-mikrocontroller och Azure-molntjänster. 
   Lösningen kommer att samla in data från en fuktighetssensor och överföra den till Azure IoT Hub för bearbetning och visualisering.

- Projektkomponenter
  - ESP8266-mikrocontroller: Används för att ansluta och samla in data från fuktighetssensorn samt kommunicera med Azure IoT Hub.
    Fuktighetssensor: En sensor som mäter fuktighetsnivåer i omgivningen.
    Azure IoT Hub: En molntjänst som agerar som navet för datainsamling och -hantering. Den tar emot och lagrar data från ESP8266-enheten.
    Azure-molntjänster: Data från fuktighetssensorn kan lagras och visualiseras i Azure, och användaren kan få insikter och övervaka fuktighetsförändringar i 
    realtid.

- Översikt
  ************BILD

- Kopplingsschema
  
  - ESP8266-modul (t.ex., NodeMCU eller Wemos D1 Mini)
  - Fuktighetssensor (t.ex., DHT11 eller DHT22)
  - Anslutningskablar
  - En dator med Arduino IDE installerat
  *********KORT TEXT SAMT BILDER
  
- **Installation**
  - För att installera och använda de nödvändiga biblioteken i Arduino IDE för projektet, följ dessa steg:
    1. Ladda ner och installera den senaste versionen av Arduino IDE från [Arduinos officiella webbplats](https://www.arduino.cc/en/software).
    2. Installera ESP8266-kortpaketet i Arduino IDE genom att lägga till följande URL i inställningarna för ytterligare kortadministratörer: 
       `http://arduino.esp8266.com/stable/package_esp8266com_index.json`.
    3. Installera [Azure SDK för C-biblioteket](https://github.com/Azure/azure-sdk-for-c-arduino). Följande bibliotek kommer också att installeras automatiskt som en del av 
       Azure IoT-biblioteket: `AzureIoTHub`, `AzureIoTUtility`, `AzureIoTProtocol_MQTT`.
    4. Installera [ArduinoJson](https://github.com/bblanchon/ArduinoJson) från Arduino biblioteket.
    5. Installera [PubSubClient](https://github.com/knolleary/pubsubclient) från Arduino biblioteket.

- Uppstart
  - **Användare och temperatursensor:** En användare använder en temperatursensor för att mäta och samla in temperaturdata från omgivningen.

  - **IoT-enhet:** En IoT-enhet, som exempelvis ESP8266 i ditt projekt, fungerar som en datainsamlingsenhet. Den ansluter till temperatursensorn och samlar in 
      temperaturdata       regelbundet.

  - **Kommunikation:** IoT-enheten skickar den insamlade temperaturdatan till Azure IoT Hub. Detta kan göras med hjälp av en säker och pålitlig anslutning för att       
      säkerställa dataintegritet och konfidentialitet.
  - **Datahantering:** Inom Azure IoT Hub hanteras den inkommande temperaturdatan och kan sedan vidarebefordras till andra Azure-tjänster för lagring, bearbetning eller   
      analys, beroende på användningsområdet.

- Konfigurera WiFi-anslutning:
 - För att ansluta din IoT-enhet till ditt WiFi-nätverk, använd följande kod i config.h-filen:
 - Ersätt "Ditt_WiFi_SSID" och "Ditt_WiFi_lösenord" med ditt faktiska WiFi-nätverks SSID (namn) och lösenord.

- Konfigurera Azure IoT Hub-anslutning:
  - För att ansluta din IoT-enhet till Azure IoT Hub, använd följande kod i config.h-filen:
  - Ersätt "Ditt_Azure_IoT_Hub_värddator", "Din_Enhet_ID", och "Din_Enhet_Nyckel" med dina specifika uppgifter från din Azure IoT Hub-konfiguration.
  - När du har uppdaterat dessa inställningar med dina egna värden, är din IoT-enhet redo att ansluta till både WiFi och Azure IoT Hub i ditt projekt.
 


- Cosmos DB
  - Konfigurera en Cosmos DB-databas för att lagra de analyserade sensordata. Med Cosmos DB kan du effektivt och säkert lagra och hantera sensordata i din IoT-lösning. 
    Denna     skalbara och flexibla databastjänst gör det möjligt att enkelt tillgängliggöra sensordata för analys och användning, vilket är avgörande för att optimera din 
    IoT-miljö       och dra nytta av insikterna från dina data.
 
- Azure Storage Integration

  - **Datainsamling:** ESP8266-mikrokontrollenheten samlar in fuktighetsdata från fuktighetsmätaren och förbereder den för överföring.

  - **Azure IoT Hub:** Data överförs från ESP8266 till Azure IoT Hub, som fungerar som en bro mellan enheten och Azure Cloud.

  - **Azure Functions:** Vi använder Azure Functions för att bearbeta de inkommande sensordata och formatera dem enligt våra behov.

  - **Azure Storage:** De bearbetade sensordata sparas i Azure Storage, som erbjuder en pålitlig och skalbar lagringslösning för vår IoT-data.
 

- Azure Functions Integration

  - Datainsamling: ESP8266-mikrokontrollenheten samlar in fuktighetsdata från fuktighetsmätaren och förbereder den för överföring.
  - Azure IoT Hub: Data överförs från ESP8266 till Azure IoT Hub, som fungerar som en bro mellan enheten och Azure Cloud.
  - Azure Functions: En Azure Function aktiveras av inkommande data från IoT Hub. Den tar emot datan, bearbetar den och formaterar den enligt projektets behov.

- Funktionens syfte:

  - Azure Function i detta projekt har följande syfte:
 
  - Data Transformation: Den tar emot rå fuktighetsdata från IoT Hub och omvandlar den till ett mer strukturerat format om det behövs.
  - Data Validation: Funktionen kan utföra validering av inkommande data och verifiera att den är inom de önskade gränserna.
  - Data Lagring: Den sparar den bearbetade datan i Azure Storage för senare åtkomst och analys.
 
- Telegram Integration:
  - Aviseringar: När fuktighetsnivån når en fördefinierad tröskel, genererar Azure Function aviseringar som skickas till en Telegram-bots chattgrupp.
  - Rapporter: Användare kan också begära fukt.
 
- IoT Hub Stream Analytics Integration:
  - Databearbetning: IoT Hub Stream Analytics används för att bearbeta och transformera den inkommande sensordatan från IoT Hub i realtid. Det möjliggör komplexa     
    datahanteringsoperationer, inklusive filtrering, aggregering och tidsbaserade beräkningar.
  - Sensordataanalys: Bearbetad data används för att generera insikter och analyser om fuktighetsnivåerna. Detta kan innefatta att upptäcka avvikelser, identifiera mönster 
    och generera rapporter.
  - Dataexport: Slutligen skickas de analyserade dataresultaten till andra Azure-tjänster, inklusive Azure Storage och Azure Functions, för ytterligare hantering och 
    lagring.


- IoT Hub Stream Analytics Integration:
  - Databearbetning: IoT Hub Stream Analytics används för att bearbeta och transformera den inkommande sensordatan från IoT Hub i realtid. Det möjliggör komplexa       
    datahanteringsoperationer, inklusive filtrering, aggregering och tidsbaserade beräkningar.
  - Sensordataanalys: Bearbetad data används för att generera insikter och analyser om fuktighetsnivåerna. Detta kan innefatta att upptäcka avvikelser, identifiera mönster 
    och generera rapporter.
  - Dataexport: Slutligen skickas de analyserade dataresultaten till andra Azure-tjänster, inklusive Azure Storage och Azure Functions, för ytterligare hantering och 
    lagring.

- Power BI Integration:
  - Datavisualisering: Power BI används för att skapa interaktiva och informativa datavisualiseringar baserade på den insamlade fuktighetsdatan. Detta inkluderar grafer, 
    diagram och anpassade dashboard som ger användaren en översiktlig vy över fuktighetsnivåerna.
  - Real-tidsdatauppdatering: Power BI integreras med Azure IoT Hub för att uppdatera visualiseringarna i realtid när nya mätdatabitar kommer in. Detta möjliggör för 
    användaren att övervaka fuktighetsnivåerna i realtid.
  - Rapportgenerering: Projektet kan generera och dela rapporter baserat på den samlade fuktighetsdatan. Rapporterna kan vara användbara för att fatta beslut, spåra trender 
    och övervaka långsiktiga förändringar i fuktighetsnivåerna.  


-  Förbättrad Säkerhet och Skalbarhet för ESP8266 IoT Fuktighetssensor

  - För att säkerställa en hög nivå av säkerhet i din IoT-lösning med ESP8266 och fuktighetssensor, är det viktigt att implementera flera skyddsåtgärder. Dessa åtgärder är         utformade för att minimera potentiella sårbarheter och stärka den övergripande säkerheten.

- Åtgärder för Förhöjd Säkerhet:
  - Tvåfaktorsautentisering (2FA): Inför tvåfaktorsautentisering för att kräva ytterligare autentiseringssteg utöver lösenord vid åtkomst till IoT-enheten eller         
    hanteringsgränssnittet. Detta förhindrar obehörig åtkomst även om lösenordet skulle komprometteras.
  - Säkerhetskopiering av data: Implementera regelbundna säkerhetskopieringar av sensordata till en säker och isolerad lagringsplats, såsom Azure Storage eller Cosmos DB. 
    Detta garanterar att data inte går förlorad i händelse av en enhetsfel eller säkerhetsincident.
  - Nätverkssäkerhet: Använd brandväggar och nätverksåtgärder, såsom nätverkssegmentering och VLAN, för att isolera och skydda IoT-enheter från potentiella attacker i     
    nätverket.
  - Säker kommunikation: Implementera end-to-end-kryptering för kommunikationen mellan IoT-enheter och molntjänster, inklusive Azure IoT Hub. Detta garanterar att data 
    förblir konfidentiell och inte kan avlyssnas under överföringen.
  - Implementering av MQTTS-protokollet (MQTT Secure): Införa MQTTS-protokollet för att öka säkerheten vid dataöverföring. Genom att införa kryptering i kommunikationen 
    mellan IoT-noder, som Node-MCU ESP8266, och Azure IoT Hub med hjälp av MQTT-protokollet, säkerställs en trygg informationsöverföring och minimerar risken för avlyssning 
    eller obehörig åtkomst.

- Det är viktigt att förstå att de säkerhetsåtgärder som nämndes ovan utgör endast en del av de möjliga åtgärderna som kan implementeras för att stärka säkerheten i din 
  IoT- lösning. Säkerhet är en ständigt pågående process som kräver uppmärksamhet och anpassning till nya hot och sårbarheter.


- Sammanfattning:
  - I detta projekt har en ESP8266-enhet integrerats med en fuktighetssensor för att möjliggöra övervakning och insamling av fuktnivåer i en given miljö. Sensorerna på 
    ESP8266-enheten mäter kontinuerligt fuktnivån och skickar data till Azure IoT Hub för analys och hantering. Informationen om fuktnivåerna lagras säkert i en Cosmos DB- 
    databas för senare åtkomst och användning.

    För att ge användare realtidsinformation och möjliggöra aviseringar har en Telegram-bottjänst implementerats. Denna tjänst skickar meddelanden till användare med 
    relevant information om fuktnivåer och eventuella avvikelser.

    Slutligen möjliggör projektet visualisering av fuktnivådata i realtid med hjälp av Power BI, vilket ger användarna en omfattande lösning för övervakning och analys av 
    fuktighetsförhållanden i den aktuella miljön.  
      


  
    
    







 



























 



















