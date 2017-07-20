title: Hacer un backup de hexo.io
date: 2017-01-27 21:09:31
tags:
  - Hexo.io
categories:
  - Hexo.io
---

Al comenzar a utilizar [hexo.io](https://hexo.io/) lo primero que se me vino a la cabeza fue hacer un backup del tema (personalización, adds, archivos estáticos) así como todos los archivos de configuración y post en markdown.

Así que lo primero que híze fue instalar [hexo-git-backup](https://github.com/coneycode/hexo-git-backup) y la verdad es que una vez configurado funciona**ba** perfectamente.. pero las últimas veces al hacer backup mi hacía un merge de las ramas que utiliza el plugin internamente para funcionar, además al usar el repositorio del blog en otro equipo distinto al habitual su funcionamiento no era el mismo.

Al final, lo más sencillo es lo más eficaz, ahora para hacer un backup tengo dos ramas en el repo del blog, [master](https://github.com/Luisangonzalez/blog.luisangonzalez.github.io) donde se encuentran los archivos estaticos del blog y [backup](https://github.com/Luisangonzalez/blog.luisangonzalez.github.io/tree/backup) donde esta toda la configuración y archivos necesarios en local para utilizar [hexo.io](https://hexo.io/).

De modo que **en local siempre me encuentro en la rama backup, y en github la rama principal es master**.

Lo único a tener en cuenta, es añadir la rama donde se hacen los deploys en el archivo de configuiración:

```yaml
# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:Luisangonzalez/bog.luisangonzalez.github.io.git
  branch: master
  message: New post
```
**Es importante si no se hará el deploy en la rama en la que nos encontramos.**

En definitiva, muchas veces lo mejor es no añadir complejidad innecesaria.
