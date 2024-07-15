---
title: "Parche MDVA-32012: validación de códigos postales de Corea del Sur y Argentina"
description: El parche MDVA-32012 resuelve el problema en el que los códigos postales argentinos y surcoreanos no se validan debido a cambios o variaciones en los formatos de los códigos postales nacionales. Los códigos postales de Corea del Sur ahora deben tener 5 dígitos, mientras que antes eran de 6 dígitos. Los códigos postales argentinos pueden ser numéricos y alfanuméricos. El parche MDVA-32012 significa que estos formatos para valores de código postal se validarán para estos países. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.2 de Adobe Commerce.
exl-id: 9602f50d-6acd-4724-9734-6aeb65393a25
feature: Communications
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Parche MDVA-32012: validación de códigos postales de Corea del Sur y Argentina

El parche MDVA-32012 resuelve el problema en el que los códigos postales argentinos y surcoreanos no se validan debido a cambios o variaciones en los formatos de los códigos postales nacionales. Los códigos postales de Corea del Sur ahora deben tener 5 dígitos, mientras que antes eran de 6 dígitos. Los códigos postales argentinos pueden ser numéricos y alfanuméricos. El parche MDVA-32012 significa que estos formatos para valores de código postal se validarán para estos países. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.9. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.2 de Adobe Commerce.

## Productos y versiones afectados

* El parche se ha diseñado para Adobe Commerce en la infraestructura en la nube 2.3.5.
* El parche también es compatible con las siguientes versiones de Adobe Commerce: Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.0 - 2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La introducción de códigos postales de 5 dígitos de Corea del Sur o de Argentina alfanuméricos genera una advertencia:

*El código postal proporcionado parece no ser válido. Ejemplo: [1234 (si se especificó una dirección argentina alfanumérica)] o [123-456 (si se especificó una dirección surcoreana de 5 dígitos)]. Si cree que es el correcto, puede ignorar este aviso.*

<u>Pasos a seguir</u>:

1. Abra la tienda.
1. Añadir elemento al carro de compras.
1. Proceso de cierre de compra.
1. Añada una nueva dirección con Corea del Sur para el país, introduzca un código postal de 5 dígitos o añada una nueva dirección con Argentina para el país, e introduzca un código postal alfanumérico.
1. Intente guardar.

<u>Resultados esperados</u>:

La dirección debe guardarse sin previo aviso.

<u>Resultados reales</u>:

La dirección de almacenamiento devuelve una advertencia.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
