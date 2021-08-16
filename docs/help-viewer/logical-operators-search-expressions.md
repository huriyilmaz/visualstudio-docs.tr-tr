---
title: Arama İfadelerindeki mantıksal işleçler (Yardım Görüntüleyicisi)
description: Microsoft Yardım Görüntüleyicisi içinde arama ifadelerini iyileştirmek için mantıksal işleçler ve gelişmiş arama işleçlerini nasıl kullanacağınızı anlayın.
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
ms.openlocfilehash: 5302c5a59595b98c601f98b1fbe6ca1168106f52aceb12081a4cf37875cf258e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358408"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Arama ifadelerinde mantıksal ve gelişmiş işleçler

**Yardım görüntüleyicisindeki** yardım içeriği aramanızı iyileştirmek için mantıksal işleçleri ve gelişmiş arama işleçlerini kullanabilirsiniz.

## <a name="logical-operators"></a>Mantıksal işleçler

Mantıksal işleçler, birden çok arama terimlerinin bir arama sorgusunda nasıl birleştirilmesi gerektiğini belirtir. Aşağıdaki tabloda, mantıksal işleçler ve, veya, DEĞIL ve YAKıNıNDA gösterilmektedir.

|Arama yapmak için|Kullanın|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Aynı makalede her iki terim|AND|DIB ve palet|Hem "DIB" hem de "palet" içeren konular.|
|Bir makalede her iki terim|OR|Raster veya vektör|"Tarama" ya da "vektör" içeren konular.|
|Aynı makalede ikinci terim olmadan ilk terim|NOT|"işletim sistemi" DOS DEĞIL|"İşletim sistemi" ("DOS" değil) içeren konular.|
|Her iki terim de bir makalede birlikte yakın|KALEMIN|çekirdeğin YAKıNıNDA Kullanıcı|"Kernel" öğesinin yakın yakınına "user" içeren konular.|

> [!IMPORTANT]
> Arama altyapısının bunları tanıması için tüm büyük harflerle mantıksal işleçler girmeniz gerekir.

## <a name="advanced-operators"></a>Gelişmiş işleçler

Gelişmiş Arama işleçleri, arama terimini nerede araytığın bir makalesinde belirterek içerik Aramanızı iyileştirin. Aşağıdaki tabloda, kullanılabilen dört gelişmiş arama işleci açıklanmaktadır.

|Arama yapmak için|Kullanın|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Makalenin başlığındaki bir terim|`title:`|`title:binaryreader`|Başlıklarında "BinaryReader" içeren konular.|
|Kod örneğinde bir terim|`code:`|`code:readdouble`|Kod örneğinde "readDouble" içeren konular.|
|Belirli bir programlama diline örnek olarak bir terim|`code:vb:`|`code:vb:string`|Visual Basic bir kod örneğinde "string" içeren konular.|
|Belirli bir dizin anahtar sözcüğüyle ilişkili bir makale|`keyword:`|`keyword:readbyte`|"ReadByte" Dizin anahtar sözcüğüyle ilişkili konular.|

> [!IMPORTANT]
> Gelişmiş arama işleçlerini, son iki nokta ile ve arama altyapısının bunları tanıması için iki nokta üst üste gelmeden önce boşluk olmadan girmeniz gerekir.

### <a name="programming-languages-for-code-examples"></a>Kod örnekleri için programlama dilleri

`code:`Birkaç programlama dilinin içeriğini bulmak için işlecini kullanabilirsiniz. Belirli bir programlama diline yönelik örnekleri döndürmek için aşağıdaki programlama dili değerlerinden birini kullanın:

|Programlama Dili|Arama işleci sözdizimi|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:`İşleci yalnızca bir programlama dili etiketiyle işaretlenmiş içeriği bulur. Bu, kod olarak genel olarak işaretlenmiş içeriğin aksine.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: konu arama](../help-viewer/find-topics.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)
