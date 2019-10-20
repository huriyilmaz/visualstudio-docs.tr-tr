---
title: Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ce72f9d4f93db5d4f96bfe54e6cb0d29f4e0727b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639974"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

Bu ileti, **Sunucu Gezgini** veya **Veritabanı Gezgini** SQL Server için .NET Framework veri sağlayıcısı kullanmayan öğeleri [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde görüntülenir.

**O/R Tasarımcısı** , SQL Server için yalnızca .NET Framework sağlayıcıyı kullanan veri bağlantılarını destekler. Yalnızca Microsoft SQL Server veya Microsoft SQL Server veritabanı dosyası bağlantıları geçerlidir.

Bu hatayı düzeltmek için, yalnızca SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantılarından yalnızca **O/R tasarımcısına**öğe ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
