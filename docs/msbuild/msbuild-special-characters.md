---
title: MSBuild Özel Karakterler | Microsoft Dokümanlar
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdc9024db06fe27fab5dfdf9589300a6eb671368
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633219"
---
# <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

MSBuild, belirli bağlamlarda özel kullanım için bazı karakterler ayırır. Bu tür karakterlerden sadece bu tür karakterleri tam anlamıyla saklı oldukları bağlamda kullanmak istiyorsanız kaçabilirsiniz. Örneğin, yıldız işaretinin yalnızca madde `Include` tanımının `Exclude` özniteliklerinde ve ''ye `CreateItem`yapılan aramalarda özel bir anlamı vardır. Yıldız işaretinin bu bağlamlardan birinde yıldız işareti olarak görünmesini istiyorsanız, ondan kaçmalısınız. Diğer tüm bağlamlarda, yıldız işaretinin görünmesini istediğiniz yere yazmanız gereken yıldız işaretini yazmanız.

 Özel bir karakterden kaçmak için,\<xx> \<karakterin ASCII hexadecimal değerini temsil ettiği sözdizimini % xx> kullanın. Daha fazla bilgi için [bkz: MSBuild'teki özel karakterlerden kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Özel karakterler

 Aşağıdaki tabloda MSBuild özel karakterleri listele:

|**Karakter**|**Ascıı**|**Ayrılmış kullanım**|
|-------------------|---------------|------------------------|
|%|%25|Meta verilere başvurma|
|$|%24|Başvuru özellikleri|
|@|%40|Madde listelerine başvurma|
|'|%27|Koşullar ve diğer ifadeler|
|;|%3B|Liste ayırıcı|
|?|%3F|Dosya adları `Include` ve `Exclude` öznitelikleri için Joker karakter|
|*|%2A|Dosya adlarında ve `Include` `Exclude` özniteliklerde kullanılmak üzere Joker karakter|

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
- [Öğeler](../msbuild/msbuild-items.md)
