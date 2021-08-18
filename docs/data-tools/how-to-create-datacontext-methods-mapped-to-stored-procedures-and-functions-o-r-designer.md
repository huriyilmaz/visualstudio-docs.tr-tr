---
title: DataContext yöntemlerini sprocs ve işlevlerle eşleme
description: Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) kullanarak saklı yordamlara (sprocs) ve işlevlere eşlenen DataContext yöntemleri oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 366d13085c14eebda3e9ca257d726d59167852b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036868"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)

Saklı yordamları ve işlevleri **O/R Tasarımcısı'na yöntemler olarak** <xref:System.Data.Linq.DataContext> ekebilirsiniz. yöntemini çağırarak ve gerekli parametreleri geçirme, veritabanında saklı yordamı veya işlevi çalıştırır ve yöntemin dönüş türünde verileri <xref:System.Data.Linq.DataContext> döndürür. Yöntemler hakkında ayrıntılı <xref:System.Data.Linq.DataContext> bilgi için bkz. [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Saklı yordamları, varlık sınıflarından veritabanına değişiklikler kaydediken Eklemeler, Güncelleştirmeler ve Silmeler gerçekleştiren varsayılan çalışma zamanı davranışını geçersiz kılmak için [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] de kullanabilirsiniz. Daha fazla bilgi için bkz. Nasıl kullanılır: Güncelleştirmeleri, eklemeleri ve silmeleri gerçekleştirmek için [saklı yordamları atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>DataContext yöntemleri oluşturma

Saklı yordamları veya işlevleri Sunucu Gezgini veya <xref:System.Data.Linq.DataContext> <strong>**Veritabanı Gezgini</strong> O/R Tasarımcısı'na **sürükleyerek yöntemler oluşturabilirsiniz.**

> [!NOTE]
> Oluşturulan yöntemin dönüş türü, saklı yordamı veya işlevi O/R Tasarımcısı'nda nereye bırakmanıza <xref:System.Data.Linq.DataContext> **bağlı olarak farklılık gösterir.** Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, varlık <xref:System.Data.Linq.DataContext> sınıfının dönüş türüyle bir yöntem oluşturur. Öğeleri **O/R** Tasarımcısı'nın boş bir alanına bırakmak, otomatik <xref:System.Data.Linq.DataContext> olarak oluşturulan bir tür döndüren bir yöntem oluşturur. Bir yöntemi Yöntemler bölmesine <xref:System.Data.Linq.DataContext> ekledikten sonra dönüş **türünü değiştirebilirsiniz.** Bir yöntemin dönüş türünü incelemek veya değiştirmek için, yöntemi seçin ve Özellikler penceresinde <xref:System.Data.Linq.DataContext> **Dönüş** Türü **özelliğini** inceler. Daha fazla bilgi için, bkz. How to: Change the return [type of a DataContext method (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Otomatik olarak oluşturulan türleri geri getiren DataContext yöntemleri oluşturmak için

1. Sunucu Gezgini  veya **Veritabanı Gezgini** içinde, **çalışmakta olduğu** veritabanının Saklı Yordamlar düğümünü genişletin.

2. İstenen saklı yordamı bulun ve **O/R** Tasarımcısı'nın boş bir alanına sürükleyin.

     yöntemi <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir dönüş türüyle oluşturulur ve Yöntemler **bölmesinde** görünür.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Varlık sınıfının dönüş türüne sahip DataContext yöntemleri oluşturmak için

1. Sunucu Gezgini  veya **Veritabanı Gezgini** içinde, **çalışmakta olduğu** veritabanının Saklı Yordamlar düğümünü genişletin.

2. İstenen saklı yordamı bulun ve O/R Tasarımcısı'nda mevcut bir **varlık sınıfına sürükleyin.**

     yöntemi, <xref:System.Data.Linq.DataContext> seçilen varlık sınıfının dönüş türüyle oluşturulur ve Yöntemler **bölmesinde** görünür.

> [!NOTE]
> Var olan yöntemlerin dönüş türünü değiştirme hakkında bilgi için <xref:System.Data.Linq.DataContext> [bkz. Nasıl kullanılır: DataContext yönteminin dönüş türünü değiştirme (O/R Tasarımcısı)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic'de LINQ'e Giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# üzerinde LINQ](/dotnet/csharp/linq/linq-in-csharp)
