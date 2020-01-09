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
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9576bdf06593ae3cde3bc29e2585a7ab475671a3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566624"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bir `Condition` özniteliğine izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Eğer `stringA` eşittir `stringB` ise `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|
|'`stringA`' != '`stringB`'|`stringA` `stringB`eşitse `true` değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|
|\<, >, \<=, >=|İşleçlerin sayısal değerlerini karşılaştırır. İlişkisel değerlendirme doğru olması durumunda `true` döndürür. İşlenenler, bir ondalık ya da onaltılık sayıya dönüşebilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de, `<` ve `>` karakterlerin kaçışlı olması gerekir. `<` simgesi `&lt;` olarak temsil edilir. `>` simgesi `&gt;` olarak temsil edilir.|
|Exists('`stringA`')|`stringA` adında bir dosya veya klasör varsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|
|Hastrailingeðik çizgi ('`stringA`')|Belirtilen dize, geriye doğru eğik çizgi (\\) veya eğik çizgi (/) karakteri içeriyorsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|
|!|İşlenen `false`değerlendirilirse `true` olarak değerlendirilir.|
|And|Her iki işlenen de `true`değerlendirmesi `true` olarak değerlendirilir.|
|Veya|İşlenenlerin en az biri `true`olarak değerlendirilirse `true` olarak değerlendirilir.|
|()|İçinde yer alan ifadeler `true`olarak değerlendiriyorsa `true` değerlendirilen gruplandırma mekanizması.|
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` geçirilen özel şablon parametresinin dize değeriyle eşleşip eşleşmediğini denetler. `$if$` koşulu `true`olarak değerlendirilirse, deyimleri çalıştırılır; Aksi takdirde `$else$` koşulu denetlenir. `$else$` koşul `true`ise, deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşulu ifade değerlendirmesini sonlandırır.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
