# PM2 Commands Reference Guide

Una guía rápida y directa con los comandos esenciales de PM2 para la gestión, monitoreo y persistencia de procesos en entornos de producción.

## ¿Qué es PM2?

PM2 (Process Manager 2) es un gestor de procesos de producción diseñado para aplicaciones Node.js. A diferencia de la ejecución local en desarrollo, PM2 permite que las aplicaciones se ejecuten continuamente en segundo plano, se reinicien automáticamente ante fallos imprevistos y optimicen el uso de los núcleos de la CPU.

## 1. Gestión de Procesos

| Comando | ¿Qué hace? |
| :--- | :--- |
| `pm2 start app.js` | Inicia una aplicación en segundo plano. |
| `pm2 start app.js --name "api"` | Inicia la aplicación asignándole un nombre específico. |
| `pm2 start npm --name "front" -- run start` | Inicia un script empaquetado de npm (común en Next.js o Nuxt). |
| `pm2 start app.js --watch` | Inicia la aplicación y la reinicia automáticamente al detectar cambios en los archivos. |
| `pm2 list` | Muestra el estado actual y la lista de todas las aplicaciones activas. |
| `pm2 stop <id\|name>` | Detiene temporalmente una aplicación específica sin eliminarla de la lista. |
| `pm2 restart <id\|name>` | Detiene y vuelve a iniciar una aplicación específica. |
| `pm2 delete <id\|name>` | Detiene definitivamente y remueve la aplicación del registro de PM2. |
| `pm2 stop all` | Detiene todos los procesos activos simultáneamente. |

## 2. Monitoreo y Diagnóstico

| Comando | ¿Qué hace? |
| :--- | :--- |
| `pm2 logs` | Muestra el flujo de logs combinados en tiempo real. |
| `pm2 logs <id\|name>` | Filtra y muestra únicamente los logs de una aplicación específica. |
| `pm2 logs --lines 50` | Muestra las últimas 50 líneas del historial acumulado de logs. |
| `pm2 flush` | Vacía por completo los archivos de logs para liberar espacio en el almacenamiento. |
| `pm2 monit` | Abre un panel interactivo en la terminal con métricas de uso de CPU y memoria en tiempo real. |

## 3. Escalabilidad y Clusterización

| Comando | ¿Qué hace? |
| :--- | :--- |
| `pm2 start app.js -i max` | Inicia la aplicación en modo Cluster, duplicándola en todos los núcleos de CPU disponibles. |
| `pm2 reload <id\|name>` | Reinicia los procesos del cluster de forma secuencial, garantizando cero tiempo de inactividad para el usuario. |

## 4. Persistencia del Sistema

| Comando | ¿Qué hace? |
| :--- | :--- |
| `pm2 save` | Guarda el listado actual de aplicaciones activas en el disco. |
| `pm2 startup` | Genera y muestra el comando de configuración necesario para que PM2 se inicie automáticamente tras un reinicio del sistema operativo. |
| `pm2 resurrect` | Restaura los procesos previamente guardados con el comando `pm2 save`. |
