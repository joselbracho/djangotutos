# djangotutos

## 1- Serialización con modelo Snippet

- Cada modelo en una app debe tener serializers.py (se crea manual este archivo)
- Se crean los campos que devolvera el JSON.
- Los métodos CRUD se pueden redefinir (son abstractos)
- Posee las validaciones a los métodos CRUD. 

Crear módelos en el shell de python
`python manage.py shell`


```
from snippets.models import Snippet
from snippets.serializers import SnippetSerializer
from rest_framework.renderers import JSONRenderer
from rest_framework.parsers import JSONParser

snippet = Snippet(code='foo = "bar"\n')
snippet.save()

snippet = Snippet(code='print("hello, world")\n')
snippet.save()
```
- @csrf_exempt Omite la validación de cross domain para las vistas
```
@csrf_exempt
```
- El arhivo urls.py de cada aplicación se crea manualmente y se enlaza a ulrs.py del proyecto
- la libreria httpie permite hacer consultas tipo CURL con sintaxis:
`http http://127.0.0.1:8000/snippets/`

## Requests & Responses

- Extienden de `HttpRequest`
- `request.POST` solo maneja form data (en el proyecto todo se esta enviando por body form data cuando es POST)
- `Response` como segundo parametro puede retornar las respuestas 201,404,... status=status.HTTP_201_CREATED
- El decorador en las vistas `@api_view` posee los métodos de la petición `@api_view(['GET', 'POST'])`
