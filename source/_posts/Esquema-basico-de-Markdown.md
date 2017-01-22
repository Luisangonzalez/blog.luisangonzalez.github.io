title: Esquema básico de Markdown
tags:
  - Hexo.io
  - Markdown
categories:
  - Hexo.io
date: 2015-02-23 00:41:00
---
Buenas, aquí un esquema de uso básico de Markdown. Para más información vean la [especificación oficial de su creador John Gruber](http://daringfireball.net/projects/markdown/) o el [ejemplo de Github](https://help.github.com/articles/github-flavored-markdown/).

> 
#### Voy a mostrar primero el código markdown y posteriormente el resultado.

> 
> 
## Texto básico :

##### Código markdown:
```
Cursiva:  *italic* y  así tambien  _italic_ , en  negrita **bold**  y también __bold__ , resaltar  texto : `important` text. signo de porcentaje : % y `%`
Paragrafo con nota de pie (builtin parser only). [^note-id]
Insertar `[ TOC ]` sin espacions genera una tabla de contenidos (builtin parsers only)

```
##### Resultado:

Cursiva:  *italic* y  así tambien  _italic_ , en  negrita **bold**  y también __bold__ , resaltar  texto : `important` text. signo de porcentaje : % y `%`
Paragrafo con nota de pie (builtin parser only). [^note-id]
Insertar `[ TOC ]` sin espacions genera una tabla de contenidos (builtin parsers only)



> 
> 
## Indentación :

##### Código markdown:

```
> Aquí texto indentado
>> aún mas indentado

```

##### Resultado:

> Aquí texto indentado
>> aún mas indentado



> 
> 
## Titulo cabeceras :

##### Código markdown:
```
# El más grande (h1)
## Mediano (h2)
### Pequeño (h3)
#### más pequeno (hX)
##### y más pequeño (hX)
###### y más pequeño.. (hX)
```
##### Resultado:

# El más grande (h1)
## Mediano (h2)
### Pequeño (h3)
#### más pequeno (hX)
##### y más pequeño (hX)
###### y más pequeño.. (hX)


> 
> 
## Listas :

##### Código markdown:
```
- Los puntos/guinoes puedne ser con :  `-`, `+`, or `*`
- Punto uno
- Punto dos 
  - sub item 1
  - sub item 2
Con texto indentado dentro
- Punto de la lista 3
+ Punto de la lista 4
* Punto de la lista 5

1. Punto ordenado uno
2. Punto ordenado dos
...  y así sucesivamente

```
##### Resultado:

- Los puntos/guinoes puedne ser con :  `-`, `+`, or `*`
- Punto uno
- Punto dos 
  - sub item 1
  - sub item 2
Con texto indentado dentro
- Punto de la lista 3
+ Punto de la lista 4
* Punto de la lista 5

1. Punto ordenado uno
2. Punto ordenado dos
...  y así sucesivamente

> 
> 
## Links :

##### Código markdown:
```
Esto es un ejemplo  [de link a mi blog](http://luisangonzalez.es/).
```
##### Resultado:


Esto es un ejemplo  [de link a mi blog](http://luisangonzalez.es/).

> 
> 
## Imágenes :

##### Código markdown:
```
Un simple imagen :
![Fenix logo](http://luisangonzalez.es/img/fenix.jpg "Fenix logo")
```
##### Resultado:

![Fenix logo](http://luisangonzalez.es/img/fenix.jpg "Fenix logo")

> 
> 
## Código :

##### Código markdown:
```
Es sencillo mostrar código en markdown.
Puede hacerse  `highlight` para algunas palabras.
Y bloques de código :
<script>
int cinco = 5;
</script>
En hexo en la línea del principio 3 x ` y 3 x ` al final

```

>
>
##### Resultado:

Es sencillo mostrar código en markdown.
Puede hacerse  `highlight` para algunas palabras.
Y bloques de código :

```
<script>
Ojo en la línea del principio 3 x ` 
document.location = 'http://lmgtfy.com/?q=markdown+cheat+sheet';
 y 3 x ` al final 
</script>
```

> 
> 
## Tablas :

##### Código markdown:
```
| Año  | Mínima temperatura | Máxima temperatura |
| ---- | ------------------ | -------------------|
| 1900 | -10 				|				  25 |
| 1910 | -15 				|                 30 |
| 1920 | -10 				|			      32 |
```
##### Resultado:

| Año  | Mínima temperatura | Máxima temperatura |
| ---- | ------------------ | -------------------|
| 1900 | -10 				|				  25 |
| 1910 | -15 				|                 30 |
| 1920 | -10 				|			      32 |
