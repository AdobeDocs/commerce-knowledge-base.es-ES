---
title: "MDVA-13203 patch: 503 error homepage post full reindex"
description: '"El parche de MDVA-13203 Adobe Commerce corrige el problema en el que el sitio muestra una página de mantenimiento y hay errores *CRÍTICO: SQLSTATE\[23000\]: Infracción de restricción de integridad* en system.log". El ID del parche es MDVA-13203. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Parche MDVA-13203: error 503 homepage tras reindexación completa

El parche de MDVA-13203 Adobe Commerce corrige el problema en el que el sitio muestra una página de mantenimiento y hay *CRÍTICO: SQLSTATE\[23000\]: infracción de restricción de integridad* errores en `system.log`. El ID del parche es MDVA-13203. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:** Adobe Commerce en la infraestructura en la nube 2.2.4.

**Compatible con versiones de Adobe Commerce:** Adobe Commerce (todos los métodos de implementación) 2.3.0-2.4.1.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

<u>Pasos a seguir:</u>

1. Vaya a la dirección URL afectada.
1. Verá la página de mantenimiento.
1. Compruebe que el sitio no esté en estado de mantenimiento mediante SSH:
   <pre> mantenimiento de bin/magento:estado
    Estado: el modo de mantenimiento no está activo
    Lista de direcciones IP exentas: ninguna</pre>
1. Mire `system.log`:

<pre>grep critical -i var/log/system.log |cola

[2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Infracción de restricción de integridad: 1062 Entrada duplicada '4613' para la clave 'PRIMARY', consulta: INSERT INTO `search_tmp_5b8ebb4e994da5_88027289` (`entity_id`,`score`) VALUES (?, ?),... (?, ?), (?, ?) [] []
[2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Infracción de restricción de integridad: 1062 Entrada duplicada '4613' para la clave 'PRIMARY', consulta: INSERT INTO `search_tmp_5b8ebb51579943_52333638` (`entity_id`,`score`) VALUES (?, ?),...,(?, ?) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Infracción de restricción de integridad: 1062 Entrada duplicada '1350' para la clave 'PRIMARY', consulta: INSERT INTO `search_tmp_5b8ebb6b7028f4_68065024` (`entity_id`,`score`) VALUES (?, ?), (?, ?), (? , ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Infracción de restricción de integridad: 1062 Entrada duplicada '1350' para la clave 'PRIMARY', consulta: INSERT INTO `search_tmp_5b8ebb6b7885a9_23360993` (`entity_id`,`score`) VALUES (?, ?), (?, ?), (? , ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []

fecha

Martes, 4 de septiembre de 2018, 17:06:11 UTC</pre>

<u>Resultados esperados:</u> Debería ver el sitio.

<u>Resultados reales:</u> La página de mantenimiento se muestra debido a problemas de coherencia de la base de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) en nuestra base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [Parches disponibles en QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) en nuestra documentación para desarrolladores.
