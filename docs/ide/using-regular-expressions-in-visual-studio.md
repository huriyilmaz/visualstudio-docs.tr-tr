---
title: Normal ifadeler kullanma
description: Örneklerde kullanabileceğiniz bazı normal ifade karakterleri, işleçler, yapılar ve desen örnekleri hakkında Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/01/2020
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8825efcb35bd36d2165ad9abe490ad67ad58beb5
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431113"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Normal ifadeleri Visual Studio

Visual Studio bulmak [ve değiştirmek için .NET](/dotnet/standard/base-types/regular-expressions) normal ifadelerini kullanır.

## <a name="regular-expression-examples"></a>Normal ifade örnekleri

Aşağıdaki tabloda bazı normal ifade karakterleri, işleçler, yapılar ve desen örnekleri yer almaktadır. Daha eksiksiz bir başvuru için bkz. [Normal ifade dili.](/dotnet/standard/base-types/regular-expression-language-quick-reference)

|Amaç|Expression|Örnek|
|-------------|----------------|-------------|
|Herhangi bir tek karakteri (satır sonu dışında) eşler. Daha fazla bilgi için bkz. [Herhangi bir karakter.](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)|.|`a.o` "about" içinde "around" ve "abo" içinde "aro" ile eşler, ancak "across" içinde "acro" ile eşleşmez|
|Önceki ifadenin sıfır veya daha fazla oluşumunu eşle (mümkün olduğunca çok karakterle eşle). Daha fazla bilgi için [bkz. Sıfır veya daha fazla kez eşleşme.](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)|*|`a*r` "raf" içinde "r", "ark" içinde "ar" ve "aardvark" içinde "aar" ile eşler|
|Herhangi bir karakteri sıfır veya daha fazla kez eşler.|.*|`c.*e` "comment" içinde "cke", "comme" ile ve "code" içinde "code" ile eşler|
|Önceki ifadenin bir veya daha fazla oluşumunu eşle (mümkün olduğunca çok karakterle eşle). Daha fazla bilgi için [bkz. Bir veya daha fazla kez eşleşme.](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)|+|`e+d` "akış" içinde "eed" ve "soluk" içinde "ed" ile eşler|
|Herhangi bir karakteri bir veya daha fazla kez eşler.|.+|`e.+e` "akış" içinde "eede" ile eşler ancak "akışta" eşleşme bulur|
|Önceki ifadenin sıfır veya daha fazla oluşumunu eşler (mümkün olduğunca az karakterle eşler). Daha fazla bilgi için [bkz. Sıfır veya daha fazla kez eşleşme (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` yavaş eşleşme nedeniyle "soluk" sözcüğünde "fad" ve "ed" ile eşleşti, ancak "soluk" sözcüğün tamamını eşleşmez|
|Önceki ifadenin bir veya daha fazla oluşumunu eşler (mümkün olduğunca az karakterle eşler). Daha fazla bilgi için [bkz. Bir veya daha fazla kez eşle (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` "soluk" ifadesinde "uykuda" ve "ed" içinde "ee" ile eşler, ancak "soluk" içinde hiçbir eşleşme bulmaz|
|Eşleşme dizesini bir [satırın veya dizenin başına sabitle](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` yalnızca bir satırın başında göründüğünde "araba" sözcüğüyle eş görünür|
|Eşleşme dizesini bir [satırın sonuna sabitle](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$` yalnızca bir satırın sonunda göründüğünde "araba" ile eş görünür|
|Eşleşme dizesini dosyanın sonuna sabitle|$|`car$` yalnızca dosyanın sonunda göründüğünde "araba" ile eşler|
|Kümedeki tek bir karakterle eşleşme|[abc]|`b[abc]` "ba", "bb" ve "bc" ile eşlenir|
|Bir karakter aralığındaki herhangi bir karakterle eşleşme|[a-f]|`be[n-t]` "between" içinde "bet", "below" içinde "ben" ve "beside" içinde "bes" ile eşler, ancak "aşağıdaki" içinde hiçbir eşleşme bulmaz|
|Parantez içinde bulunan ifadeyi yakalama ve örtülü olarak sayma|()|`([a-z])X\1` "aXa" ve "bXb" ile eştir, ancak "aXb" ile eşleşmez. "\1", "[a-z]" ilk ifade grubunu ifade eder. Daha fazla bilgi için [bkz. Yakalama grupları ve değiştirme desenleri.](#capture-groups-and-replacement-patterns) |
|Eşleşmeyi geçersiz kılın|(?! abc)|`real(?!ity)` "realty" ve "really" ile "real" (gerçek) eşleşmesi ancak "gerçeklik" ile eşleşmez. Ayrıca "realityreal" içinde ikinci "gerçek" (ancak ilk "gerçek" değil) bulur.|
|Verilen karakter kümesinde yer alan herhangi bir karakterle eşle. Daha fazla bilgi için [bkz. Negatif karakter grubu.](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)|[^abc]|`be[^n-t]` "before", "beh" içinde "bef" ile "behind" ve "below" içinde "bel" ile eşler, ancak "altta" içinde hiçbir eşleşme bulur|
|İfadeyi sembolden önce veya simgeden sonra gelen ifadeyle eşle|&#124;|`(sponge|mud) bath` "maça" ve "maça" ile eştir|
|[Ters eğik çizginin](/dotnet/standard/base-types/character-escapes-in-regular-expressions) ardından karakterin kaçış karakteri| \\ |`\^` ^ karakteriyle eşler|
|Önceki karakterin veya grubun oluşum sayısını belirtin. Daha fazla bilgi için bkz. [Tam olarak n kez eşle.](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)|{n}, burada 'n', oluşum sayısıdır|`x(ab){2}x` "xababx" ile eşler<br/>`x(ab){2,3}x` "xababx" ve "xabababx" ile eştir, ancak "xaba akabx" ile eşleşmez|
|[Unicode kategorisindeki metinleri eşler.](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p) Unicode karakter sınıfları hakkında daha fazla bilgi için [bkz. Unicode Standart 5.2 Karakter Özellikleri.](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)|\p{X}, burada "X", Unicode sayısıdır.|`\p{Lu}` "Thomas Doe" içinde "T" ve "D" ile eşler|
|[Bir sözcük sınırını eşleşme](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (Bir karakter sınıfı dışında bir sözcük sınırı ve bir `\b` karakter sınıfının içinde bir geri alanı `\b` belirtir.)|`\bin` "inside" içinde "in" ile eştir, ancak "pinto" içinde hiçbir eşleşme bulmaz|
|Satır sonu eşleşmesi (başka bir ifadeyle satır başı ve ardından yeni bir satır)|\r?\n|`End\r?\nBegin` yalnızca "End" bir satırda son dize olduğunda ve "Begin" sonraki satırda ilk dize olduğunda "End" ve "Begin" ile eşler|
|Herhangi bir sözcük [karakteriyle eşleşme](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` "add" ve "a1d" ile eştir, ancak "a d" ile eşleşmez|
|Herhangi bir [boşluk karakteriyle eşleşme](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` "Genel Arabirim" tümceciğiyle eş|
|Herhangi bir ondalık [basamak karakteriyle eşleşme](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` "wd40" içinde "4" ve "0" ile eşler|

Onaltılık bir sayıyla eşleşmesi için bazı işleçleri ve yapıları birleştiren örnek bir normal ifade `\b0[xX]([0-9a-fA-F]+)\b` şeklindedir. Bu ifade "0xc67f" ile eştir ancak "0xc67g" ile eşleşmez.

> [!TIP]
> İşletim Windows çoğu satırın sonunda "\r\n" (bir satır başı ve ardından yeni bir satır) gelir. Bu karakterler görünür değildir, ancak düzenleyicide mevcuttur ve .NET normal ifade hizmetine geçirebilirsiniz.

## <a name="capture-groups-and-replacement-patterns"></a>Grupları ve değiştirme desenlerini yakalama

Yakalama grubu, bir normal ifadenin alt ifadesini satıra alır ve bir giriş dizesinin alt dizesini yakalar. Yakalanan grupları normal ifadenin içinde (örneğin, yinelenen bir sözcük için) veya değiştirme düzeninde kullanabilirsiniz. Ayrıntılı bilgi için [bkz. Normal ifadelerde yapıları gruplama.](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)

Numaralı bir yakalama grubu oluşturmak için, alt ifadeyi normal ifade desende parantezlerle çevreler. Yakalamalar, normal ifadede açma parantezlerinin konumu temel alarak otomatik olarak soldan sağa doğru numaralenir. Yakalanan gruba erişmek için:

- **normal ifadenin içinde:** `\number` kullanın. Örneğin, `\1` normal ifadede ilk `(\w+)\s\1` yakalama grubuna `(\w+)` başvurur.

- **değiştirme desenini kullanın:** `$number` kullanın. Örneğin, gruplu normal ifade iki grup tanımlar: ilk grup tek bir ondalık basamak içerir ve ikinci grup ile z arasında tek `(\d)([a-z])` **bir karakter** **içerir.** ifadesi şu dizede dört eşleşme bulur: **1a 2b 3c 4d.** Değiştirme dizesi yalnızca `z$1` ilk gruba () başvurur ve `$1` dizeyi **z1 z2 z3 z4'e dönüştürür.**

Aşağıdaki görüntüde normal bir ifade ve `(\w+)\s\1` yerine bir dize yer `$1` alır. Hem normal ifade hem de değiştirme deseni, otomatik olarak 1 numaralı ilk yakalama grubuna başvurur. Hızlı Değiştir **iletişim kutusundaki** Tüm sözcükleri **değiştir'i** Visual Studio yinelenen sözcükler metinden kaldırılır.

![Hızlı Değiştirme, Visual Studio'de numaralı yakalama grubunu Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Hızlı Değiştir **iletişim kutusunda Normal** İfadeleri Kullan düğmesinin seçili **olduğundan** emin olun.

### <a name="named-capture-groups"></a>Adlandırılmış yakalama grupları

Bir yakalama grubunun otomatik numaralama özelliğine güvenmek yerine bir ad ve ardından bu gruba bir ad vesersiniz. Adlandırılmış yakalama grubunun söz dizimi şu `(?<name>subexpression)` şekildedir: .

Numaralı yakalama grupları gibi adlandırılmış yakalama grupları normal ifadenin içinde veya değiştirme düzeninde kullanılabilir. Adlandırılmış yakalama grubuna erişmek için:

- **normal ifadenin içinde:** `\k<name>` kullanın. Örneğin, normal ifadede adlı ve alt ifadesi olan `\k<repeated>` `(?<repeated>\w+)\s\k<repeated>` yakalama grubuna `repeated` `\w+` başvurur.

- **değiştirme desenini kullanın:** `${name}` kullanın. Örneğin, `${repeated}`.

Örnek olarak, aşağıdaki görüntüde normal bir ifade ve `(?<repeated>\w+)\s\k<repeated>` değiştirme dizesi yer `${repeated}` alır. Hem normal ifade hem de değiştirme deseni adlı yakalama grubuna `repeated` başvurur. Hızlı Değiştir **iletişim kutusundaki** Tüm sözcükleri **değiştir'i** Visual Studio yinelenen sözcükler metinden kaldırılır.

![Hızlı Değiştirme, Visual Studio'de adlandırılmış yakalama grubunu Visual Studio](media/named-capture-group.png)

> [!TIP]
> Hızlı Değiştir **iletişim kutusunda Normal** İfadeleri Kullan düğmesinin seçili **olduğundan** emin olun.

Adlandırılmış yakalama grupları hakkında daha fazla bilgi için [bkz. Adlandırılmış eşdükey alt ifadeleri.](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions) Değiştirme desenlerinde kullanılan normal ifadeler hakkında daha fazla bilgi için [bkz. Normal ifadelerde Değiştirmeler.](/dotnet/standard/base-types/substitutions-in-regular-expressions)

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifade dili](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
