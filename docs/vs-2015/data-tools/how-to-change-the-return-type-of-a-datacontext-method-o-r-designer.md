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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658834"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: Bir DataContext metodunun dönüş türünü değiştirme (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir yöntemin dönüş türü <xref:System.Data.Linq.DataContext> (bir saklı yordama veya işleve göre oluşturulan), içindeki saklı yordamı veya işlevi nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Bir öğeyi doğrudan mevcut bir varlık sınıfına bırakırsanız, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüne sahip bir yöntem oluşturulur (saklı yordam veya işlev tarafından döndürülen verilerin şeması, varlık sınıfının şekliyle eşleşiyorsa). Öğesinin boş bir alanına bir öğe bıraktığınızda [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren bir yöntem oluşturulur. Bir yöntemin dönüş türünü <xref:System.Data.Linq.DataContext> Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , seçin ve **Özellikler** penceresinde **dönüş türü** özelliğine tıklayın.

> [!NOTE]
> <xref:System.Data.Linq.DataContext> **Özellikler** penceresini kullanarak otomatik oluşturulan türü döndürmek için bir dönüş türü bir varlık sınıfına ayarlanmış olan yöntemleri geri döndüremezsiniz. Bir <xref:System.Data.Linq.DataContext> yöntemi otomatik üretilmiş bir tür döndürecek şekilde geri döndürmek için, özgün veritabanı nesnesini O/R tasarımcısına yeniden sürüklemeniz gerekir.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Bir DataContext yönteminin dönüş türünü otomatik olarak oluşturulan türden bir varlık sınıfına değiştirmek için

1. <xref:System.Data.Linq.DataContext>Yöntemler bölmesinde yöntemi seçin.

2. **Özellikler** penceresinde **dönüş türü** ' nü seçin ve ardından **dönüş türü** listesinde kullanılabilir bir varlık sınıfı seçin. İstenen varlık sınıfı listede yoksa, onu listeye eklemek için öğesine ekleyin veya içinde oluşturun [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

3. . Dbml dosyasını kaydedin.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Bir DataContext yönteminin dönüş türünü bir varlık sınıfından otomatik oluşturulan türe değiştirmek için

1. <xref:System.Data.Linq.DataContext>Yöntemler bölmesinde yöntemi seçin ve silin.

2. Veritabanı nesnesini **Sunucu Gezgini** / **veritabanı Gezgini** öğesinden O/R tasarımcısının boş bir alanına sürükleyin.

3. . Dbml dosyasını kaydedin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [DataContext yöntemleri (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (o/r Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
