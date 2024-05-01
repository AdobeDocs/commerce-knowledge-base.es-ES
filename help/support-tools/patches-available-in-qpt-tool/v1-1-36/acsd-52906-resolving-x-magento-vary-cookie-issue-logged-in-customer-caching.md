---
title: "ACSD-52906: resolviendo el problema de cookie X-Magento-Vary para el almacenamiento en caché de clientes que iniciaron sesión"
description: Aplique el parche ACSD-52906 para corregir el problema de Adobe Commerce en el que la cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: resolución del problema de la cookie X-Magento-Vary para los clientes que iniciaron sesión

El parche ACSD-52906 corrige el problema en el que la cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión. Este parche está disponible cuando la variable [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. El ID del parche es ACSD-52906. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se crea para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con las versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]: Página Buscar Parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión y que pertenecen al mismo segmento de cliente, lo que provoca un almacenamiento en caché incorrecto para algunas páginas.

<u>Requisitos previos</u>:

Los módulos Adobe Commerce Inventory management (MSI) están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Configurar [!DNL Varnish] o [!DNL Fastly] caché.
1. Cree un nuevo segmento de cliente y asígnelo al *Registrados* clientes.
1. Cree dos clientes, por ejemplo, cliente1 y cliente2.
1. Borre la caché.
1. Inicie sesión como cliente1 y vaya a la página de inicio.
1. Abra una página de incógnito en el explorador.
1. Vaya a cualquier página que no sea la página principal.
1. Inicie sesión como cliente2.
1. Vaya a la página principal.
1. Compruebe si la página se almacena en caché en la consola de desarrollo del explorador.

<u>Resultados esperados</u>:

La página se recupera de la caché.

<u>Resultados reales</u>:

La página no se almacena en caché.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en el [!DNL Quality Patches Tool] guía.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce sobre infraestructura en la nube.

## Lectura relacionada

Para obtener más información acerca de [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autogestionar parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce con [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener más información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en el [!DNL Quality Patches Tool] guía.
