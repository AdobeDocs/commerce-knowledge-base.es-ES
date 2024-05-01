---
title: 'MDVA-35910: validación de formulario dañada cuando "Iniciar sesión como cliente" está deshabilitado'
description: El parche MDVA-35910 resuelve el problema de que la validación del formulario Crear cuenta de cliente se interrumpe cuando se desactiva la extensión **Iniciar sesión como cliente**. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. El ID del parche es MDVA-35910. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: la validación del formulario se ha interrumpido cuando se deshabilitaba &quot;Iniciar sesión como cliente&quot;

El parche MDVA-35910 resuelve el problema en el que la validación del formulario Crear cuenta de cliente se interrumpe cuando el **Iniciar sesión como cliente** La extensión de está desactivada. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalado. El ID del parche es MDVA-35910. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1-2.4.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas > Configuración > Clientes**. Deshabilitar **Iniciar sesión como cliente** en el Administrador.
1. En **Iniciar sesión como cliente**, configurado **Habilitar extensión** = *No*.
1. Guarde la configuración y vacíe la caché.
1. Vuelva a la tienda y haga clic en **Registrar** (Crear una cuenta de cliente).
1. Rellene el formulario de cuenta y confirme si la validación en **Confirmar correo electrónico** está funcionando o no.

<u>Resultados esperados</u>:

El proceso de creación de cuentas de cliente se completa sin errores.

<u>Resultados reales</u>:

El proceso de creación de la cuenta del cliente no se completa y, en su lugar, aparecen errores de la consola de JavaScript.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
