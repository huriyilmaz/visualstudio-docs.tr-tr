---
title: Bir DataContext yöntemin dönüş türünü değiştirme işlemi geri alınamaz
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 95d75e084b4824cf7cc8e717b1ce9174e76aa2e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648685"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Bir DataContext yöntemin dönüş türünü değiştirme işlemi geri alınamaz

DataContext metodunun dönüş türünü değiştirmek geri alınamaz. Otomatik olarak oluşturulan türe geri dönmek için öğeyi **Sunucu Gezgini** veya **veritabanı Gezgini** ' den O/R tasarımcısına yeniden sürüklemeniz gerekir. Dönüş türünü değiştirmek istediğinizden emin misiniz?

Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, öğeyi [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bıraktığınızda nereye göre farklılık gösterir. Bir öğeyi doğrudan mevcut bir varlık sınıfına bırakırsanız, varlık sınıfının dönüş türüne sahip bir <xref:System.Data.Linq.DataContext> yöntemi oluşturulur. Bir öğeyi [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] boş bir alanına bırakırsanız, otomatik olarak oluşturulan bir tür döndüren bir <xref:System.Data.Linq.DataContext> yöntemi oluşturulur. @No__t_0 yönteminin dönüş türünü Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğine tıklayın.

## <a name="to-change-the-return-type-of-a-datacontext"></a>DataContext 'in dönüş türünü değiştirmek için

- **Evet**'i tıklayın.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>İleti kutusundan çıkmak ve dönüş türünü değiştirmeden bırakmak için

- **Hayır**'a tıklayın.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Dönüş türünü değiştirdikten sonra özgün dönüş türüne dönmek için

1. @No__t_1 <xref:System.Data.Linq.DataContext> yöntemi seçin ve silin.

2. **Sunucu Gezgini/veritabanı Gezgini** içindeki öğeyi bulun ve [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sürükleyin.

    Özgün varsayılan dönüş türüyle bir <xref:System.Data.Linq.DataContext> yöntemi oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)