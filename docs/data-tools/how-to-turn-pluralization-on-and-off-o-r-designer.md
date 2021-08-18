---
title: 'Nasıl yapılır: plurseli açma ve kapatma (O-R Designer)'
description: Nesne İlişkisel Tasarımcısı (O/R Designer) ' de plurselleştirmeyi açma ve kapatma hakkında bilgi sahibi olun. Varsayılan ayar, çoğul adlarını tekil olarak dönüştürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f51d48f2d4af4ed723dbe0dcd720ee460e1feb1b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139679"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: Çoğullaştırmayı açıp kapatma (O/R Tasarımcısı)
varsayılan olarak, **Sunucu Gezgini** veya **Veritabanı Gezgini** son görüntülenen adlara sahip veritabanı nesnelerini [Visual Studio LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde, oluşturulan varlık sınıflarının adları plural 'den tekil 'e değiştirilir. Bu, Örneklenmiş varlık sınıfının tek bir veri kaydıyla eşlendiği olguyu daha doğru bir şekilde temsil etmek için yapılır. Örneğin, `Customers` **u/R tasarımcısına** tablo eklemek, `Customer` sınıfı yalnızca tek bir müşteri için veri tutacağından, adlı bir varlık sınıfı ile sonuçlanır.

> [!NOTE]
> Pluralization, varsayılan olarak yalnızca Visual Studio Türkçe dil sürümünde bulunur.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma 'ı açmak ve kapatmak için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Seçenekler** Iletişim kutusunda **veritabanı araçları**' nı genişletin.

    > [!NOTE]
    > **Veritabanı araçları** düğümü görünür değilse **tüm ayarları göster** ' i seçin.

3. **O/R Tasarımcısı**' na tıklayın.

4. **Adların**   =  , sınıf adlarını değiştirmemesi adına, **O/R tasarımcısını** ayarlamak için **false** olarak etkin olarak ayarlayın.

5. **Adı**   =  , **O/R tasarımcısına** eklenen nesnelerin sınıf adlarına, çoğullaştırma kuralları uygulamak için **true** olarak Enabled olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
