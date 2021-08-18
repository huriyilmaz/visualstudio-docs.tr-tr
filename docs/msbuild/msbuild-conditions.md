---
title: MSBuild Koşullar | Microsoft Docs
description: Bir MSBuild koşulu özniteliğine izin verilmiyorsa belirli bir koşul kümesine nasıl uygulana bir dizi koşulu desteklediğini öğrenin.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e0527e1c32be41a9f9bbfe906477329661e63e72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136865"
---
# <a name="msbuild-conditions"></a>MSBuild koşulları

MSBuild, bir öznitelik izin verilmiyorsa uygulana belirli bir koşullar `Condition` kümesi destekler. Aşağıdaki tabloda bu koşullar açıkmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|ise `true` olarak `stringA` `stringB` değerlendirilir.<br /><br /> Örnek:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya boole değerleri için tek tırnak gerekli değildir. Ancak boş değerler için tek tırnak gereklidir. Bu denetim büyük/harfe duyarlı değildir.|
|'`stringA`' != '`stringB`'|ile eşit `true` olup `stringA` olmadığını `stringB` değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya boole değerleri için tek tırnak gerekli değildir. Ancak boş değerler için tek tırnak gereklidir. Bu denetim büyük/harfe duyarlı değildir.|
|\<, >, \<=, >=|İşlecilerin sayısal değerlerini değerlendirir. İlişkisel `true` değerlendirme doğruysa döndürür. İşleçlerin ondalık veya onaltılık sayı veya dört parçalı noktalı sürüm olarak değerlendirmesi gerekir. Onaltılık sayılar "0x" ile başlasın. **Not:**  XML'de ve `<` `>` karakterlerinin kaçmalıdır. Simgesi `<` olarak temsil `&lt;` edildi. Simgesi `>` olarak temsil `&gt;` edildi.|
|Exists(' `stringA` ')|Adı olan `true` bir dosya veya klasörün mevcut olup olduğunu `stringA` değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> Basit alfasayısal dizeler veya boole değerleri için tek tırnak gerekli değildir. Ancak boş değerler için tek tırnak gereklidir.|
|HasTrailingSlash(' `stringA` ')|Belirtilen dizede sonda bir ters eğik çizgi ( ) veya eğik çizgi `true` \\ (/) karakteri bulunsa değerlendirilir.<br /><br /> Örnek:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeler veya boole değerleri için tek tırnak gerekli değildir. Ancak boş değerler için tek tırnak gereklidir.|
|!|`true`İşlecinin değerlendirmesi ise olarak `false` değerlendirilir.|
|`And`|Her iki işlenen `true` de olarak değerlendirilirse olarak `true` değerlendirilir.|
|`Or`|`true`İşlecilerden en az birinin değerlendirmesi ise olarak `true` değerlendirilir.|
|()|içinde yer alan ifadelerin `true` değerlendirmesi için değerlendirilen gruplama `true` mekanizması.|
|$if$ ( %expression% ), $else$, $endif$|Belirtilen değerin geçirilen `%expression%` özel şablon parametresinin dize değeriyle eş olup olmadığını denetler. Koşul `$if$` olarak değerlendirilirse `true` deyimleri çalıştırlır; aksi takdirde `$else$` koşul denetlenir. Koşul `$else$` ise `true` deyimleri çalıştırlır; aksi takdirde koşul ifade `$endif$` değerlendirmesini sona erer.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı.](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)|

Dize yöntemlerini, aşağıdaki örnekte gösterildiği gibi, dizenin yalnızca ilgili kısmını karşılaştırmak için [trimEnd()](/dotnet/api/system.string.trimend) işlevinin .NET Framework ve .NET Core hedef çerçeveleri arasında ayrım yapmak için kullandığı koşullarda kullanabilirsiniz.

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

Bu MSBuild dosyalarında gerçek bir Boole türü yoktur. Boole verileri, boş veya herhangi bir değere ayarlanmış özelliklerde temsil edildi. Bu `'$(Prop)' == 'true'` nedenle, "Prop ise" anlamına gelir, ancak "Prop ise veya başka bir şey `true` `'$(Prop)' != 'false'` `true` ayarlanmamışsa" anlamına gelir.

Boole mantığı yalnızca koşullar bağlamında değerlendirilir, bu nedenle gibi özellik ayarları bir dize olarak temsil edilen (değişken genişletmeden sonra) Boole değerleri olarak `<Prop2>'$(Prop1)' == 'true'</Prop>` değerlendirilmez.  

MSBuild boole değerleri olarak kullanılan dize özellikleriyle daha kolay çalışmak için birkaç özel işleme kuralı uygulanır. Boole sabitleri kabul edilir, bu nedenle `Condition="true"` ve `Condition="false"` beklendiği gibi çalışır. MSBuild Boole olumsuzlama işlecini desteklemek için özel kurallar da içerir. Bu nedenle , 'true' ise genişletilen ve beklediğiniz `$(Prop)` gibi ile eşit olarak `!$(Prop)` `!true` `false` karşılaştıran bir değerdir.

## <a name="comparing-versions"></a>Sürümleri karşılaştırma

, , ve ilişkisel işleçleri, tarafından ayrıştırıldı olarak sürümleri destekler, böylece dört sayısal parçaya sahip `<` `>` sürümleri birbirine `<=` `>=` <xref:System.Version?displayProperty=fullName> karşılaştırabiliyoruz. Örneğin: `'1.2.3.4' < '1.10.0.0'` `true` .

> [!CAUTION]
> `System.Version` karşılaştırmaları, bir veya her iki sürüm dört parçanın hepsini belirtmezken şaşırtıcı sonuçlar üretebilir. Örneğin, sürüm 1.1, sürüm 1.1.0'dan eskidir.

MSBuild, [semantik](property-functions.md#msbuild-version-comparison-functions) sürümle (semver) uyumlu farklı kurallar kümesine sahip sürümleri karşılaştırmak için özellik işlevleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
