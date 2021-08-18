---
title: JavaScript IntelliSense
description: Daha Visual Studio IntelliSense, modern JavaScript özellikleri için destek ve gelişmiş üretkenlik özellikleri sunma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c5f997b7a4be43e6a8482a6282ecaaf2e3babf3e13bb5b08e734bb149b9ea75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357836"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio hemen güçlü bir JavaScript düzenleme deneyimi sağlar. TypeScript tabanlı bir dil hizmeti tarafından desteklenen Visual Studio, daha zengin IntelliSense, modern JavaScript özellikleri için destek ve Tanıma Git, yeniden düzenleme gibi gelişmiş üretkenlik özellikleri sunar.

> [!NOTE]
> 2017'Visual Studio başlayarak, JavaScript dil hizmeti dil hizmeti için yeni bir altyapı ("Salsa" olarak adlandırılır) kullanır. Ayrıntılar bu makalede yer almaktadır ve bu blog gönderisine de [bakabilirsiniz.](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/) Yeni düzenleme deneyimi çoğunlukla yeni Visual Studio Code. Daha fazla [VS Code için bkz.](https://code.visualstudio.com/docs/languages/javascript) VS Code belgeleri.

Uygulamanın genel IntelliSense işlevselliği hakkında daha fazla bilgi Visual Studio [bkz. IntelliSense kullanma.](../ide/using-intellisense.md)

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Visual Studio 2017'de JavaScript dil hizmet Visual Studio

2017'Visual Studio başlayarak, JavaScript IntelliSense parametre ve üye listeleri hakkında çok daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planlarda statik analiz kullanan TypeScript dil hizmeti tarafından sağlanır.

TypeScript, bu bilgileri oluşturmak için çeşitli kaynaklar kullanır:

- [Tür çıkarca göre IntelliSense](#TypeInference)
- [JSDoc tabanlı IntelliSense](#JsDoc)
- [TypeScript bildirim dosyalarını temel alan IntelliSense](#TsDeclFiles)
- [Tür tanımlarının otomatik olarak alınması](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>Tür çıkarca göre IntelliSense

JavaScript'te çoğu zaman açık tür bilgisi yoktur. Neyse ki, çevreleyen kod bağlamına göre bir tür bulmak genellikle oldukça kolaydır.
Bu işleme tür çıkarı denir.

Bir değişken veya özellik için, tür genellikle onu başlatmak için kullanılan değerin t dır veya en son değer ataması.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Bir işlev için dönüş türü, dönüş deyimlerinden ertelenmiş olabilir.

İşlev parametreleri için şu anda çıkarım yoktur, ancak JSDoc veya TypeScript *.d.ts* dosyalarını kullanarak bu soruna yönelik bir çalışma yapabilirsiniz (sonraki bölümlere bakın).

Ayrıca, aşağıdakiler için özel çıkarım vardır:

- Bir oluşturucu işlevi kullanılarak belirtilen "ES3 stili" sınıfları ve prototype özelliğine atamalar.
- Nesnede özellik atamaları olarak belirtilen CommonJS stili modül `exports` desenleri veya özelliğin `module.exports` atamaları.

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

Tür çıkarması istenen tür bilgilerini (veya belgeleri desteklemek için) sağlamazsa, tür bilgileri JSDoc ek açıklamaları aracılığıyla açıkça sağlanıyor olabilir.  Örneğin, kısmen bildirilen bir nesneye belirli bir tür vermek için aşağıda gösterildiği gibi `@type` etiketini kullanabilirsiniz:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Yukarıda belirtildiği gibi işlev parametreleri hiçbir zaman ertelenmez. Ancak JSDoc etiketini `@param` kullanarak işlev parametrelerine türler de ebilirsiniz.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Şu anda desteklenen JsDoc ek açıklamaları için bkz. [JavaScript'te JSDoc](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) desteği.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>TypeScript bildirim dosyalarını temel alan IntelliSense

JavaScript ve TypeScript artık aynı dil hizmetini temel alarak daha zengin bir şekilde etkileşim kurabilecek. Örneğin, Bir *.d.ts* dosyasında bildirilen değerler için JavaScript IntelliSense sağlanmalıdır [(bkz. TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)belgeleri) ve TypeScript'te bildirilen arabirimler ve sınıflar gibi türler JsDoc açıklamalarında tür olarak kullanılabilir.

Aşağıda, aynı projede yer alan bir JavaScript dosyasına (etiket kullanarak) bu tür bilgilerini (arabirim aracılığıyla) sağlayan bir TypeScript tanım dosyasının basit bir örneğini `JsDoc` gösteriyoruz.

![TypeScript tanım dosyası](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Tür tanımlarının otomatik olarak alınması

TypeScript dünyasında, en popüler JavaScript kitaplıklarının API'leri *.d.ts* dosyaları tarafından açıklanmıştır ve bu tür tanımlar için en yaygın depo [KesinlikleTyped üzerindedir.](https://github.com/DefinitelyTyped/DefinitelyTyped)

Varsayılan olarak, Salsa dil hizmeti hangi JavaScript kitaplıklarının kullanımda olduğunu algılamaya çalışır ve daha zengin IntelliSense sağlamak için kitaplığı açıklayan ilgili *.d.ts* dosyasını otomatik olarak indirip başvurur. Dosyalar % *LOCALAPPDATA%\Microsoft\TypeScript* konumundaki kullanıcı klasörü altında bulunan bir önbelleğe indirilir.

> [!NOTE]
> Yapılandırma dosyasında **bir yapılandırma** dosyası tsconfig.jsbu özellik varsayılan olarak devre dışı bırakılır, ancak aşağıda daha fazla özetlenen şekilde etkinleştirilebilir.

Şu anda otomatik algılama npm'den indirilen bağımlılıklar (dosyada *package.js* okuyarak), Bower (dosyada *bower.js* okuyarak) ve projenizin en popüler 400 JavaScript kitaplığının listesiyle eşan gevşek dosyalar için çalışır. Örneğin, *projenizejquery-1.10.min.js* daha iyi bir düzenleme deneyimi sağlamak için *jquery.d.ts* dosyası getirilsin ve yüklenir. Bu *.d.ts* dosyasının projeniz üzerinde hiçbir etkisi olmaz.

Otomatik alma özelliğini kullanmak için aşağıda özetlenen bir yapılandırma dosyası ekleyerek devre dışı indirebilirsiniz. Tanım dosyalarını doğrudan projenizin içine el ile kullanmak üzere yine de ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliSense'i kullanma](../ide/using-intellisense.md)
- [JavaScript desteği (Mac için Visual Studio)](/visualstudio/mac/javascript)
