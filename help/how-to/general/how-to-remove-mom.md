---
title: Cómo quitar el Magento Order Management (MOM)
description: Este artículo explica cómo quitar el sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Cómo quitar el Magento Order Management (MOM)

1. Deshabilite la integración de MOM siguiendo los pasos indicados en [Desactivar o activar la integración](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration).
1. Deshabilite el módulo MOM siguiendo los pasos indicados en [Desinstalación de módulos](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Para extraer datos de pedidos completos, ofrecemos la API. Para obtener más información, consulte [Ordenar repositorio](https://omsdocs.magento.com/specifications/#magento.sales.order_repository) en nuestro Adobe | Documentos de OMS de Magento, que tratan sobre la información de pedidos (order_repository). Utilice el [sección de especificaciones](https://omsdocs.magento.com/specifications/#services) en nuestro Adobe | Magento OMS Docs para utilizar otras API y extraer distintos tipos de información.
