---
title: Desteklenmeyen sağlayıcıdan nesne
description: Desteklenmeyen bir veritabanı sağlayıcısından bir veritabanı nesnesi seçtiniz
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84841c5e0759618430f9c2e4f0146cbc2d21fae9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036723"
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
