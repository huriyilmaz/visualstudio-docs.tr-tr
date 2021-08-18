---
title: DataContext yönteminin dönüş türünü değiştirme
description: DataContext yönteminin dönüş türünü değiştirme hakkında bilgi için bkz. Bir saklı yordamı veya işlevi Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7429a9d9f3cbc7353322a65cd1f5f1be5381704d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113932"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: Bir DataContext metodunun dönüş türünü değiştirme (O/R Tasarımcısı)
Bir yöntemin dönüş türü (saklı yordama veya işleve göre oluşturulur) saklı yordamı veya işlevi O/R Tasarımcısı'nda nereye bırakarak bırak <xref:System.Data.Linq.DataContext> **istediğinize bağlı olarak farklılık gösterir.** Bir öğeyi doğrudan var olan bir varlık sınıfına bırakmanız, varlık sınıfının dönüş türüne sahip bir yöntem oluşturulur (saklı yordam veya işlev tarafından döndürülen verilerin şeması varlık sınıfının şekliyle <xref:System.Data.Linq.DataContext> eşlanıyorsa). Bir öğeyi **O/R** Tasarımcısı'nın boş bir alanına bıraksanız, otomatik olarak oluşturulan bir tür <xref:System.Data.Linq.DataContext> döndüren bir yöntem oluşturulur. Bir yöntemi yöntemler bölmesine <xref:System.Data.Linq.DataContext> ekledikten sonra dönüş türünü değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için, yöntemi seçin ve Özellikler <xref:System.Data.Linq.DataContext> **penceresinde Dönüş** Türü **özelliğine** tıklayın.

> [!NOTE]
> Özellikler penceresini kullanarak otomatik olarak oluşturulan türü döndüren bir varlık sınıfına ayarlanmış dönüş türüne sahip <xref:System.Data.Linq.DataContext> yöntemleri geri **döndüresiniz.** Otomatik olarak oluşturulan bir türü döndürme yöntemini geri dönmek için özgün veritabanı nesnesini <xref:System.Data.Linq.DataContext> **yeniden O/R Tasarımcısı'na sürüklemeniz** gerekir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>DataContext yönteminin dönüş türünü otomatik olarak oluşturulan türden varlık sınıfına değiştirmek için

1. Yöntemler <xref:System.Data.Linq.DataContext> bölmesinden yöntemini seçin.

2. Özellikler **penceresinde Dönüş** **Türü'ne** tıklayın ve ardından Dönüş Türü listesinden kullanılabilir bir **varlık sınıfı** seçin. İstenen varlık sınıfı listede yoksa, listeye eklemek için **sınıfını O/R Tasarımcısı'na** ekleyin veya oluşturun.

3. *.dbml dosyasını* kaydedin.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>DataContext yönteminin dönüş türünü varlık sınıfından otomatik olarak oluşturulan türe geri değiştirmek için

1. Yöntemler <xref:System.Data.Linq.DataContext> bölmesinde **yöntemini seçin** ve silin.

2. Veritabanı nesnesini Sunucu Gezgini **veya** **Veritabanı Gezgini** **O/R** Tasarımcısı'nın boş bir alanına sürükleyin.

3. *.dbml dosyasını* kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
