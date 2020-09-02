---
title: "Nasıl yapılır: MSBuild 'de özel karakterleri kaçış | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178351"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl Yapılır: MSBuild'de Kaçış Özel Karakterleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli karakterlerin proje dosyalarında özel anlamı vardır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Karakter örnekleri arasında noktalı virgül (;) ve yıldız işaretleri (*). Bu özel karakterlerin tüm listesi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).  
  
 Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için, *xx* , karakterin ASCII onaltılık değerini temsil eden%*xx*sözdizimi kullanılarak belirtilmelidir.  
  
## <a name="msbuild-special-characters"></a>MSBuild Özel Karakterleri  
 Özel karakterlerin kullanıldığı bir örnek, `Include` öğe listelerinin özniteliğidir. Örneğin, aşağıdaki öğe listesi iki öğe bildirir: `MyFile.cs` ve `MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Adında noktalı virgül içeren bir öğe bildirmek istiyorsanız, noktalı virgülden çıkmak ve*xx* [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] iki ayrı öğe bildirmenizi engellemek için% xx söz dizimini kullanmanız gerekir. Örneğin, aşağıdaki öğe noktalı virgülden çıkar ve adlı bir öğe bildirir `MyFile.cs;MyClass.cs` .  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Bir MSBuild özel karakterini sabit karakter olarak kullanmak için  
  
- Özel karakterin yerine%*xx* gösterimini kullanın; burada *xx* , ASCII karakterinin onaltılı değerini temsil eder. Örneğin, bir yıldız işareti (*) sabit karakter olarak kullanmak için değerini kullanın `%2A` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md) [öğeleri](../msbuild/msbuild-items.md)
