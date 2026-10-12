---
title: El nuevo dominio se está redireccionando al dominio predeterminado
description: Este artículo proporciona una solución al problema en el que el nuevo dominio redirige al dominio predeterminado en el entorno existente o diferente.
exl-id: 88e9eb3f-9b82-4ca3-aa80-e49f360b3eb9
feature: Configuration
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%
---
# El nuevo dominio se está redireccionando al dominio predeterminado

Este artículo proporciona una solución al problema en el que el nuevo dominio redirige al dominio predeterminado en el entorno existente o diferente.

## Productos y versiones afectados

* Adobe Commerce en la infraestructura de cloud pro (todas las versiones)

## Problema

El nuevo dominio está redirigiendo al dominio predeterminado en el entorno actual o al dominio predeterminado de otro entorno.

## Causa

Sucede cuando las variables no se actualizan después de agregar un nuevo dominio o cuando se ha configurado el servicio [!DNL Fastly] incorrecto en el entorno.

## Solución

1. Si el dominio se está redireccionando dentro del mismo entorno, asegúrese de haber configurado las [variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#modify-variables).
1. Si el dominio se está redireccionando a otro entorno, compruebe si ha configurado el servicio [!DNL Fastly] correcto ejecutando el siguiente comando: `bin/magento fastly:conf:get -s`

>[!NOTE]
>
>Puede encontrar las credenciales de la API [!DNL Fastly] iniciando sesión en cada entorno (Ensayo/Producción) y comprobando el archivo `/mnt/shared/fastly_tokens.txt`. Para obtener más información, consulte [configure [!DNL Fastly] services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) en la Guía de infraestructura en la nube de Commerce.

Si las dos configuraciones anteriores son correctas, envíe un ticket de asistencia.

## Lectura relacionada

* [Lista de comprobación para configurar un nuevo dominio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/checklist-for-setting-up-a-new-domain.html) en nuestra base de conocimiento de soporte.
