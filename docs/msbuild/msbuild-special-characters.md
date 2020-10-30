---
title: MSBuild özel karakterler | Microsoft Docs
description: Belirli bağlamlarda özel kullanım için MSBuild ayrılmış karakterleri ve bu karakterlerin ne zaman ve nasıl kaçış hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67de0c2e5aa35fa3a1f54e26f425f4b0916cb428
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049114"
---
# <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

MSBuild belirli bağlamlarda özel kullanım için bazı karakterleri ayırır. Bu karakterleri yalnızca ayrıldıkları bağlamda kullanmak istiyorsanız, bu karakterleri atlamanız gerekir. Örneğin, bir yıldız işareti yalnızca `Include` `Exclude` bir öğe tanımının ve özniteliklerinde, öğesine yapılan çağrılar için özel anlamı vardır `CreateItem` . Bir yıldız işareti bu bağlamların birinde bir yıldız işareti olarak görünmesini istiyorsanız, bunu atlamanız gerekir. Diğer her bağlamda, görünmesini istediğiniz yere yıldız işareti yazmanız yeterlidir.

 Özel bir karakterden çıkmak için, \<xx> \<xx> karakterin ASCII onaltılık değerini temsil eden% sözdizimini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild 'teki özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Özel karakterler

 Aşağıdaki tabloda MSBuild özel karakterleri listelenmiştir:

|**Karakter**|**ASCII**|**Ayrılmış kullanım**|
|-------------------|---------------|------------------------|
|%|%25|Meta verilere başvuruluyor|
|$|%24|Başvuru özellikleri|
|@|%40|Öğe listelerine başvurma|
|'|%27|Koşullar ve diğer ifadeler|
|;|% 3B|Liste ayırıcı|
|?|% 3F|`Include`Ve özniteliklerinde dosya adları için joker karakter `Exclude`|
|*|%2A|`Include`Ve özniteliklerindeki dosya adlarında kullanılmak üzere joker karakter `Exclude`|

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
- [Öğeler](../msbuild/msbuild-items.md)
