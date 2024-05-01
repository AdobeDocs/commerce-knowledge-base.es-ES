---
title: "Parche MDVA-33516: error al editar la lista de solicitudes de productos empaquetados"
description: El parche de MDVA-33516 soluciona el problema en el que, al editar el tipo de producto del paquete desde la Lista de solicitudes, se le redirige a una página de error de elemento de la lista de solicitudes. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.
exl-id: 76a16982-f977-4674-b05e-23f4ac355d52
feature: B2B, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Parche MDVA-33516: error al editar la lista de solicitudes de productos empaquetados

El parche de MDVA-33516 soluciona el problema en el que, al editar el tipo de producto del paquete desde la Lista de solicitudes, se le redirige a una página de error de elemento de la lista de solicitudes. Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14 está instalado. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.4

**Compatible con las versiones de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error al editar productos agrupados en la lista de solicitudes.

<u>Requisitos previos</u>:

* B2B está instalado.
* La lista de solicitudes está activada.

<u>Pasos a seguir</u>:

1. Cree un producto agrupado con dos productos simples.
1. Vaya a la página del producto agrupado y haga clic en **Personalizar y agregar al carro de compras** botón.
1. Seleccione una de las opciones del menú desplegable y haga clic en **Añadir a la lista de solicitudes** para crear una nueva lista de solicitudes. Para ver los pasos detallados, consulte [Guía del Usuario del Magento > Mis Listas de Solicitudes > Creación de una lista de solicitudes](https://docs.magento.com/user-guide/customers/account-dashboard-requisition-lists.html#create-a-requisition-list) en nuestra guía del usuario.
1. Vaya a la lista de solicitudes recién creada (Mi cuenta > **Mis listas de solicitudes**).
1. Haga clic en **Ver** botón en el *Acciones* columna.
1. Haga clic en **Editar** botón.

<u>Resultados esperados</u>:<br>

Sin errores.

<u>Resultados reales</u>:

Página &quot;Su personalización&quot;, que contiene una imagen del producto agrupado, el precio y el siguiente mensaje de error:

```
Fatal error: Uncaught Error: Call to a member function isAvailableForCompare() on null in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml:1 Stack trace: #0 /var/www/html/vendor/magento/framework/View/TemplateEngine/Php.php(59): include() #1 /var/www/html/vendor/magento/framework/View/Element/Template.php(271): Magento\Framework\View\TemplateEngine\Php->render(Object(Magento\Catalog\Block\Product\View\AddTo\Compare), '/var/www/html/v...', Array) #2 /var/www/html/vendor/magento/framework/View/Element/Template.php(301): Magento\Framework\View\Element\Template->fetchView('/var/www/html/v...') #3 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1099): Magento\Framework\View\Element\Template->_toHtml() #4 /var/www/html/vendor/magento/framework/View/Element/AbstractBlock.php(1103): Magento\Framework\View\Element\AbstractBlock->Magento\Framework\View\Element   {closure} () #5 /var/www/html/vendor/magento/framework/View/Element/ in /var/www/html/var/view_preprocessed/pub/static/vendor/magento/module-catalog/view/frontend/templates/product/view/addto/compare.phtml
  on line 1
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
