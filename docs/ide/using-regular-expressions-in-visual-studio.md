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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568626"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio'da düzenli ifadeler kullanma

Visual Studio metni bulmak ve değiştirmek için [.NET düzenli ifadeleri](/dotnet/standard/base-types/regular-expressions) kullanır.

## <a name="regular-expression-examples"></a>Normal ifade örnekleri

Aşağıdaki tablobazı normal ifade karakterleri, işleçleri, yapıları ve desen örneklerini içerir. Daha eksiksiz bir başvuru için [normal ifade diline](/dotnet/standard/base-types/regular-expression-language-quick-reference)bakın.

|Amaç|İfadeler|Örnek|
|-------------|----------------|-------------|
|Herhangi bir tek karakter (satır sonu hariç) eşleştirin. Daha fazla bilgi için herhangi [bir karakterbakın.](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)|.|`a.o`"aro" içinde "etrafında" ve "abo" içinde "hakkında" ama "genelinde" "acro" eşleşir|
|Önceki ifadenin sıfır veya daha fazla oluşumlarını eşleştirin (mümkün olduğunca çok karakter eşleştirin). Daha fazla bilgi için sıfır [veya daha fazla kez Eşleştir'e](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)bakın.|*|`a*r`"raf"ta "r", "ark"ta "ar", "aardvark"ta "aar" ile eşleşir.|
|Herhangi bir karakter sıfır veya daha fazla kez eşleştirin.|.*|`c.*e`"raket", "comme" içinde "yorum", "kod" "kod" ile eşleşir|
|Önceki ifadenin bir veya daha fazla oluşumunu eşleştirin (mümkün olduğunca çok karakter eşleştirin). Daha fazla bilgi için bir [veya daha fazla kez Eşleştir'e](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)bakın.|+|`e+d`"besleyici" ile "eed" ve "soluk" "ed" ile eşleşir|
|Herhangi bir karakteri bir veya daha fazla kez eşleştirin.|.+|`e.+e`"besleyici" içinde "eede" eşleşir ama "besleme" hiçbir eşleşme bulur|
|Önceki ifadenin sıfır veya daha fazla oluşumlarını eşleştirin (mümkün olduğunca az karakter eşleştirin). Daha fazla bilgi için sıfır [veya daha fazla kez Maç 'a (tembel eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)bakın.|*?|`\w*?d`"soluk" ve "ed" ile eşleşen "soluk" ancak tembel maç nedeniyle "soluk" sözcüğünün tamamı|
|Önceki ifadenin bir veya daha fazla olaylarını eşleştirin (mümkün olduğunca az karakter eşleştirin). Daha fazla bilgi için bkz: [Bir veya daha fazla kez Eşleştir (tembel eşleşme)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?`"uykuda" ve "ed" ile "solmuş" ile eşleşen ancak "solma" içinde eşleşme bulmuştu|
|Eşleşme dizesini [bir çizginin veya dizenin başına](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-) bağlama|^|`^car`"araba" sözcüğüyle yalnızca bir satırın başında göründüğünde eşleşir|
|Eşleşme dizesini [satırın sonuna](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-) bağlama|\r?$|`car\r?$`"araba" ile eşleşir, yalnızca bir satırın sonunda göründüğünde|
|Eşleşme dizesini dosyanın sonuna bağlama|$|`car$`yalnızca dosyanın sonunda göründüğünde "araba" ile eşleşir|
|Kümedeki herhangi bir karakteri eşleştirme|[abc]|`b[abc]`"ba", "bb" ve "bc" ile eşleşir|
|Karakter aralığındaki herhangi bir karakteri eşleştirme|[a-f]|`be[n-t]`"between", "under"da "ben" ve "bes"te "bes" ile eşleşir, ancak "aşağıda" hiçbir eşleşme bulur|
|Parantez içinde yer alan ifadeyi yakalama ve dolaylı olarak numaralandırma|()|`([a-z])X\1`"aXa" ve "bXb" ile eşleşir, ancak "aXb" ile eşleşmez. "\1" ilk ifade grubu "[a-z]" anlamına gelir. Daha fazla bilgi için [bkz.](#capture-groups-and-replacement-patterns) |
|Eşleşmeyi geçersiz kılma|(?! abc)|`real(?!ity)`"Realty" ve "really" ile "gerçek" ile eşleşir ama "gerçeklik" ile eşleşmez. Aynı zamanda ikinci "gerçek" (ama ilk "gerçek") bulur "realreal".|
|Belirli bir karakter kümesinde olmayan herhangi bir karakteri eşleştirin. Daha fazla bilgi için [Negatif karakter grubuna](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)bakın.|[^abc]|`be[^n-t]`"önce", "beh", "arkasında" ve "bel" ile "aşağıda" ile eşleşen, ancak "altında" hiçbir eşleşme bulur|
|Simgeden önceki ifadeyi veya sembolden sonraki ifadeyi eşleştir|&#124;|`(sponge|mud) bath`"sünger banyosu" ve "çamur banyosu" eşleşir|
|Backslash aşağıdaki [karakter kaçış](/dotnet/standard/base-types/character-escapes-in-regular-expressions)| \\ |`\^`karakter ^ eşleşir|
|Önceki karakter veya grubun oluşum sayısını belirtin. Daha fazla bilgi için, [tam olarak n kez Eşleştir'e](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)bakın.|{n}, 'n' oluşum sayısı|`x(ab){2}x`"xababx" ile eşleşir<br/>`x(ab){2,3}x`"xababx" ve "xabababx" ile eşleşir ama "xababababx" ile eşleşmez.|
|[Metni Unicode kategorisinde eşleştir.](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p) Unicode karakter sınıfları hakkında daha fazla bilgi için [Unicode Standart 5.2 Karakter Özellikleri'ne](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)bakın.|\p{X}, "X" Unicode numarasıdır.|`\p{Lu}`"Thomas Doe" ile "T" ve "D" ile eşleşir|
|[Sözcük sınırını eşleştirme](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (Bir karakter `\b` sınıfı dışında bir sözcük sınırı `\b` belirtir ve bir karakter sınıfı içinde bir arka boşluk belirtir.)|`\bin`"içinde" ile eşleşen ancak "pinto" içinde eşleşme bulmusa|
|Satır sonu yla eşleştirme (diğer bir süre sonra yeni bir satır)|\r?\n|`End\r?\nBegin`"End" ve "Begin" ile eşleşir, ancak "End" bir satırdaki son dize olduğunda ve "Begin" bir sonraki satırdaki ilk dize olduğunda|
|Herhangi bir [sözcük karakterini](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w) eşleştirme|\w|`a\wd`"add" ve "a1d" ile eşleşir ama "a d" ile eşleşmez|
|Herhangi bir [boşluk karakterini](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s) eşleştirme|\s|`Public\sInterface`"Ortak Arabirim" ibaresiile eşleşir|
|Herhangi bir [ondalık basamak karakterini](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d) eşleştirme|\d|`\d`"wd40" ile "4" ve "0" ile eşleşir|

Bazı işleçleri birleştiren ve bir hexadecimal sayı yı eşleştirecek şekilde yapılan örnek bir normal ifadedir. `\b0[xX]([0-9a-fA-F]+\)\b` Bu ifade "0xc67f" ile eşleşir, ancak "0xc67g" ile eşleşmez.

> [!TIP]
> Windows işletim sistemlerinde, çoğu satır "\r\n" (yeni bir satır ardından bir satır geri dönüşü) ile biter. Bu karakterler görünür değildir, ancak editörde bulunur ve .NET normal ifade hizmetine geçer.

## <a name="capture-groups-and-replacement-patterns"></a>Yakalama grupları ve değiştirme desenleri

Yakalama grubu normal bir ifadenin bir alt ifadesini algılar ve giriş dizesinin bir alt dizesini yakalar. Yakalanan grupları normal ifadenin içinde (örneğin, yinelenen bir sözcüğü aramak için) veya değiştirme deseni olarak kullanabilirsiniz. Ayrıntılı bilgi için, [düzenli ifadelerdeki yapıgruplandırma'ya](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)bakın.

Numaralanmış bir yakalama grubu oluşturmak için, alt ifadeyi normal ifade desenindeki parantezlerle çevrele. Yakalamalar, normal ifadedeki açılış parantezinin konumuna bağlı olarak soldan sağa otomatik olarak numaralandırılır. Yakalanan gruba erişmek için:

- **normal ifade içinde** `\number`: Kullanın . Örneğin, `\1` normal ifadede `(\w+)\s\1` ilk yakalama `(\w+)`grubuna başvurur.

- **bir değiştirme deseni**: Kullanın. `$number` Örneğin, gruplanmış normal `(\d)([a-z])` ifade iki grup tanımlar: ilk grup tek bir ondalık basamak içerir ve ikinci grup **a** ve **z**arasında tek bir karakter içerir. İfade aşağıdaki dize dört maç bulur: **1a 2b 3c 4d**. Yedek dize `z$1` yalnızca ilk`$1`gruba başvurur ( ) ve dizeyi **z1 z2 z3 z4'e**dönüştürür.

Aşağıdaki resimde normal bir `(\w+)\s\1` ifade ve `$1`değiştirme dizesi gösterilmektedir. Hem normal ifade hem de değiştirme deseni, otomatik olarak 1 numaralı ilk yakalama grubuna başvurur. Visual Studio'daki **Hızlı Değiştir** iletişim kutusunda **tümlerini değiştir'i** seçtiğinizde, yinelenen sözcükler metinden kaldırılır.

![Visual Studio'da numaralanmış bir yakalama grubunu gösteren Hızlı Değiştirme](media/numbered-capture-group.png)

> [!TIP]
> **Hızlı Değiştir** iletişim kutusunda **Düzenli İfadeleri Kullan** düğmesinin seçildiğinden emin olun.

### <a name="named-capture-groups"></a>Adlandırılmış yakalama grupları

Bir yakalama grubunun otomatik numaralandırması yerine, ona bir ad verebilirsiniz. Adlandırılmış bir yakalama grubunun `(?<name>subexpression)`sözdizimi.

Numaralı yakalama grupları gibi adlandırılmış yakalama grupları, normal ifadenin kendisi içinde veya değiştirme deseninde kullanılabilir. Adlandırılmış yakalama grubuna erişmek için:

- **normal ifade içinde** `\k<name>`: Kullanın . Örneğin, `\k<repeated>` normal ifadede, `(?<repeated>\w+)\s\k<repeated>` adlandırılmış `repeated` ve alt ifadesi `\w+`.

- **bir değiştirme deseni**: Kullanın. `${name}` Örneğin, `${repeated}`.

Örnek olarak, aşağıdaki resimde normal `(?<repeated>\w+)\s\k<repeated>` bir ifade `${repeated}`ve değiştirme dizesi gösterilmektedir. Hem normal ifade hem de değiştirme deseni, yakalama grubunu adlandırılmış olarak adlandırılmış `repeated`olarak adlandırılmış. Visual Studio'daki **Hızlı Değiştir** iletişim kutusunda **tümlerini değiştir'i** seçtiğinizde, yinelenen sözcükler metinden kaldırılır.

![Visual Studio'da adlandırılmış bir yakalama grubunu gösteren Hızlı Değiştirme](media/named-capture-group.png)

> [!TIP]
> **Hızlı Değiştir** iletişim kutusunda **Düzenli İfadeleri Kullan** düğmesinin seçildiğinden emin olun.

Adlandırılmış yakalama grupları hakkında daha fazla bilgi için [Bkz.](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions) Değiştirme desenlerinde kullanılan normal ifadeler hakkında daha fazla bilgi [için, normal ifadelerdeki değiştirmelere](/dotnet/standard/base-types/substitutions-in-regular-expressions)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifade dili](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
