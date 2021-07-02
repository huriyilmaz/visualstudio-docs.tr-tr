---
title: MSBuild Koşullar | Microsoft Docs
description: MSBuild, koşul özniteliğine izin verildiğinde uygulanabilecek belirli bir koşul kümesini nasıl desteklediğini öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d72b69b2c80c4e20b5a4dadae18764a138210295
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222714"
---
# <a name="msbuild-conditions"></a>MSBuild koşulları

MSBuild `Condition` , bir özniteliğe izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Eşitse olarak `true` değerlendirilir `stringA` `stringB` .<br /><br /> Örneğin:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir. Bu denetim büyük/küçük harfe duyarlıdır.|
|'`stringA`' != '`stringB`'|`true` `stringA` Eşit değilse olarak değerlendirilir `stringB` .<br /><br /> Örneğin:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir. Bu denetim büyük/küçük harfe duyarlıdır.|
|\<, >, \<=, >=|İşlenenlerinin sayısal değerlerini değerlendirir. `true`İlişkisel değerlendirmenin doğru olup olmadığını döndürür. İşlenenler bir ondalık ya da onaltılık sayı ya da dört bölümlü noktalı bir sürüm olarak değerlendirilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de karakterler `<` ve `>` kaçışlı olmalıdır. Sembol `<` olarak temsil edilir `&lt;` . Sembol `>` olarak temsil edilir `&gt;` .|
|Var (' `stringA` ')|`true`Ada sahip bir dosya veya klasör varsa olarak değerlendirilir `stringA` .<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|Hastrailingeðik çizgi (' `stringA` ')|`true`Belirtilen dize bir ters eğik çizgi ( \\ ) veya eğik çizgi (/) karakteri içeriyorsa olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|!|İşlenen olarak değerlendirilir `true` `false` .|
|`And`|`true`Her iki işlenen de olarak değerlendirilir `true` .|
|`Or`|`true`İşlenenlerin en az biri olarak değerlendiriliyorsa, olarak değerlendirilir `true` .|
|()|`true`İçinde içerilen ifadeler olarak değerlendirilen gruplandırma mekanizması `true` .|
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` özel şablon parametresinin dize değeri ile eşleşip eşleşmediğini denetler. `$if$`Koşul olarak değerlendirilirse `true` , deyimleri çalıştırılır; Aksi takdirde `$else$` koşul denetlenir. `$else$`Koşul ise `true` , deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşul ifade değerlendirmesini sonlandırır.<br /><br /> kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

aşağıdaki örnekte gösterildiği gibi, koşullarda dize yöntemlerini, .NET Framework ve .net Core hedef çerçevelerini birbirinden ayırt etmek için, dizenin yalnızca ilgili bölümünü karşılaştırmak üzere kullanılan [trimend ()](/dotnet/api/system.string.trimend) işlevinin kullanıldığı şekilde kullanabilirsiniz.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

MSBuild proje dosyalarında, doğru boole türü yoktur. Boole verileri boş olabilecek veya herhangi bir değere ayarlanmış özelliklerde temsil edilir. Bu nedenle, `'$(Prop)' == 'true'` "Eğer Prop ise" anlamına gelir `true` , ancak `'$(Prop)' != 'false'` "Eğer Prop ise `true` veya ayarlandıysa ya da başka bir şekilde ayarlanırsa" anlamına gelir.

Boolean Logic yalnızca koşulların bağlamında değerlendirilir, bu nedenle gibi özellik ayarları `<Prop2>'$(Prop1)' == 'true'</Prop>` , Boole değerleri olarak değerlendirilmez bir dize (değişken genişletmeden sonra) olarak gösterilir.  

MSBuild, Boolean değer olarak kullanılan dize özellikleriyle çalışmayı kolaylaştırmak için birkaç özel işlem kuralı uygular. Boole sabit değerleri kabul edilir `Condition="true"` ve `Condition="false"` beklendiği gibi çalışır. MSBuild Boolean olumsuzlama işlecini desteklemek için özel kurallar da içerir. Bu nedenle, `$(Prop)` ' true ' ise,, `!$(Prop)` `!true` bekledikçe, ve şuna eşit olarak karşılaştırılmaktadır `false` .

## <a name="comparing-versions"></a>Sürümleri karşılaştırma

İlişkisel işleçler `<` , `>` ,, `<=` ve `>=` tarafından ayrıştırılabilen destek sürümleri <xref:System.Version?displayProperty=fullName> , bu sayede dört sayısal parçaya sahip sürümleri birbirleriyle karşılaştırabilirsiniz. Örneğin `'1.2.3.4' < '1.10.0.0'` , `true` .

> [!CAUTION]
> `System.Version` bir veya iki sürüm dört parçayı de belirtmediğinde karşılaştırmalar, ortaya çıkmış sonuçlar üretebilir. Örneğin sürüm 1,1, sürüm 1.1.0 'dan daha eski.

MSBuild, anlamsal sürüm oluşturma (semver) ile uyumlu farklı kurallar kümesine sahip [sürümleri karşılaştırmak için özellik işlevleri](property-functions.md#msbuild-version-comparison-functions) sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
