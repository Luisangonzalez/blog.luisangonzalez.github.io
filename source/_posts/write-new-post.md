title: Escribir nuevo post en hexo.io
tags:
  - Hexo.io
categories:
  - Hexo.io
date: 2016-03-13 19:19:29
---
Para escribir una nueva entrada en [hexo.io](https://hexo.io/) la forma más rápida es:

* En la carpeta raiz del blog hexo.io:

```bash
$ hexo new nombre_post
```

*Se debe de tener en cuenta no incluir espacios en el nombre, para ello utilizar nombre_post y automaticamente lo transforma en nombre-post*

Una vez ejecutado `hexo new nombre_post` se crea un archivo `nombre_post.md` en la carpeta `/source/_post/`

Podemos ver la nueva entrada en blanco lanzando el server: `hexo server` e ir modificando el archivo `nombre_post.md` de nuestra nueva entrada.

En mi caso utilizo [atom.io](https://atom.io/) con el plugin [markdown_preview](https://atom.io/packages/markdown-preview) que permite ver en tiempo real como va quedando el markdown de nuestra entrada.

Cuando ya tenemos nuestra entrada terminada, simplemente generar y desplegar en nuestro bloq:
 ` hexo generate --deploy`
