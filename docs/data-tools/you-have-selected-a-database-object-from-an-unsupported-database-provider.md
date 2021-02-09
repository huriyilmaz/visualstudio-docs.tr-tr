---
title: Desteklenmeyen sağlayıcıdan nesne
description: Desteklenmeyen bir veritabanı sağlayıcısından veritabanı nesnesi seçtiniz. Bu Visual Studio (O/R Designer) iletisiyle ilgili bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c3ccd477882382962efcc2f87c5dc99f59c14be1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858052"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Desteklenmeyen bir veritabanı sağlayıcısından bir veritabanı nesnesi seçtiniz

**O/R Tasarımcısı** yalnızca SQL Server () için .NET Framework veri sağlayıcısı destekler <xref:System.Data.SqlClient> . **Tamam** ' a tıklayıp desteklenmeyen veritabanı sağlayıcılarından nesnelerle çalışmaya devam edebilseniz de çalışma zamanında beklenmeyen davranışlarla karşılaşabilirsiniz.

> [!NOTE]
> Yalnızca SQL Server için .NET Framework Veri Sağlayıcısı kullanan veri bağlantıları desteklenir.

## <a name="options"></a>Seçenekler

- Desteklenmeyen veritabanı sağlayıcısını kullanan bağlantıyla eşlenen varlık sınıflarını tasarlamaya devam etmek için **Tamam** ' a tıklayın. Desteklenmeyen veritabanı sağlayıcıları kullandığınızda beklenmeyen davranışlarla karşılaşabilirsiniz.

- Eylemi durdurmak için **iptal** ' e tıklayın. SQL Server için .NET Framework sağlayıcısını kullanan farklı bir veri bağlantısı oluşturun veya kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
