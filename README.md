![Home Assistant](https://img.shields.io/badge/Home%20Assistant-2026%2B-blue.svg)
![Documentation](https://img.shields.io/badge/Home%20Assistant-Documentation-success.svg)

# Handleiding – Twee Home Assistant-installaties beheren met één telefoon

**Doel:** de Home Assistant van een tweede woning beheren vanuit de bestaande Home Assistant Companion-app, zonder de twee installaties aan elkaar te koppelen.

De handleiding bestaat uit twee delen: eerst de voorbereiding op zijn/haar (eigenaar) Home Assistant en
daarna het toevoegen van zijn installatie aan jouw (beheerder) bestaande Android-app.

De uitgangspunten zijn dat jullie een aantal kilometers uit elkaar wonen, zijn Home Assistant al
op afstand bereikbaar is via Nabu Casa / DuckDNS of een andere aanbieder, ik ga hier uit van Nabu Casa, jij een eigen beheerdersaccount krijgt en beide
installaties volledig gescheiden blijven.
Voor het toevoegen van een tweede server is geen koppeling tussen de twee Home Assistant-installaties nodig.

## 1. Uitgangssituatie

- De eigenaar heeft een eigen Home Assistant-installatie.
- De beheerder heeft eveneens een eigen Home Assistant-installatie.
- De woningen staan een aantal kilometers uit elkaar.
- De Home Assistant van de eigenaar is al op afstand bereikbaar via Nabu Casa.
- De beheerder krijgt een eigen gebruikersaccount met beheerdersrechten.
- Beide installaties blijven volledig zelfstandig.

De bestaande Companion-app op de telefoon van de beheerder wordt uitgebreid met een tweede server. Een tweede app installeren is niet nodig.

---

## DEEL A – Voorbereiding op de Home Assistant van de eigenaar

### Stap 1. Controleer de externe toegang

1. Open de eigen Home Assistant.
2. Controleer of de installatie ook via de externe URL van Nabu Casa bereikbaar is.
3. Test deze URL eventueel via een browser op een telefoon die niet met het thuisnetwerk verbonden is.
4. Controleer of het inloggen met een gebruikersnaam en wachtwoord werkt.

Bewaar de volledige externe URL. Deze is later nodig om de server aan de Companion-app toe te voegen.

**Let op:** gebruik de externe HTTPS-URL van Nabu Casa en niet het lokale IP-adres van de installatie.

### Stap 2. Maak een afzonderlijk beheerdersaccount

De eigenaar maakt een eigen account in Home Assistant voor de beheerder aan.

1. Ga naar **Instellingen → Personen**.
2. Open het tabblad **Gebruikers**.
3. Kies de optie om een gebruiker toe te voegen.
4. Vul een herkenbare gebruikersnaam in.
5. Stel een sterk, uniek wachtwoord in.
6. Schakel de optie **Beheerder (Administrator)** in.
7. Sla de gebruiker op.

De exacte benaming van knoppen kan per Home Assistant-versie verschillen.

Een beheerdersaccount geeft toegang tot de configuratie, integraties, apparaten en systeeminstellingen. De eigenaar houdt zijn eigen account en wachtwoord.

### Stap 3. Controleer de benodigde toegang voor YAML

Beheerdersrechten en toegang tot YAML-bestanden zijn niet precies hetzelfde.

Als de beheerder automatiseringen uitsluitend via de gebruikersinterface maakt, kan hij de beschikbare automatiseringseditor gebruiken.

Voor het bewerken van bestanden zoals `automations.yaml` en `configuration.yaml` is daarnaast een geschikte bestandseditor of andere configuratie toegang nodig. Denk bijvoorbeeld aan File editor of Studio Code Server.

1. Controleer of er al een geschikte editor beschikbaar is.
2. Controleer of de beheerder de configuratiebestanden kan openen en opslaan.
3. Maak vóór ingrijpende wijzigingen een back-up.
4. Test nieuwe configuraties voordat ze in gebruik worden genomen.

Installeer niet onnodig extra add-ons als de bestaande werkwijze al voldoet.

---

## DEEL B – De tweede server toevoegen aan de telefoon

### Stap 4. Open de bestaande Companion-app

1. Pak de Android-telefoon waarop de eigen Home Assistant al werkt.
2. Open de Home Assistant-app.
3. Controleer of de eigen installatie nog normaal bereikbaar is.

Verwijder de bestaande server niet. We voegen uitsluitend een tweede server toe.

### Stap 5. Voeg de server van de eigenaar toe

1. Open **Instellingen**.
2. Ga naar **Companion-app**.
3. Kies **Server toevoegen**.
4. Wacht tot de app eventueel beschikbare servers heeft gevonden.

Omdat de andere woning op afstand staat, is het mogelijk dat de server niet automatisch verschijnt.

5. Kies in dat geval **Adres handmatig invoeren**.
6. Vul de externe HTTPS-URL van de Home Assistant van de eigenaar in.
7. Bevestig de URL.

De officiële documentatie beschrijft deze werkwijze onder *Adding additional servers*.

### Stap 6. Log in met het nieuwe account

1. Vul de gebruikersnaam in die voor jou is aangemaakt.
2. Vul het bijbehorende wachtwoord in.
3. Voltooi de aanmeldprocedure.
4. Geef de server een herkenbare naam als de app daarom vraagt, bijvoorbeeld `Home Assistant – tweede woning`.

Gebruik je eigen accountgegevens van de tweede installatie. Gebruik niet het account van de eigenaar.

### Stap 7. Controleer de verbinding

Controleer of je:

- het dashboard van de tweede woning kunt openen;
- de apparaten en entiteiten kunt bekijken;
- een lamp of andere ongevaarlijke testentiteit kunt bedienen;
- de instellingen kunt openen;
- de automatiseringen kunt bekijken en bewerken;
- de benodigde configuratiebestanden kunt openen als YAML-bewerking gewenst is.

Test ook of de verbinding blijft werken wanneer je telefoon via mobiel internet verbonden is.

---

## DEEL C – Privacy en gescheiden installaties

### Stap 8. Controleer de sensorgegevens van de telefoon

De Companion-app kan sensorgegevens naar Home Assistant sturen, bijvoorbeeld locatiegegevens en informatie over de telefoon.

Omdat de installaties bewust gescheiden blijven, is het verstandig om de gegevensoverdracht naar de tweede server te controleren.

1. Open de Companion-app.
2. Ga naar **Instellingen → Companion-app**.
3. Selecteer de server van de tweede woning.
4. Zoek naar de privacy- of sensorinstellingen.
5. Schakel het verzenden van sensorgegevens uit als die niet nodig zijn.

De precieze opties hangen af van de appversie. Controleer ook eventuele afzonderlijke sensorinstellingen.

### Stap 9. Houd de installaties zelfstandig

De volgende zaken blijven gescheiden:

- apparaten en integraties;
- automatiseringen en scripts;
- dashboards;
- helpers en entiteiten;
- configuratiebestanden;
- back-ups en herstelprocedures.

Een automatisering die op de ene installatie wordt gemaakt, wordt niet automatisch op de andere installatie uitgevoerd.

Wijzigingen aan de tweede woning moeten dus worden aangebracht op de server van die woning.

---

## DEEL D – Een aantal problemen waar je tegenaan kan lopen

| Probleem | Mogelijke oplossing |
|---|---|
| De tweede server wordt niet gevonden | Kies handmatig invoeren en gebruik de externe HTTPS-URL. |
| De URL werkt niet | Controleer Nabu Casa en test de URL via mobiel internet. |
| Inloggen lukt niet | Controleer gebruikersnaam, wachtwoord en of het account actief is. |
| De app toont alleen het eigen huis | Controleer of de tweede server daadwerkelijk is toegevoegd. |
| Ik kan geen YAML-bestanden openen | Controleer of een bestandseditor beschikbaar is en of je toegang hebt tot de configuratiebestanden. |
| De verbinding werkt alleen thuis | Controleer de externe toegang en gebruik de HTTPS-URL. |

---

## Officiële documentatie

1. **Companion-app – Getting Started**  
   https://companion.home-assistant.io/docs/getting_started/

2. **Gebruikers en beheerders**  
   https://www.home-assistant.io/docs/configuration/user-configuration/

3. **Configuratiebestanden bewerken**  
   https://www.home-assistant.io/docs/configuration/


**Resultaat:** één Companion-app op de telefoon, twee afzonderlijke Home Assistant-servers en één beheerder die beide installaties kan onderhouden.

Nog een puntje: de externe URL van Nabu Casa is persoonlijk. De eigenaar hoeft die alleen aan jou te verstrekken om de server toe te voegen; het is niet nodig om zijn wachtwoord met je te delen. Je gebruikt het eigen account dat hij voor je aanmaakt.


## Licentie en gebruiksvoorwaarden

Deze handleiding mag vrij worden gebruikt en aangepast voor eigen gebruik.

Bij het publiceren, verspreiden of delen van deze handleiding, of van geheel of gedeeltelijk daarop gebaseerde aangepaste versies, is bronvermelding verplicht. Daarbij moet de oorspronkelijke auteur worden vermeld en moet, waar redelijkerwijs mogelijk, een verwijzing naar de oorspronkelijke repository worden opgenomen.

Het is niet toegestaan deze handleiding of afgeleide versies als volledig eigen oorspronkelijk werk te presenteren zonder de oorspronkelijke auteur te erkennen.

Deze handleiding wordt aangeboden zonder enige garantie. Gebruik en aanpassing geschieden op eigen risico. Voor zover wettelijk toegestaan aanvaardt de auteur geen aansprakelijkheid voor schade die voortvloeit uit het gebruik of de aanpassing ervan.

