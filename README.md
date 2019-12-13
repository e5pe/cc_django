# cc_django

Repository for a full crash course on Python Django

## Part 2

### Django administration

Viene directamente con django al crear cualquier proyecto.

Podemos tener varias apps en un proyecto, pudiendo reutilizar partes.

## Part 3

### Views in Django

Esta es la parte 3 del curso.

Todo en Django se considera una _vista_.

Django sólo quiere una respuesta HttpResponse o una _excepción_. Así que podemos generar un PDF, sacarlo como XML, crear un zip al vuelo o lo que queramos, usando las librerías de _Python_ que queramos.

Traducción de esto:
`"{% url 'detail' question.id %}/"`

Para la url, usa la función _detail_ y pásale el argumento id de _question_.

[Seguir por aquí](https://youtu.be/JT80XhYJdBw?t=6623)

### [Namespacing URL names](https://docs.djangoproject.com/en/3.0/intro/tutorial03/#namespacing-url-names)

Es importante meter los templates en una carpeta separada para que luego no colisionen. Porque ahora en el tutorial hay una app pero podrían haber 5, incluso más. Por eso hemos cambiado esto:
`<li><a href="{% url 'detail' question.id %}">{{ question.question_text }}</a></li>`

a esto:
`<li><a href="{% url 'polls:detail' question.id %}/">{{question.question_text}}</a></li>`

## Generic Views

[Seguir tutorial](https://youtu.be/JT80XhYJdBw?t=6902)

Vamos a añadir un form al que le vamos a añadir información.

`{% csrf_token %}` es Cross Site Request Forgeries. Se usa para comprobar que vengan las peticiones del front al back, no de otro medio. En resumen, todos los forms de tipo POST tienen que se dirigan a urls internas deben usar el _tag_ `{% csrf_token %}`.

_action_ is what appens when you submit a form.

[Seguir tutorial](https://youtu.be/JT80XhYJdBw?t=8199)
