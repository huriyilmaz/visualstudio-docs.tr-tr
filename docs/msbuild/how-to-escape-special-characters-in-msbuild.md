---
title: 'Nasıl yapılır: MSBuild özel karakterleri kaçış | Microsoft Docs'
description: bu karakterleri MSBuild proje dosyalarında değişmez değer olarak kullanabilmeniz için özel karakterleri nasıl atlacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: bd111e53e2b2765614808b808ee1744681bfbce0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136969"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl yapılır: MSBuild özel karakterleri kaçış

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Karakterlere örnek olarak noktalı virgül ( `;` ) ve yıldız işareti ( `*` ) verilebilir. bu özel karakterlerin tüm listesi için bkz. [MSBuild özel karakterler](../msbuild/msbuild-special-characters.md).

Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için, söz dizimi kullanılarak belirtilmelidir `%<xx>` ; burada `<xx>` karakter ASCII onaltılık değerini temsil eder.

## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

Özel karakterlerin kullanıldığı bir örnek, `Include` öğe listelerinin özniteliğidir. Örneğin, aşağıdaki öğe listesi iki öğe bildirir: *Dosyam. cs* ve *MyClass. cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

adında noktalı virgül içeren bir öğe bildirmek istiyorsanız, `%<xx>` noktalı virgülden çıkmak ve MSBuild iki ayrı öğe bildirmesinin önüne geçmek için söz dizimini kullanmanız gerekir. Örneğin, aşağıdaki öğe noktalı virgülden çıkar ve adlı bir öğe bildirir `MyFile.cs;MyClass.cs` .

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Dizeleri kaçış için de bir [Özellik işlevi](../msbuild/property-functions.md) kullanabilirsiniz. Örneğin, yukarıdaki örneğe eşdeğerdir.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>MSBuild özel bir karakteri sabit karakter olarak kullanmak için

Özel karakter yerine gösterimi kullanın `%<xx>` ; burada `<xx>` ASCII karakterinin onaltılı değeri temsil eder. Örneğin, bir yıldız işareti ( `*` ) sabit karakter olarak kullanmak için değerini kullanın `%2A` .

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Öğeler](../msbuild/msbuild-items.md)
