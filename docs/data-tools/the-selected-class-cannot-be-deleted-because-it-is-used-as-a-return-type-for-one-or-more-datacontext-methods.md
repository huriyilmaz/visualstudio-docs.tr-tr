---
title: Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 249a5338985983509f04e0ff268b2f30e2773f71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113553"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor

Bir veya daha fazla <xref:System.Data.Linq.DataContext> yönteminin dönüş türü Seçili varlık sınıfıdır. Bir <xref:System.Data.Linq.DataContext> yöntemi için dönüş türü olarak kullanılan bir varlık sınıfını silmek, projenin derlenmesi başarısız olur. Seçili varlık sınıfını silmek için, onu kullanan <xref:System.Data.Linq.DataContext> yöntemleri belirleyin ve dönüş türlerini farklı bir varlık sınıfına ayarlayın.

<xref:System.Data.Linq.DataContext> yöntemlerinin dönüş türlerini özgün otomatik oluşturulan türlere geri döndürmek için, önce **Yöntemler** bölmesinden <xref:System.Data.Linq.DataContext> yöntemini silin ve sonra nesneyi **Sunucu Gezgini**/**veritabanı Gezgini** ' den **O/R tasarımcısına** sürükleyin.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. **Yöntemler** bölmesinde bir <xref:System.Data.Linq.DataContext> yöntemi seçerek ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyerek, bir dönüş türü olarak varlık sınıfını kullanan <xref:System.Data.Linq.DataContext> yöntemlerini belirleme.

2. **Dönüş türünü** farklı bir varlık sınıfına ayarlayın veya <xref:System.Data.Linq.DataContext> yöntemini Yöntemler bölmesinden silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
