---
title: Cómo quitar el Magento Order Management (MOM)
description: Este artículo explica cómo quitar el sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 77f41d6034f985794e5c5b89cc007a69858683b9
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Cómo quitar el Magento Order Management (MOM)

1. Deshabilite la integración de MOM siguiendo los pasos de [Deshabilite o habilite la integración](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Deshabilite el módulo MOM siguiendo los pasos de [Desinstalar módulos](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
1. Para extraer datos de pedidos completos, ofrecemos la API. Puede obtener más información revisando [Repositorio de pedidos](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) en nuestro Adobe | Documentos de OMS de Magento, que tratan sobre la información de pedidos (order_repository). Use la [sección de especificaciones](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) en nuestro Adobe | Magento OMS Docs para utilizar otras API y extraer distintos tipos de información.
