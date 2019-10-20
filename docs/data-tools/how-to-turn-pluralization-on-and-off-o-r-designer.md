---
title: 'Nasıl yapılır: plurseli açma ve kapatma (O-R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 578a6333d1206553db50ce81f2f499da0481456d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648340"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: plurselleştirmeyi açma ve kapatma (O/R Tasarımcısı)
Varsayılan olarak, **Sunucu Gezgini** veya **veritabanı Gezgini** son görüntülenen adlara sahip veritabanı nesnelerini [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde, oluşturulan varlık sınıflarının adları çoğul olarak değiştirilir Tekil. Bu, Örneklenmiş varlık sınıfının tek bir veri kaydıyla eşlendiği olguyu daha doğru bir şekilde temsil etmek için yapılır. Örneğin, **u/R tasarımcısına** `Customers` tablo eklemek, sınıf yalnızca tek bir müşteri için veri tutacağından, `Customer` adlı bir varlık sınıfına neden olur.

> [!NOTE]
> Pluralization, varsayılan olarak yalnızca Visual Studio 'nun Ingilizce sürümünde bulunur.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma 'ı açmak ve kapatmak için

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Seçenekler** Iletişim kutusunda **veritabanı araçları**' nı genişletin.

    > [!NOTE]
    > **Veritabanı araçları** düğümü görünür değilse **tüm ayarları göster** ' i seçin.

3. **O/R Tasarımcısı**' na tıklayın.

4. **Adların** , sınıf adlarını değiştirmemesi adına, **O/R tasarımcısını** ayarlamak için**false**  =  **etkin** olarak ayarlayın.

5. **Adların çoğullaştırma** özelliğini **etkin** **olarak ayarlayın  = ,** **O/R tasarımcısına**eklenen nesnelerin sınıf adlarına plurselleştirme kuralları uygular.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)