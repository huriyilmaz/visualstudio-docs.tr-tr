---
title: Arama Ifadelerinde gelişmiş arama Işleçleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620345"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Arama İfadelerindeki Gelişmiş Arama İşleçleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gelişmiş arama işleçlerini kullanarak, daha karmaşık arama ifadelerini daha basit bir şekilde oluşturarak içerik aramanızı iyileştirebilirsiniz. Aşağıdaki tabloda gösterildiği gibi, bu işleçler bir sorgunun çalıştırıldığı bağlamı kısıtlar.

> [!WARNING]
> Gelişmiş arama işleçlerini, son iki nokta ile ve arama altyapısının bunları tanıması için iki nokta üst üste gelmeden önce boşluk olmadan girmeniz gerekir.

|Arama yapmak için|Kullanın|Örnek|Sonuç|
|-------------------|---------|-------------|------------|
|Konunun başlığındaki bir terim|başlık:|Başlık: BinaryReader|Başlıklarında "BinaryReader" içeren konular.|
|Kod örneğinde bir terim|kod:|kod: Read|Kod örneğinde "readDouble" içeren konular.|
|Belirli bir programlama diline örnek olarak bir terim|kod: vb:|kod: vb: dize|Bir Visual Basic örneğinde "String" içeren konular.|
|Belirli bir dizin anahtar sözcüğüyle ilişkili bir konu|sözcükle|anahtar sözcük: ReadByte|"ReadByte" Dizin anahtar sözcüğüyle ilişkili konular.|

 Birkaç programlama dili ile ilgili içerik bulmak için Code: işlecini kullanabilirsiniz, ancak sonuçları yalnızca belirli bir programlama diliyle işaretlenmiş içerikler için döndürür. Aşağıdaki tabloda, bu işlecin desteklediği programlama dilleri listelenmektedir:

|Programlama Dili|Kullanın|
|--------------------------|---------|
|Visual Basic|kod: vb<br /><br /> veya<br /><br /> kod: VisualBasic|
|C#|kod: c #<br /><br /> veya<br /><br /> kod: CSharp|
|C++|kod: cpp<br /><br /> veya<br /><br /> kod: c++<br /><br /> veya<br /><br /> kod: CPlusPlus|
|F#|kod: f #<br /><br /> veya<br /><br /> kod: FSharp|
|JavaScript|kod: JavaScript<br /><br /> veya<br /><br /> kod: JS|
|XAML|kod: xaml|

## <a name="see-also"></a>Ayrıca Bkz.
 [Arama İfadelerindeki mantıksal işleçler](../ide/logical-operators-in-search-expressions.md) [tam metin arama ipuçları](../ide/full-text-search-tips.md)
