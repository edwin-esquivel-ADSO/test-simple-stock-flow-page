# test-simple-stock-flow-page

> **Prueba técnica · Ficha ADSO 3413974**
> Horario: de **9:00 a. m. a 3:00 p. m.** (15:00)

Este repositorio es el **sitio público estático de presentación** de *Simple Stock Flow*. **Empieza vacío a propósito**: se construye en el fork de cada aprendiz.

## Instrucciones

Cada aprendiz debe **crear el fork** de los seis repositorios del proyecto y **resolver el proyecto
con el spec planteado**.

1. Hacer fork, a su cuenta de GitHub, de cada repositorio de la tabla del final.
2. Leer el spec en [`test-simple-stock-flow-docs`](https://github.com/code-sena/test-simple-stock-flow-docs).
   Se entrega en dos versiones: `spec-python/` y `spec-.net/`.
3. Desarrollar en los forks.

## El reto se desarrolla con React y PHP (Laravel)

El spec está escrito para Python y para .NET, pero el reto **no** se hace en esos lenguajes:

| Capa | Tecnología del reto |
|---|---|
| Frontend | React |
| Backend | PHP con Laravel |

Lo que el spec define sobre el negocio —historias, criterios de aceptación, reglas, contrato de la
API, modelo de datos— se respeta. Lo que define sobre la tecnología se traduce a React y Laravel.

## La prueba no consiste en escribir el código

El propósito principal es ver la **capacidad de desempeño con SDD** (*Spec-Driven Development*,
desarrollo guiado por especificación): cómo se lee, se interpreta y se aplica una especificación
para llevarla a un stack distinto. El código es el medio, no el fin.

## Los seis repositorios

| Repositorio | Qué va ahí |
|---|---|
| [`test-simple-stock-flow-docs`](https://github.com/code-sena/test-simple-stock-flow-docs) | El spec: `spec-python/` y `spec-.net/` |
| [`test-simple-stock-flow-api`](https://github.com/code-sena/test-simple-stock-flow-api) | Backend en PHP (Laravel) |
| [`test-simple-stock-flow-app`](https://github.com/code-sena/test-simple-stock-flow-app) | Frontend en React |
| [`test-simple-stock-flow-page`](https://github.com/code-sena/test-simple-stock-flow-page) | Sitio público estático de presentación |
| [`test-simple-stock-flow-infra`](https://github.com/code-sena/test-simple-stock-flow-infra) | Contenedores, red, volúmenes y motor de base de datos vacío |
| [`test-simple-stock-flow-tool`](https://github.com/code-sena/test-simple-stock-flow-tool) | Utilidades: sembrador de datos de demostración |

---

# Documentación Técnica del Sitio Público — Nivel Senior

## 1. Alcance y Propósito Institucional

`test-simple-stock-flow-page` es el portal comercial y punto de divulgación técnica de *Simple Stock Flow*. Comunica el valor del producto y los fundamentos arquitectónicos implementados:
- Las 3 Afirmaciones Innegociables del negocio (Stock Real, Ventas Inalterables, Reportes Consistentes).
- Características clave (Prevención de sobreventa, Inmutabilidad histórica, Arquitectura Onion).
- Acceso a los repositorios de código fuente y documentación técnica del reto.

---

## 2. Invariante de Red y Desacoplamiento

- **Artefacto 100% Estático:** Construido exclusivamente en HTML5 semántico y CSS3 puro con variables y CSS Grid/Flexbox.
- **Cero Estado del Servidor:** No contiene scripts del lado del servidor ni dependencias de frameworks dinámicos pesados.
- **Independencia Operativa:** No realiza llamadas HTTP directas a endpoints privados de la API, pudiendo ser servido desde cualquier CDN, GitHub Pages o un contenedor Nginx ultraligero.

---

## 3. Despliegue y Visualización

### Modo Local:
Abrir directamente `index.html` en cualquier navegador web moderno, o mediante un servidor HTTP local:
```bash
npx serve .
# o con Python:
python -m http.server 8085
```

### Despliegue en Producción (Docker / Nginx):
Puede servirse mediante una imagen oficial `nginx:alpine`:
```bash
docker run -d -p 8085:80 -v $(pwd):/usr/share/nginx/html:ro --name stockflow-page nginx:alpine
```
Disponible en `http://localhost:8085`.
