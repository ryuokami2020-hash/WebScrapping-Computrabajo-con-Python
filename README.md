Web Scraping de Ofertas Laborales — Computrabajo 🇵🇪

Proyecto universitario desarrollado en Python que automatiza la búsqueda y extracción de ofertas de trabajo del portal Computrabajo Perú, enfocado en puestos de Ingeniero de Sistemas.


¿Qué hace este proyecto?

El programa utiliza Selenium para navegar automáticamente por Computrabajo, acceder a cada oferta de trabajo y extraer la siguiente información:

CampoDescripciónTítuloNombre del puesto de trabajoEmpresaNombre de la empresa empleadoraUbicaciónCiudad o región donde se ofrece el trabajoSalarioRemuneración ofrecida (si está disponible)

Todos los datos recopilados se exportan automáticamente a un archivo CSV, listo para ser analizado en Excel u otras herramientas.


Tecnologías utilizadas


Python 3.x
Selenium — automatización y control del navegador Chrome
WebDriver Manager — instalación y gestión automática del ChromeDriver
csv / os — manejo de archivos (librerías estándar de Python)



Instalación


Clona este repositorio:


bashgit clone https://github.com/ryuokami2020-hash/WebScrapping-Computrabajo-con-Python.git
cd WebScrapping-Computrabajo-con-Python


Instala las dependencias necesarias:


bashpip install -r requirements.txt


Asegúrate de tener Google Chrome instalado en tu equipo.




Uso

Ejecuta el script principal desde la terminal:

bashpython main.py

El programa realizará los siguientes pasos de forma automática:


Abrirá Google Chrome y accederá a Computrabajo
Recopilará los enlaces de todas las ofertas disponibles en la página
Ingresará a cada oferta y extraerá título, empresa, ubicación y salario
Guardará toda la información en el archivo ListaTrabajo.csv



Estructura del proyecto

WebScrapping-Computrabajo-con-Python/
│
├── main.py              # Script principal con la lógica de scraping y exportación
├── requirements.txt     # Dependencias del proyecto
└── README.md            # Documentación del proyecto


Ejemplo de salida (CSV)

Titulo,Empresa,Ubicacion,Salario
Ingeniero de Sistemas,Tech Corp SAC,Lima,S/. 3000 - S/. 4000
Analista de Sistemas,Soluciones IT,Miraflores,S/. 2500


Consideraciones


El scraping depende de la estructura HTML actual de Computrabajo; puede verse afectado si el sitio actualiza su diseño.
Se recomienda no modificar los tiempos de espera (time.sleep) para evitar bloqueos por parte del servidor.
Este proyecto es de uso educativo y respeta los términos de uso del portal.



Autor

iTzRyuta · Proyecto para curso universitario
