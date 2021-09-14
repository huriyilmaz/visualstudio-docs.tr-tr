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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631125"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

SQL Server için .NET Framework Veri Sağlayıcısı kullanmayan öğeleri Sunucu Gezgini veya **Veritabanı Gezgini'daki** LINQ to SQL  [araçlarına sürüklerken bu Visual Studio.](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

**O/R Tasarımcısı yalnızca** .NET Framework Sağlayıcısı'nın SQL Server. Yalnızca veritabanı Microsoft SQL Server veya Microsoft SQL Server bağlantılar geçerlidir.

Bu hatayı düzeltmek için, yalnızca O/R Tasarımcısı'na .NET Framework Veri Sağlayıcısı SQL Server veri **bağlantılarından öğeleri ekleyin.**

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
