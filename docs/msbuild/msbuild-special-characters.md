---
title: MSBuild Özel Karakterler | Microsoft Docs
description: Belirli bağlamlarda MSBuild özel kullanım için ayrılmış karakterlerin nasıl ve ne zaman ve nasıl kaçış karakteri olarak kullanılacazı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 43dc7f5841e493eae7628da6014cc3100a869894
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130212188"
---
# <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

MSBuild belirli bağlamlarda özel kullanım için bazı karakterler yedekler. Bu tür karakterleri yalnızca ayrılmış olduğu bağlamda kullanmak istediğiniz durumlarda kaçış karakteri olarak kullanabilirsiniz. Örneğin, yıldız işareti yalnızca bir öğe tanımının ve özniteliklerinde ve çağrısında özel `Include` `Exclude` bir anlamı `CreateItem` vardır. Bir yıldız işaretinin bu bağlamlardan biri içinde yıldız işareti olarak görünmesini istemiyorsanız, yıldız işaretine kaçış karakteri uygulamanız gerekir. Diğer tüm bağlamlarda yıldız işaretlerini görünmesini istediğiniz yere yazmanız gerekir.

 Özel bir karakterden kaçış karakteri için % sözdizimini kullanın; burada karakterin \<xx> \<xx> ASCII onaltılık değerini temsil eder. Daha fazla bilgi için, [bkz. How to: Escape special characters in MSBuild.](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Özel karakterler

 Aşağıdaki tabloda özel MSBuild listele ve listele:

|**Karakter**|**ASCII**|**Ayrılmış kullanım**|
|-------------------|---------------|------------------------|
|%|%25|Meta verilere başvuru|
|$|%24|Başvuru özellikleri|
|@|%40|Öğe listelerine başvuru|
|'|%27|Koşullar ve diğer ifadeler|
|(|%28|Birden çok kullanım|
|)|%29|Birden çok kullanım|
|;|%3B|Liste ayırıcı|
|?|%3F|ve özniteliklerinde dosya adları için `Include` joker `Exclude` karakter|
|*|%2A|ve özniteliklerinde dosya adlarında kullanmak için `Include` joker `Exclude` karakter|

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
- [Öğeler](../msbuild/msbuild-items.md)
