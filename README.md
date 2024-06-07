# 🕹 Game Server en Client

Deze uitwerking laat zien hoe een gameserver en client kunnen samenwerken. De server komt online, waarna gebruikers met de client kunnen:

- **Inloggen (naam + kleur kiezen) `/signin`**
    - Bij inloggen krijgt de speler een ‘id’ waarmee ze zich in het vervolg identificeren.
    - Deze id noemen we ook wel een ‘session id’, maar het staat verder los van sessions in PHP.
- **Bewegen (x en y aanpassen) van eigen speler `/move`**
    - We sturen de player id mee, zodat we kunnen bewijzen aan de server dat we onze eigen speler proberen te verplaatsen.
- **Ophalen van alle spelers en posities `/screen`**
    - De client vraagt de server om de zoveel milliseconden: welke spelers zijn er, en waar zijn ze?
    - De client gebruikt dit om op een HTML Canvas de spelers te tekenen.

1. **De server (server.js) werkt dankzij Node.JS**
    - Node.JS maakt dat het mogelijk is om JavaScript buiten de browser te gebruiken.
    - Vergelijkbaar met Python, die zorgt dat .py python scripts werken.
    - Het online zetten hiervan vereist een VPS (Virtual Private Server) die het script kan uitvoeren, en actief kan houden.

2. **De client (client.html)**
    - Deze zou je beschikbaar maken via je hosting.
    - In de JavaScript in de client.html wordt met `API_URL` aangegeven waar de server is.
    - De client doet verzoeken aan de `/signin`, `/move` en `/screen` ‘endpoints’ in de server.

## Toekomstige verbeteringen

- **Kwetsbaarheid:** de `/screen` endpoint stuurt óók de id’s van alle spelers naar iedereen die daarom vraagt. Dat is een risico, want om iemand te verplaatsen is de player id nodig. Die geheim houden is dus kritisch voor eerlijke werking van de applicatie.
- Na inloggen zou de inlog moeten verdwijnen.
- Na inloggen zou de x en y ‘move’ pas zichtbaar moeten worden.
- De server moet eigenlijk voorkomen dat iemand de server ‘aanvalt’ met veel verzoeken. Nu kan een speler met een loop constant inloggen, daardoor loopt de server vol met informatie (en de verbonden clients ook). Met ‘throttling’ zouden we spelers kunnen blokkeren die te veel verzoeken doen.
- Wat voor verbeteringen kun je zelf nog meer vinden?

## Hoe te gebruiken

1. Installeer Node.JS

2. Open dit project in Visual Studio Code

3. Installeer om de `client.html` te kunnen zien de Live Server extensie in Visual Studio Code

4. Open een terminal in Visual Studio Code en voer het volgende commando uit:

    ```bash
    npm install
    ```

5. Voer het volgende commando uit om de server te starten:

    ```bash
    npm run start
    ```

6. Het bovenstaande zou je ook doen op een echte server, als je dit online wilt zetten.

7. Om de client beschikbaar te stellen zou je de `client.html` kunnen uploaden naar een webserver. Voor nu kun je de Live Server extensie gebruiken om het lokaal te bekijken.

8. Open de `client.html` in je browser en je kunt beginnen met spelen.
