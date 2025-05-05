---
title: Buscar tablas MySQL grandes
description: '"Para identificar las tablas grandes, conéctese a la base de datos como se describe en el artículo [Conectarse a la base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) y ejecute el siguiente comando, donde "project_id" es su ID de proyecto en la nube:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Buscar tablas MySQL grandes

Para identificar las tablas grandes, conéctese a la base de datos como se describe en el artículo [Conectarse a la base de datos](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) y ejecute el siguiente comando, donde `project_id` es su Id. de proyecto en la nube:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Esto mostraría la lista completa de tablas y su tamaño. Puede ir a través de la lista e identificar qué tablas requieren atención debido al gran tamaño.

## Lectura relacionada

[Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce
