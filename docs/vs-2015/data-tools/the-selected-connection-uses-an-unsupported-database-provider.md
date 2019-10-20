---
title: Seçilen bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667192"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Seçili bağlantı desteklenmeyen bir veritabanı sağlayıcısı kullanıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu ileti, **Sunucu Gezgini** /**Veritabanı Gezgini** SQL Server için .NET Framework veri sağlayıcısı kullanmayan öğeleri [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde görüntülenir.

 @No__t_0, yalnızca SQL Server için .NET Framework sağlayıcısını kullanan veri bağlantılarını destekler. Yalnızca Microsoft SQL Server veya Microsoft SQL Server veritabanı dosyası bağlantıları geçerlidir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yalnızca [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantılarından öğeleri ekleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Data.SqlClient> [.NET Framework veri sağlayıcıları](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)