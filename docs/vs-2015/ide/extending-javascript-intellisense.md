---
title: JavaScript IntelliSense 'ı genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665759"
---
# <a name="extending-javascript-intellisense"></a>JavaScript IntelliSense Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense genişletilebilirlik özelliği, üçüncü taraf kitaplıklar için JavaScript düzenleyicisinde IntelliSense sonuçlarını özelleştirmenize olanak sağlar. Bu, bu kitaplıkları kullanan geliştiricilerin deneyimini geliştirebilir.

 JavaScript Language Service, bir projeye eklenen üçüncü taraf JavaScript kitaplıkları için IntelliSense özellikleri sağlar. Çoğu kitaplık için, bildirim tamamlama dil hizmeti tarafından otomatik olarak sağlanır. Aşağıdaki çizimde bir ifade tamamlama örneği gösterilmektedir:

 ![Deyimin tamamlanmasına örnek](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Kitaplığınız standart JavaScript açıklama etiketleri (//) içindeki değişkenlerin, işlevlerin ve nesnelerin açıklamalarını içeriyorsa, varsayılan olarak, bir tamamlanma listesindeki öğelerin sağında görüntülenen bir açılır kutuda veya bir işlev çağrısında açma ayracı yazdığınızda açıklayıcı bilgiler sağlayan IntelliSense genişletilebilirlik özelliklerinden otomatik olarak yararlanabilirsiniz. Açılır kutudaki açıklamalar üyenin açıklamasını içerir. Aşağıdaki örnek, bir tamamlanma listesinin açılan kutusunu gösterir.

 ![Hızlı bilgi pop&#45;yukarı kutusu örneği](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Geliştirici deneyimini daha da geliştirmek için, açılır kutuda geliştiricilere tür bilgileri sağlamak isteyebilirsiniz. Standart açıklama etiketleri yerine JavaScript [XML belge açıklamalarını](../ide/xml-documentation-comments-javascript.md) kullanarak tür bilgisi sağlayabilirsiniz. XML belge açıklamalarını, Üçlü eğik çizgi açıklama etiketleri (//) ve tanımlanmış bir XML öğeleri kümesi kullanarak eklersiniz.

 Alternatif olarak, JavaScript IntelliSense genişletilebilirliği kullanarak tür bilgisi sağlayabilirsiniz. Bu özellik, JavaScript uzantıları oluşturarak ve bunları betik bağlamına ekleyerek IntelliSense sonuçlarını özelleştirmenize olanak sağlar. Bir JavaScript dosyası olan uzantısında, dil hizmetinin nesnesi tarafından açığa çıkarılan olaylara abone olursunuz `intellisense` . Kitaplık için tercih edilen bir davranış deseninin JavaScript dil hizmetinin istenen düzeyde IntelliSense desteği sağlaması ve bildirime dayalı XML belgesi Yorumları için de gerekli olması durumunda JavaScript IntelliSense genişletilebilirliği, kitaplıklar için tercih edilen çözümdür. IntelliSense sonuçlarını özelleştirerek, dil hizmetinin varsayılan yeteneklerini kısıtlayabilen herhangi bir davranış deseninden bağımsız olarak birinci sınıf bir IntelliSense deneyimi oluşturabilirsiniz. Daha fazla bilgi için bkz. [tanımlayıcılar Için deyimin tamamlanması](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Betik bağlamına uzantı ekleme
 Bir IntelliSense uzantısının yürütülmesi için, geçerli betik bağlamına eklenmesi gerekir. Uzantı otomatik bulma mekanizması tarafından otomatik olarak komut dosyası bağlamına eklenebilir veya başvuru gruplarını veya başvuru yönergesini kullanarak uzantıyı betik bağlamına el ile ekleyebilirsiniz.

 Otomatik bulma mekanizması, dil hizmetinin, dosya adlandırma kuralı *LibraryName*.intellisense.js izleyen ve uzantının uygulandığı kitaplıkla aynı dizinde bulunan uzantıları otomatik olarak bulmasını sağlar. Örneğin, jQuery kitaplığı için geçerli bir uzantı jQuery.intellisense.js. Daha kısıtlayıcı jQuery uzantıları için jQuery-1.7.1.intellisense.js (sürüme özgü bir uzantı) veya jQuery.ui.intellisense.js (kapsamlı jQuery kitaplığı için bir uzantı) gibi dosya adlarını kullanabilirsiniz. Belirli bir kitaplık için birden fazla uzantı bulunursa, uzantının en kısıtlayıcı sürümü kullanılır.

 Uzantıyı tüm JavaScript proje dosyalarınız için kullanmak istiyorsanız, bunun yerine uzantıyı bir başvuru grubuna eklemeyi tercih edebilirsiniz. Örtük başvurular ve adanmış çalışan başvuruları dahil olmak üzere çeşitli türlerde başvuru grupları vardır. Uzantı eklemek için genellikle dosyayı örtük **(Windows)**, **örtük (Web)** olarak örtük bir başvuru grubu olarak eklemeniz gerekir. Örtük başvurular, kod Düzenleyicisi 'nde açılan her. js dosyası için kapsamdadır. Bu yöntemi kullandığınızda, hem uzantıyı hem de uzantının takıma girecek dosyasını eklemeniz gerekir.

 Bir uzantıyı başvuru grubu olarak eklemek için **Seçenekler** Iletişim kutusunun **IntelliSense** sayfasını kullanın. **IntelliSense** sayfasına, menü çubuğunda **Araçlar**, **Seçenekler** ' i ve ardından **metin Düzenleyicisi**, **JavaScript**, **IntelliSense**, **Başvurular**' ı seçerek erişebilirsiniz. Başvuru grupları hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md) ve [Seçenekler, metin düzenleyici, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Uzantıyı belirli bir dosya kümesi için kullanmak istiyorsanız, bir başvuru yönergesi kullanın. Bu yöntemi kullandığınızda, hem uzantıya hem de uzantının takıma girecek dosyaya başvurmanız gerekir. Başvuru yönergesini kullanma hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>IntelliSense olaylarını işleme
 Genişletilebilirlik özelliği, `statementcompletion` dil hizmeti nesnesinin olayı gibi olaylara abone olarak IntelliSense sonuçlarını özelleştirmenizi sağlar `intellisense` . Aşağıdaki örnek, bir alt çizgiyle başlayan üyeleri bir ifade tamamlamada gizlemek için dil hizmeti tarafından kullanılan basit bir uzantıyı gösterir. Bu kod underscorefilter.js içindedir ve \\ \\ *Visual Studio yükleme yolu*\javascript\references klasöründedir.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 Önceki kodda uzantı, ve gibi nesneleri hariç tutmak [targetName Property](#TargetName) [target Property](#Target) `statementcompletion` `this` `window` ve geçerli bir deyimin tamamlanma listesinin tanımlanmasını sağlamak Için olay nesnesinin TargetName özelliğini ve hedef özellik özelliklerini denetler. Bir tamamlama listesi tanımlanamıyorsa, uzantı alt çizgiyle başlayan üyeleri filtreleyerek deyimin tamamlanma [öğeleri Özellik](#Items) koleksiyonunu günceller.

 Daha fazla örnek için \\ \\ *Visual Studio yükleme yolu*\javascript\references klasörüne bakın. Bu klasördeki showPlainComments.js dosyası, standart JavaScript açıklama etiketleri (//) için varsayılan IntelliSense desteği sağlamak üzere diğer olayları kullanma örnekleri sunar. underscorefilter.js gibi, showPlainComments.js zaten bir çalışma uzantısı olarak kullanılabilir ve kodunuzda, işlevlerde ve nesneler için kodunuzda açıklama etiketleri kullanırken elde edilen IntelliSense bilgilerini görebilirsiniz. Daha fazla örnek için bkz. [kod örnekleri](#CodeExamples).

> [!WARNING]
> Visual Studio ile birlikte gelen uzantı dosyalarını değiştirirseniz, JavaScript IntelliSense veya uzantının desteklediği özelliği devre dışı bırakabilirsiniz.

 Uzantı kodunuzda aşağıdaki olay türleri için işleyicileri şunu kullanarak oluşturabilirsiniz `addEventListener` :

- `statementcompletion`, bir deyimin tamamlanma olayı için bir işleyici ekler. Deyimle tamamlama, belirli bir tür için, nokta (.) gibi özel bir karakter yazdıktan sonra veya yazarken veya CTRL + J tuşlarına bastığınızda görüntülenen tanımlayıcıların listesini içeren bir üye listesi sağlar. İşleyici, aşağıdaki üyeleri destekleyen, türünde bir olay nesnesi alır `CompletionEvent` : [Items özelliği](#Items), [target özelliği](#Target), [TargetName özelliği](#TargetName)ve [Scope özelliği](#Scope).

- `signaturehelp`, IntelliSense parametre bilgisi için bir işleyici ekler. Parametre bilgileri, bir işlevin gerektirdiği parametre sayısı, adları ve türleri hakkında bilgi verir. İşleyici, aşağıdaki üyeleri destekleyen, türünde bir olay nesnesi alır `SignatureHelpEvent` : [target özelliği](#Target), [ParentObject özelliği](#ParentObject), [functionComments özelliği](#FunctionComments), [functionHelp özelliği](#FunctionHelp).

- `statementcompletionhint`IntelliSense hızlı Info için bir işleyici ekler. Hızlı bilgi açılır kutusu, kodunuzdaki tanımlayıcıların tam bildirimini gösterir. İşleyici, aşağıdaki üyeleri destekleyen, türünde bir olay nesnesi alır `CompletionHintEvent` : [completionItem özelliği](#CompletionItem)ve [symbolHelp özelliği](#SymbolHelp).

  İfade tamamlama, parametre bilgileri ve hızlı bilgi gibi IntelliSense özelliklerini gösteren örnekler için bkz. [IntelliSense kullanma](../ide/using-intellisense.md).

> [!NOTE]
> JavaScript 'te hızlı bilgi, tamamlanma listesinin sağında görüntülenen açılır kutuyu ifade eder. Hızlı bilgileri el ile çağıramazsınız.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> IntelliSense nesnesi
 Aşağıdaki tablo, nesnesi için kullanılabilir olan işlevleri gösterir `intellisense` . `intellisense`Nesne yalnızca tasarım zamanında kullanılabilir.

|İşlev|Açıklama|
|--------------|-----------------|
|`addEventListener(type, handler);`|IntelliSense olayı için bir olay işleyicisi ekler.<br /><br /> `type` bir dize değeridir. Geçerli değerler `statementcompletion` ,, `signaturehelp` ve içerir `statementcompletionhint` .<br /><br /> `handler` , aşağıdaki türlerden birine ait bir olay nesnesi alan olay işleyicisi işlevidir:<br /><br /> -   `CompletionEvent`, olay için kullanılır `statementcompletion` .<br />-   `SignatureHelpEvent`, olay için kullanılır `signaturehelp` .<br />-   `CompletionHintEvent`, olay için kullanılır `statementcompletionhint` .<br /><br /> Bu işlevi kullanan örnekler için bkz. [kod örnekleri](#CodeExamples).|
|`annotate(obj, doc);`|Belge açıklamalarını bir nesneden başka bir nesneye kopyalayarak nesnenin belgelerini belirtir.<br /><br /> `obj` belgenin kopyalanacağı nesneyi belirtir.<br /><br /> `doc` belgenin kopyalanacağı nesneyi belirtir.<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz. [IntelliSense ek açıklamalarını ekleme](#Annotations).|
|`getFunctionComments(func);`|Belirtilen işlev için açıklamaları döndürür.<br /><br /> `func` açıklamaların döndürüleceği işlevi belirtir.<br /><br /> `func`Parametresini kullanarak ayarlayabilirsiniz `completionItem.value` .<br /><br /> Döndürülen `functionComments` nesne aşağıdaki üyeleri içerir: `above` , `inside` , ve `paramComment` . Daha fazla bilgi için bkz. [functionComments özelliği](#FunctionComments) özelliği.<br /><br /> `getFunctionComments` , yalnızca tarafından kaydedilen olay işleyicilerinden biri içinden çağrılabilir `addEventListener` .<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için bkz \\ \\ . *Visual Studio yükleme yolu*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Tanılama iletilerini çıkış penceresine gönderir.<br /><br /> `msg` iletiyi içeren bir dizedir.<br /><br /> Bu işlevin nasıl kullanılacağını gösteren bir örnek için, bkz. [iletileri çıkış penceresi gönderme](#Logging).|
|`nullWithCompletionsOf(value);`|Tamamlanma listesinin parametre içinde geçirildiği nesne tarafından belirlendiği özel bir null değer döndürür `value` .<br /><br /> `value` döndürülen değerin tamamlanma listesini belirler. `value` herhangi bir tür olabilir.<br /><br /> Null dönüş değeri tasarım zamanında null olarak değerlendirilir, ancak dönüş değeri için tamamlama listesi, parametrenin tamamlanma listesiyle aynıdır `value` .<br /><br /> Bu işlev için bir kullanım, dönüş türü çalışma zamanında tahmin edildiğinde, ancak dönüş değeri tasarım zamanı olduğunda bir dönüş değeri için IntelliSense sağlamaktır `null` .|
|`redirectDefinition(func, definition);`|Parametre yardımı veya **tanım 'e git** Istendiğinde, IntelliSense 'in özgün Func işlevi yerine sağlanan tanım işlevini kullanmasını söyler.<br /><br /> `func` Hedef işlevi belirtir.<br /><br /> `definition` parametre bilgileri için hedef işlev yerine kullanılacak işlevi belirtir ve **Tanıma Git**.|
|`setCallContext(func, thisArg);`|Belirtilen işlev için çağrı bağlamını veya kapsamını ayarlar.<br /><br /> `func` kapsam ayarlanacak işlevi belirtir.<br /><br /> `thisArg` , `this` anahtar sözcüğünün başvurabileceği ve üyenin yeni kapsamını belirten bir nesne sabit değeri. Bu parametreye geçirilecek bağımsız değişkenleri ekleyebilirsiniz, örneğin `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext``Function.prototype.bind`, yalnızca tasarım zamanı IntelliSense desteği için kullanılması dışında şuna benzer bir davranış sağlar. `setCallContext`Başka türlü erişilebilir olmayan bir koda çağrı benzetimi yapmanız gerekiyorsa işlev kapsamını ayarlamak için kullanabilirsiniz, böylece işlevi çağırdığınızda işlev çağrısı doğru kapsam ve bağımsız değişkenleri içerecektir.|
|`undefinedWithCompletionsOf(value);`|Tamamlanma listesinin parametre içinde geçirildiği nesne tarafından belirlendiği özel bir tanımsız değer döndürür `value` .<br /><br /> `value` döndürülen değerin tamamlanma listesini belirler. `value` herhangi bir tür olabilir.<br /><br /> Tanımsız dönüş değeri tasarım zamanında tanımsız olarak değerlendirilir, ancak dönüş değeri için tamamlama listesi, parametrenin tamamlanma listesiyle aynıdır `value` .<br /><br /> Bu işlev için bir kullanım, dönüş türü çalışma zamanında tahmin edildiğinde, ancak tasarım zamanında dönüş değeri tanımsız olduğunda bir dönüş değeri için IntelliSense sağlamaktır.|
|`version()`|Visual Studio sürümünü döndürür.|

## <a name="event-members"></a>Olay üyeleri
 Aşağıdaki bölümler, aşağıdaki olaylar için olay nesnesinde sunulan üyeleri anlatmaktadır: `statementcompletion` , `signaturehelp` ve `statementcompletionhint` .

### <a name="completionitem-property"></a><a name="CompletionItem"></a> completionItem özelliği
 Bir hızlı bilgi açılır kutusu istenen, tamamlanma öğesi olarak bilinen tanımlayıcıyı döndürür. Bu özellik olay nesnesi `statementcompletionhint` ve olay nesnesinin [Items özelliği](#Items) özelliği için kullanılabilir `statementcompletion` .

 Dönüş değeri: `completionItem` nesne

 Nesnenin üyeleri aşağıda verilmiştir `completionItem` :

- `name`. Koleksiyonda kullanıldığında okuma/yazma `items` ; Aksi takdirde, salt okunurdur. Tamamlama öğesini tanımlayan bir dize döndürür.

- `kind`. Koleksiyonda kullanıldığında okuma/yazma `items` ; Aksi takdirde, salt okunurdur. Tamamlanma öğesi türünü temsil eden bir dize döndürür. Olası değerler yöntemi, alanı, özelliği, parametresi, değişkeni ve ayrılmış değerlerdir.

- `glyph`. Koleksiyonda kullanıldığında okuma/yazma `items` ; Aksi takdirde, salt okunurdur. Tamamlama listesinde görüntülenen bir simgeyi temsil eden bir dize döndürür. İçin olası değerler `glyph` Şu biçimi kullanır: vs:*GlyphType*, burada *GlyphType* , Numaralandırmadaki dilden bağımsız üyelere karşılık gelir <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> . Örneğin, `vs:GlyphGroupMethod` için olası bir değerdir `glyph` . Ayarlandığında `glyph` , `kind` özelliği varsayılan simgeyi belirler.

- `parentObject`. Salt okunur. Ana nesneyi döndürür.

- `value`. Salt okunur. Tamamlama öğesinin değerini temsil eden bir nesne döndürür.

- `comments`. Salt okunur. Alanın veya değişkenin üzerinde olan açıklamaları içeren bir dize döndürür.

- `scope`. Salt okunur. Tamamlama öğesinin kapsamını döndürür. Olası değerler genel, yerel, parametre ve üyesidir.

### <a name="items-property"></a><a name="Items"></a> Items özelliği
 İfade tamamlama öğelerinin dizisini alır veya ayarlar. Dizideki her öğe bir [completionItem Özellik](#CompletionItem) nesnesidir. `items`Özelliği `statementcompletion` olay nesnesi için kullanılabilir.

 Dönüş değeri: dizi

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> functionComments özelliği
 İşlevin açıklamalarını döndürür. Bu özellik olay nesnesi için kullanılabilir `signaturehelp` .

 Dönüş değeri: `comments` nesne

 Nesnenin üyeleri aşağıda verilmiştir `comments` :

- `above`. İşlevin üzerindeki açıklamaları döndürür.

- `inside`. Genellikle VSDoc biçiminde işlev içindeki açıklamaları döndürür.

- `paramComments`. İşlevdeki her bir parametre için açıklamaları temsil eden bir dize döndürür. Dizi üyeleri şunları içerir:

  - `name`. Parametre adını temsil eden bir dize döndürür.

  - `comment`. Parametre açıklamasını içeren bir dize döndürür.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> functionHelp özelliği
 İşlevin yardımını döndürür. Bu özellik olay nesnesi için kullanılabilir `signaturehelp` .

 Dönüş değeri: `functionHelp` nesne

 Nesnenin üyeleri aşağıda verilmiştir `functionHelp` :

- `functionName`. Okuma/yazma. İşlev adını içeren bir dize döndürür.

- `signatures`. Okuma/yazma. İşlev imzalarının dizisini alır veya ayarlar. Dizideki her öğe bir `signature` nesnedir. Gibi bazı `signature` Özellikler, `locid` ortak [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md) özniteliklerine karşılık gelir.

  `signature`Nesnenin üyeleri şunları içerir:

  - `description`. Okuma/yazma. İşlevi tanımlayan bir dize döndürür.

  - `locid`. Okuma/yazma. İşlevle ilgili yerelleştirme bilgilerini içeren bir dize tanımlayıcısı döndürür.

  - `helpKeyword`. Okuma/yazma. Help anahtar sözcüğünü içeren bir dize döndürür.

  - `externalFile`. Okuma/yazma. Üye KIMLIĞINI içeren dosyayı temsil eden bir dize döndürür.

  - `externalid`. Okuma/yazma. İşlevin üye KIMLIĞINI temsil eden bir dize döndürür.

  - `params`. Okuma/yazma. İşlevin parametre dizisini alır veya ayarlar. Parameters dizisindeki her öğe, `parameter` öğesinin aşağıdaki özniteliklerine karşılık gelen özellikleri olan bir nesnedir [\<param>](../ide/param-javascript.md) :

    - `name`. Okuma/yazma. Parametre adını temsil eden bir dize döndürür.

    - `type`. Okuma/yazma. Parametre türünü temsil eden bir dize döndürür.

    - `elementType`. Okuma/yazma. Tür ise `Array` , dizideki öğelerin türünü temsil eden bir dize döndürür.

    - `description`. Okuma/yazma. Parametresini tanımlayan bir dize döndürür.

    - `locid`. Okuma/yazma. İşlevle ilgili yerelleştirme bilgilerini içeren bir dize tanımlayıcısı döndürür.

    - `optional`. Okuma/yazma. Parametrenin isteğe bağlı olup olmadığını gösteren bir dize döndürür. `true` parametrenin isteğe bağlı olduğunu belirtir; `false` olmadığını gösterir.

  - `returnValue`. Okuma/yazma. Öğesinin aşağıdaki özniteliklerine karşılık gelen özelliklerle birlikte bir dönüş değeri nesnesi alır veya ayarlar [\<returns>](../ide/returns-javascript.md) :

    - `type`. Okuma/yazma. Dönüş türünü temsil eden bir dize döndürür.

    - `elementType`. Okuma/yazma. Tür ise `Array` , dizideki öğelerin türünü temsil eden bir dize döndürür.

    - `description`. Okuma/yazma. Dönüş değerini tanımlayan bir dize döndürür.

    - `locid`. Okuma/yazma. İşlevle ilgili yerelleştirme bilgilerini içeren bir dize tanımlayıcısı döndürür.

    - `helpKeyword`. Okuma/yazma. Help anahtar sözcüğünü içeren bir dize döndürür.

    - `externalFile`. Okuma/yazma. Üye KIMLIĞINI içeren dosyayı temsil eden bir dize döndürür.

    - `externalid`. Okuma/yazma. İşlevin üye KIMLIĞINI temsil eden bir dize döndürür.

### <a name="parentobject-property"></a><a name="ParentObject"></a> parentObject özelliği
 Bir üye işlevinin üst nesnesini döndürür. Örneğin, için, `document.getElementByID` `parentObject` `document` nesnesini döndürür. Bu özellik olay nesnesi için kullanılabilir `signaturehelp` .

 Dönüş değeri: nesne

### <a name="target-property"></a><a name="Target"></a> Target özelliği
 Bir nokta (.) olan tetikleyici karakterinin solundaki öğeyi temsil eden bir nesne döndürür. İşlevler için, `target` parametre bilgisinin istendiği işlevi döndürür. Bu özellik `statementcompletion` ve olay nesneleri için kullanılabilir `signaturehelp` .

 Dönüş değeri: nesne

### <a name="targetname-property"></a><a name="TargetName"></a> targetName özelliği
 Hedefi temsil eden bir dize döndürür. Örneğin, "this." için `targetName` "This" döndürür. "A. B" (imleç "B" olduğunda) için `targetName` "b" döndürür. Bu özellik olay nesnesi için kullanılabilir `statementcompletion` .

 Dönüş değeri: dize

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> symbolHelp özelliği
 Bir hızlı bilgi açılır kutusu istenen tamamlama öğesini döndürür. Bu özellik olay nesnesi için kullanılabilir `statementcompletionhint` .

 Dönüş değeri: `symbolHelp` nesne.

 Nesnesinin bazı özellikleri (gibi), `symbolHelp` `locid` ortak [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md) özniteliklerine karşılık gelir.

 Nesnenin üyeleri aşağıda verilmiştir `symbolHelp` :

- `name`. Okuma/yazma. Tanımlayıcı adını içeren bir dize döndürür.

- `symbolType`. Okuma/yazma. Sembol türünü temsil eden bir dize döndürür. Olası değerler bilinmeyen, Boole, sayı, dize, nesne, Işlev, dizi, tarih ve Regex içerir.

- `symbolDisplayType`. Okuma/yazma. Görüntülenecek tür adını içeren bir dize döndürür. `symbolDisplayType`Ayarlanmamışsa, `symbolType` kullanılır.

- `elementType`. Okuma/yazma. `symbolType`İse `Array` , dizideki öğelerin türünü temsil eden bir dize döndürür.

- `scope`. Okuma/yazma. Simgenin kapsamını temsil eden bir dize döndürür. Olası değerler genel, yerel, parametre ve üyeyi içerir.

- `description`. Okuma/yazma. Simgenin açıklamasını içeren bir dize döndürür.

- `locid`. Okuma/yazma. Sembol hakkında yerelleştirme bilgilerini içeren bir dize tanımlayıcısı döndürür.

- `helpKeyword`. Okuma/yazma. Help anahtar sözcüğünü içeren bir dize döndürür.

- `externalFile`. Okuma/yazma. Üye KIMLIĞINI içeren dosyayı temsil eden bir dize döndürür.

- `externalid`. Okuma/yazma. Simgenin üye KIMLIĞINI temsil eden bir dize döndürür.

- `functionHelp`. Okuma/yazma. , Işlevi olduğunda bilgi içerebilen bir [functionHelp özelliği](#FunctionHelp)döndürür `symbolType` .

### <a name="scope-property"></a><a name="Scope"></a> Scope özelliği
 Etkinliğin tamamlanma kapsamını döndürür. Tamamlama kapsamı için olası değerler geneldir ve üyeleridir. Bu özellik olay nesnesi için kullanılabilir `statementcompletion` .

 Dönüş değeri: dize

## <a name="debugging-intellisense-extensions"></a>IntelliSense uzantılarında hata ayıklama
 Uzantılara hata ayıklaması yapamazsınız, ancak Visual Studio çıktı penceresine bilgi göndermek için [IntelliSense nesne](#intellisenseObject) işlevini kullanabilirsiniz. Bu işlevin nasıl kullanılacağını gösteren bir örnek için, bu konunun ilerleyen kısımlarında [Çıkış penceresi Iletileri gönderme](#Logging) bölümüne bakın. `logMessage`Çalışmak için en az bir olay işleyicisinin bir uzantıya kayıtlı olması gerekir.

## <a name="code-examples"></a><a name="CodeExamples"></a> Kod örnekleri
 Bu bölüm, IntelliSense genişletilebilirlik API 'Lerinin nasıl kullanılacağını gösteren kod örnekleri içerir. Bu API 'Leri kullanmanın başka yolları da vardır. Daha fazla örnek için, \\ \\ *Visual Studio yükleme yolu*\javascript\references klasöründe aşağıdaki dosyalara bakın. Bunlar, JavaScript dil hizmeti tarafından kullanılan çalışma örnekleridir.

- underscoreFilter.js. Bu kod, özel üyeleri IntelliSense 'den gizler. Olaya yönelik olay işleyicilerini içerir `statementcompletion` .

- showPlainComments.js. Bu kod, standart Yorumlar için IntelliSense desteği sağlar. Ve olayları için olay işleyicilerini içerir `signaturehelp` `statementcompletionhint` .

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> IntelliSense ek açıklamalarını ekleme
 Aşağıdaki yordamda, kitaplığı doğrudan değiştirmek zorunda kalmadan bir üçüncü taraf kitaplığı için IntelliSense belge desteğinin nasıl sağlanması gösterilmektedir. Bunu yapmak için `intellisense.annotate` bir uzantıda kullanabilirsiniz.

 Bu örneğin çalışması için, projenizde aşağıdaki JavaScript dosyaları gerekir:

- Bir üçüncü taraf kitaplığını temsil eden bir proje dosyası olan demoLib.js.

- IntelliSense uzantısı olan demoLib.intellisense.js. Bu dosyanın projeye dahil olması gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.

- Uygulama kodunu temsil eden bir proje dosyası olan appCode.js.

##### <a name="to-add-an-intellisense-annotation"></a>Bir IntelliSense ek açıklaması eklemek için

1. demoLib.js için aşağıdaki kodu ekleyin.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. demoLib.intellisense.js için aşağıdaki kodu ekleyin.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. Aşağıdaki başvuru yönergesini appCode.js ilk satır olarak ekleyin. Burada kullanılan yol, JavaScript dosyalarının aynı klasörde olduğunu gösterir.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. appCode.js ' de aşağıdaki kodu yazın. XML belge açıklamalarını IntelliSense parametre bilgisi olarak görüntülenmiş şekilde görürsünüz.

     ![IntelliSense 'in kullanımını gösteren örnek. Not](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. appCode.js ' de aşağıdaki kodu yazın. Yazdığınızda, standart açıklamaları IntelliSense hızlı bilgileri olarak görüntülenmiş şekilde görürsünüz.

     ![IntelliSense 'in kullanımını gösteren örnek. Not](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> Çıkış Penceresi Ileti gönderme
 Aşağıdaki yordamda, çıkış penceresine nasıl ileti gönderileceğini gösterilmektedir. IntelliSense uzantılarının hatalarını ayıklamanıza yardımcı olmak için iletiler gönderebilirsiniz.

 Bu örneğin çalışması için, projenizde aşağıdaki JavaScript dosyaları gerekir:

- Bir üçüncü taraf kitaplığını temsil eden bir proje dosyası olan exampleLib.js.

- IntelliSense uzantısı olan exampleLib.intellisense.js. Bu dosyanın projeye dahil olması gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.

- Uygulama kodunu temsil eden bir proje dosyası olan appCode.js.

##### <a name="to-send-a-message-to-the-output-window"></a>Çıkış penceresine bir ileti göndermek için

1. exampleLib.js için aşağıdaki kodu ekleyin.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. exampleLib.intellisense.js için aşağıdaki kodu ekleyin.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. Aşağıdaki başvuru yönergesini appCode.js ilk satır olarak ekleyin. Burada kullanılan yol, JavaScript dosyalarının aynı klasörde olduğunu gösterir.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. Çıkış penceresinde **çıktıyı göster** listesinden **JavaScript Language Service** ' yi seçin. (Çıkış penceresini görüntülemek için, Görünüm menüsünden **Çıkış** ' ı seçin.)

5. appCode.js ' de aşağıdaki kodu yazın. Yazarken, çıkış penceresinde dil hizmetinden iletiler görüntülenir. Çıkış penceresindeki ilk ileti, geçerli kapsamın bildiri tamamlanmasının istendiğini gösterir.

    ```javascript
    some
    ```

     Aşağıda, görmeniz gereken çıktının kısmi bir görünümü verilmiştir.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Çıkış penceresindeki **Tümünü Temizle** düğmesini seçin.

7. Aşağıdaki kodu yazın. Çıkış penceresindeki ilk ileti, bir üye listesinin istenmiş olduğunu gösterir.

    ```javascript
    someVar.
    ```

     Aşağıda, görmeniz gereken çıktının kısmi bir görünümü verilmiştir:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> IntelliSense simgelerini değiştirme
 Aşağıdaki yordamda, varsayılan olarak IntelliSense tarafından gösterilen simgelerin nasıl değiştirileceği gösterilmektedir. Bu, ad alanları, sınıflar, arabirimler ve numaralandırmalar gibi kitaplığa özel kavramlar hakkında IntelliSense bilgileri sağladığınızda yararlı olabilir.

 Kullanılabilir simge değerleri için bkz <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> ..

 Bu örneğin çalışması için, projenizde aşağıdaki JavaScript dosyaları gerekir:

- Üçüncü taraf kitaplığı represens bir proje dosyası olan exampleLib.js.

- IntelliSense uzantısı olan exampleLib.intellisense.js. Bu dosyanın projeye dahil olması gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.

- Uygulama kodunu temsil eden bir proje dosyası olan appCode.js.

##### <a name="to-change-the-icons"></a>Simgeleri değiştirmek için

1. exampleLib.js için aşağıdaki kodu ekleyin.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. exampleLib.intellisense.js için aşağıdaki kodu ekleyin.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. Aşağıdaki başvuru yönergesini appCode.js ilk satır olarak ekleyin. Burada kullanılan yol, JavaScript dosyalarının aynı klasörde olduğunu gösterir.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. appCode.js ' de aşağıdaki kodu yazın. Siz yazarken, {} C# ' de kullanıldığı gibi ad alanı simgesinin "" olarak değiştirildiğini görürsünüz.

     ![Glif özelliğinin kullanımını gösteren örnek](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. appCode.js ' de aşağıdaki kodu yazın. Yazarken, Enum1 üyesi için yeni bir sabit listesi simgesi ve SomeClass1 üyesi için yeni bir sınıf simgesi görürsünüz.

     ![Glif özelliğinin kullanımını gösteren örnek](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> IntelliSense sonuçları üzerinde çalışma zamanı etkileri önleme
 JavaScript dil hizmeti, IntelliSense bilgilerini dinamik olarak sağlamak için kodu çalıştırır. Sonuç olarak, çalışma zamanı davranışı zaman zaman istenen sonuçlara engel olabilir. Aşağıdaki yordam, çalışma zamanı davranışı yanlış IntelliSense ile sonuçlandığı zaman IntelliSense sonuçlarının nasıl geçersiz kılınacağını göstermektedir.

 Bu örneğin çalışması için, projenizde aşağıdaki JavaScript dosyaları gerekir:

- Bir üçüncü taraf kitaplığını temsil eden bir proje dosyası olan exampleLib.js.

- IntelliSense uzantısı olan exampleLib.intellisense.js. Bu dosyanın projeye dahil olması gerekmez, ancak exampleLib.js aynı klasörde olması gerekir.

- Uygulama kodunu temsil eden bir proje dosyası olan appCode.js.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>IntelliSense sonuçlarında çalışma zamanı etkilerine engel olmak için

1. exampleLib.js için aşağıdaki kodu ekleyin.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     Yukarıdaki kodda, Sarmalanan işlev, değerine göre ilk çağrıları yoksayar `count` ve sonuç döndürmez.

2. Aşağıdaki başvuru yönergesini appCode.js ilk satır olarak ekleyin. Burada kullanılan yol, JavaScript dosyalarının aynı klasörde olduğunu gösterir.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. appCode.js ' de aşağıdaki kodu yazın. Sarmalanan işlev hiçbir şekilde çağrılmadığından, `throttled` işlevin hiçbir sonuç döndürmediği anlamına gelen tanımlayıcı liste IntelliSense yerine görünür.

     ![IntelliSense sonuçlarını geçersiz kılma örneği](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. exampleLib.intellisense.js için aşağıdaki kodu ekleyin. Bu, tasarım zamanı davranışını IntelliSense 'in beklendiği gibi sarmalanmış işlev için gösterilmesi için değiştirir.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. appCode.js, daha önce yazdığınız kodu yazarak sonuçları test edin. Bu kez, IntelliSense istenen bilgileri sağlar.

     ![IntelliSense sonuçlarını geçersiz kılma örneği](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Ayrıca Bkz.
 Tanımlayıcılar için [JavaScript IntelliSense](../ide/javascript-intellisense.md) [bildiri tamamlama](../ide/statement-completion-for-identifiers.md)
