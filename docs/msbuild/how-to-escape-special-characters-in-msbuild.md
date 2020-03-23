---
title: 'Nasıl: MSBuild Özel Karakterler Kaçış | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633882"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Nasıl: MSBuild özel karakterler kaçış

Belirli karakterlerin MSBuild proje dosyalarında özel anlamı vardır. Karakterlere örnek olarak yarı kolon`;`( ) ve`*`yıldız işaretleri verilebilir. Bu özel karakterlerin tam listesi için [MSBuild özel karakterleri](../msbuild/msbuild-special-characters.md)bölümüne bakın.

Bu özel karakterleri proje dosyasında gerçek olarak kullanabilmek için, karakterin ASCII `<xx>` hexadecimal değerini temsil eden sözdizimi `%<xx>`kullanılarak belirtilmelidir.

## <a name="msbuild-special-characters"></a>MSBuild özel karakterleri

Özel karakterlerin kullanıldığı bir örnek madde `Include` listelerinin özniteliğidir. Örneğin, aşağıdaki madde listesi iki öğe bildirir: *MyFile.cs* ve *MyClass.cs.*

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

Adında bir yarı nokta nokta içeren bir öğeyi bildirmek istiyorsanız, yarı sütundan kaçmak ve MSBuild'in `%<xx>` iki ayrı öğe beyan etmesini önlemek için sözdizimini kullanmanız gerekir. Örneğin, aşağıdaki öğe yarı iki nokta üst üste `MyFile.cs;MyClass.cs`kaçar ve adlı bir öğe yi bildirir.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

Dizeleri kaçmak için bir [özellik işlevi](../msbuild/property-functions.md) de kullanabilirsiniz. Örneğin, bu yukarıdaki örneğe eşdeğerdir.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>MsBuild özel karakterini gerçek bir karakter olarak kullanmak için

ASCII `%<xx>` karakterinin hexadecimal değerini temsil eden `<xx>` özel karakterin yerine gösterimi kullanın. Örneğin, yıldız işaretini (`*`) gerçek bir karakter olarak `%2A`kullanmak için değeri kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Msbuild](../msbuild/msbuild.md)
- [Öğeler](../msbuild/msbuild-items.md)
