---
title: Cambio a OpenSearch para Adobe Commerce en la nube 2.4.4
promoted: true
description: Adobe Commerce en la infraestructura en la nube 2.4.4 no admitirá versiones de Elasticsearch posteriores a la 7.10. **Primero debe actualizar a Adobe Commerce 2.4.4 y luego cambiar inmediatamente de Elasticsearch a OpenSearch 1.2.x.** El Adobe le proporcionará instrucciones detalladas más cerca de la versión Adobe Commerce 2.4.4 GA.
exl-id: 0cb34cee-d4d9-428e-a7fd-7301a86dd8f6
feature: Cloud, Iaas, Paas, Search, Services
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# Cambio a OpenSearch para Adobe Commerce en la nube 2.4.4

Adobe Commerce en la infraestructura en la nube 2.4.4 no admitirá versiones de Elasticsearch posteriores a la 7.10. **Primero debe actualizar a Adobe Commerce 2.4.4 y luego cambiar inmediatamente de Elasticsearch a OpenSearch 1.2.x.** Adobe proporcionará instrucciones detalladas más cerca de la versión de Adobe Commerce 2.4.4 GA.

>[!NOTE]
>
>El cambio debe realizarse independientemente del proveedor de la nube.

Adobe Commerce local añade compatibilidad con Elasticsearch 7.16 y OpenSearch 1.2 en todas las versiones de parches de marzo de 2022 (2.4.4, 2.4.3-p2 y 2.3.7-p3). En 2.4.4, Adobe Commerce en la infraestructura en la nube pasará a OpenSearch como motor de búsqueda predeterminado, por lo que los comerciantes deben utilizar OpenSearch en lugar de Elasticsearch antes de actualizar a Adobe Commerce 2.4.4 o posterior. Los comerciantes con implementaciones locales de Adobe Commerce pueden utilizar Elasticsearch u OpenSearch, ya que Adobe Commerce seguirá admitiendo ambas opciones.


## ¿Qué es OpenSearch?

OpenSearch es una ramificación de Elasticsearch y Kibana. Es mantenido por AWS en lugar de Elastic.com. Para obtener más información, consulte GitHub [opensearch-project/OpenSearch](https://github.com/opensearch-project/OpenSearch).

**Compatibilidad entre versiones:**

**¿Admitirá Adobe Commerce en la infraestructura en la nube la versión 7.10 del Elasticsearch?**

**Sí** : a partir de mediados de enero de 2022, Adobe Commerce en las versiones de infraestructura en la nube 2.4.3-p1, 2.4.3-p2 y 2.3.7-p3 admitirán el Elasticsearch 7.10.

Para Adobe Commerce local, se recomienda la última versión 7.16.x para mitigar Log4j.

## Migración:

## ¿Cuándo pueden migrar los comerciantes a OpenSearch?

Después de Adobe Commerce 2.4.4.

Sin embargo, antes de comenzar el proceso de actualización a Adobe Commerce 2.4.4, los comerciantes deben contar con una versión actual de Adobe Commerce compatible con Elasticsearch 7.10 y contar con al menos un Elasticsearch antes de iniciar el proceso de actualización a Adobe Commerce 2.4.4 o a OpenSearch.

## ¿Qué pueden hacer los comerciantes (Adobe Commerce en la infraestructura en la nube y Adobe Commerce local) que no están en la versión 2.4.4? ¿Pueden actualizar a una versión compatible de Elasticsearch (7.10, 7.16.1) o a OpenSearch? ¿Necesita la última versión compatible para hacerlo (como 2.4.3-p1, 2.3.7-p2, 2.4.3-p1)?

Si la versión principal de Adobe Commerce en la que se encuentran admite Elasticsearch 7.10, pueden utilizarlo.

Revisar [Requisitos del sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) en nuestra documentación para desarrolladores para la compatibilidad de versiones.

>[!NOTE]
>
>Se recomienda planificar la actualización a Adobe Commerce 2.4.4 lo antes posible, ya que el Elasticsearch 7.10 dejará de funcionar en mayo de 2022.

Los socios de Adobe pueden inscribirse en nuestro programa beta [aquí](https://experienceleague.adobe.com/docs/commerce-operations/release/beta-program.html) para obtener acceso al último código beta4 que se ha probado con Elasticsearch 7.16.1 y OpenSearch 1.1.
