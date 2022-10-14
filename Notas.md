
# Explicacion codigo de python


## rstrip()
Quita los espacion del final de una cadena en esta caso se usa para generar una lista

![image](https://user-images.githubusercontent.com/63270579/195608543-e5e91337-2f01-4900-b7c4-b12c254b3332.png)

>https://stackoverflow.com/questions/7984169/remove-trailing-newline-from-the-elements-of-a-string-list

## lista

Fijate como se crea una lista el codigo comentado es lo mismo que el de abajo desglosado


## Python Get Current time

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












