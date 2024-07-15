---
title: "MDVA-30265: el vínculo de seguimiento en el correo electrónico devuelve 404 Página no encontrada"
description: El parche MDVA-30265 soluciona el problema del error "404 Page not Found" (404 página no encontrada) cuando el cliente hace clic en el vínculo de seguimiento de envíos en el correo electrónico de confirmación del pedido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 53e1ca98-dfa0-445b-a71a-56fd01b630ec
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# MDVA-30265: el vínculo de seguimiento en el correo electrónico devuelve 404 Página no encontrada

El parche MDVA-30265 soluciona el problema del error &quot;404 Page not Found&quot; (404 página no encontrada) cuando el cliente hace clic en el vínculo de seguimiento de envíos en el correo electrónico de confirmación del pedido. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 a 2.4.1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una vez creado el envío para un pedido realizado, se envía un correo electrónico al cliente con información de seguimiento y un vínculo para rastrear el pedido. Sin embargo, cuando el cliente hace clic en el vínculo de seguimiento de envío del correo electrónico, se devuelve el error &quot;404 Page not Found&quot;.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce 2.4. Para ver los pasos, consulte [Instalar Adobe Commerce mediante Compositor](https://devdocs.magento.com/guides/v2.4/install-gde/composer.html) en nuestra documentación para desarrolladores.
1. Haga un pedido.
1. Vaya al Panel de administración > **Ventas** > **Pedidos**. Busque el pedido que acaba de crear y ábralo.
1. Cree un envío y añada un número de seguimiento (Transportista = Valor personalizado). Para ver los pasos, consulte [Order Management > Creación de un envío](https://docs.magento.com/user-guide/sales/shipments-create.html) en nuestra guía del usuario.
1. Recibe un correo electrónico. Haga clic en el vínculo de seguimiento para comprobar si funciona.
1. Crear una factura. Para ver los pasos, consulte [Order Management > Creación de una factura](https://docs.magento.com/user-guide/sales/invoice-create.html) en nuestra guía del usuario. A continuación, haga clic de nuevo en el vínculo de seguimiento anterior.

<u>Resultados esperados</u>:

El vínculo de seguimiento debe funcionar incluso después de crear la factura.

<u>Resultados reales</u>:

Después de crear la factura, el vínculo de seguimiento no funciona y devuelve la página de error &quot;404 Page not Found&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
