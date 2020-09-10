---
title: Desteklenmeyen veritabanı sağlayıcısı
description: Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9ff4120796a40da00e258026d8db84ba6e9dbb21
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743265"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

Bu ileti, **Sunucu Gezgini** veya **Veritabanı Gezgini** SQL Server için .NET Framework veri sağlayıcısı kullanmayan öğeleri [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde görüntülenir.

**O/R Tasarımcısı** , SQL Server için yalnızca .NET Framework sağlayıcıyı kullanan veri bağlantılarını destekler. Yalnızca Microsoft SQL Server veya Microsoft SQL Server veritabanı dosyası bağlantıları geçerlidir.

Bu hatayı düzeltmek için, yalnızca SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantılarından yalnızca **O/R tasarımcısına**öğe ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
