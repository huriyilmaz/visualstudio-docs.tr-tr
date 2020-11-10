---
title: DataContext metodunun dönüş türünü değiştir
description: Nesne İlişkisel Tasarımcısı (O/R Designer) içinde bir saklı yordam veya işlevi bıraktığınızda bir DataContext yönteminin dönüş türünün nasıl değiştirileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 20ff0e4764acf4f2f0f8dea77ed815a9aa430abe
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435058"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: Bir DataContext metodunun dönüş türünü değiştirme (O/R Tasarımcısı)
Bir yöntemin dönüş türü <xref:System.Data.Linq.DataContext> (saklı yordam veya işlevi temel alınarak oluşturulur), saklı yordamı veya Işlevi **O/R tasarımcısında** nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir. Bir öğeyi doğrudan mevcut bir varlık sınıfına bırakırsanız, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüne sahip bir yöntem oluşturulur (saklı yordam veya işlev tarafından döndürülen verilerin şeması, varlık sınıfının şekliyle eşleşiyorsa). Bir öğeyi **O/R tasarımcısının** boş bir alanına bırakırsanız, <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren bir yöntem oluşturulur. Bir yöntemin dönüş türünü <xref:System.Data.Linq.DataContext> Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , seçin ve **Özellikler** penceresinde **dönüş türü** özelliğine tıklayın.

> [!NOTE]
> <xref:System.Data.Linq.DataContext> **Özellikler** penceresini kullanarak otomatik oluşturulan türü döndürmek için bir dönüş türü bir varlık sınıfına ayarlanmış olan yöntemleri geri döndüremezsiniz. Bir <xref:System.Data.Linq.DataContext> yöntemi otomatik üretilmiş bir tür döndürecek şekilde geri döndürmek için, özgün veritabanı nesnesini **O/R tasarımcısına** yeniden sürüklemeniz gerekir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Bir DataContext yönteminin dönüş türünü otomatik olarak oluşturulan türden bir varlık sınıfına değiştirmek için

1. <xref:System.Data.Linq.DataContext>Yöntemler bölmesinde yöntemi seçin.

2. **Özellikler** penceresinde **dönüş türü** ' nü seçin ve ardından **dönüş türü** listesinde kullanılabilir bir varlık sınıfı seçin. İstenen varlık sınıfı listede yoksa, onu listeye eklemek için **o/R tasarımcısında** ekleyin veya oluşturun.

3. *. Dbml* dosyasını kaydedin.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Bir DataContext yönteminin dönüş türünü bir varlık sınıfından otomatik oluşturulan türe değiştirmek için

1. <xref:System.Data.Linq.DataContext> **Yöntemler** bölmesinde yöntemi seçin ve silin.

2. Veritabanı nesnesini **Sunucu Gezgini** veya **veritabanı Gezgini** ' den **O/R tasarımcısının** boş bir alanına sürükleyin.

3. *. Dbml* dosyasını kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
