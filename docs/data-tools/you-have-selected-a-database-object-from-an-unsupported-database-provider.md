---
title: Desteklenmeyen sağlayıcıdan nesne
description: Desteklenmeyen bir veritabanı sağlayıcısından bir veritabanı nesnesi seçtik. Bu Visual Studio (O/R Tasarımcısı) iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4f113dfbe1480beff311786afcb15ad13b20498
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121909"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Desteklenmeyen bir veritabanı sağlayıcısından bir veritabanı nesnesi seçtiniz

**O/R Tasarımcısı yalnızca** .NET Framework Veri Sağlayıcısı () için SQL Server <xref:System.Data.SqlClient> destekler. Tamam'a **tıklar** ve desteklenmeyen veritabanı sağlayıcılarından nesnelerle çalışmaya devam edersiniz, ancak çalışma zamanında beklenmeyen bir davranışla karşılaşabilirsiniz.

> [!NOTE]
> Yalnızca veri bağlantıları .NET Framework Veri Sağlayıcısı SQL Server destekler.

## <a name="options"></a>Seçenekler

- Desteklenmeyen **veritabanı** sağlayıcısını kullanan bağlantıyla eşilen varlık sınıflarını tasarlamaya devam etmek için Tamam'a tıklayın. Desteklenmeyen veritabanı sağlayıcılarını kullanırken beklenmeyen bir davranışla karşılaşabilirsiniz.

- Eylemi **durdurmak için** İptal'e tıklayın. .NET Framework Sağlayıcısı'nın kullandığı farklı bir veri bağlantısı oluşturun veya SQL Server.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
