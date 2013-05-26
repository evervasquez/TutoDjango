TUTORIAL - APRENDIENDO EN DJANGO
================================

###1.-ASPECTOS BASICOS DE CONFIGURACION
####a.-Editamos el archivo settings.py de la aplicación
Importamos el modulo `import os` y establecemos la ruta de proyecto:
    
	import os
	RUTA_PROYECTO = os.path.dirname(os.path.realpath(__file__))
		
Establecemos al Administrador

```js
	ADMINS = (
	('eveR Vasquez', 'sonico999@gmail.com'),
		 )
```
Configuramos la base de datos

```js
	DATABASES = {
	'default': {
	'ENGINE': 'django.db.backends.mysql', 
	'NAME': 'sisventa',
	'USER': 'root',
	'PASSWORD': 'admin',
	'HOST': 'localhost',
	'PORT': '3306', 
	            }
		     }
```		
Zona Horaria

```js
	TIME_ZONE = 'America/Lima'
```
Lenguaje

```js
	LANGUAGE_CODE = 'es-PE'
```

Instalamos la aplicación admin

```js
	INSTALLED_APPS = (
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.sites',
	'django.contrib.messages',
	'django.contrib.staticfiles',
        'django.contrib.admin',
			 )
```

###2.-LANZAR LA INTERFAZ DE ADMINISTRACIÓN
Agregamos el código al archivo `'aplicacion'/urls.py` de modo que quede así

```js
	from django.contrib import admin
	admin.autodiscover()
	urlpatterns = patterns('',
        url(r'^admin/', include(admin.site.urls)),
        		      )
```

Sincronizamos la Base de datos
	
	python manage.py syncdb	
	
######NOTA = hasta aqui queda configurado la aplicación en django, de aquí se tratara de manejar modelos, vistas, enviar y recibir datos.


###3.-CONFIGURAR LOS CSS, JS, IMG - ARCHIVOS STATIC
settings.py

* directorio de archivos staticos

```js
		STATICFILES_DIRS = (
    		os.path.join(RUTA_PROYECTO,'static'),
			   )
```

* directorio para plantillas

```js
		TEMPLATE_DIRS = (
    		os.path.join(RUTA_PROYECTO,'plantillas')
				)
```

* Crear carpetas `static, plantillas`, de modo que quede así:
	
	<img src="http://imageshack.us/a/img109/3413/statica.png">

###4.-ENVIO DE PARAMETROS Y RENDERIZAR PLANTILLAS
* view.py

```js
		from django.shortcuts import render_to_response
		from django.template import RequestContext
		# definimos el metodos, para el envio de los css en /static/ se pone el ultimo parametro
		def web(request):
    			titulo = 'Bienvenido a la web del congreso'
    			return render_to_response('index.html', {'title': titulo},context_instance=RequestContext(request))
```
* urls.py

```js
		from webcongreso.view import web
		urlpatterns = patterns('',
    		url(r'^admin/', include(admin.site.urls)),
    		url(r'^$', web),
    		url(r'web/^$', web),
				      )
```
###5.-RECIBIR PARAMETROS EN VISTAS

* Crear archivo `base.html` y `index.html`

	<img src="http://img703.imageshack.us/img703/764/indexlvh.png">
	
	* base.html `{{ STATIC URL}}` - css, js
	
		```
		<link rel="stylesheet" href="{{ STATIC_URL }}css/bootstrap.css">
		<script src="{{ STATIC_URL }}js/fanbox_init.js"></script>
		{% block contenido %}{% endblock %}
		```
	* index.html
		```
		{% extends 'base.html' %}
		{% block contenido %}
		<div>contenido</div>
		{% end block %}
		```

