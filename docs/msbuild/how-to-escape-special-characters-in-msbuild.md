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
ms.openlocfilehash: f9958ae93e2605ad3c89decb4ac9fabc18102148
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633882"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl yapılır: MSBuild 'de özel karakterleri kaçış

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Karakter örnekleri arasında noktalı virgül (`;`) ve yıldız işareti (`*`) bulunur. Bu özel karakterlerin tüm listesi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).

Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için, `%<xx>`sözdizimi kullanılarak belirtilmelidir; burada `<xx>` karakterin ASCII onaltılık değerini temsil eder.

## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

Özel karakterlerin kullanıldığı bir örnek, öğe listelerinin `Include` özniteliğidir. Örneğin, aşağıdaki öğe listesi iki öğe bildirir: *MyFile.cs* ve *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Adında noktalı virgül içeren bir öğe bildirmek istiyorsanız, noktalı virgülden çıkmak ve MSBuild 'in iki ayrı öğeyi bildirmesinin önüne geçmek için `%<xx>` sözdizimini kullanmanız gerekir. Örneğin, aşağıdaki öğe noktalı virgülden çıkar ve `MyFile.cs;MyClass.cs`adlı bir öğe bildirir.

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
