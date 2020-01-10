---
title: Normal ifadeler kullanma
ms.date: 09/13/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568626"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio'da normal ifadeler kullanma

Visual Studio, metni bulmak ve değiştirmek için [.net normal ifadelerini](/dotnet/standard/base-types/regular-expressions) kullanır.

## <a name="regular-expression-examples"></a>Normal ifade örnekleri

Aşağıdaki tabloda bazı normal ifade karakterleri, işleçler, yapılar ve model örnekleri yer almaktadır. Daha kapsamlı bir başvuru için bkz. [normal ifade dili](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Amaç|İfade|Örnek|
|-------------|----------------|-------------|
|Tek bir karakterle Eşleştir (satır sonu hariç). Daha fazla bilgi için, bkz. [herhangi bir karakter](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` "About" ve "Acro" içinde "" değil "About" ve "ABO" içinde "Aro" ile eşleşir|
|Önceki ifadenin sıfır veya daha fazla tekrarlamalarını eşleştirin (mümkün olduğunca çok karakterle Eşleştir). Daha fazla bilgi için bkz. [sıfır veya daha fazla kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` "rack" daki "r", "ark" içinde "ar" ve "aardvark", "aar" ile eşleşir.|
|Herhangi bir karakteri sıfır veya daha fazla kez eşleştirin.|.*|`c.*e` "comme" "racket", "comment" "comme" ve "Code" ve "code" ile eşleşir.|
|Önceki ifadenin bir veya daha çok tekrarı ile Eşleştir (mümkün olduğu kadar çok karakterle Eşleştir). Daha fazla bilgi için bkz. [bir veya daha fazla kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d`, "faed" içinde "besleyici" ve "Ed" içinde "eed" ile eşleşir|
|Karakterleri bir veya daha fazla kez eşleştirin.|.+|`e.+e` "besleyici" içinde "eleştirme" ile eşleşir, ancak "Feed" içinde eşleşme buluyor|
|Önceki ifadenin sıfır veya daha fazla tekrarlamalarını eşleştirin (mümkün olduğunca az karakter eşleştirin). Daha fazla bilgi için bkz. [sıfır veya daha fazla kez eşleşme (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` "FAD" ve "Ed" ile eşleşir, ancak geç eşleşme nedeniyle "Faded" sözcüğünün tamamını kullanmaz|
|Önceki ifadenin bir veya daha çok tekrarı ile Eşleştir (mümkün olduğu kadar az karakterle Eşleştir). Daha fazla bilgi için bkz. [bir veya daha fazla kez eşleşme (geç eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` "i" içinde "Ee" ve "faed" içinde "Ed" ile eşleşir, ancak "Soldur" içinde eşleşme bulmazlar|
|Eşleşme dizesini [bir satırın veya dizenin başına](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-) bağla|^|`^car`, "otomobil" kelimesiyle eşleşir ve yalnızca bir satırın başlangıcında görüntülenir|
|Eşleşme dizesini [bir satırın sonuna](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-) bağla|\r?$|`car\r?$`, "otomobil" ile yalnızca bir satırın sonunda göründüğünde eşleşir|
|Eşleşme dizesini dosyanın sonuna bağlantı|$|`car$`, yalnızca dosyanın sonunda göründüğünde "otomobil" ile eşleşir|
|Bir kümedeki tek bir karakterle eşleştir|[abc]|`b[abc]` "ba", "BB" ve "BC" ile eşleşir|
|Karakter aralığındaki herhangi bir karakterle eşleştir|[a-f]|`be[n-t]`, "Below" içinde "with", "Ben" içindeki "i" ve "yanýndaki" içinde "bes" ile eşleşir, ancak "aşağıda" içinde hiçbir eşleşme bulmuyor|
|Yakalama ve parantez içinde yer alan ifadesi örtük olarak numaralandır|()|`([a-z])X\1` "aXa" ve "bXb" ancak değil "aXb" ile eşleşir. "\1", ilk ifade grubu "[a-z]" anlamına gelir. Daha fazla bilgi için bkz. [yakalama grupları ve değiştirme desenleri](#capture-groups-and-replacement-patterns). |
|Eşlemeyi geçersiz kıl|(?!abc)|`real(?!ity)` "gerçek" bir "realty" ve "really" eşleşir ancak değil içinde "gerçeklik." Ayrıca ikinci "real" (ancak değil ilk "real") "realityreal" içinde bulur.|
|Belirli bir karakter kümesinde olmayan herhangi bir karakterle eşleştirin. Daha fazla bilgi için bkz. [negatif karakter grubu](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]` "önceki" içinde "BEF", "Behind" içinde "beh", "ın" içinde "Bel" ile eşleşir, ancak "aşağıda" içinde eşleşme yok buluyor|
|Simgeden önceki veya bir ifadeden sonraki ifadeyle Eşleştir|&#124;|`(sponge|mud) bath` "sünge banyo" ve "Mud banyo" ile eşleşir|
|Ters eğik çizgiden sonraki [karakteri kaçış](/dotnet/standard/base-types/character-escapes-in-regular-expressions)| \\ |`\^`, ^ karakteriyle eşleşir|
|Önceki karakterin veya grubun oluşum sayısını belirtin. Daha fazla bilgi için bkz. [tam n kez eşleşme](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, burada ' n ' oluşum sayısıdır|`x(ab){2}x` "xabex" ile eşleşir<br/>`x(ab){2,3}x` "xabex" ve "xabababx" ile eşleşir ancak "xababababx" değil|
|[Unicode kategorisindeki metni eşleştirin](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Unicode karakter sınıfları hakkında daha fazla bilgi için bkz. [Unicode standart 5,2 karakter özellikleri](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, "X" değerinin Unicode numarası olduğu.|`\p{Lu}` "Thomas tikan" içinde "T" ve "D" ile eşleşir|
|[Sözcük sınırını Eşleştir](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (bir karakter sınıfı dışında `\b` bir sözcük sınırını belirler ve bir karakter sınıfı içinde `\b` Geri Al ile eşleşir.)|`\bin` "in" içinde "içinde" eşleşir, ancak "Pinto" içinde eşleşme yok buluyor|
|Satır sonuyla eşleştir (diğer bir deyişle, satır başı, izleyen yeni bir satır)|\r?\n|`End\r?\nBegin` "End" ve "Begin" ile eşleşir, yalnızca "End" satırdaki son dize ve "Begin" ise sonraki satırdaki ilk dizedir|
|Herhangi bir [sözcük karakteri](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w) Eşleştir|\w|`a\wd` "Add" ve "A1D" ile eşleşir, ancak "a d" eşleşmez|
|Herhangi bir [boşluk karakteriyle](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s) Eşleştir|\s|`Public\sInterface`, "ortak arabirim" ifadesi ile eşleşir|
|Herhangi bir [ondalık basamak karakteriyle](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d) Eşleştir|\d|"WD40" içinde "4" ve "0" ile eşleşir `\d`|

Bazı işleçleri ve yapıları bir onaltılık sayıyla eşleşecek şekilde birleştiren örnek bir normal ifade `\b0[xX]([0-9a-fA-F]+\)\b`. Bu ifade "0xc67f" ile eşleşir ancak "0xc67g" olarak eşleşmez.

> [!TIP]
> Windows işletim sistemlerinde satırların çoğu "\r\n" (bir yeni satırın izlediği bir satır başı) bitmelidir. Bu karakterler görünmez, ancak düzenleyicide bulunur ve .NET normal ifade hizmetine geçirilir.

## <a name="capture-groups-and-replacement-patterns"></a>Yakalama grupları ve değiştirme desenleri

Yakalama grubu, normal bir ifadenin alt ifadesini toplar ve bir giriş dizesinin alt dizesini yakalar. Normal ifadenin içinde yakalanan grupları kullanabilirsiniz (örneğin, yinelenen bir sözcüğe bakmak için) veya değiştirme düzeninde. Ayrıntılı bilgi için bkz. [normal ifadelerde yapıları gruplandırma](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Numaralandırılmış bir yakalama grubu oluşturmak için, alt ifadeyi normal ifade deseninin parantezleri ile çevreleyin. Yakalamaları, normal ifadede açma parantezinin konumuna göre otomatik olarak soldan sağa numaralandırılır. Yakalanan gruba erişmek için:

- **normal ifade içinde**: `\number`kullanın. Örneğin, normal ifadede `\1`, ilk yakalama grubuna `(\w+)`başvurur `(\w+)\s\1`.

- **değiştirme**düzeninde: `$number`kullanın. Örneğin, gruplanan normal ifadeyle `(\d)([a-z])` iki grupları tanımlar: ilk grubu tek bir ondalık basamak içeren ve ikinci grubu arasında tek bir karakter içeren **bir** ve **z**. İfade, aşağıdaki dizede dört eşleşme bulur: **1a 2b 3c 4d**. Değiştirme dizesi `z$1` yalnızca ilk gruba (`$1`) başvurur ve dizeyi **Z1 Z2 Z3 Z4**öğesine dönüştürür.

Aşağıdaki görüntüde `(\w+)\s\1` bir normal ifade ve bir değiştirme dizesi `$1`gösterilmektedir. Normal ifade ve değiştirme deseninin her ikisi de otomatik olarak numaralandırılan ilk yakalama grubuna başvurur. Visual Studio 'daki **hızlı değiştirme** iletişim kutusunda **Tümünü Değiştir** ' i seçtiğinizde, yinelenen sözcükler metinden kaldırılır.

![Visual Studio 'da Numaralandırılmış yakalama grubunu gösteren hızlı değiştirme](media/numbered-capture-group.png)

> [!TIP]
> **Hızlı değiştirme** Iletişim kutusunda **Normal ifadeleri kullan** düğmesinin seçili olduğundan emin olun.

### <a name="named-capture-groups"></a>Adlandırılmış yakalama grupları

Bir yakalama grubunun otomatik numaralandırmasına güvenmek yerine, buna bir ad verebilirsiniz. Adlandırılmış bir yakalama grubunun sözdizimi `(?<name>subexpression)`.

Numaralandırılmış yakalama grupları gibi adlandırılmış yakalama grupları, normal ifadenin içinde veya değiştirme düzeninde kullanılabilir. Adlandırılmış yakalama grubuna erişmek için:

- **normal ifade içinde**: `\k<name>`kullanın. Örneğin, normal ifadede `\k<repeated>` `(?<repeated>\w+)\s\k<repeated>` `repeated` adlı ve alt ifadesi `\w+`olan yakalama grubuna başvurur.

- **değiştirme**düzeninde: `${name}`kullanın. Örneğin: `${repeated}`.

Örnek olarak, aşağıdaki görüntüde `(?<repeated>\w+)\s\k<repeated>` bir normal ifade ve bir değiştirme dizesi `${repeated}`gösterilmektedir. Hem normal ifade hem de değiştirme deseninin `repeated`adlı yakalama grubu başvurusu. Visual Studio 'daki **hızlı değiştirme** iletişim kutusunda **Tümünü Değiştir** ' i seçtiğinizde, yinelenen sözcükler metinden kaldırılır.

![Visual Studio 'da adlandırılmış bir yakalama grubunu gösteren hızlı değiştirme](media/named-capture-group.png)

> [!TIP]
> **Hızlı değiştirme** Iletişim kutusunda **Normal ifadeleri kullan** düğmesinin seçili olduğundan emin olun.

Adlandırılmış yakalama grupları hakkında daha fazla bilgi için bkz. [eşleşen alt Ifadeler adlandırılmış](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Değiştirme desenlerinde kullanılan normal ifadeler hakkında daha fazla bilgi için bkz. [normal Ifadelerde değişimler](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifade dili](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
