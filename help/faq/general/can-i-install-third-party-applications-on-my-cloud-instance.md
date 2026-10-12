---
title: ¿Puedo instalar aplicaciones de terceros en mi instancia de la nube?
description: No. No se permite la instalación de aplicaciones de terceros (como WordPress o Drupal) en Adobe Commerce en servidores de infraestructura en la nube. Debe alojar dichas aplicaciones en servidores externos.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%
---
# ¿Puedo instalar aplicaciones de terceros en mi instancia de la nube?

No. No se permite la instalación de aplicaciones de terceros (como WordPress o Drupal) en Adobe Commerce en servidores de infraestructura en la nube. Debe alojar dichas aplicaciones en servidores externos.

## Razones

### Condiciones del contrato de servicio

El Contrato de términos de servicio [Adobe Commerce on cloud Infrastructure Edition](https://magento.com/legal/terms/cloud-terms) establece lo siguiente en su artículo 18:

> El cliente acepta que Adobe Commerce y el Servicio no se utilizarán para alojar otras aplicaciones de software de terceros que no dependan directamente del Software.

Al ser una solución en la nube, Adobe asume toda la responsabilidad de la seguridad de su servidor. Para garantizar una alta seguridad, solo permitimos el alojamiento de la aplicación de Adobe Commerce en el servidor de nube dedicado.

### Conformidad con PCI

Como proveedor de soluciones de nivel 1 con certificación PCI, Adobe Commerce en la infraestructura en la nube debe seguir el estándar de seguridad de datos PCI y asegurarse de lo siguiente:

>... Desarrollar y mantener sistemas y aplicaciones seguros
> ([Enfoque de Adobe para el cumplimiento de PCI](https://magento.com/pci-compliance) Requisito 6, Mantener un programa de administración de vulnerabilidades)

Dado que Adobe no puede garantizar la conformidad con PCI de las aplicaciones de terceros, la instalación de dichas aplicaciones en servidores en la nube no está permitida.

## Sugerencia: Utilice las extensiones de Commerce Marketplace para mejorar las integraciones

Para mejorar la integración de su aplicación de infraestructura de Adobe Commerce en la nube con las soluciones de terceros alojadas en servidores externos, le recomendamos que utilice las extensiones de [Commerce Marketplace](https://marketplace.magento.com) que puedan adaptarse a su propósito.
