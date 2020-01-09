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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593726"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio, hemen kullanıma hazır güçlü bir JavaScript düzenlemesi deneyimi sağlar. TypeScript tabanlı bir dil hizmeti tarafından desteklenen Visual Studio daha zengin IntelliSense, modern JavaScript özelliklerine yönelik destek ve tanım, yeniden düzenleme ve daha fazlası gibi geliştirilmiş üretkenlik özellikleri sunar.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak, JavaScript dil hizmeti dil hizmeti için yeni bir altyapı kullanır ("Salsa" adı verilir). Ayrıntılar bu makaleye dahildir ve bu [blog gönderisini](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/)de okuyabilirsiniz. Yeni düzen deneyimi genellikle Visual Studio Code için de geçerlidir. Daha fazla bilgi için [vs Code belgelerine](https://code.visualstudio.com/docs/languages/javascript) bakın.

Visual Studio 'nun genel IntelliSense işlevselliği hakkında daha fazla bilgi için bkz. [IntelliSense kullanma](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Visual Studio 2017 ' de JavaScript dil hizmetindeki yenilikler

Visual Studio 2017 ' den başlayarak, JavaScript IntelliSense parametre ve üye listeleri hakkında daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planda statik analiz kullanan TypeScript dil hizmeti tarafından sağlanır.

TypeScript, bu bilgileri oluşturmak için birkaç kaynak kullanır:

- [Tür çıkarımı temelinde IntelliSense](#TypeInference)
- [JSDoc tabanlı IntelliSense](#JsDoc)
- [TypeScript bildirim dosyalarını temel alan IntelliSense](#TsDeclFiles)
- [Tür tanımlarının otomatik alımı](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>Tür çıkarımı temelinde IntelliSense

JavaScript 'te, çoğu zaman açık tür bilgisi yoktur. Yağckily, çevreleyen kod bağlamı verilen bir türü kolayca anlamak oldukça kolaydır.
Bu işleme tür çıkarımı adı verilir.

Bir değişken veya özellik için, türü genellikle onu başlatmak için kullanılan değerin türü veya en son değer atamasını kullanır.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Bir işlev için, dönüş türü dönüş deyimlerinden çıkarsanamıyor.

İşlev parametreleri için şu anda bir çıkarım yoktur, ancak bunu JSDoc veya TypeScript *. d. TS* dosyalarını kullanarak geçici olarak çözmek için yollar vardır (sonraki bölümlere bakın).

Ayrıca, aşağıdakiler için özel çıkarım de vardır:

- "ES3-Style" sınıfları, bir Oluşturucu işlevi ve prototip özelliğine atamalar kullanılarak belirtilir.
- `exports` nesnesinde özellik atamaları olarak belirtilen CommonJS stili modül desenleri veya `module.exports` özelliğine atamalar.

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

### <a name="intellisense-based-on-jsdoc"></a>JSDoc tabanlı IntelliSense

Tür çıkarımı istenen tür bilgilerini sağlamıyorsa (veya belgeleri desteklemek için), JSDoc ek açıklamaları aracılığıyla açıkça bir tür bilgisi sağlanmayabilir.  Örneğin, kısmen tanımlanmış bir nesneye belirli bir tür vermek için, `@type` etiketini aşağıda gösterildiği gibi kullanabilirsiniz:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Belirtildiği gibi, işlev parametreleri hiçbir şekilde çıkarsanamıyor. Ancak, JSDoc `@param` etiketini kullanarak, işlev parametrelerine de tür ekleyebilirsiniz.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Şu anda desteklenen JsDoc ek açıklamaları için bkz. [JavaScript 'Te JSDoc desteği](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) .

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>TypeScript bildirim dosyalarını temel alan IntelliSense

JavaScript ve TypeScript artık aynı dil hizmetini temel aldığı için, daha zengin bir şekilde etkileşim kurabilir. Örneğin, JavaScript IntelliSense, bir *. d. TS* dosyasında belirtilen değerler için (bkz. [TypeScript belgelerine](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)bakın) ve TypeScript 'te belirtilen arabirimler ve sınıflar, JSDoc açıklamalarında türler olarak kullanılabilir.

Aşağıda, bu tür bilgilerini (bir arabirim aracılığıyla) aynı projede bir JavaScript dosyasına (bir `JsDoc` etiketi kullanarak) sağlayan bir TypeScript tanım dosyasının basit bir örneğini gösteririz.

![TypeScript tanım dosyası](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Tür tanımlarının otomatik alımı

TypeScript dünyasında en popüler JavaScript kitaplıklarının API 'Leri *. d. TS* dosyaları tarafından tanımlanır ve bu tür tanımlar için en yaygın depo, [Definitelytyped](https://github.com/DefinitelyTyped/DefinitelyTyped)' dedir.

Varsayılan olarak, salsa dili hizmeti hangi JavaScript kitaplıklarının kullanımda olduğunu algılamaya çalışır ve daha zengin IntelliSense sağlamak için kitaplığı tanımlayan ilgili *. d. TS* dosyasını otomatik olarak indirir. Dosyalar, *%LocalAppData%\microsoft\typescript*konumundaki Kullanıcı klasörünün altında bulunan bir önbelleğe indirilir.

> [!NOTE]
> *Tsconfig. JSON* yapılandırma dosyası kullanılıyorsa, bu özellik varsayılan olarak **devre dışıdır** , ancak aşağıda açıklandığı gibi etkin olarak ayarlanabilir.

Şu anda otomatik algılama, NPM 'den indirilen bağımlılıklar için ( *Package. JSON* dosyasını okuyarak), Bower ( *Bower. JSON* dosyasını okuyarak) ve projenizde en popüler 400 en popüler JavaScript kitaplıklarının listesiyle eşleşen gevşek dosyalar için geçerlidir. Örneğin, projenizde *jQuery-1,10. min. js* varsa, daha iyi bir düzen deneyimi sağlamak amacıyla *jQuery. d. TS* dosyası getirilir ve yüklenir. Bu *. d. TS* dosyası projeniz üzerinde hiçbir etkiye sahip olmayacaktır.

Otomatik alma 'yı kullanmak istemiyorsanız, aşağıda özetlenen bir yapılandırma dosyası ekleyerek devre dışı bırakın. Tanım dosyalarını, doğrudan projeniz içinde kullanmak üzere el ile de yerleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [JavaScript desteği (Mac için Visual Studio)](/visualstudio/mac/javascript)
