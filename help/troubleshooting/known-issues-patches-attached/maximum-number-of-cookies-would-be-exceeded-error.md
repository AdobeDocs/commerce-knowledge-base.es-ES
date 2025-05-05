---
title: Se superaría el número máximo de cookies por error en Adobe Commerce
description: Obtenga información sobre cómo resolver el problema de Adobe Commerce en el que se produce un error que indica que se superaría el número máximo de cookies.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
source-git-commit: 44e167c801bbcd313f74c9fc51f9cde9473ef96f
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# *Se superaría el número máximo de cookies* error en Adobe Commerce

Este artículo proporciona parches para resolver el error que indica *Se superaría el número máximo de cookies* en Adobe Commerce.

## Productos y versiones afectados

Adobe Commerce (todos los métodos de implementación) 2.4.4 a 2.4.7, con uno de los siguientes parches aplicado:

* Parche MDVA-12304 aplicado con el [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [Parche de seguridad aislado APSB25-08](/help/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08.md)
* [Parches de nube para [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problema

Los problemas relacionados con las cookies en Adobe Commerce están provocando que aparezca el siguiente error en los registros de errores:

*informe.ADVERTENCIA: no se puede enviar la cookie. Se superaría el número máximo de cookies.*

### Causa

El problema ocurre porque el número máximo de cookies permitidas está establecido en *50*.

## Solución

1. Quite el parche MDVA-12304 si lo aplicó usando el [!DNL Quality Patches Tool (QPT)].

   * Para Adobe Commerce en la infraestructura en la nube, quite el parche de `.magento.env.yaml`.
   * Para las instalaciones locales de Adobe Commerce, ejecute el siguiente comando para revertir el parche:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Aplique los parches adjuntos según la versión de Adobe Commerce:

   * Para las versiones 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 y 2.4.7-p4, aplique el [parche ACSD-64710](assets/acsd-64710_2.4.5-p11.patch.zip).

   * Para las versiones 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 y 2.4.8, aplique el [parche ACSD-65562](assets/acsd-65562_2.4.5-p12.patch.zip).

### Lectura relacionada

* [Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-operations/upgrade-guide/patches/apply) en la guía de actualización de Adobe Commerce
* [Prácticas recomendadas para distribuir parches de Adobe Commerce a escala](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) en el manual de implementación de Adobe Commerce
* [Notas de la versión de Commerce Cloud Tools Suite](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) en la Guía de Commerce en la nube.
