---
title: Desteklenmeyen veritabanı sağlayıcısı
description: Seçilen bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanır. Bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b4956314b994d66e972a9e65a30ee5eb8d8aac13
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121961"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

Bu ileti, SQL Server için .NET Framework Veri Sağlayıcısı kullanmayan öğeleri Sunucu Gezgini veya **Veritabanı Gezgini'LINQ to SQL**  [araçlarına sürüklerken Visual Studio.](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

**O/R Tasarımcısı yalnızca** .NET Framework Sağlayıcısını kullanan veri bağlantılarını SQL Server. Yalnızca veritabanı Microsoft SQL Server veritabanı Microsoft SQL Server bağlantılar geçerlidir.

Bu hatayı düzeltmek için, O/R Tasarımcısı'na yalnızca .NET Framework Veri Sağlayıcısı için SQL Server **kullanan veri bağlantılarından öğeleri ekleyin.**

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
