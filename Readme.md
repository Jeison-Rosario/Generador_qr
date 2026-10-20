# Generador de códigos QR

Aplicación estática para convertir texto o una URL en un código QR y descargarlo como imagen PNG. Desarrollada con HTML, CSS, JavaScript y QRCode.js.

**[Probar demo](https://jeison-rosario.github.io/Generador_qr/)** · **[Ver portafolio](https://jeison-rosario.github.io/proyectos/)**

## Funcionalidades

- Texto o enlaces como entrada.
- Aviso si la entrada está vacía o contiene solo espacios.
- Código negro sobre fondo blanco de **200 × 200 píxeles**.
- Corrección de errores **H** configurada en QRCode.js.
- Sustitución del resultado al volver a generar.
- Descarga como `codigo-qr.png`.

No crea redirecciones dinámicas ni permite cambiar el contenido de un PNG ya descargado. No requiere cuentas, base de datos, Node.js ni una API de generación.

## Ejecución local

```sh
git clone https://github.com/Jeison-Rosario/Generador_qr.git
cd Generador_qr
```

Abrir `index.html` en un navegador moderno. Opcionalmente, con Python instalado:

```sh
python -m http.server 8000
```

Abrir http://localhost:8000/. No hay instalación de paquetes ni compilación.

## Uso

1. Introducir texto o una URL completa, por ejemplo `https://example.com`.
2. Pulsar **Generar QR**.
3. Esperar a que aparezcan el código y la descarga.
4. Pulsar **Descargar QR**.
5. Escanear el PNG con otro dispositivo para verificar su contenido.

La aplicación comprueba que haya contenido; no valida que la URL exista o sea segura. La lectura depende del lector, la cámara y la calidad de la imagen.

## Funcionamiento y estructura

| Recurso | Uso |
| --- | --- |
| `index.html` | Interfaz y función `generarQR()` |
| `style.css` | Tarjeta, formulario y botones |
| QRCode.js 1.0.0 desde cdnjs | Generación en el navegador |
| Google Tag Manager | Integración incluida en el HTML |

La función vacía el contenedor anterior y construye un `QRCode`. Tras una espera fija de 300 ms busca la imagen o el lienzo generado y configura su enlace de descarga. El flujo actual no controla explícitamente fallos del CDN, contenido que exceda la capacidad de la biblioteca o ausencia de imagen.

La biblioteca necesita conexión para descargarse. La función no envía el texto a una API de QR, pero la página carga scripts de terceros, incluido Google Tag Manager; no se describe como completamente libre de conexiones externas.

## Publicación y comprobación

Puede alojarse en GitHub Pages, conservando `index.html` y `style.css`. La demo no necesita un proceso en alwaysdata.

Comprobar texto, URL HTTPS, entrada vacía, segunda generación y descarga. Escanear tanto la vista como el PNG descargado. Probar acentos y entradas largas antes de garantizar su lectura. Revisar pantallas estrechas: la tarjeta tiene ancho fijo de 320 px más relleno.

No hay pruebas automatizadas incluidas. Esta ampliación se basa en lectura de HTML, JavaScript y CSS; no realizó un escaneo ni una descarga real.

## Mejoras posibles

Ancho adaptable, etiqueta accesible, mensajes de estado, idioma español del documento, separación del JavaScript y manejo de errores. También puede incorporarse exportación a mayor resolución y una política explícita de analítica.

## Autor

[Jeison Rosario](https://github.com/Jeison-Rosario)
