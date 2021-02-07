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