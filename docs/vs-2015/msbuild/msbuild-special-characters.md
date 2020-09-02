---
title: MSBuild özel karakterler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a54f446cb82b3181ee057d4887b37940868a5920
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150761"
---
# <a name="msbuild-special-characters"></a>MSBuild Özel Karakterleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] belirli bağlamlarda özel kullanım için bazı karakterleri ayırır. Bu karakterleri yalnızca ayrıldıkları bağlamda kullanmak istiyorsanız, bu karakterleri atlamanız gerekir. Örneğin, bir yıldız işareti yalnızca `Include` `Exclude` bir öğe tanımının ve özniteliklerinde, öğesine yapılan çağrılar için özel anlamı vardır `CreateItem` . Bir yıldız işareti bu bağlamların birinde bir yıldız işareti olarak görünmesini istiyorsanız, bunu atlamanız gerekir. Diğer her bağlamda, görünmesini istediğiniz yere yıldız işareti yazmanız yeterlidir.  
  
 Özel bir karakterden çıkmak için%*xx*sözdizimini kullanın; burada *xx* , karakterin ASCII onaltılık değerini temsil eder. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild 'Teki özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Özel Karakterler  
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özel karakterler listelenmektedir:  
  
|**İnde**|**ASCII**|**Ayrılmış kullanım**|  
|-------------------|---------------|------------------------|  
|%|%25|Meta verilere başvuruluyor|  
|$|%24|Başvuru özellikleri|  
|@|%40|Öğe listelerine başvurma|  
|'|%27|Koşullar ve diğer ifadeler|  
|;|% 3B|Liste ayırıcı|  
|?|% 3F|`Include`Ve özniteliklerinde dosya adları için joker karakter `Exclude`|  
|*|%2A|`Include`Ve özniteliklerindeki dosya adlarında kullanılmak üzere joker karakter `Exclude`|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)   
 [Öğeler](../msbuild/msbuild-items.md)
