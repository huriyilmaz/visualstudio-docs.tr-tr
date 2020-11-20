---
title: Desteklenmeyen veritabanı sağlayıcısı
description: Seçilen bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor. Bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Designer) iletisiyle ilgili bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 06e08f9a9c28698ae2ee2fecfbcec64c39666c8a
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998353"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor

Bu ileti, **Sunucu Gezgini** veya **Veritabanı Gezgini** SQL Server için .NET Framework veri sağlayıcısı kullanmayan öğeleri [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde görüntülenir.

**O/R Tasarımcısı** , SQL Server için yalnızca .NET Framework sağlayıcıyı kullanan veri bağlantılarını destekler. Yalnızca Microsoft SQL Server veya Microsoft SQL Server veritabanı dosyası bağlantıları geçerlidir.

Bu hatayı düzeltmek için, yalnızca SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantılarından yalnızca **O/R tasarımcısına** öğe ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient>
- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
