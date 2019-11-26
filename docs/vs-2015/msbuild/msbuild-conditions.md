---
title: MSBuild Koşulları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71bb48290d0eb64f91b918d22624755c2edb6153
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303117"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], bir `Condition` özniteliğine izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.  
  
|Koşul|Açıklama|  
|---------------|-----------------|  
|'`stringA`' = = '`stringB`'|`stringA` `stringB`eşitse `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|  
|'`stringA`'! = '`stringB`'|`stringA` `stringB`eşitse `true` değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|  
|\<, >, \<=, > =|İşleçlerin sayısal değerlerini karşılaştırır. İlişkisel değerlendirme true ise `true` döndürür. İşlenenler, bir ondalık ya da onaltılık sayıya dönüşebilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de, `<` ve `>` karakterlerin kaçışlı olması gerekir. Sembol `<` `<`olarak temsil edilir. Sembol `>` `>`olarak temsil edilir.|  
|Var ('`stringA`')|`stringA` adında bir dosya veya klasör varsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|  
|Hastrailingeðik çizgi ('`stringA`')|Belirtilen dize, geriye doğru eğik çizgi (\\) veya eğik çizgi (/) karakteri içeriyorsa `true` olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dize veya Boole değerleri için tek tırnak gerekmez. Ancak boş değerler için tek tırnak gereklidir.|  
|!|İşlenen `false`değerlendirilirse `true` olarak değerlendirilir.|  
|Ve|Her iki işlenen de `true`değerlendirmesi `true` olarak değerlendirilir.|  
|Veya|İşlenenlerin en az biri `true`olarak değerlendirilirse `true` olarak değerlendirilir.|  
|()|İçinde yer alan ifadeler `true`olarak değerlendiriyorsa `true` değerlendirilen gruplandırma mekanizması.|  
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` geçirilen özel şablon parametresinin dize değeriyle eşleşip eşleşmediğini denetler. `$if$` koşulu `true`olarak değerlendirilirse, deyimleri çalıştırılır; Aksi takdirde `$else$` koşulu denetlenir. `$else$` koşul `true`ise, deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşulu ifade değerlendirmesini sonlandırır.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)   
 [İzlenecek Yol: Sıfırdan MSBuild Proje Dosyası Oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
