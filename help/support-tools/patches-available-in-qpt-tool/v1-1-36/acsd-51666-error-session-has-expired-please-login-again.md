---
title: 'ACSD-51666: Error "La sesión ha caducado, vuelva a iniciar sesión". después de iniciar sesión'
description: Aplique el parche ACSD-51666 para solucionar el problema de Adobe Commerce donde el error * La sesión ha caducado, vuelva a iniciar sesión.* se produce después de intentar iniciar sesión.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666: error *La sesión ha caducado. Inicie sesión de nuevo.* después de iniciar sesión

El parche ACSD-51666 corrige el problema donde el error *La sesión ha caducado. Inicie sesión de nuevo.* se produce después de intentar iniciar sesión. Este parche está disponible cuando la variable [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.36 está instalado. El ID del parche es ACSD-51666. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se obtiene el error *La sesión ha caducado. Inicie sesión de nuevo.* al intentar iniciar sesión con la nueva contraseña desde un dispositivo después de restablecer la contraseña en otro dispositivo. Solo sucede si hay una solicitud de Ajax adicional en la página agregada por un módulo personalizado.

<u>Pasos a seguir</u>:

1. Instale un módulo personalizado que agregue una solicitud de Ajax a todas las páginas de la tienda.
1. Cree una nueva cuenta.
1. Cierre la sesión y vuelva a la página de inicio de sesión.
1. Abra el *Contraseña olvidada* en un navegador diferente y envíe el *Restablecer contraseña* correo electrónico.
1. Abra el correo electrónico para restablecer la contraseña en el primer explorador y establezca la nueva contraseña.
1. Intente iniciar sesión en el segundo explorador.

<u>Resultados esperados</u>:

Puede iniciar sesión correctamente en el primer intento.

<u>Resultados reales</u>:

* Verá el *La sesión ha caducado. Inicie sesión de nuevo.* error.
* No ha iniciado sesión ni se le ha redirigido a la página principal.
* El segundo intento de iniciar sesión se ha realizado correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
