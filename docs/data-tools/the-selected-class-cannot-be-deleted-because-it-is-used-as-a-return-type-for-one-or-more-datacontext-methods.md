---
title: Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aff8d7c01291c410f81b00c689f600507841965b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640049"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor

Bir veya daha fazla <xref:System.Data.Linq.DataContext> yönteminin dönüş türü Seçili varlık sınıfıdır. Bir <xref:System.Data.Linq.DataContext> yöntemi için dönüş türü olarak kullanılan bir varlık sınıfını silmek, projenin derlenmesi başarısız olur. Seçili varlık sınıfını silmek için, onu kullanan <xref:System.Data.Linq.DataContext> yöntemleri belirleyin ve dönüş türlerini farklı bir varlık sınıfına ayarlayın.

@No__t_0 yöntemlerinin dönüş türlerini özgün otomatik olarak oluşturulan türlere geri döndürmek için, önce **Yöntemler** bölmesinden <xref:System.Data.Linq.DataContext> yöntemini silin ve sonra nesneyi **Sunucu Gezgini** /**veritabanı Gezgini** , **O/R üzerine sürükleyin Tasarımcıyı** yeniden deneyin.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. **Yöntemler** bölmesinde bir <xref:System.Data.Linq.DataContext> yöntemi seçerek ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyerek, bir dönüş türü olarak varlık sınıfını kullanan <xref:System.Data.Linq.DataContext> yöntemlerini belirleme.

2. **Dönüş türünü** farklı bir varlık sınıfına ayarlayın veya <xref:System.Data.Linq.DataContext> yöntemini Yöntemler bölmesinden silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)