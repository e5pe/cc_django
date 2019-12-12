# cc_django

Repository for a full crash course on Python Django

## Django administration

Viene directamente con django al crear cualquier proyecto.

Podemos tener varias apps en un proyecto, pudiendo reutilizar partes.

## Views in Django

Esta es la parte 3 del curso.

Todo en Django se considera una *vista*.

Django sólo quiere una respuesta HttpResponse o una *excepción*. Así que podemos generar un PDF, sacarlo como XML, crear un zip al vuelo o lo que queramos, usando las librerías de *Python* que queramos.

Traducción de esto:
`"{% url 'detail' question.id %}/"`

Para la url, usa la función *detail* y pásale el argumento id de *question*.

[Seguir por aquí](https://youtu.be/JT80XhYJdBw?t=6623)