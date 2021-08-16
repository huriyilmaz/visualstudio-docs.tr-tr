---
title: Dönüş türü değişikliği geri alınamaz
description: DataContext yönteminin dönüş türünü değiştirmek geri alınamaz. Bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 43ef9c3e00c987bfb56e6360470b30de440c153830060eb0b85c7f5897b1f149
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380695"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Bir DataContext yöntemin dönüş türünü değiştirme işlemi geri alınamaz

DataContext yönteminin dönüş türünü değiştirmek geri alınamaz. Otomatik olarak oluşturulan türe geri dönmek için öğeyi yeniden Sunucu Gezgini  veya **Veritabanı Gezgini** O/R Tasarımcısı'na sürüklemelisiniz. Dönüş türünü değiştirmek istediğinizden emin misiniz?

Bir yöntemin dönüş <xref:System.Data.Linq.DataContext> türü, öğesini içinde nereye bırakmanıza bağlı olarak farklılık [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] gösterir. Bir öğeyi doğrudan var olan bir varlık sınıfına bırakmanız, varlık <xref:System.Data.Linq.DataContext> sınıfının dönüş türüne sahip bir yöntem oluşturulur. Bir öğeyi boş bir alanına [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] bıraksanız, otomatik olarak oluşturulan bir tür <xref:System.Data.Linq.DataContext> döndüren bir yöntem oluşturulur. Bir yöntemi yöntemler bölmesine <xref:System.Data.Linq.DataContext> ekledikten sonra dönüş türünü değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için, yöntemi seçin ve Özellikler <xref:System.Data.Linq.DataContext> **penceresinde Dönüş** Türü **özelliğine** tıklayın.

## <a name="to-change-the-return-type-of-a-datacontext"></a>DataContext'in dönüş türünü değiştirmek için

- **Evet**'e tıklayın.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>İleti kutusundan çıkmak ve dönüş türünü değiştirmeden bırakmak için

- **Hayır**'a tıklayın.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Dönüş türünü değiştirdikten sonra özgün dönüş türüne dönmek için

1. üzerinde <xref:System.Data.Linq.DataContext> yöntemini seçin [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ve silin.

2. öğesini **Sunucu Gezgini/Veritabanı Gezgini** ve üzerine [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] sürükleyin.

    Özgün <xref:System.Data.Linq.DataContext> varsayılan dönüş türüyle bir yöntem oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)