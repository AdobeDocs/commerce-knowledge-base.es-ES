---
title: ¿Puedo instalar aplicaciones de terceros en mi instancia de la nube?
description: No. No se permite la instalación de aplicaciones de terceros (como WordPress o Drupal) en Adobe Commerce en servidores de infraestructura en la nube. Debe alojar dichas aplicaciones en servidores externos.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# ¿Puedo instalar aplicaciones de terceros en mi instancia de la nube?

No. No se permite la instalación de aplicaciones de terceros (como WordPress o Drupal) en Adobe Commerce en servidores de infraestructura en la nube. Debe alojar dichas aplicaciones en servidores externos.

## Razones

### Condiciones del contrato de servicio

Adobe Commerce on cloud Infrastructure Edition [Acuerdo de condiciones de servicio](https://magento.com/legal/terms/cloud-terms) En su artículo 18 dispone lo siguiente:

> El cliente acepta que Adobe Commerce y el Servicio no se utilizarán para alojar otras aplicaciones de software de terceros que no dependan directamente del Software.

Al ser una solución en la nube, el Adobe asume toda la responsabilidad por la seguridad de su servidor. Para garantizar una alta seguridad, solo permitimos el alojamiento de la aplicación de Adobe Commerce en el servidor de nube dedicado.

### Conformidad con PCI

Como proveedor de soluciones de nivel 1 con certificación PCI, Adobe Commerce en la infraestructura en la nube debe seguir el estándar de seguridad de datos PCI y asegurarse de lo siguiente:

>... Desarrollar y mantener sistemas y aplicaciones seguros
> ([Enfoque de Adobe para el cumplimiento de PCI](https://magento.com/pci-compliance) Requisito 6, Mantener un programa de administración de vulnerabilidades)

Dado que el Adobe no puede garantizar la conformidad con PCI de las aplicaciones de terceros, la instalación de dichas aplicaciones en servidores en la nube no está permitida.

## Sugerencia: Utilice extensiones de Commerce Marketplace para mejorar las integraciones

Para mejorar la integración de su aplicación de Adobe Commerce en la infraestructura en la nube con las soluciones de terceros alojadas en servidores externos, le recomendamos que utilice el [Commerce Marketplace](https://marketplace.magento.com) extensiones que pueden adaptarse a su propósito.
