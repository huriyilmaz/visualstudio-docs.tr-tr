---
title: MSBuild Koşulları | Microsoft Dokümanlar
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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f13910e2481e574e18c7a8efaee6601137c0720
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224478"
---
# <a name="msbuild-conditions"></a>MSBuild koşulları

MSBuild, bir öznitelik izin verilen her `Condition` yerde uygulanabilecek belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Eğer eşitse `true` `stringA` `stringB`değerlendirir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir. Bu çek büyük bir olay dır duyarsız.|
|'`stringA`' != '`stringB`'|`true` Eğer `stringB`eşit `stringA` değilse değerlendirir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir. Bu çek büyük bir olay dır duyarsız.|
|\<, >, \<=, >=|Operandların sayısal değerlerini değerlendirir. İlişkisel değerlendirme doğruysa döndürür. `true` Operands ondalık veya hexadecimal sayı değerlendirmek gerekir. Hexadecimal sayılar "0x" ile başlamalıdır. **Not:**  XML'de, karakterler `<` `>` ve kaçılmalıdır. Sembol `<` olarak `&lt;`temsil edilir. Sembol `>` olarak `&gt;`temsil edilir.|
|Var('`stringA`')|Ada `stringA` `true` sahip bir dosya veya klasörün var olup olmadığını değerlendirir.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|HasTrailingSlash('`stringA`')|Belirtilen dize, geriye doğru çizgi ( `true` )\\veya ileri eğik çizgi (/) karakteri nin olup olmadığını değerlendirir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|!|Operand'ın `true` değerlendirilip `false`değerlendirmeme.|
|And|Her iki `true` operands değerlendirmek `true`eğer değerlendirir.|
|Veya|Operandlardan en az birinin .'a `true` `true`göre değerlendirilip değerlendirmeyeceklerini değerlendirir.|
|()|İçerde yer alan `true` ifadelerin `true`değerlendirilmesi için değerlendiren gruplandırma mekanizması.|
|$if$ ( %ifade% ), $else$, $endif$|Belirtilen `%expression%` özel şablon parametresinin dize değeriyle eşleşip eşleşmediğini denetler. `$if$` Koşul , ifadeleri `true`çalıştırılır; aksi `$else$` takdirde, durum kontrol edilir. `$else$` Koşul `true`ise , ifadeleri çalıştırılır; aksi takdirde, durum ifade değerlendirmesini `$endif$` sona erdirer.<br /><br /> Kullanım örnekleri için [Visual Studio proje/öğe şablonu parametre mantığına](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)bakın.|

Dize yöntemlerini, .NET Framework ve .NET Core hedef çerçeveleri arasında ayrım yapmak için dizeyalnızca ilgili bölümünü karşılaştırmak için [TrimEnd()](/dotnet/api/system.string.trimend) işlevinin kullanıldığı aşağıdaki örnekte gösterildiği gibi koşullarda kullanabilirsiniz.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd('0123456789.'))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [Walkthrough: Sıfırdan bir MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
