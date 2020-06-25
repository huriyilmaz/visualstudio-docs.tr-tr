---
title: Bir DataContext yöntemin dönüş türünü değiştirme işlemi geri alınamaz
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d5b24337c9233aeeb060029cb54cd661b7591309
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282793"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Bir DataContext yöntemin dönüş türünü değiştirme işlemi geri alınamaz

DataContext metodunun dönüş türünü değiştirmek geri alınamaz. Otomatik olarak oluşturulan türe geri dönmek için öğeyi **Sunucu Gezgini** veya **veritabanı Gezgini** ' den O/R tasarımcısına yeniden sürüklemeniz gerekir. Dönüş türünü değiştirmek istediğinizden emin misiniz?

Bir yöntemin dönüş türü <xref:System.Data.Linq.DataContext> , öğesinde öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] . Bir öğeyi doğrudan mevcut bir varlık sınıfına bırakırsanız, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüne sahip bir yöntem oluşturulur. Öğesinin boş bir alanına bir öğe bıraktığınızda [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren bir yöntem oluşturulur. Bir yöntemin dönüş türünü <xref:System.Data.Linq.DataContext> Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , seçin ve **Özellikler** penceresinde **dönüş türü** özelliğine tıklayın.

## <a name="to-change-the-return-type-of-a-datacontext"></a>DataContext 'in dönüş türünü değiştirmek için

- **Evet**' e tıklayın.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>İleti kutusundan çıkmak ve dönüş türünü değiştirmeden bırakmak için

- **Hayır**'a tıklayın.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Dönüş türünü değiştirdikten sonra özgün dönüş türüne dönmek için

1. <xref:System.Data.Linq.DataContext>Üzerinde yöntemi seçin [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ve silin.

2. **Sunucu Gezgini/veritabanı Gezgini** içindeki öğeyi bulun ve üzerine sürükleyin [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

    <xref:System.Data.Linq.DataContext>Özgün varsayılan dönüş türüyle bir yöntem oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)