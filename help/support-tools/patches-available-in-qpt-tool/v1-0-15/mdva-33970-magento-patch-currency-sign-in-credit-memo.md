---
title: "parche de MDVA-33970: inicio de sesión de moneda en nota de crédito"
description: El parche MDVA-33970 resuelve el problema en el que se mostraba un signo de dólar ($) en lugar de la moneda localizada en una nota de crédito. Esto ocurre cuando se utiliza un ámbito **Sitio web** para un atributo **Price**.
exl-id: 47a03067-86ef-4a55-8c21-921781062b53
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# parche de MDVA-33970: inicio de sesión de moneda en nota de crédito

El parche MDVA-33970 resuelve el problema en el que se mostraba un signo de dólar ($) en lugar de la moneda localizada en una nota de crédito. Esto ocurre cuando un **Sitio web** se utiliza un ámbito para un **Precio** atributo.

Este parche está disponible cuando la variable [Herramienta Parches de calidad (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15 está instalado. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:** Adobe Commerce en infraestructura en la nube 2.3.4-p2

**Compatible con las versiones de Adobe Commerce:** Adobe Commerce en infraestructura en la nube y Adobe Commerce local 2.3.4 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Condiciones previas</u>:

Para este ejemplo, se utiliza esta configuración:

* Hay 2 sitios web: cada uno tiene una **Almacenar** y una **Vista de tienda**.
* El **Configuración predeterminada** tiene el dólar de Singapur como **Moneda** (**Tiendas > Configuración > General > Configuración de divisa**):
   * **Moneda base** = *Dólar de Singapur*
   * **Divisa para mostrar predeterminada** = *Dólar de Singapur*
   * **Divisas permitidas** = *Dólar de Singapur*
* **Sitio web 1** tiene un **Configuración predeterminada**.
* **Sitio web 2** tiene el ringgit malasio como **Moneda**:
   * **Moneda base** = *Ringgit malasio*
   * **Divisa para mostrar predeterminada** = *Ringgit malasio*
   * **Divisas permitidas** = *Ringgit malasio*
* Ir a **Tiendas > Símbolos de moneda** y Establecer:
   * **MYR (ringgit malasio)** = *RM*
   * **SGD (dólar singapurense)** = *SGD* (**Usar estándar** = *Comprobado*)
* Algunos **Product** existe.

<u>Pasos a seguir</u>:

1. Crear un **Pedido** desde el **Sitio web 2** (puede configurarlo como Predeterminado para evitar ajustes adicionales).
1. Inicie sesión en **Administrador**.
1. Abra el pedido recién creado.
1. Compruebe que la variable **Símbolo de moneda** = *RM*.
1. Crear un **Factura**.
1. Compruebe que la variable **Símbolo de moneda** = *RM* en la factura.
1. Crear un **Nota de crédito**.
1. Compruebe que la variable **Símbolo de moneda**  ** ** = *RM* en el **Nota de crédito**.
1. Abra el **Notas de abono** pestaña en **Pedido**.
1. Compruebe la **Símbolo de moneda** en la cuadrícula.
1. Abrir **Ventas > Notas de abono**.
1. Compruebe la **Símbolo de moneda** en la cuadrícula.

<u>Resultados esperados</u>:

Se utiliza el símbolo de moneda localizado correcto, según lo esperado.

<u>Resultados reales</u>:

Se utiliza el signo de dólar ($), aunque no esté configurado en la configuración de administración.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos, según el producto de Adobe Commerce:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de Calidad: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en la herramienta QPT, consulte la [Parches disponibles en la herramienta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sección.
