<!-- No borrar o modificar -->
[Inicio](./index.md)

## Sesión 4


<!-- Su documentación aquí -->
## Actividad: Resolver utilizando funciones en Python
**Calculadora Básica**: Crea una función llamada calculadora que tome tres argumentos: dos números y un operador (+, -, *, /). La función debe realizar la operación indicada en los dos números y devolver el resultado.

```
def calculadora (operador, a, b):
    if operador == "+":
        result = int(a) + int(b);
    elif operador == "-":
        result = int(a) - int(b);
    elif operador == "*":
        result = int(a) * int(b);
    elif operador == "/": 
        if a > b :
            result = int(a) / int(b);
        else:
            result = int(b) / int(a);
    else:
         result = "el operador no existe"
    return print(result)
```

*Conteo de Vocales*: Crea una función llamada contar_vocales que tome una cadena como argumento y devuelva el número de vocales (a, e, i, o, u) que contiene la cadena.
def contar_vocales (frase):
```
    letras = []
    for letra in frase:
        if letra == "a" or letra == "e" or letra == "i"or letra == "o"or letra == "u":
            letras.append(letra)

    return print("la cantidad de vocales que tienes es de ", len(letras))
  ```
  

**Primo o No Primo**: Escribe una función llamada es_primo que tome un número entero positivo como argumento y determine si es un número primo (es decir, solo es divisible por 1 y por sí mismo). La función debe devolver True si es primo y False si no lo es.
```
def es_primo(numero):
    for n in range(2, numero):
        if numero % n == 0:
            print("No es primo")
            return False
    print("Es primo")
    return True
```
  

**Contador de Palabras**: Escribe una función llamada contar_palabras que tome una cadena como argumento y devuelva el número de palabras en esa cadena. Supón que las palabras están separadas por espacios.

 ```
def contar_palabras (frase):
    palabras = frase.split(" ")
    return print("la cantidad de palabras que tiene es de ", len(palabras))
```
  

**Cálculo de Potencia**: Escribe una función llamada potencia que tome dos números enteros como argumentos, uno como base y otro como exponente, y devuelva el resultado de elevar la base al exponente.

  
```
def potencia(base, exp):
    result = pow(base, exp)
    return print("el resultado de la potencia es ", result)

potencia(3, 5)
  ```





