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
ms.openlocfilehash: ba0c26ce4c9b7b06703ab6dead8b77a0bdc1fccf13d707a5feb066006626a290
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346772"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

.NET Framework Veri Sağlayıcısı for SQL Server kullanmayan öğeleri Sunucu Gezgini veya **Veritabanı Gezgini'den** LINQ to SQL [araçlarına sürüklerken bu Visual Studio.](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 

**O/R Tasarımcısı yalnızca** veri sağlayıcısı için .NET Framework sağlayıcısını kullanan veri bağlantılarını SQL Server. Yalnızca veritabanı Microsoft SQL Server Microsoft SQL Server bağlantılar geçerlidir.

Bu hatayı düzeltmek için, yalnızca O/R Tasarımcısı'na .NET Framework Veri Sağlayıcısı SQL Server veri **bağlantılarından öğeleri ekleyin.**

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
