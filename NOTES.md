# Notas del curso

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

El código de votar una opción tiene un pequeño problema. Primero obtiene la opción seleccionada (`selected_choice`) de la base de datos, entonces calcula el nuevo valor de votos y lo vuelve a guardar en la base de datos. Si dos usuarios votan al mismo tiempo _exacto_, esto podría salir mal. Por ejemplo, digamos que el valor de votos es 42. Entonces, para ambos usuarios el nuevo valor de 43 es calculado y guardado, pero 44 sería el esperado.

Esto se conoce como una **_race condition_**. Puedes leer más [aquí](https://docs.djangoproject.com/en/3.0/ref/models/expressions/#avoiding-race-conditions-using-f).

[Seguir tutorial](https://youtu.be/JT80XhYJdBw?t=9380)

## Automated testing

Los tests te ahorrarán tiempo. Ya que te ayudarán a encontrar las causas de errores antes. Si están bien hechos, reforzarán la calidad del código. Porque además de identificar problemas, te ayudan a prevenirlos.
Los tests ayudan a que los equipos trabajen mejor juntos.

`manage.py test polls` busca subclases de TestCase, crea una base de datos especial para _testing_ y luego busca los tests, es decir, aquellos métodos que empiezan con _test_. En el caso del tutorial:
**test_was_published_recently_with_future_question**.

Luego hemos creado algún test más porque es importante asegurarnos de que los métodos que creamos funcionan de la forma esperada, y si dejan de funcionar bien lo sepamos .

### Tests para vistas

Necesitamos herramientas especiales para esto, en este caso:

```shell
>>> from django.test.utils import setup_test_environment
>>> setup_test_environment()
```

Esto instala un _template_ o plantilla que nos permite examinar atributos adicionales en respuestas como `response.context` que de otra forma no estarían disponibles.

Con este trozo de código ya podemos pedirle al _Client_ que haga trabajo por nosotros:

```shell
>>> from django.test import Client
>>> # create an instance of the client for our use
>>> client = Client()
```
