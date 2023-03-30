# Svelte Documentation

## Bibliotheken
### Web3
- Empfohlene Bibliothek zur Anbindung von Smart Contracts
- Link: https://www.npmjs.com/package/svelte-web3
- Zum Installieren muss folgender Befehl in der Konsole eingegeben werden: ```npm i svelte-web3```
- Im Code wird wie folgt importiert: ```import Web3 from 'web3';```

### Alternative: ether.js
- Es gibt alternativ die Bibliothek ethers
- Link: https://www.npmjs.com/package/ethers
- Wurde allerdings nach mehreren erfolgslosen Versuchen nicht weiter verwendet
- Die Dokumentation ist leider unzureichend um als Anfänger direkt sie anwenden zu können

## Code Aufbau 
- Mithilfe von ```window.ethereum``` wird eine Web3-Instanz erzeugt
- Die Web3-Instanz hat als Methode einen Contract (Konstruktor), siehe nächster Punkt
- ABI des Contracts wurde in einer ```Contract.js``` Datei abgespeichert, in der eine Contract-Instanz des Smart Contracts im Goerli erzeugt wird
- Außerdem wird die Contract-Adress des deployten Smart Contracts zusätzlich zur ABI mitgegeben, um eine Contract-Instanz zu erzeugen
- In einer zusätzlichen Svelte-Datei ```App.svelte``` wird dann die Verbindung mit der Wallet in der Methode ```connectWallet()``` hergestellt. Beispielsweise Metamask
- Einzelne Funktionen des Smart-Contracts können wie folgt aufgerufen werden:
- Lesend: ```await contract.methods.getName().call({
		from: userAddress,
	});```
- Schreibend: ```contract.methods.setName(newUsername).send({
		from: userAddress
	});```
- Mithilfe von Buttons werden die Funktionen aufgerufen und der Nutzer muss die Transaktion mittels des Providers bestätigen (zum Beispiel Metamask)

## Probleme
- Das Testnetzwerk Goerli scheint stellenweise so stark ausgelastet zu sein, dass die Gebühr beispielsweise nur 0,07125 ETH betragen soll und maximal bis zu knapp 13,37 ETH: 
- ![image](https://user-images.githubusercontent.com/73344372/227541541-a44183be-36c7-4389-bd18-d7c950ae5f91.png)
- Zwei Minuten später kostet die folgende Transaktion mit genau denselben Daten und Aufrufen: 
- ![image](https://user-images.githubusercontent.com/73344372/227542160-10571052-30f3-4ec0-9a76-1aebb52b4480.png)
- Aus diesem Grund ist aus Effizienzgründen ein komplettes Frontend nicht möglich aufzubauen (dafür kann gerne das Flutter-Projekt angeschaut werden), da ein Test sowieso nicht möglich ist außer man ist Goerli-Reich
- Aus Dokumentationszwecken noch die Hexadezimaldaten, die man an den Smart-Contract für mehr als 4 ETH senden würde:
- ![image](https://user-images.githubusercontent.com/73344372/227543212-cd7cea24-b996-4a6d-b250-b64be521002f.png)
