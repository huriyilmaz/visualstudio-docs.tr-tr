---
title: 'Nasıl yapılır: plurseli açma ve kapatma (O-R Designer)'
description: Nesne İlişkisel Tasarımcısı (O/R Designer) ' de plurselleştirmeyi açma ve kapatma hakkında bilgi sahibi olun. Varsayılan ayar, çoğul adlarını tekil olarak dönüştürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ea872d96e59365f3dbef5dc3568641c30e51606
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434902"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: Çoğullaştırmayı açıp kapatma (O/R Tasarımcısı)
Varsayılan olarak, **Sunucu Gezgini** veya **veritabanı Gezgini** son görüntülenen adlara sahip veritabanı nesnelerini [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde, oluşturulan varlık sınıflarının adları plural 'den tekil 'e değiştirilir. Bu, Örneklenmiş varlık sınıfının tek bir veri kaydıyla eşlendiği olguyu daha doğru bir şekilde temsil etmek için yapılır. Örneğin, `Customers` **u/R tasarımcısına** tablo eklemek, `Customer` sınıfı yalnızca tek bir müşteri için veri tutacağından, adlı bir varlık sınıfı ile sonuçlanır.

> [!NOTE]
> Pluralization, varsayılan olarak yalnızca Visual Studio 'nun Ingilizce sürümünde bulunur.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma 'ı açmak ve kapatmak için

1. **Tools** (Araçlar) menüsünde **Options** ’a (Seçenekler) tıklayın.

2. **Seçenekler** Iletişim kutusunda **veritabanı araçları** ' nı genişletin.

    > [!NOTE]
    > **Veritabanı araçları** düğümü görünür değilse **tüm ayarları göster** ' i seçin.

3. **O/R Tasarımcısı** ' na tıklayın.

4. **Adların** **Enabled**  =  , sınıf adlarını değiştirmemesi adına, **O/R tasarımcısını** ayarlamak için **false** olarak etkin olarak ayarlayın.

5. **Adı** **Enabled**  =  , **O/R tasarımcısına** eklenen nesnelerin sınıf adlarına, çoğullaştırma kuralları uygulamak için **true** olarak Enabled olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
