---
title: 'Nasıl yapılır: DataContext metodunun dönüş türünü değiştirme (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658834"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: DataContext metodunun dönüş türünü değiştirme (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türü (saklı yordam veya işlev temelinde oluşturulan), [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] saklı yordamı veya işlevi nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir. Bir öğeyi doğrudan mevcut bir varlık sınıfına bırakırsanız, varlık sınıfının dönüş türüne sahip bir <xref:System.Data.Linq.DataContext> yöntemi oluşturulur (saklı yordam veya işlev tarafından döndürülen verilerin şeması, varlık sınıfının şekliyle eşleşiyorsa). Bir öğeyi [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] boş bir alanına bırakırsanız, otomatik olarak oluşturulan bir tür döndüren bir <xref:System.Data.Linq.DataContext> yöntemi oluşturulur. @No__t_0 yönteminin dönüş türünü Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğine tıklayın.

> [!NOTE]
> **Özellikler** penceresini kullanarak otomatik oluşturulan türü döndürmek için bir dönüş türü bir varlık sınıfına ayarlanmış <xref:System.Data.Linq.DataContext> metotları geri döndüremezsiniz. Otomatik olarak oluşturulan bir tür döndürmek için bir <xref:System.Data.Linq.DataContext> metodunu geri döndürmek için, özgün veritabanı nesnesini O/R tasarımcısına yeniden sürüklemeniz gerekir.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Bir DataContext yönteminin dönüş türünü otomatik olarak oluşturulan türden bir varlık sınıfına değiştirmek için

1. Yöntemler bölmesinde <xref:System.Data.Linq.DataContext> yöntemini seçin.

2. **Özellikler** penceresinde **dönüş türü** ' nü seçin ve ardından **dönüş türü** listesinde kullanılabilir bir varlık sınıfı seçin. İstenen varlık sınıfı listede yoksa, bunu listeye ekleyin veya [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] listeye ekleyin.

3. . Dbml dosyasını kaydedin.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Bir DataContext yönteminin dönüş türünü bir varlık sınıfından otomatik oluşturulan türe değiştirmek için

1. Yöntemler bölmesinde <xref:System.Data.Linq.DataContext> yöntemi seçin ve silin.

2. Veritabanı nesnesini **Sunucu Gezgini** /**veritabanı Gezgini** ' den O/R tasarımcısının boş bir alanına sürükleyin.

3. . Dbml dosyasını kaydedin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [DataContext yöntemleri (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (o/r Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
