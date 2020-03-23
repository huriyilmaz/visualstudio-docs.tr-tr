---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2459c9ab7b6dc6e49bbbe86729d25a2adb5bdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593726"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio kutunun hemen dışında güçlü bir JavaScript düzenleme deneyimi sağlar. TypeScript tabanlı bir dil hizmetiyle güçlendirilen Visual Studio, daha zengin IntelliSense, modern JavaScript özellikleri desteği ve Go to Definition, refactoring ve daha fazlası gibi gelişmiş üretkenlik özellikleri sunar.

> [!NOTE]
> Visual Studio 2017'den itibaren JavaScript dil hizmeti, dil hizmeti için yeni bir motor kullanır ("Salsa"). Ayrıntılar bu makalede yer alıyor ve ayrıca bu [blog yazısı](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/)okuyabilirsiniz. Yeni düzenleme deneyimi çoğunlukla Visual Studio Code için de geçerlidir. Daha fazla bilgi için [VS Kodu dokümanlarına](https://code.visualstudio.com/docs/languages/javascript) bakın.

Visual Studio'nun genel IntelliSense işlevselliği hakkında daha fazla bilgi için Bkz. [IntelliSense'i kullanma.](../ide/using-intellisense.md)

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Visual Studio 2017'deki JavaScript dil hizmetinde yenilikler

Visual Studio 2017'den itibaren JavaScript IntelliSense parametre ve üye listeleri hakkında çok daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planda statik çözümleme kullanan TypeScript dil hizmeti tarafından sağlanır.

TypeScript bu bilgileri oluşturmak için çeşitli kaynaklar kullanır:

- [Tür çıkarımına göre IntelliSense](#TypeInference)
- [IntelliSense JSDoc dayalı](#JsDoc)
- [TypeScript bildirim dosyalarına dayalı IntelliSense](#TsDeclFiles)
- [Tür tanımlarının otomatik olarak edinimi](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>Tür çıkarımına göre IntelliSense

JavaScript'te çoğu zaman açık tür bilgisi yoktur. Neyse ki, genellikle çevreleyen kod bağlamında verilen bir türü anlamaya oldukça kolaydır.
Bu işleme tür çıkarımı denir.

Bir değişken veya özellik için, tür genellikle onu veya en son değer atamasını başlatmada kullanılan değerin türüdür.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Bir işlev için, iade türü iade ifadelerinden çıkarılabilir.

İşlev parametreleri için şu anda çıkarım yoktur, ancak JSDoc veya TypeScript *.d.ts* dosyalarını kullanarak bu işi aşmanın yolları vardır (sonraki bölümlere bakın).

Ayrıca, aşağıdakiler için özel çıkarım vardır:

- "ES3 stili" sınıfları, bir oluşturucu işlevi ve prototip özelliği atamaları kullanılarak belirtilir.
- Nesnedeki `exports` özellik atamaları veya özellik atamaları olarak belirtilen CommonJS tarzı `module.exports` modül desenleri.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>IntelliSense JSDoc dayalı

Tür çıkarımlarının istenilen tür bilgilerini sağlamadığı durumlarda (veya belgeleri desteklemek için), tür bilgileri JSDoc ek açıklamaları aracılığıyla açıkça sağlanabilir.  Örneğin, kısmen bildirilen bir nesneye belirli bir tür `@type` vermek için etiketi aşağıda gösterildiği gibi kullanabilirsiniz:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Belirtildiği gibi, işlev parametreleri asla çıkarılamaz. Ancak, JSDoc `@param` etiketini kullanarak işlev parametrelerine de türleri ekleyebilirsiniz.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Şu anda desteklenen JsDoc ek açıklamaları için [JavaScript'te JSDoc desteğine](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) bakın.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>TypeScript bildirim dosyalarına dayalı IntelliSense

JavaScript ve TypeScript artık aynı dil hizmetini temel aldıklarından, daha zengin bir şekilde etkileşim kurabilirler. Örneğin, JavaScript IntelliSense bir *.d.ts* dosyasında bildirilen değerler için sağlanabilir (bkz. [TypeScript belgeleri),](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)ve TypeScript'te bildirilen arabirimler ve sınıflar gibi türler JsDoc yorumlarında tür olarak kullanılabilir.

Aşağıda, aynı projedeki bir JavaScript dosyasına (bir arayüz üzerinden) bu tür bilgileri sağlayan bir TypeScript tanım dosyasının basit bir örneğini (etiket `JsDoc` kullanarak) gösteririz.

![TypeScript tanım dosyası](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Tür tanımlarının otomatik olarak edinimi

TypeScript dünyasında, en popüler JavaScript kitaplıkları *API'lerinin .d.ts* dosyaları tarafından açıklanan api'lerine sahiptir ve bu tür tanımlar için en yaygın depo [DefinitelyTyped'dadır.](https://github.com/DefinitelyTyped/DefinitelyTyped)

Varsayılan olarak, Salsa dil hizmeti hangi JavaScript kitaplıklarının kullanımda olduğunu algılamaya çalışır ve daha zengin IntelliSense sağlamak için kitaplığı açıklayan ilgili *.d.ts* dosyasını otomatik olarak karşıdan yükleyip başvurur. Dosyalar *%LOCALAPPDATA%\Microsoft\TypeScript*adresindeki kullanıcı klasörünün altında bulunan bir önbelleğe indirilir.

> [!NOTE]
> Bu özellik, *bir tsconfig.json* yapılandırma dosyası kullanıyorsanız varsayılan olarak **devre dışı bırakılır,** ancak aşağıda belirtildiği gibi etkin olarak ayarlanabilir.

Şu anda otomatik algılama npm *(package.json* dosyasını okuyarak), Bower *(bower.json* dosyasını okuyarak) indirilen bağımlılıklar için çalışır ve projenizde kabaca en popüler 400 JavaScript kitaplıklarının bir listesini eşleşen gevşek dosyalar için çalışır. Örneğin, projenizde *jquery-1.10.min.js* varsa, daha iyi bir düzenleme deneyimi sağlamak için *jquery.d.ts* dosyası getirilir ve yüklenir. Bu *.d.ts* dosyasının projeniz üzerinde hiçbir etkisi olmayacaktır.

Otomatik edinme kullanmak istemiyorsanız, aşağıda belirtildiği gibi bir yapılandırma dosyası ekleyerek bu dosyayı devre dışı edin. Tanım dosyalarını doğrudan projenizin içinde el ile kullanmaya devam edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [JavaScript desteği (Mac için Visual Studio)](/visualstudio/mac/javascript)
