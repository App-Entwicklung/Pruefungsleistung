# Flutter Documentation

## Grundlagen
- Mobiles App-Entwicklungs-Framework
- Programmiersprache: Dart
- Widget-basiertes UI-Framework: Jede Komponente in einer App wird als Widget betrachtet
- Bietet eine umfangreiche Sammlung von Material Design-Widgets und Templates z.B.:
    - [Material Components Widgets](https://docs.flutter.dev/development/ui/widgets/material)
    - [Flutter-Templates etc.](https://github.com/Solido/awesome-flutter)

## Views
### Chat View
- Stellt eine Chat-Ansicht dar
- Über ```sendMessage()``` können neue Nachrichten in die Ansicht hinzugefügt werden, wenn der Inhalt der Nachricht nicht leer ist
### Chat Overview
- Ansicht mit allen aktuellen Chat-Views
- In jeder Chat-Card ist der Name, Datum und die letzte Nachricht angegeben


##  MetaMask Anbindung in Flutter
### flutter_web3 package 
- Mit ```flutter_web3``` können Funktionen für die Interaktion mit der Ethereum-Blockchain über die Web3-Browser-Provider bereitgestellt werden
- Installieren mit ```flutter pub add flutter_web3```
- Importieren mit ```import 'package:flutter_web3/flutter_web3.dart'```
- Link: https://pub.dev/packages/flutter_web3

### Methoden
-  ```isEnabled``` - gibt zurück, ob das Ethereum -Plugin aktiviert ist oder nicht
-  ```isInOperatingChain``` - gibt zurück, ob der Benutzer auf der Goerli-Testnetzwerk-Chain aktiv ist
- ```isConnected``` - gibt zurück, ob der Benutzer mit einer Ethereum-Adresse verbunden ist
- ```connect()``` - Methode, die aufgerufen wird, um den Benutzer mit MetaMask zu verbinden. 
- ```requestAccount()``` - Methode auf, um die Ethereum-Adresse des Benutzers abzurufen
- ```getChainId()``` - Methode, um die ID der aktuellen Chain abzurufen

## Probleme
- SendTransaction wirft dauerhaft den Fehler -32000 mit msg "insufficient funds" oder ähnliches (trotz genügend funds)
  - Paralelle Erstellung von Svelte-Frontends zum Ausprobieren von anderen Libraries und Frameworks
    - ethers: funktioniert nicht, Doku nicht passend zum aktuellen Stand
      - funktioniert doch => Doku auf dem Stand von v5, aber v6 aktuell
    - web3: funktioniert nicht, Doku nicht passend zum aktuellen Stand
    - klassische JavaScript-Varianten laufen auch nicht
  - Deployment auf anderem Testnet
    - nichtssagende RPC-Error-Messages
  - andere RPC-Endpunkte ausprobiert
    - andere Fehlermessages, selbes Problem
- web3dart seit Februar 2022 nicht mehr maintained, aber keine alternative
- MetaMask supported vieles nicht mehr



