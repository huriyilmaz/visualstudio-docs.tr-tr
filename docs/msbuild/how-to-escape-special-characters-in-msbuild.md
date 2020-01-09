---
title: "Nasıl yapılır: MSBuild 'de özel karakterleri kaçış | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955739372605b9e4f9fe58f73669322e2724de31
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595013"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl yapılır: MSBuild 'de özel karakterleri kaçış

Belirli karakterlerin [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyalarında özel anlamları vardır. Karakter örnekleri arasında noktalı virgül (`;`) ve yıldız işareti (`*`) bulunur. Bu özel karakterlerin tüm listesi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).

Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için, `%<xx>`sözdizimi kullanılarak belirtilmelidir; burada `<xx>` karakterin ASCII onaltılık değerini temsil eder.

## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

Özel karakterlerin kullanıldığı bir örnek, öğe listelerinin `Include` özniteliğidir. Örneğin, aşağıdaki öğe listesi iki öğe bildirir: *MyFile.cs* ve *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Adında noktalı virgül içeren bir öğe bildirmek istiyorsanız, noktalı virgülden çıkmak ve [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] iki ayrı öğe bildirmesinin önlenmesi için `%<xx>` sözdizimini kullanmanız gerekir. Örneğin, aşağıdaki öğe noktalı virgülden çıkar ve `MyFile.cs;MyClass.cs`adlı bir öğe bildirir.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Dizeleri kaçış için de bir [Özellik işlevi](../msbuild/property-functions.md) kullanabilirsiniz. Örneğin, yukarıdaki örneğe eşdeğerdir.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Bir MSBuild özel karakterini sabit karakter olarak kullanmak için

Özel karakterin yerine `%<xx>` gösterimini kullanın; burada `<xx>` ASCII karakterinin onaltılı değerini temsil eder. Örneğin, bir yıldız işareti (`*`) sabit karakter olarak kullanmak için, `%2A`değerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Öğeler](../msbuild/msbuild-items.md)
