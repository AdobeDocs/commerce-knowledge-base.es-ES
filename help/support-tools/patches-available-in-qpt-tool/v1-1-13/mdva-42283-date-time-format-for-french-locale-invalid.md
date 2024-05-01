---
title: "MDVA-42283: El formato de fecha y hora de la configuración regional en francés no es válido"
description: El parche MDVA-42283 corrige el problema en el que el formato de fecha y hora de la cuadrícula de orden de administración de la configuración regional en francés no es válido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. El ID del parche es MDVA-42283. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
exl-id: 9b470e7b-4b73-4100-9a9d-1a45a5ac628b
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42283: El formato de fecha y hora de la configuración regional en francés no es válido

El parche MDVA-42283 corrige el problema en el que el formato de fecha y hora de la cuadrícula de orden de administración de la configuración regional en francés no es válido. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalado. El ID del parche es MDVA-42283. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El formato de fecha y hora de la cuadrícula de orden de administración de la configuración regional en francés no es válido.

<u>Pasos a seguir</u>:

1. Cree un pedido, un cliente, una página de CMS o un bloque de CMS.
1. Ir a **Administrador** > **Configuración de cuenta** y establezca la configuración regional de la interfaz para el administrador en **Français (Canada)**/**français (Canadá)(fr_CA)** o **Portugués brasileño (pt_BR)**.
1. Observe el valor en la columna de fecha para cualquier orden, envío, nota de crédito, cliente, página de CMS o cuadrícula de bloques de CMS.

<u>Resultados esperados</u>:

La fecha tiene el formato que aparece en la página de edición real de la entidad.

<u>Resultados reales</u>:

El valor de fecha y hora es incorrecto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
