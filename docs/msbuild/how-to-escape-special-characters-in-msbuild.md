---
title: 'Nasıl MSBuild |: MSBuild | Microsoft Docs'
description: Bu karakterleri proje dosyalarında değişmez karakter olarak kullanmak için özel karakterlerden MSBuild öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625731"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl MSBuild

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Karakterlere örnek olarak noktalı virgül ( `;` ) ve yıldız işareti ( ) yer `*` alır. Bu özel karakterlerin tam listesi için bkz. [MSBuild karakterleri.](../msbuild/msbuild-special-characters.md)

Bu özel karakterleri bir proje dosyasında değişmez değer olarak kullanmak için söz dizimi kullanılarak belirtilmelidir. Burada, karakterin ASCII onaltılık değerini `%<xx>` `<xx>` temsil eder.

## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

Öğe listelerinin özniteliğinde özel karakterlerin `Include` kullanılmaya bir örneğidir. Örneğin, aşağıdaki öğe listesi iki öğe bildirer: *MyFile.cs* ve *MyClass.cs*.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Adda noktalı virgül içeren bir öğe bildirerek noktalı virgülden kaçarak iki ayrı öğe `%<xx>` MSBuild istemeniz gerekir. Örneğin, aşağıdaki öğe noktalı virgülden kaçarak adlı bir öğe `MyFile.cs;MyClass.cs` bildirer.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Dizeleri kaçış olarak kullanmak [için bir özellik](../msbuild/property-functions.md) işlevi de kullanabilirsiniz. Örneğin, bu yukarıdaki örnekle eşdeğerdir.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Özel bir MSBuild sabit karakter olarak kullanmak için

ASCII karakterinin onaltılık değerini temsil eden özel karakter yerine `%<xx>` `<xx>` bu ifadeyi kullanın. Örneğin, değişmez karakter olarak yıldız işareti ( `*` ) kullanmak için değerini `%2A` kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Öğeler](../msbuild/msbuild-items.md)
