---
title: Desteklenmeyen sağlayıcıdan nesne
description: Desteklenmeyen bir veritabanı sağlayıcısından veritabanı nesnesi seçtiniz. Bu Visual Studio (O/R Designer) iletisiyle ilgili bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f4f4a24e085cf4d268512ca90e5d1b3205abc9fe
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998168"
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
