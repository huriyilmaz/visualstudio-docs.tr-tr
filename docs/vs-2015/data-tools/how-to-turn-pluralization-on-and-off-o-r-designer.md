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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665943"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Nasıl yapılır: Çoğullaştırmayı açıp kapatma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, **Sunucu Gezgini**veritabanı Gezgini son görüntülenen adlara sahip veritabanı nesnelerini / **Database Explorer** [Visual Studio 'daki LINQ to SQL araçlarına](../data-tools/linq-to-sql-tools-in-visual-studio2.md)sürüklediğinizde, oluşturulan varlık sınıflarının adları plural 'den tekil 'e değiştirilir. Bu, Örneklenmiş varlık sınıfının tek bir veri kaydıyla eşlendiği olguyu daha doğru bir şekilde temsil etmek için yapılır. Örneğin, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sınıf yalnızca tek bir müşteri için veri tutacağından, müşteri adlı bir varlık sınıfındaki sonuçlara müşteriler tablosu ekleme.

> [!NOTE]
> Pluralization, varsayılan olarak yalnızca Visual Studio 'nun Ingilizce sürümünde bulunur.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Çoğullaştırma 'ı açmak ve kapatmak için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Seçenekler** Iletişim kutusunda **veritabanı araçları**' nı genişletin.

> [!NOTE]
> **Veritabanı araçları** düğümü görünür değilse **tüm ayarları göster** ' i seçin.

1. **O/R Tasarımcısı**' na tıklayın.

2. **Adları** **Enabled**  =  **False** , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sınıf adlarını değiştirmemesi adına ayarlamak için false olarak etkin olarak ayarlayın.

3. ' A eklenen nesnelerin sınıf adlarına plurselleştirme kuralları uygulamak için **Adların pluralseli** değerini **etkin**olarak ayarlayın  =  **True** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio 'da LINQ to SQL [LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)
