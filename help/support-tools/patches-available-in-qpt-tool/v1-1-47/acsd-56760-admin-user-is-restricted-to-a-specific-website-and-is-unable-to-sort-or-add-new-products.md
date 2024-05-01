---
title: "ACSD-56760: El usuario administrador está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos"
description: Aplique el parche ACSD-56760 para solucionar el problema de Adobe Commerce en el que el usuario administrador, que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: el usuario administrador está restringido a un sitio web específico y no puede ordenar ni agregar nuevos productos

El parche ACSD-56760 corrige el problema en el que el usuario administrador, que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. El ID del parche es ACSD-56760. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador que está restringido a un sitio web específico y no puede ordenar o agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz.

<u>Pasos a seguir</u>:

1. Crear *2* sitios web.
1. Crear un **[!UICONTROL restricted admin user]** con acceso solo a *1* sitio web.
1. Inicie sesión como **[!UICONTROL restricted admin user]** e intente cambiar las posiciones de los productos en una categoría.

*Caso 1*:

* *2* tiendas.
* *2* categorías raíz, cada sitio web asignado a su propia raíz de categoría.

*Caso 2*:

* *2* tiendas.
* Solo *1* la categoría raíz se ha asignado a ambos sitios web.

<u>Resultados esperados</u>:

* *Caso 1*: el administrador restringido debe poder ordenar los productos dentro de la categoría disponible.
* *Caso 2*: el administrador restringido no puede ordenar productos dentro de la categoría disponible, porque esto también afectará al almacén restringido.

<u>Resultados reales</u>:

* *Caso 1*: el administrador restringido no puede ordenar productos dentro de la categoría disponible.
* *Caso 2*: el administrador restringido puede ordenar los productos dentro de la categoría disponible, lo que afecta a las tiendas restringidas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
