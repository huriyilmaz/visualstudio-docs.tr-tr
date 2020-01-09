---
title: MSBuild özel karakterler | Microsoft Docs
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
ms.openlocfilehash: 5f18339dbbddb09e44e8c5fa53ba517f3d60c025
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566065"
---
# <a name="msbuild-special-characters"></a>MSBuild özel karakterleri
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] belirli bağlamlarda özel kullanım için bazı karakterleri ayırır. Bu karakterleri yalnızca ayrıldıkları bağlamda kullanmak istiyorsanız, bu karakterleri atlamanız gerekir. Örneğin, bir yıldız işareti yalnızca bir öğe tanımının `Include` ve `Exclude` özniteliklerinde ve `CreateItem`çağrılarında özel anlamları vardır. Bir yıldız işareti bu bağlamların birinde bir yıldız işareti olarak görünmesini istiyorsanız, bunu atlamanız gerekir. Diğer her bağlamda, görünmesini istediğiniz yere yıldız işareti yazmanız yeterlidir.

 Özel bir karakteri atlamak için%\<xx > sözdizimini kullanın; burada \<xx >, karakterin ASCII onaltılık değerini temsil eder. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild 'teki özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Özel karakterler
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] özel karakterler listelenmektedir:

|**Karakter**|**ASCII**|**Ayrılmış kullanım**|
|-------------------|---------------|------------------------|
|%|%25|Meta verilere başvuruluyor|
|$|%24|Başvuru özellikleri|
|@|%40|Öğe listelerine başvurma|
|'|%27|Koşullar ve diğer ifadeler|
|;|% 3B|Liste ayırıcı|
|?|% 3F|`Include` ve `Exclude` özniteliklerindeki dosya adları için joker karakter|
|*|%2A|`Include` ve `Exclude` özniteliklerindeki dosya adlarında kullanılacak joker karakter|

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
- [Öğeler](../msbuild/msbuild-items.md)
