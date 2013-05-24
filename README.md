TUTORIAL - APRENDIENDO EN DJANGO
================================

###1.-ASPECTOS BASICOS DE CONFIGURACION
####a.-Editamos el archivo settings.py de la aplicación
Importamos el modulo `import os` y establecemos la ruta de proyecto:
    
	import os
	RUTA_PROYECTO = os.path.dirname(os.path.realpath(__file__))
		
Establecemos al Administrador

	ADMINS = (
	('eveR Vasquez', 'sonico999@gmail.com'),
		 )
Configuramos la base de datos

	DATABASES = {
	'default': {
	'ENGINE': 'django.db.backends.mysql', 
	'NAME': 'sisventa',
	'USER': 'root',
	'PASSWORD': 'admin',
	'HOST': 'localhost',
	'PORT': '3126', 
	            }
		     }
		
Zona Horaria

	TIME_ZONE = 'America/Lima'

Lenguaje
		
	LANGUAGE_CODE = 'es-PE'

Instalamos la aplicación admin
 		
	INSTALLED_APPS = (
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.sites',
	'django.contrib.messages',
	'django.contrib.staticfiles',
        'django.contrib.admin',
			 )
			
###2.-LANZAR LA INTERFAZ DE ADMINISTRACIÓN
Agregamos el código al archivo 'aplicacion'/urls.py de modo que quede así

	from django.contrib import admin
	admin.autodiscover()
	urlpatterns = patterns('',
        url(r'^admin/', include(admin.site.urls)),
					)
######NOTA = hasta aqui queda configurado la aplicación en django, de aquí se tratara de manejar modelos, vistas, enviar y recibir datos.


