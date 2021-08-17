---
title: LINQ to SQL sınıfları arasındaki ilişkiler
description: Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) iletişim kutusunu kullanarak LINQ to SQL sınıfları arasında ilişki oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: edaa571a5b58411cfd004907414f389a10ab91733b01140324f4cf12d05e7b11
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347122"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Nasıl kullanılır: LINQ to SQL sınıfları (O/R Tasarımcısı) arasında ilişki oluşturma
içinde varlık sınıfları arasındaki [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ilişkilendirmeler, veritabanındaki tablolar arasındaki ilişkilere benzer. İlişki Düzenleyici iletişim kutusunu kullanarak varlık sınıfları arasında **ilişki** oluşturabilirsiniz.

İlişki oluşturma için İlişki düzenleyici iletişim kutusunu kullanırken bir üst sınıf **ve** alt sınıf seçmeniz gerekir. Üst sınıf, birincil anahtarı içeren varlık sınıfıdır; alt sınıfı, yabancı anahtarı içeren varlık sınıfıdır. Örneğin, ve tablolarına eşlene varlık sınıfları oluşturulduktan sonra sınıf üst `Northwind Customers` `Orders` `Customer` sınıf, `Order` sınıf ise alt sınıf olur.

> [!NOTE]
> Tabloları Sunucu Gezgini **Veritabanı Gezgini** **(O/R Tasarımcısı)** **Nesne İlişkisel Tasarımcısı** üzerine sürüklerken, ilişkilendirmeler veritabanındaki mevcut yabancı anahtar ilişkilerine göre otomatik olarak oluşturulur. 

## <a name="association-properties"></a>İlişki özellikleri
bir ilişkilendirme oluşturduk sonra, **O/R Tasarımcısı'nda ilişkilendirmeyi** seçerek Özellikler penceresinde bazı yapılandırılabilir **özellikler** vardır. (İlişkili sınıflar arasındaki çizgi ilişkilendirmedir.) Aşağıdaki tablo, bir ilişkilendirmenin özellikleri için açıklamalar sağlar.

|Özellik|Açıklama|
|--------------|-----------------|
|**Kardinalite**|İlişkinin bire çok mu yoksa bire bir mi olduğunu kontrol eder.|
|**Alt Özellik**|Üst öğede bir koleksiyon veya ilişkilendirmenin yabancı anahtar tarafında alt kayıtlara başvuru bir özellik oluşturulıp oluşturul olmadığını belirtir. Örneğin, ve arasındaki ilişkide, Alt Özellik True olarak ayarlanırsa, üst sınıfta `Customer` `Order` adlı bir özellik   `Orders` oluşturulur.|
|**Üst Özellik**|İlişkili üst sınıfa başvurulan alt sınıftaki özelliği. Örneğin, ve arasındaki ilişkide, sınıfında bir sipariş için ilişkili müşteriye `Customer` `Order` `Customer` başvurulan adlı bir özellik `Order` oluşturulur.|
|**Katılan Özellikler**|İlişki özelliklerini görüntüler ve İlişki **düzenleyici iletişim kutusunu** yeniden açan bir üç nokta **düğmesi** (...) sağlar.|
|**Benzersiz**|Yabancı hedef sütunların benzersizlik kısıtlaması olup olmadığını belirtir.|

## <a name="to-create-an-association-between-entity-classes"></a>Varlık sınıfları arasında ilişki oluşturmak için

1. İlişkide üst sınıfı temsil eden varlık sınıfına sağ tıklayın, Ekle'nin üzerine **gelin** ve İlişkile'ye **tıklayın.**

2. İlişki Düzenleyici iletişim **kutusunda doğru** Üst Sınıfın **seçili olduğunu** doğrulayın.

3. Birleşik **giriş kutusunda Alt** Sınıf'ı seçin.

4. Sınıfları **ilişkili İlişkili** İlişkili Özellikler'i seçin. Bu genellikle veritabanında tanımlanan yabancı anahtar ilişkisiyle eşler. Örneğin, ve `Customers` `Orders` ilişkilendirmesinde, İlişki **özellikleri her** sınıf `CustomerID` için 'tir.

5. İlişkiyi **oluşturmak** için Tamam'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl: Birincil anahtarları temsil etme](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
