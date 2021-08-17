---
title: Desteklenmeyen veri türü
description: Bir veya daha fazla seçili öğe, tasarımcı tarafından desteklemez bir veri türü içerir. Bu çalışma Visual Studio O/R Tasarımcısı iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 55402288d52f6f4b5eeac41efbb15d9f164ff5cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075157"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Seçilen bir veya birden çok öğe, tasarımcı tarafından desteklenmeyen bir veri türü içeriyor

Sunucu Gezgini veya **Veritabanı Gezgini'dan** **O/R Tasarımcısı'na** sürüklenen öğelerden biri veya daha  **fazlası, O/R Tasarımcısı** tarafından desteklenen bir veri türü içerir, örneğin CLR kullanıcı tanımlı [türleri.](/dotnet/framework/data/adonet/sql/clr-user-defined-types)

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. İstenen tabloyu temel alan ve desteklenmeyen veri türünü içermemiş bir görünüm oluşturun.

2. Görünümü Sunucu Gezgini **veya** **Veritabanı Gezgini** tasarımcıya sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
