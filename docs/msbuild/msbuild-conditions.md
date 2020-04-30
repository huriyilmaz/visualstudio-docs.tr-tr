---
title: MSBuild Koşulları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61ffb650a87fa992a07d749687498cbb8ec6482d
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586828"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları

MSBuild, bir `Condition` özniteliğe izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|`stringA` Eşitse `stringB`olarak `true` değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir. Bu denetim büyük/küçük harfe duyarlıdır.|
|'`stringA`' != '`stringB`'|Eşit değilse `true` olarak `stringA` değerlendirilir `stringB`.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir. Bu denetim büyük/küçük harfe duyarlıdır.|
|\<, >, \<=, >=|İşlenenlerinin sayısal değerlerini değerlendirir. İlişkisel `true` değerlendirmenin doğru olup olmadığını döndürür. İşlenenler bir Decimal veya on altılı sayı olarak değerlendirilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de karakterler `<` ve `>` kaçışlı olmalıdır. Sembol `<` olarak `&lt;`temsil edilir. Sembol `>` olarak `&gt;`temsil edilir.|
|Var ('`stringA`')|Ada `stringA` sahip `true` bir dosya veya klasör varsa olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|Hastrailingeðik çizgi (`stringA`' ')|Belirtilen dize `true` bir ters eğik çizgi (\\) veya eğik çizgi (/) karakteri içeriyorsa olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|!|`true` İşlenen olarak değerlendirilir `false`.|
|And|`true` Her iki işlenen de olarak `true`değerlendirilir.|
|Veya|İşlenenlerin `true` en az biri olarak `true`değerlendiriliyorsa, olarak değerlendirilir.|
|()|İçinde içerilen ifadeler olarak `true` `true`değerlendirilen gruplandırma mekanizması.|
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` özel şablon parametresinin dize değeri ile eşleşip eşleşmediğini denetler. `$if$` Koşul olarak `true`değerlendirilirse, deyimleri çalıştırılır; Aksi takdirde, `$else$` koşul denetlenir. `$else$` Koşul ise `true`, deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşul ifade değerlendirmesini sonlandırır.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

Aşağıdaki örnekte gösterildiği gibi, koşullarda dize yöntemlerini, .NET Framework ve .NET Core hedef çerçevelerini birbirinden ayırt etmek için, dizenin yalnızca ilgili bölümünü karşılaştırmak üzere kullanılan [TrimEnd ()](/dotnet/api/system.string.trimend) işlevinin kullanıldığı şekilde kullanabilirsiniz.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789.`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
