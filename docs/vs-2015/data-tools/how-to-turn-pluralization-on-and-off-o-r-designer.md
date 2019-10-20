---
title: 'Nasıl yapılır: plurselleştirmeyi açma ve kapatma (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665943"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: plurselleştirmeyi açma ve kapatma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, **Sunucu Gezgini** **veritabanı Gezgini** / son görüntülenen adlara sahip veritabanı nesnelerini [Visual Studio 'daki LINQ to SQL araçlar](../data-tools/linq-to-sql-tools-in-visual-studio2.md)üzerine sürüklediğinizde, oluşturulan varlık sınıflarının adları plural 'den olarak değiştirilir Tekil. Bu, Örneklenmiş varlık sınıfının tek bir veri kaydıyla eşlendiği olguyu daha doğru bir şekilde temsil etmek için yapılır. Örneğin, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bir Customers tablosu eklemek, sınıf yalnızca tek bir müşteri için veri tutacağından, müşteri adlı bir varlık sınıfına neden olur.

> [!NOTE]
> Pluralization, varsayılan olarak yalnızca Visual Studio 'nun Ingilizce sürümünde bulunur.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma 'ı açmak ve kapatmak için

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Seçenekler** Iletişim kutusunda **veritabanı araçları**' nı genişletin.

> [!NOTE]
> **Veritabanı araçları** düğümü görünür değilse **tüm ayarları göster** ' i seçin.

1. **O/R Tasarımcısı**' na tıklayın.

2. **Adların** , sınıf adlarını değiştirmemesi için **,** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ayarlamak üzere  = **false** olarak ayarlayın.

3. **Adların pluralselleştirilmesi** , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] eklenen nesnelerin sınıf adlarına plurme kuralları **uygulamak Için** **true  =  true** olarak ayarlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio 'da LINQ to SQL [LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)
