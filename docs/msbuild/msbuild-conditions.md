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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf77e4630cd52e8dcb354b5625ae24eabc9d8ae9
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912080"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], bir `Condition` özniteliğine izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|' `stringA`' = = '`stringB`'|`stringA` `stringB`eşitse `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|' `stringA`'! = '`stringB`'|`stringA` `stringB`eşitse `true` değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|\<, >, \<=, > =|İşlenenlerinin sayısal değerlerini değerlendirir. İlişkisel değerlendirme true ise `true` döndürür. İşlenenler bir Decimal veya on altılı sayı olarak değerlendirilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de, `<` ve `>` karakterlerin kaçışlı olması gerekir. Sembol `<` `&lt;`olarak temsil edilir. Sembol `>` `&gt;`olarak temsil edilir.|
|Var ('`stringA`')|`stringA` adında bir dosya veya klasör varsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|Hastrailingeðik çizgi ('`stringA`')|Belirtilen dize, geriye doğru eğik çizgi (\\) veya eğik çizgi (/) karakteri içeriyorsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|
|!|İşlenen `false`değerlendirilirse `true` olarak değerlendirilir.|
|'|Her iki işlenen de `true`değerlendirmesi `true` olarak değerlendirilir.|
|Veya|İşlenenlerin en az biri `true`olarak değerlendirilirse `true` olarak değerlendirilir.|
|()|İçinde yer alan ifadeler `true`olarak değerlendiriyorsa `true` değerlendirilen gruplandırma mekanizması.|
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` geçirilen özel şablon parametresinin dize değeriyle eşleşip eşleşmediğini denetler. `$if$` koşulu `true`olarak değerlendirilirse, deyimleri çalıştırılır; Aksi takdirde `$else$` koşulu denetlenir. `$else$` koşul `true`ise, deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşulu ifade değerlendirmesini sonlandırır.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
