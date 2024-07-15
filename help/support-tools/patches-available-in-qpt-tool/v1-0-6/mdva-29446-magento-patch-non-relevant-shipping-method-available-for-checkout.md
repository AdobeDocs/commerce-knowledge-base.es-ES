---
title: "MDVA-29446: método de envío no relevante disponible para el cierre de compra"
description: El parche MDVA-29446 soluciona el problema en el que un método de envío no aplicable aparece en las opciones del método de envío de pago y, si se selecciona, un mensaje de error "*Operador con dicho método no se encuentra nulo, tarifa plana*". muestra. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Está previsto que el problema se solucione en versiones posteriores de Adobe Commerce.
exl-id: 74de5ec4-1f57-4d63-8fbc-614b23783ee3
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-29446: método de envío no relevante disponible para el pago y envío

El parche MDVA-29446 resuelve el problema en el que un método de envío no aplicable aparece en las opciones del método de envío de pago y, si se selecciona, un mensaje de error &quot;*El transportista con dicho método no encuentra una tarifa plana nula*&quot;. muestra. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6. Está previsto que el problema se solucione en versiones posteriores de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en infraestructura en la nube 2.3.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3-2.4.0.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problemas

Tienes un método de envío que no es aplicable pero que sigue apareciendo en las opciones del método de envío de pago y puedes seleccionar este método de envío no relevante.

<u>Pasos a seguir</u>:

1. Instale el desarrollo limpio 2.3.
1. Activar tarifa plana y definir:

   * Enviar a los países aplicables = *Países específicos*
   * Enviar a países específicos = *Antártida*
   * Mostrar método si no es aplicable = *Sí*

1. Deshabilitar todos los demás métodos de envío.
1. Vaya al front-end y cree un cliente con una dirección de EE. UU.
1. Seleccione un elemento y haga clic en **Agregar al carro**.
1. Haga clic en el carrito y luego en **Continuar con la compra**.

<u>Resultados reales</u>:

1. En la página **Envío**, verá lo siguiente:

   * La tarifa plana es visible
   * La tarifa única es de 0 $
1. Después de que el usuario haga clic en **Siguiente**, recibirá el siguiente error:

*&quot;No se encontró el operador con este método: null, flatrate&quot;*

<u>Resultados esperados</u>:

* El precio del método de envío no es visible si el método de envío no es aplicable.
* El botón **Siguiente** no debe estar activo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
