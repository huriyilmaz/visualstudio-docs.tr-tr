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
ms.openlocfilehash: 2e69e5c8fc7404c0c313774271fd07b6315e5270
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633375"
---
# <a name="msbuild-conditions"></a>MSBuild koşulları

MSBuild, bir öznitelik izin verilen her `Condition` yerde uygulanabilecek belirli bir koşul kümesini destekler. Aşağıdaki tabloda bu koşullar açıklanmaktadır.

|Koşul|Açıklama|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Eğer eşitse `true` `stringA` `stringB`değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|'`stringA`' != '`stringB`'|`true` Eğer `stringB`eşit `stringA` değilse değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|\<, >, \<=, >=|Operandların sayısal değerlerini değerlendirir. İlişkisel değerlendirme doğruysa döndürür. `true` Operands ondalık veya hexadecimal sayı değerlendirmek gerekir. Hexadecimal sayılar "0x" ile başlamalıdır. **Not:**  XML'de, karakterler `<` `>` ve kaçılmalıdır. Sembol `<` olarak `&lt;`temsil edilir. Sembol `>` olarak `&gt;`temsil edilir.|
|Var('`stringA`')|Ada `stringA` `true` sahip bir dosya veya klasörün var olup olmadığını değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|HasTrailingSlash('`stringA`')|Belirtilen dize, geriye doğru çizgi ( `true` )\\veya ileri eğik çizgi (/) karakteri nin olup olmadığını değerlendirir.<br /><br /> Örnek:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Basit alfasayısal dizeleri veya boolean değerleri için tek tırnak gerekli değildir. Ancak, boş değerler için tek tırnak işaretleri gereklidir.|
|!|Operand'ın `true` değerlendirilip `false`değerlendirmeme.|
|And|Her iki `true` operands değerlendirmek `true`eğer değerlendirir.|
|Veya|Operandlardan en az birinin .'a `true` `true`göre değerlendirilip değerlendirmeyeceklerini değerlendirir.|
|()|İçerde yer alan `true` ifadelerin `true`değerlendirilmesi için değerlendiren gruplandırma mekanizması.|
|$if$ ( %ifade% ), $else$, $endif$|Belirtilen `%expression%` özel şablon parametresinin dize değeriyle eşleşip eşleşmediğini denetler. `$if$` Koşul , ifadeleri `true`çalıştırılır; aksi `$else$` takdirde, durum kontrol edilir. `$else$` Koşul `true`ise , ifadeleri çalıştırılır; aksi takdirde, durum ifade değerlendirmesini `$endif$` sona erdirer.<br /><br /> Kullanım örnekleri için [Visual Studio proje/öğe şablonu parametre mantığına](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [Walkthrough: Sıfırdan bir MSBuild proje dosyası oluşturma](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
