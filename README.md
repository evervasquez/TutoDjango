TUTORIAL ECHO PARA RECORDAR LO QUE VOY APRENDIENDO

1.-ASPECTOS BASICOS DE CONFIGURACION
   a)Archivo settings.py de la aplicación
     	**Importamos el modulo os y establecemos la ruta de proyecto.
		#codigo
		import os
		RUTA_PROYECTO = os.path.dirname(os.path.realpath(__file__))
     	**Establecemos al Administrador
		#codigo
		ADMINS = (
    		('eveR Vasquez', 'sonico999@gmail.com'),
			)
     	**Configuramos la base de datos
		#codigo
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
     	**Zona Horarioa
		#código
		TIME_ZONE = 'America/Lima'

     	**Lenguaje
		#código
		LANGUAGE_CODE = 'es-PE'

	**Instalamos la app admin
 		#código
		INSTALLED_APPS = (
    		'django.contrib.auth',
    		'django.contrib.contenttypes',
    		'django.contrib.sessions',
    		'django.contrib.sites',
    		'django.contrib.messages',
    		'django.contrib.staticfiles',
    		'django.contrib.admin',
				)
2.-LANZAR LA INTERFACE DE ADMINISTRACION
   a)Agregamos el código al archivo 'aplicacion'/urls.py de modo que quede así
		#código
		from django.contrib import admin
		admin.autodiscover()
		urlpatterns = patterns('',
	   ---->url(r'^admin/', include(admin.site.urls)),
					)

NOTA = hasta aqui queda configurado la aplicación en django, de aquí se tratara de manejar modelos, vistas, enviar y recibir datos.


