---
title: Seçilen sınıf silinemiyor
description: Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1099369fdf2ebe4ef2ba4cfc8b8d6fabf7e47323
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631131"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor

Bir veya daha fazla yöntemin dönüş türü <xref:System.Data.Linq.DataContext> Seçili varlık sınıfıdır. Bir yöntemi için dönüş türü olarak kullanılan bir varlık sınıfını silmek, <xref:System.Data.Linq.DataContext> projenin derlenmesi başarısız olur. Seçili varlık sınıfını silmek için, <xref:System.Data.Linq.DataContext> onu kullanan yöntemleri belirleyin ve dönüş türlerini farklı bir varlık sınıfına ayarlayın.

Yöntemlerin dönüş türlerini <xref:System.Data.Linq.DataContext> özgün otomatik oluşturulan türlere geri döndürmek için, önce <xref:System.Data.Linq.DataContext> **yöntemleri yöntemler** bölmesinden silin ve sonra nesneyi **Sunucu Gezgini** / **veritabanı Gezgini** öğesinden **O/R tasarımcısına** yeniden sürükleyin.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext> **Yöntemler** bölmesinde bir yöntem seçerek ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyerek, bir dönüş türü olarak varlık sınıfını kullanan yöntemleri belirler.

2. **Dönüş türünü** farklı bir varlık sınıfına ayarlayın veya <xref:System.Data.Linq.DataContext> yöntemi Yöntemler bölmesinden silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
