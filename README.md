# Workflows n8n para ITSI

- **Autor**: Daniel Salas Alonso

Este repositorio contiene una colección de flujos de trabajo de n8n desarrollados como parte de las prácticas del curso ITSI. Los flujos automatizan diversas tareas, como obtener chistes, procesar datos, interactuar con APIs, gestionar tareas a través de RabbitMQ e integrar con Google Sheets y PostgreSQL.

## Estructura del Proyecto

- `workflows/`: Directorio que contiene carpetas de flujos de trabajo (P01 a P08), cada una con archivos JSON que definen flujos de n8n.
- `docker-compose.yaml`: Configuración de Docker Compose para ejecutar n8n con los servicios necesarios.
- `.env`: Archivo de variables de entorno (ignorado en Git).
- `.gitignore`: Especifica archivos a ignorar en el control de versiones.
- `.github/workflows/deploy.yml`: Flujo de trabajo de GitHub Actions para desplegar flujos específicos a producción.

## Prerrequisitos

- Docker y Docker Compose instalados.
- Instancia de n8n ejecutándose (configurada vía Docker Compose).
- Claves de API y credenciales para servicios externos (ej. Google Sheets, PostgreSQL, RabbitMQ) configuradas en `.env`.

## Ejecutando el Proyecto

1. Clona el repositorio.
2. Copia `.env.example` a `.env` y completa las variables de entorno requeridas.
3. Ejecuta `docker-compose up` para iniciar n8n y servicios relacionados.
4. Accede a n8n en `http://localhost:5678` (o el puerto configurado).
5. Importa flujos de trabajo desde el directorio `workflows/` en n8n.

## Resumen de Flujos de Trabajo

- **P01**: Activador manual básico y solicitud HTTP para chistes.
- **P02**: Flujos programados para obtener y categorizar chistes.
- **P03**: Procesamiento de datos e integración con Google Sheets para clasificación de chistes.
- **P04**: Subflujos para validación de productos, procesamiento de imágenes y manejo de errores.
- **P05**: Integración con servicio de gestor de tareas (repositorio externo enlazado en `workflows/P05/README.md`).
- **P06**: Cola de mensajes con RabbitMQ para gestión de tareas.
- **P07**: Resumen de tareas impulsado por IA y evaluación de prioridades usando Gemini.
- **P08**: Creación de tareas basada en webhooks y registro en Google Sheets.

## Despliegue

El flujo `deploy.yml` teoricamente despliega automáticamente cambios en `workflows/P08/Practica08_Guiado.json` en pushes a la rama `main`, utilizando la CLI de n8n.