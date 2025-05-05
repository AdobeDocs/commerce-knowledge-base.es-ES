---
title: Reorganizar ramas en la nube en Adobe Commerce
description: En este artículo se explican los pasos que puede seguir para reorganizar las ramas de la nube en Adobe Commerce si no están organizadas según la jerarquía correcta. Si no tiene las ramas organizadas en la jerarquía correcta, no podrá combinar con la rama principal correcta; se dirigirá a la rama principal existente.
exl-id: 4fc0de96-da66-4634-a38a-6a1536855f8f
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Reorganizar ramas en la nube en Adobe Commerce

En este artículo se explican los pasos que puede seguir para reorganizar las ramas de la nube en Adobe Commerce si no están organizadas según la jerarquía correcta. Si no tiene las ramas organizadas en la jerarquía correcta, no podrá combinar con la rama principal correcta; se dirigirá a la rama principal existente.

## Productos y versiones afectados:

* Adobe Commerce en infraestructura en la nube, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Organización de ramas de nube

La organización de jerarquía correcta para sus ramas es:

* [!DNL Master [main] > Production > Staging > Integration]
* [!DNL Master [main] > Production > Staging > Integration2]

## Solución para la organización incorrecta de ramas en la nube

Para reorganizar las ramas de la nube:

1. Debe tener el rol [[!DNL Super User]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=es).
1. Instale la nube de Magento [!DNL CLI] (si aún no lo ha hecho).
1. Ejecute el siguiente comando para las ramas que deben moverse:
   `magento-cloud environment:info -e <branch to move> parent <target parent>`

Nota: Puede especificar la rama principal al crear una nueva rama. Para ver los pasos, consulte [Introducción a la creación de ramas](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/cli-branches) en nuestra documentación para desarrolladores.

Puede crear una nueva rama de entorno usando el comando de entorno de la nube de Magento `branch <environment-name> <parent-environment-ID>`.

Puede llevar algún tiempo adicional crear y activar una nueva rama de entorno.

## Lectura relacionada

[Administre ramas con [!DNL CLI]](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/cli-branches) en nuestra documentación para desarrolladores.
