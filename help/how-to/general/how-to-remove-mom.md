---
title: Cómo eliminar Magento Order Management (MOM)
description: Este artículo explica cómo eliminar el sistema Magento Order Management (MOM).
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 724a30310c3841f8280628436925f9a3e5933b14
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Cómo eliminar Magento Order Management (MOM)

1. Deshabilite la integración de MOM siguiendo los pasos de [Deshabilite o habilite la integración](https://commerce-docs.github.io/oms-documentation-archive/integration/connector/#disable-or-enable-the-integration).
1. Deshabilite el módulo MOM siguiendo los pasos de [Desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html?lang=es).
1. Para extraer datos de pedidos completos, ofrecemos la API. Para obtener más información, revisa [Repositorio de pedidos](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository) en nuestro Adobe | Documentos de Magento OMS, que abarcan información de pedidos (order_repository). Use la [sección de especificaciones](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services) en nuestro Adobe | Magento OMS Docs para utilizar otras API y extraer distintos tipos de información.
