---
title: Desteklenmeyen bir veritabanı sağlayıcısından veritabanı nesnesi seçtiniz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657784"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Desteklenmeyen bir veritabanı sağlayıcısından bir veritabanı nesnesi seçtiniz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), SQL Server için yalnızca .NET Framework Veri Sağlayıcısı destekler (<xref:System.Data.SqlClient>). **Tamam** ' a tıklayıp desteklenmeyen veritabanı sağlayıcılarından nesnelerle çalışmaya devam edebilseniz de çalışma zamanında beklenmeyen davranışlarla karşılaşabilirsiniz.

> [!NOTE]
> Yalnızca SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantıları desteklenir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Desteklenmeyen veritabanı sağlayıcısını kullanan bağlantıyla eşlenen varlık sınıflarını tasarlamaya devam etmek için **Tamam** ' a tıklayın. Desteklenmeyen veritabanı sağlayıcıları kullandığınızda beklenmeyen davranışlarla karşılaşabilirsiniz.

     veya

- **Iptal 'e**tıklayın.

     Eylem durduruldu. SQL Server için .NET Framework sağlayıcısını kullanan bir veri bağlantısı oluşturun veya kullanın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio LINQ to SQL LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [.NET Framework veri sağlayıcıları](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)