---
title: JavaScript
description: IDE'de JavaScript kodu yazmak için standart düzenleme yardımlarının (kod parçacıkları, IntelliSense gibi) çoğunu veya hepsini kullanabileceğinizi Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 79c7c13ea80e32e80d32c04052269cb814072aeb
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232914"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017’de JavaScript

JavaScript, Visual Studio. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türü ve hizmeti için JavaScript kodu yazabilirsiniz.

> [!NOTE]
> Microsoft'un JavaScript docs.microsoft.com API başvurusu olan tüm (500'den fazla sayfa) [MDN web](https://developer.mozilla.org/en-US/) belgelerini MDN web belgelerinden MDN'lerine ve MDN'lerine yönlendirerek topluluk genelindeki çabalara katıldık. Ayrıntılar için bu duyuruya [bakın.](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> ECMAScript 2015 (ES6) ve ötesinde destek

Visual Studio artık ECMAScript 2015/2016 gibi ECMAScript dil güncelleştirmeleri için söz dizimi desteği de sağlar.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015 nedir?

JavaScript hala bir programlama dili olarak gelişmektedir ve [güncelleştirmelerden TC39](https://www.ecma-international.org/memento/tc39-m.htm) sorumlu komitesidir.
ECMAScript 2015, Yararlı yeni söz dizimi ve işlevsellik getiren bir JavaScript dili güncelleştirmesidir. ES6 özelliklerine derinlemesine bir göz at için bu [başvuru sitesine](http://es6-features.org/#Constants) göz atabilirsiniz.

VISUAL STUDIO, ECMAScript 2015 desteğine ek olarak ECMAScript 2016'yı da destekler ve yayınlandırıldıklarında ECMAScript'in gelecek sürümleri için de destek içerir. TC39'a ve ECMAScript'te yapılan en son değişikliklere devam etmek için, [GitHub.](https://github.com/tc39)

### <a name="transpile-javascript"></a>Transpile JavaScript

JavaScript ile ilgili yaygın bir sorun, en son ES6+ dil özelliklerini kullanmak istemenizdir çünkü bunlar daha üretken çalışmanıza yardımcı olur, ancak çalışma zamanı ortamlarınızı (genellikle tarayıcılar) henüz bu yeni özellikleri desteklemez. Bu, hangi tarayıcıların hangi özellikleri (sıkıcı olabilir) desteklemektedir veya ES6+ kodunuzu hedef çalışma zamanlarınızı anlayacaktır (genellikle ES5) bir sürüme dönüştürmek için bir yol gerekir. Kodunuzu çalışma zamanının an anlayacağı bir sürüme dönüştürmek genellikle "dönüştürme" olarak adlandırılır.

TypeScript'in önemli özelliklerinden biri, ES6+ kodunu ES5 veya ES3'e çevirip en üretken hale getirirken kodunuzu herhangi bir platformda çalıştırmaya devam etmektir. içinde JavaScript, TypeScript ile aynı dil hizmetini kullandığı [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] için, ES6+ ile ES5 arasında geçişe kadar da faydalanabilirsiniz.

Geçişin ayarlanmadan önce yapılandırma seçeneklerinin anlaşılması gerekir.
TypeScript bir dosya aracılığıyla `tsconfig.json` yapılandırılır.
Böyle bir dosyanın olmaması, bazı varsayılan değerler kullanılır.
Uyumluluk nedeniyle, bu varsayılanlar yalnızca JavaScript dosyalarının (ve isteğe bağlı olarak dosyaların) bulunduğu `.d.ts` bir bağlamda farklıdır.
JavaScript dosyalarını derlemek `tsconfig.json` için bir dosya eklenmeli ve bu seçeneklerden bazıları açıkça ayar gerektir.

tsconfig dosyası için gerekli ayarlar aşağıdaki gibidir:

- `allowJs`: JavaScript dosyalarının `true` tanınması için bu değerin olarak ayarlanmış olması gerekir. TypeScript JavaScript'e derleyene ve derleyici az önce derlenmiş dosyaları içermesi gerekmay olduğundan varsayılan `false` değer değeridir.
- `outDir`: Bu değer, yayılan JavaScript dosyalarının algılanmayacak ve sonra projeye dahil edilmayacak şekilde projeye dahil edilmayacak bir konuma ayarlandırılması gerekir (bkz. `exclude` ).
- `module`: Modül kullanıyorsanız, bu ayar derleyiciye, yayılan kodun hangi modül biçimini (node veya Browserify gibi paketleyiciler) `commonjs` kullanması gerektiğini söyler.
- `exclude`: Bu ayar hangi klasörlerin projeye dahil olmadığını ifade ediyor.
Çıkış konumu ve veya gibi proje dışı klasörler `node_modules` `temp` bu ayara eklenmiştir.
- `enableAutoDiscovery`: Bu ayar, önceden özetlenen tanım dosyalarının otomatik olarak algılanmasına ve indir indirebilirsiniz.
- `compileOnSave`: Bu ayar, bir kaynak dosya her kaydedilse yeniden derlemesi gerektirse de derleyiciye Visual Studio.
- `typeAcquisition`: Bu ayar kümesi, otomatik tür alımının davranışını denetleme (bu bölümde daha [fazla açıklayacak)](../ide/javascript-intellisense.md#Auto)

JavaScript dosyalarını CommonJS modüllerine dönüştürmek ve bir klasöre `./out` yer etmek için aşağıdaki dosyayı `tsconfig.json` kullanabilirsiniz:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Ayarlar mevcutken, bir kaynak dosya ( ) varsa ve aşağıdaki gibi birkaç `./app.js` ECMAScript 2015 dil özelliği içeriyorsa:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Ardından, aşağıdakine benzer bir şekilde `./out/app.js` görünen ECMAScript 5'i (varsayılan) hedeflemek için bir dosya yayımlar:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Daha iyi IntelliSense

içinde JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] artık parametreler ve üye listeleri hakkında çok daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planlarda statik analiz kullanan TypeScript dil hizmeti tarafından sağlanır. Yeni IntelliSense deneyimi ve nasıl çalıştığını burada [okuyabilirsiniz.](../ide/javascript-intellisense.md)

## <a name="jsx-syntax-support"></a><a name="JSX"></a> JSX söz dizimi desteği

içinde [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] JavaScript, JSX söz dizimi için zengin destek içerir. JSX, JavaScript dosyalarında HTML etiketlerine izin veren bir söz dizimi kümesidir.

Aşağıdaki çizimde, TypeScript React tanımlanan bir bileşen ve ardından dosyadan kullanılan bu bileşen, JSX ifadeleri içindeki tamamlamalar ve belgeler için `comps.tsx` `app.jsx` IntelliSense ile tamamlanmıştır.
Burada TypeScript'e ihtiyacınız yok, bu özel örnekte yalnızca bazı TypeScript kodu da vardır.

![JSX söz dizimi](../javascript/media/js-react.png)

> [!NOTE]
> JSX söz dizimlerini çağrılara React için, `"jsx": "react"` ayar dosyasında `compilerOptions` dosyasına `tsconfig.json` eklenmiştir.

Derleme sırasında './out/app.js' üzerinde oluşturulan JavaScript dosyası şu kodu içerebilir:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript projenizi yapılandırma

Dil hizmeti statik analizle güçlendirilmiştir. Başka bir ifadeyle IntelliSense sonuçları almak ve diğer düzenleme özelliklerini sağlamak için kaynak kodunuzu gerçekten yürütmeden analiz eder.
Bu nedenle, proje bağlamınıza dahil edilen dosyaların miktarı ve boyutu ne kadar büyükse analiz sırasında o kadar fazla bellek ve CPU kullanılır.
Bu nedenle, proje şekliniz hakkında yapılan birkaç varsayılan varsayım vardır:

- `package.json` ve `bower.json` projeniz tarafından kullanılan ve varsayılan olarak otomatik tür alımına (ATA) dahil edilen bağımlılıkları listele
- En üst düzey `node_modules` klasör kitaplık kaynak kodunu içerir ve içeriği varsayılan olarak proje bağlamının dışındadır
- Diğer `.js` tüm `.jsx` , , ve dosyaları muhtemelen kendi kaynak `.ts` `.tsx` *dosyalarındandır* ve proje bağlamına dahil edilecektir

Çoğu durumda, yalnızca projenizi açabilir ve varsayılan proje yapılandırmasını kullanarak harika bir deneyim yaşamanız mümkün olur. Ancak, büyük veya farklı klasör yapıları olan projelerde, dil hizmetini yalnızca kendi kaynak dosyalarınıza daha iyi odaklanacak şekilde daha fazla yapılandırmanız istenebilir.

### <a name="override-defaults"></a>Varsayılanları geçersiz kıl

Proje kökünü bir dosya ekleyerek varsayılan `tsconfig.json` yapılandırmayı geçersiz kılabilirsiniz.
, `tsconfig.json` proje bağlamınızı değiştiren birkaç farklı seçenek içerir.
Bunların birkaçı aşağıda listelenmiştir, ancak tüm seçeneklerin tam kümesi için şema [deposuna bakın.](http://json.schemastore.org/tsconfig)

## <a name="important-tsconfigjson-options"></a>Önemli `tsconfig.json` seçenekler

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Örnek proje yapılandırması

Aşağıdaki kuruluma sahip bir proje verildi:

- projenin kaynak dosyaları `wwwroot/js`
- projenin lib dosyaları `wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation` , ve `jquery-validation-unobtrusive``bower.json`
- `kendo-ui` lib klasörüne el ile eklendi

![Klasör yapısı](../javascript/media/js-folderstructure.png)

Dil hizmetinin yalnızca klasördeki kaynak dosyalarınızı analiz etmelerine rağmen klasördeki kitaplıklar için dosyaları alıp kullandığından emin olmak için `tsconfig.json` `js` `.d.ts` aşağıdakini `lib` kullanabilirsiniz.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Sorun Giderme JavaScript dil hizmeti aşağıdaki projelerinde devre dışı bırakıldı
Çok büyük miktarda içeriğe sahip bir JavaScript projesini açtınız, "JavaScript dil hizmeti aşağıdaki projelerde devre dışı bırakıldı" iletisini alabilirsiniz. Çok büyük miktarda JavaScript kaynağına sahip olmak için en yaygın neden, 20 MB proje sınırını aşan kaynak koduna sahip kitaplıkların dahil olmasıdır.

Projenizi iyileştirmenin basit bir yolu, dil hizmetine hangi dosyaların yoksaymak güvenli olduğunu haber sağlamak için proje kök `tsconfig.json` dosyanıza bir dosya eklemektir. Kitaplıkların depolandığı en yaygın dizinleri dışlamak için aşağıdaki örneği kullanın:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Uygun gördüğünüz şekilde daha fazla dizin ekleyin. Diğer örneklerden bazıları "vendor" veya "wwwroot/lib" dizinleridir.

> [!NOTE]
> Derleyici özelliği, `disableSizeLimit` 20 MB denetim sınırını devre dışı bırakmak için de kullanılabilir. Sınırın devre dışı bırakılması dil hizmetinin kilitlenmesine neden olabileceği için bu özelliği kullanırken özel önlemler alın.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015'te Önemli Değişiklikler

Tamamen [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] yeni bir dil hizmeti sunarken, önceki deneyimden farklı veya eksik olacak birkaç davranış vardır.
En önemli değişiklikler VSDoc'nin JSDoc ile değiştirilmesi, özel uzantıların kaldırılması ve belirli kod desenleri için `.intellisense.js` sınırlı IntelliSense'tir.

### <a name="no-more-references-or-_referencesjs"></a>Artık yok `///<references/>` veya `_references.js`

Daha önce, IntelliSense kapsamındaki dosyaların hangi anda olduğunu anlamak oldukça karmaşıktı. Bazı durumlarda tüm dosyalarınızın kapsamda ve diğer zamanlarda olması tercih edilirdi ve bu da el ile başvuru yönetimi içeren karmaşık yapılandırmalara yol açtı. Bundan sonra artık başvuru yönetimini düşünmezsiniz ve bu nedenle üç eğik çizgi başvuru açıklamasına veya dosyalarına ihtiyacınız `_references.js` yoktur.

[IntelliSense'in nasıl çalıştığını görmek için JavaScript IntelliSense](../ide/javascript-intellisense.md) sayfasına bakın.

### <a name="vsdoc"></a>VSDoc

Bazen VSDocs olarak da adlandırılan XML belge yorumları, daha önce kaynak kodunuzu IntelliSense sonuçlarının havalarını almak için kullanılacak ek verilerle dekore etmek için kullanılabilirdi.
VSDoc artık [JSDoc'nin](https://jsdoc.app/about-getting-started.html) kullanımı kolay ve JavaScript için kabul edilen standart olan JSDoc desteğine sahip değil.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` Uzantı -ları

Daha önce, üçüncü taraf kitaplıklar için özel tamamlama sonuçları eklemenize olanak sağlayan [IntelliSense](/previous-versions/visualstudio/visual-studio-2015/ide/extending-javascript-intellisense) uzantıları yazardınız.
Bu uzantıları yazmak ve yüklemek ve bunlara başvurmak oldukça zordur, bu nedenle bundan sonra yeni dil hizmeti bu dosyaları desteklemez.
Daha kolay bir alternatif olarak, eski uzantılar ile aynı IntelliSense avantajlarını sağlamak için bir TypeScript tanım `.intellisense.js` dosyası yazabilirsiniz.
Bildirim ( ) dosyası yazma hakkında `.d.ts` daha fazla bilgi için buraya [bakabilirsiniz.](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)

### <a name="unsupported-patterns"></a>Desteklenmeyen desenler

Yeni dil hizmeti bir yürütme altyapısı yerine statik analizle destekleneneden (farklar hakkında bilgi için bu sorunu okuyun), artık algılanamadı birkaç JavaScript deseni vardır. [](https://github.com/Microsoft/TypeScript/issues/4789)
En yaygın desen "expando" desenidir.
Şu anda dil hizmeti, bildirimden sonra üzerine ekli özelliklere sahip nesneler üzerinde IntelliSense sağamaz.
Örnek:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Nesne oluşturma sırasında özellikleri bildirerek bu durumla ilgili bir şeyler elde edersiniz:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Ayrıca aşağıdaki gibi bir JSDoc açıklaması da ebilirsiniz:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
