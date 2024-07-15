---
title: "MDVA-29148: ArrayBackend no asigna el valor predeterminado al guardar"
description: El parche MDVA-29148 resuelve el problema en el que \Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend no asigna el valor predeterminado al guardar. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
exl-id: 7b2f5c18-0e7a-485b-a07e-700e435697fd
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-29148: ArrayBackend no asigna un valor predeterminado al guardar

El parche MDVA-29148 resuelve el problema en el cual `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` no asigna el valor predeterminado al guardar. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en la infraestructura en la nube 2.3.3-p1.

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) >=2.3.0 &lt;2.4.2.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se crea un producto mediante un script de importación o la API de REST, los atributos que utilizan el modelo back-end `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` y tienen un valor predeterminado no se asignan al valor predeterminado.

<u>Pasos a seguir</u>:

1. Cree un nuevo atributo global que use el modelo backend `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` y un valor predeterminado que no esté vacío.
1. Utilice la API de REST para crear un nuevo producto.
1. Busque ese nuevo producto de la API de REST y confirme que el atributo no está presente en los atributos personalizados del producto.

<u>Resultados esperados</u>:

El valor predeterminado del atributo personalizado se ha guardado en el atributo del producto.

<u>Resultados reales</u>:

El valor predeterminado del atributo personalizado no se ha guardado en el atributo del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
