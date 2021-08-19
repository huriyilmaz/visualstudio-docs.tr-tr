---
title: Arama ifadelerinde mantıksal işleçler (Yardım Görüntüleyicisi)
description: Mantıksal işleçleri ve gelişmiş arama işleçlerini kullanarak veri kaynaklarında arama ifadelerini iyileştirmeyi Microsoft Yardım Görüntüleyicisi.
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 0a3580bdc4d91d2f09fc066919aa5bc66755f23c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109701"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Arama ifadelerinde mantıksal ve gelişmiş işleçler

Yardım Görüntüleyicisi'nde Yardım içeriği aramanızı geliştirmek için mantıksal işleçleri ve gelişmiş arama **işleçlerini kullanabilirsiniz.**

## <a name="logical-operators"></a>Mantıksal işleçler

Mantıksal işleçler, birden çok arama terimlerinin bir arama sorgusunda nasıl birleştir olacağını belirtir. Aşağıdaki tabloda AND, OR, NOT ve NEAR mantıksal işleçleri gösterir.

|Arama yapmak için|Kullanın|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Aynı makaledeki her iki terim de|AND|dib AND paleti|Hem "dib" hem de "palette" içeren konular.|
|Makaledeki terimler|OR|raster OR vektörü|"Tarama" veya "vektör" içeren konular.|
|Aynı makalede ikinci terim olmadan ilk dönem|NOT|"işletim sistemi" NOT DOS|"İşletim sistemi" içeren ancak "DOS" içeren konular.|
|Her iki terim de bir makalede birbirine yakın|Yakın -ındaki|user NEAR kernel|"Çekirdek" yakınlığı içinde "kullanıcı" içeren konular.|

> [!IMPORTANT]
> Arama motorunun bunları tanıması için mantıksal işleçleri tüm büyük harflerle girmeniz gerekir.

## <a name="advanced-operators"></a>Gelişmiş işleçler

Gelişmiş arama işleçleri, bir makalede arama teriminin aranma yeri belirterek içerik aramanızı daraltıyor. Aşağıdaki tabloda dört kullanılabilir gelişmiş arama işleci açık almaktadır.

|Arama yapmak için|Kullanın|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Makale başlığında bir terim|`title:`|`title:binaryreader`|Başlıklarında "binaryreader" içeren konular.|
|Kod örneğinde terim|`code:`|`code:readdouble`|Kod örneğinde "readdouble" içeren konular.|
|Belirli bir programlama dilinin örneğinde yer alan terim|`code:vb:`|`code:vb:string`|Bir kod örneğinde "dize" Visual Basic konu başlıkları.|
|Belirli bir dizin anahtar sözcüğüyle ilişkili bir makale|`keyword:`|`keyword:readbyte`|"Readbyte" index anahtar sözcüğüyle ilişkili konular.|

> [!IMPORTANT]
> Arama motorunun bunları tanıması için iki nokta üst üste olmadan son iki nokta üst üste ile gelişmiş arama işleçleri girmeniz gerekir.

### <a name="programming-languages-for-code-examples"></a>Kod örnekleri için programlama dilleri

çeşitli programlama `code:` dillerinin herhangi biri hakkında içerik bulmak için işleci kullanabilirsiniz. Belirli bir programlama diline yönelik örnekler dönmek için aşağıdaki programlama dili değerlerinden birini kullanın:

|Programlama Dili|Arama işleci söz dizimi|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> işleci, genel olarak kod olarak işaretlenmiş içeriğin aksine yalnızca bir programlama `code:` dili etiketiyle işaretlenmiş içeriği bulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılanlar: Konu arama](../help-viewer/find-topics.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
