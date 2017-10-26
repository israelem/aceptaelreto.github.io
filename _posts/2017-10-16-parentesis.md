---
layout: post
title: Parentesis balanceados
---

Se entiende que una secuencia de caracteres está correctamente equilibrada con respecto a los paréntesis si cada uno de los paréntesis de apertura tiene su paréntesis cerrado. Cuando añadimos otros mecanismos de agrupación (como los corchetes, [ y ] o las llaves, { y }), el equilibrio se da si el número de aperturas de cada símbolo coincide con el de cierres y además se cierran en el orden correcto.

Se trata de implementar un programa que indique si una cadena está correctamente balanceada con respecto a paréntesis, corchetes y llaves.

# Entrada

La entrada consistirá en distintos casos de prueba, cada uno en una línea. Cada línea no tendrá más de 10.000 caracteres.

# Salida

Para cada caso de prueba se indicará si la entrada está correctamente balanceada (se escribirá un simple YES) o hay algún error (NO).

# Entrada de ejemplo

```
({[]})()
Tengase en cuenta (obviamente) que puede haber otros simbolos.
:)
```

# Salida de ejemplo

```
YES
YES
NO
```
# Solución propuesta

``` python
if __name__ == '__main__':
    cadena = [x for x in input() if x in "{}[]()"]
    if len(cadena) % 2 != 0 or len(cadena) == 0:
        respuesta = "NO"
    else:
        respuesta = "YES"
        i = 0
        while i < len(cadena) and respuesta == "YES":
            if cadena[i] in "{[(":
                i += 1
            else:
                if cadena[i - 1] + cadena[i] in "{}" or \
                        cadena[i - 1] + cadena[i] in "[]" or \
                        cadena[i - 1] + cadena[i] in "()":
                    cadena = cadena[:i - 1] + cadena[i + 1:]
                    i -= 1
                else:
                    respuesta = "NO"
    print(respuesta)
```

[Enlace del código](https://github.com/israelem/aceptaelreto/blob/master/codes/2017-10-16-parentesis.py)

[Enlace en aceptaelreto.com](https://www.aceptaelreto.com/problem/statement.php?id=141&potw=1)