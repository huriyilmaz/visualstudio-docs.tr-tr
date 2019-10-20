---
title: Bir veya daha fazla DataContext yöntemi için dönüş türü olarak kullanıldığından, seçilen sınıf silinemiyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667253"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veya daha fazla <xref:System.Data.Linq.DataContext> yönteminin dönüş türü Seçili varlık sınıfıdır. Bir <xref:System.Data.Linq.DataContext> yöntemi için dönüş türü olarak kullanılan bir varlık sınıfını silmek, projenin derlenmesi başarısız olur. Seçili varlık sınıfını silmek için, onu kullanan <xref:System.Data.Linq.DataContext> yöntemleri belirleyin ve dönüş türlerini farklı bir varlık sınıfına ayarlayın.

 @No__t_0 yöntemlerinin dönüş türlerini özgün otomatik oluşturulan türlere geri döndürmek için, önce Yöntemler bölmesinden <xref:System.Data.Linq.DataContext> yöntemini silin ve sonra nesneyi **Sunucu Gezgini** /**veritabanı Gezgini** ' den O/R tasarımcısına sürükleyin.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Yöntemler bölmesinde bir <xref:System.Data.Linq.DataContext> yöntemi seçerek ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyerek, bir dönüş türü olarak varlık sınıfını kullanan <xref:System.Data.Linq.DataContext> yöntemlerini belirleme.

2. **Dönüş türünü** farklı bir varlık sınıfına ayarlayın veya <xref:System.Data.Linq.DataContext> yöntemini Yöntemler bölmesinden silin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [DataContext yöntemleri (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [nasıl yapılır: bir DataContext yönteminin dönüş türünü değiştirme (o/r Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
