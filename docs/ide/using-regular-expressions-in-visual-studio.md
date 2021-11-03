---
title: Normal ifadeler kullanma
description: Visual Studio için kullanabileceğiniz bazı normal ifade karakterleri, işleçler, yapılar ve model örnekleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/21/2021
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
ms.openlocfilehash: 21d95169106c05391d9c5532a6d84e34f8734e34
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127188"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio içindeki normal ifadeleri kullanma

Visual Studio, metni bulmak ve değiştirmek için [.net normal ifadelerini](/dotnet/standard/base-types/regular-expressions) kullanır.

## <a name="regular-expression-examples"></a>Normal ifade örnekleri

Aşağıdaki tabloda bazı normal ifade karakterleri, işleçler, yapılar ve model örnekleri yer almaktadır. Daha kapsamlı bir başvuru için bkz. [normal ifade dili](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Amaç|Expression|Örnek|
|-------------|----------------|-------------|
|Tek bir karakterle Eşleştir (satır sonu hariç). Daha fazla bilgi için, bkz. [herhangi bir karakter](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` "About" içinde "Acro" ve "" değil "About" ve "ABO" içinde "Aro" ile eşleşir|
|Önceki ifadenin sıfır veya daha fazla tekrarlamalarını eşleştirin (mümkün olduğunca çok karakterle Eşleştir). Daha fazla bilgi için bkz. [sıfır veya daha fazla kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` "bin", "ark" içinde "ar" ve "aardvark" içinde "aar" içinde "r" ile eşleşir|
|Herhangi bir karakteri sıfır veya daha fazla kez eşleştirin.|.*|`c.*e` "Code" içinde "ractus", "Not" ve "Code" içinde "CKE" ile eşleşir|
|Önceki ifadenin bir veya daha çok tekrarı ile Eşleştir (mümkün olduğu kadar çok karakterle Eşleştir). Daha fazla bilgi için bkz. [bir veya daha fazla kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d` "faed" içinde "besleyici" ve "Ed" içinde "eed" ile eşleşir|
|Karakterleri bir veya daha fazla kez eşleştirin.|.+|`e.+e` "besleyici" içinde "eleştirme" ile eşleşir, ancak "Feed" içinde eşleşme buluyor|
|Önceki ifadenin sıfır veya daha fazla tekrarlamalarını eşleştirin (mümkün olduğunca az karakter eşleştirin). Daha fazla bilgi için bkz. [sıfır veya daha fazla kez eşleşme (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` "faed" içinde "FAD" ve "Ed" ile eşleşir, ancak geç eşleşme nedeniyle "Faded" sözcüğünün tamamını kullanmaz|
|Önceki ifadenin bir veya daha çok tekrarı ile Eşleştir (mümkün olduğu kadar az karakterle Eşleştir). Daha fazla bilgi için bkz. [bir veya daha fazla kez eşleşme (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` "faed" içinde "Ee" ve "Ed" içinde "Ee" ile eşleşir, ancak "Soldur" içinde hiçbir eşleşme bulmazlar|
|Eşleşme dizesini [bir satırın veya dizenin başına](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-) bağla|^|`^car` "otomobil" sözcüğüyle yalnızca bir satırın başlangıcında göründüğünde eşleşir|
|Eşleşme dizesini [bir satırın sonuna](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-) bağla|\r? $|`car\r?$` "otomobil" ifadesi yalnızca bir satırın sonunda göründüğünde eşleşir|
|Eşleşme dizesini dosyanın sonuna bağla|$|`car$` Yalnızca dosyanın sonunda göründüğünde "otomobil" ile eşleşir|
|Bir küme içinde herhangi bir tek karakterle Eşleştir|ABC|`b[abc]` "ba", "BB" ve "BC" ile eşleşir|
|Karakter aralığındaki herhangi bir karakterle Eşleştir|[a-f]|`be[n-t]` "sonra", "in" içinde "", "ve" bes "içinde" Bet "ile eşleşir, ancak" aşağıda "içinde eşleşme yok buluyor|
|Parantez içinde bulunan ifadeyi yakala ve örtülü olarak sayı|()|`([a-z])X\1` "aXa" ve "bXb" ile eşleşir, ancak "aXb" ile eşleşmez. "\ 1", ilk ifade grubu "[a-z]" anlamına gelir. Daha fazla bilgi için bkz. [yakalama grupları ve değiştirme desenleri](#capture-groups-and-replacement-patterns). |
|Eşleşmeyi geçersiz kıl|(?! ABC|`real(?!ity)` "Realty" ve "gerçekten" içinde "gerçek" ile eşleşir ancak "gerçeklik" içinde değildir. Ayrıca "realityreal" içinde ikinci "Real" (ilk "Real" değil) değerini bulur.|
|Belirli bir karakter kümesinde olmayan herhangi bir karakterle eşleştirin. Daha fazla bilgi için bkz. [negatif karakter grubu](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]` "önceki" içinde "BEF", "arkasında" ve "Bel" içinde "ın" içinde "Bel" eşleşir, ancak "aşağıda" içinde eşleşme yok buluyor|
|Simgeden önceki veya bir ifadeden sonraki ifadeyle Eşleştir|&#124;|`(sponge|mud) bath` "sünge banyo" ve "Mud banyo" ile eşleşir|
|Ters eğik çizgiden sonraki [karakteri kaçış](/dotnet/standard/base-types/character-escapes-in-regular-expressions)| \\ |`\^` ^ karakteriyle eşleşir|
|Önceki karakterin veya grubun oluşum sayısını belirtin. Daha fazla bilgi için bkz. [tam n kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, burada ' n ' oluşum sayısıdır|`x(ab){2}x` "xabex" ile eşleşir<br/>`x(ab){2,3}x` "xabex" ve "xabababx" ile eşleşir ancak "xababababx" olarak eşleşmez|
|[Unicode kategorisindeki metni eşleştirin](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Unicode karakter sınıfları hakkında daha fazla bilgi için bkz. [Unicode standart 5,2 karakter özellikleri](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, burada "X" Unicode sayıdır.|`\p{Lu}` "Thomas tikan" içinde "T" ve "D" ile eşleşir|
|[Sözcük sınırını Eşleştir](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (bir karakter sınıfı dışında `\b` bir sözcük sınırı belirtir ve bir karakter sınıfı içinde `\b` geri alma belirtilir.)|`\bin` "iç" içinde "içinde" eşleşir, ancak "Pinto" içinde eşleşme yok|
|Satır sonuyla eşleştir (diğer bir deyişle, satır başı, izleyen yeni bir satır)|\r? \n|`End\r?\nBegin` "End" ve "Begin" ile yalnızca "End" satırdaki son dize olduğunda ve "Begin" bir sonraki satırdaki ilk dizeyse|
|Herhangi bir [sözcük karakteri](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w) Eşleştir|\w|`a\wd` "Add" ve "A1D" ile eşleşir, ancak "a d" eşleşmez|
|Herhangi bir [boşluk karakteriyle](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s) Eşleştir|\s|`Public\sInterface` "ortak arabirim" ifadesi ile eşleşir|
|Herhangi bir [ondalık basamak karakteriyle](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d) Eşleştir|\d|`\d` "WD40" içinde "4" ve "0" ile eşleşir|

Bazı işleçleri ve yapıları bir onaltılık sayıyla eşleşecek şekilde birleştiren örnek bir normal ifade `\b0[xX]([0-9a-fA-F]+)\b` . Bu ifade "0xc67f" ile eşleşir ancak "0xc67g" olarak eşleşmez.

> [!TIP]
> Windows işletim sistemlerinde, çoğu satır "\r\n" içinde (bir satır başı, ardından yeni bir satır) biter. Bu karakterler görünmez, ancak düzenleyicide bulunur ve .NET normal ifade hizmetine geçirilir.

## <a name="capture-groups-and-replacement-patterns"></a>Yakalama grupları ve değiştirme desenleri

Yakalama grubu, normal bir ifadenin alt ifadesini toplar ve bir giriş dizesinin alt dizesini yakalar. Normal ifadenin içinde yakalanan grupları kullanabilirsiniz (örneğin, yinelenen bir sözcüğe bakmak için) veya değiştirme düzeninde. Ayrıntılı bilgi için bkz. [normal ifadelerde yapıları gruplandırma](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Numaralandırılmış bir yakalama grubu oluşturmak için, alt ifadeyi normal ifade deseninin parantezleri ile çevreleyin. Yakalamaları, normal ifadede açma parantezinin konumuna göre otomatik olarak soldan sağa numaralandırılır. Yakalanan gruba erişmek için:

- **normal ifade içinde**: kullanın `\number` . Örneğin, `\1` normal ifadede `(\w+)\s\1` ilk yakalama grubuna başvuru yapılır `(\w+)` .

- **değiştirme** düzeninde: kullanın `$number` . Örneğin, gruplanmış normal ifade `(\d)([a-z])` iki grup tanımlar: ilk grup tek bir ondalık basamak içerir ve ikinci grup, ve **z** arasında tek bir karakter içerir.  ifadesi şu dizede dört eşleşme bulur: **1a 2b 3c 4d.** Değiştirme dizesi yalnızca `z$1` ilk gruba () başvurur ve `$1` dizeyi **z1 z2 z3 z4'e dönüştürür.**

Aşağıdaki görüntüde normal bir ifade ve `(\w+)\s\1` yerine bir dize yer `$1` alır. Hem normal ifade hem de değiştirme deseni, otomatik olarak 1 numaralı ilk yakalama grubuna başvurur. Hızlı Değiştir **iletişim kutusundaki** Tüm sözcükleri **değiştir'i** Visual Studio yinelenen sözcükler metinden kaldırılır.

![Hızlı Değiştirme, Visual Studio'da numaralı yakalama grubunu Visual Studio](media/numbered-capture-group.png)

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
