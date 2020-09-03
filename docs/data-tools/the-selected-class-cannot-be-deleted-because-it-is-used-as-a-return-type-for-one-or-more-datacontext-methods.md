---
title: Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: faea45cc7198be91a45d0bb57a62ce2730011ee2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281337"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Seçilen sınıf bir veya birden çok DataContext yöntemi için bir dönüş türü olarak kullanıldığından silinemiyor

Bir veya daha fazla yöntemin dönüş türü <xref:System.Data.Linq.DataContext> Seçili varlık sınıfıdır. Bir yöntemi için dönüş türü olarak kullanılan bir varlık sınıfını silmek, <xref:System.Data.Linq.DataContext> projenin derlenmesi başarısız olur. Seçili varlık sınıfını silmek için, <xref:System.Data.Linq.DataContext> onu kullanan yöntemleri belirleyin ve dönüş türlerini farklı bir varlık sınıfına ayarlayın.

Yöntemlerin dönüş türlerini <xref:System.Data.Linq.DataContext> özgün otomatik oluşturulan türlere geri döndürmek için, önce <xref:System.Data.Linq.DataContext> **yöntemleri yöntemler** bölmesinden silin ve sonra nesneyi **Sunucu Gezgini** / **veritabanı Gezgini** öğesinden **O/R tasarımcısına** yeniden sürükleyin.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext> **Yöntemler** bölmesinde bir yöntem seçerek ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyerek, bir dönüş türü olarak varlık sınıfını kullanan yöntemleri belirler.

2. **Dönüş türünü** farklı bir varlık sınıfına ayarlayın veya <xref:System.Data.Linq.DataContext> yöntemi Yöntemler bölmesinden silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
