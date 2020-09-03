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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74303117"
---
# <a name="msbuild-conditions"></a>MSBuild Koşulları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , bir özniteliğe izin verildiğinde uygulanabilen belirli bir koşul kümesini destekler `Condition` . Aşağıdaki tabloda bu koşullar açıklanmaktadır.  
  
|Koşul|Açıklama|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Eşitse olarak `true` değerlendirilir `stringA` `stringB` .<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|  
|'`stringA`' != '`stringB`'|`true` `stringA` Eşit değilse olarak değerlendirilir `stringB` .<br /><br /> Örneğin:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|  
|\<, >, \<=, >=|İşlenenlerinin sayısal değerlerini değerlendirir. `true`İlişkisel değerlendirmenin doğru olup olmadığını döndürür. İşlenenler bir Decimal veya on altılı sayı olarak değerlendirilmelidir. Onaltılık sayıların "0x" ile başlaması gerekir. **Note:**  XML 'de karakterler `<` ve `>` kaçışlı olmalıdır. Sembol `<` olarak temsil edilir `<` . Sembol `>` olarak temsil edilir `>` .|  
|Var (' `stringA` ')|`true`Ada sahip bir dosya veya klasör varsa olarak değerlendirilir `stringA` .<br /><br /> Örneğin:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|  
|Hastrailingeðik çizgi (' `stringA` ')|`true`Belirtilen dize bir ters eğik çizgi ( \\ ) veya eğik çizgi (/) karakteri içeriyorsa olarak değerlendirilir.<br /><br /> Örneğin:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeler veya Boole değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak gerekir.|  
|!|İşlenen olarak değerlendirilir `true` `false` .|  
|And|`true`Her iki işlenen de olarak değerlendirilir `true` .|  
|Veya|`true`İşlenenlerin en az biri olarak değerlendiriliyorsa, olarak değerlendirilir `true` .|  
|()|`true`İçinde içerilen ifadeler olarak değerlendirilen gruplandırma mekanizması `true` .|  
|$if $ (% Expression%), $else $, $endif $|Belirtilen `%expression%` özel şablon parametresinin dize değeri ile eşleşip eşleşmediğini denetler. `$if$`Koşul olarak değerlendirilirse `true` , deyimleri çalıştırılır; Aksi takdirde `$else$` koşul denetlenir. `$else$`Koşul ise `true` , deyimleri çalıştırılır; Aksi takdirde, `$endif$` koşul ifade değerlendirmesini sonlandırır.<br /><br /> Kullanım örnekleri için bkz. [Visual Studio proje/öğe şablonu parametre mantığı](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)   
 [İzlenecek yol: Sıfırdan MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
