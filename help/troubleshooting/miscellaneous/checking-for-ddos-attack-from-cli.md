---
title: Comprobación de ataques DDoS desde CLI
description: Este artículo trata sobre el problema de cómo intentar comprobar si hay ataques de denegación de servicio (DDoS) distribuidos desde la interfaz de línea de comandos (CLI) del servidor.
exl-id: dfdef289-cf51-42d7-b3fb-d4d2d3760951
feature: Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Comprobación de ataques DDoS desde CLI

Este artículo trata sobre el problema de cómo intentar comprobar si hay ataques de denegación de servicio (DDoS) distribuidos desde la interfaz de línea de comandos (CLI) del servidor.

## Productos y versiones afectados

* Adobe Commerce, todas las versiones
* Magento Open Source, todas las versiones

## Problema

Su sitio web es lento y no tiene acceso a ninguna otra herramienta de aplicación de análisis, aparte de su CLI, para comprobar si hay un posible ataque DDoS. Los síntomas de un ataque DDoS pueden variar ampliamente según la configuración de su red, el software utilizado, etc.

Sin embargo, se recomienda utilizar productos de software de análisis diseñados específicamente para ayudar a identificar ataques DDoS.

## Causa

Existen varias causas posibles para un sitio web lento, como un servidor de rendimiento lento, un uso elevado de la CPU o una configuración incorrecta en scripts, código o hardware barato. A veces podría deberse a un ataque DDoS. Dos de las herramientas básicas que tiene que comprobar para un ataque DDoS son sus registros de Adobe Commerce y su CLI.

Una vez más, es importante tener en cuenta que el uso de software específicamente diseñado para identificar ataques DDoS sería muy útil en su investigación.

## Pasos de solución

1. Compruebe sus registros de Adobe Commerce para ver si se está produciendo algo más que un ataque DDoS. Para obtener más información, consulte los siguientes artículos en nuestra documentación para desarrolladores:
   * [Adobe Commerce y ubicaciones de registros de Magento Open Source](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/cli/enable-logging)
   * [Adobe Commerce en la nube registra ubicaciones](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/log-locations)
1. Empiece a usar la CLI para comprobar todas las conexiones a Internet actuales mediante el comando `netstat`: `netstat -na`. Muestra todas las conexiones establecidas activas con el servidor. En este caso, es posible que pueda observar demasiadas conexiones procedentes de la misma dirección IP.
1. Para reducir aún más los resultados de las conexiones establecidas a sólo las que se conectan en el puerto 80 (el puerto http del sitio web), de modo que pueda ordenar y reconocer demasiadas conexiones desde una dirección IP o grupo de direcciones IP, utilice este comando: `netstat -an | grep :80 | sort`. Puede repetir el mismo comando para https en el puerto 443: `netstat -an | grep :443 | sort`. Otra opción es extender el comando original a los puertos 80 y 443: `netstat -an | egrep ":80|:443" | sort`.
1. Para ver si hay varios `SYNC_REC` activos en el servidor, use el comando:     `netstat -n -p|grep SYN_REC | wc -l`     Esto suele ser inferior a 5, pero podría ser mucho mayor para un ataque DDoS, aunque para algunos servidores un número mayor podría ser una condición normal.
1. Para enumerar todas las direcciones IP que envían estados de `SYNC_REC`, use el comando: `netstat -n -p | grep SYN_REC | sort -u`.
1. Para obtener una lista adicional de todas las direcciones IP únicas que envían los estados de `SYNC_REC`, use el comando: `netstat -n -p | grep SYN_REC | awk ‘{print $5}’ | awk -F: ‘{print $1}’`.
1. También puede usar el comando `netstat` para contar y calcular el número de conexiones que cada dirección IP realiza al servidor: `netstat -ntu | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Para enumerar el número de conexiones de protocolo UDP o TCP conectadas al servidor, use el comando: `netstat -anp |grep ‘tcp|udp’ | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -n`.
1. Para comprobar las conexiones establecidas, en lugar de sólo todas las conexiones, y mostrar el recuento de conexiones para cada dirección IP, utilice el comando: `netstat -ntu | grep ESTAB | awk ‘{print $5}’ | cut -d: -f1 | sort | uniq -c | sort -nr`.
1. Para mostrar los recuentos de conexiones enumerados por dirección IP al puerto 80, use el comando: `netstat -plan|grep :80|awk {‘print $5’}|cut -d: -f 1|sort|uniq -c|sort -nk 1`.

Asegúrese de que tiene a alguien para dar el análisis adecuado a los datos que encuentra para determinar si realmente está teniendo un ataque DDoS. El uso de los comandos `netstat` de la CLI de su servidor en los pasos anteriores le ayudará a analizar si está experimentando un ataque DDoS, pero el uso de productos de análisis de software diseñados específicamente para ayudar a identificar ataques DDoS, junto con un análisis adecuado, son las mejores herramientas para identificar amenazas DDoS.

Si encuentra que está bajo ataque DDoS, los pasos que puede seguir dependen de la configuración de su red y de cómo se esté produciendo el ataque DDoS, pero el consejo general es ponerse en contacto con su ISP, obtener una nueva dirección IP para su servidor y/o consultar a profesionales de TI expertos en el manejo de problemas DDoS para analizar y aconsejar sobre su situación particular.

## Lecturas relacionadas en nuestra documentación para desarrolladores:

* [Protección DDoS](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/cdn/fastly#ddos-protection)
* [Uso de comandos CLI](https://experienceleague.adobe.com/es/docs/commerce-operations/configuration-guide/deployment/examples/example-using-cli)
* [CLI de nube para Commerce](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-overview)
