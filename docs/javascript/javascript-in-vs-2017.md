---
title: JavaScript
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: jillfra
ms.openlocfilehash: 2a0d3657843dcf282e5c9aab8609efe5f9611965
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234962"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017’de JavaScript

JavaScript Visual Studio'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türü ve hizmeti için JavaScript kodu yazabilirsiniz.

> [!NOTE]
> Microsoft'un JavaScript API referansının tüm (500' den fazla sayfasını) docs.microsoft.com'dan MDN'deki benzerlerine [yönlendirerek, MDN web dokümanlarını](https://developer.mozilla.org/en-US/) web dokümanlarını web'in tek noktadan, prömiyer geliştirme kaynağı haline getirmek için topluluk çapındaki çabalara katıldık. Ayrıntılar için bu [duyuruya](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)bakın.

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a>ECMAScript 2015 (ES6) ve sonrası için destek

Visual Studio artık ECMAScript 2015/2016 gibi ECMAScript dil güncelleştirmeleri için sözdizimini destekler.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015 nedir?

JavaScript hala bir programlama dili olarak gelişmektedir ve [TC39](https://www.ecma-international.org/memento/tc39-m.htm) komite güncellemeleri yapmak için sorumludur.
ECMAScript 2015, JavaScript dilinde yararlı yeni sözdizimi ve işlevsellik getiren bir güncelleştirmedir. ES6 özellikleri hakkında derin bir dalış için [bu](http://es6-features.org/#Constants) referans sitesine göz atın.

VISUAL Studio, ECMAScript 2015 desteğine ek olarak ECMAScript 2016'yı da destekler ve piyasaya sürülerken ECMAScript'in gelecekteki sürümleri için destek sahibi olur. TC39 ve ECMAScript en son değişiklikleri takip etmek için, [github](https://github.com/tc39)üzerindeki çalışmalarını izleyin.

### <a name="transpile-javascript"></a>Transpile JavaScript

JavaScript ile ilgili yaygın bir sorun, daha üretken olmanıza yardımcı olduğu için en son ES6+ dil özelliklerini kullanmak istemenizdir, ancak çalışma zamanı ortamlarınız (genellikle tarayıcılar) henüz bu yeni özellikleri desteklemez. Bu, hangi tarayıcıların hangi özellikleri desteklediğini (sıkıcı olabilir) izlemeniz gerektiği veya ES6+ kodunuzu hedef çalışma sürenizin anladığı bir sürüme (genellikle ES5) dönüştürmenin bir yolunu bulmanız gerektiği anlamına gelir. Kodunuzu çalışma zamanının anladığı bir sürüme dönüştürmek genellikle "aktarma" olarak adlandırılır.

TypeScript'in temel özelliklerinden biri ES6+ kodunu ES5 veya ES3'e aktarabilmenizdir, böylece sizi en üretken kılan kodu yazabilirsiniz, ancak yine de kodunuzu herhangi bir platformda çalıştırabilirsiniz. JavaScript'teki [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] JavaScript, TypeScript ile aynı dil hizmetini kullandığından, ES6+'dan ES5'e aktarma dan da yararlanabilir.

Transpilasyon ayarlanamadan önce yapılandırma seçeneklerinin anlaşılması gerekir.
TypeScript bir `tsconfig.json` dosya üzerinden yapılandırılır.
Böyle bir dosyanın yokluğunda, bazı varsayılan değerler kullanılır.
Uyumluluk nedenleriyle, bu varsayılanlar yalnızca JavaScript dosyalarının (ve `.d.ts` isteğe bağlı dosyaların) bulunduğu bir bağlamda farklıdır.
JavaScript dosyalarını derlemek `tsconfig.json` için bir dosya eklenmelidir ve bu seçeneklerden bazıları açıkça ayarlanmalıdır.

Tsconfig dosyası için gerekli ayarlar aşağıdaki gibidir:

- `allowJs`: JavaScript dosyalarının `true` tanınması için bu değer ayarlanmalıdır. Varsayılan `false`değer, TypeScript JavaScript'e derlediği ve derleyicinin yeni derlediği dosyaları içermemesi gerektiği için dir.
- `outDir`: Yayılan JavaScript dosyalarının algılanmaması ve projeye dahil edilebilmesi için bu değer projeye dahil olmayan bir `exclude`konuma ayarlanmalıdır (bkz.
- `module`: Modülkullanıyorsanız, bu ayar derleyiciye yayılan kodun hangi modülü kullanması `commonjs` gerektiğini söyler (örneğin Düğüm veya Browserify gibi paketleyiciler).
- `exclude`: Bu ayar, hangi klasörlerin projeye dahil edilmeyeceklerini belirtir.
Çıktı konumu ve proje dışı klasörler gibi `node_modules` `temp`bu ayara eklenmelidir.
- `enableAutoDiscovery`: Bu ayar, tanım dosyalarının daha önce açıklandığı gibi otomatik olarak algılanmasını ve indirilmesini sağlar.
- `compileOnSave`: Bu ayar derleyiciye visual studio'da bir kaynak dosya kaydedilen herhangi bir zaman yeniden derlemesi gerektirebilip derlemesi gerektiğini söyler.
- `typeAcquisition`: Bu ayar kümesi otomatik tür edinimdavranışını kontrol eder [(bu bölümde](/visualstudio/ide/javascript-intellisense#Auto)daha fazla açıklayınız)

JavaScript dosyalarını CommonJS modüllerine dönüştürmek ve bunları `./out` bir klasöre yerleştirmek `tsconfig.json` için aşağıdaki dosyayı kullanabilirsiniz:

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

Bir kaynak dosya varsa ve aşağıdaki`./app.js`gibi birkaç ECMAScript 2015 dil özellikleri içeriyorsa, ayarları yerinde, eğer:

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

Daha sonra bir dosya aşağıdaki `./out/app.js` gibi bir şey görünüyor ECMAScript 5 (varsayılan) hedefleme için yayılan olacaktır:

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

## <a name="better-intellisense"></a>Daha İyi IntelliSense

JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] şimdi parametreleri ve üye listeleri hakkında çok daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planda statik çözümleme kullanan TypeScript dil hizmeti tarafından sağlanır. Yeni IntelliSense deneyimi ve [burada](/visualstudio/ide/javascript-intellisense/)nasıl çalıştığı hakkında daha fazla bilgi edinebilirsiniz.

## <a name="jsx-syntax-support"></a><a name="JSX"></a>JSX sözdizimi desteği

JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] içinde JSX sözdizimi için zengin bir destek vardır. JSX, JavaScript dosyalarında HTML etiketleri sağlayan bir sözdizimi kümesidir.

Aşağıdaki resimde `comps.tsx` TypeScript dosyasında tanımlanan bir React bileşeni ve daha `app.jsx` sonra bu bileşen, JSX ifadeleri içindeki tamamlamalar ve belgeler için IntelliSense ile birlikte dosyadan kullanılmakta olan bir Tepki bileşenini göstermektedir.
Burada TypeScript gerekmez, bu özel örnek sadece bazı TypeScript kodu da içeren olur.

![JSX sözdizimi](../javascript/media/js-react.png)

> [!NOTE]
> JSX sözdizimini Çağrıları Tepkile'ye `"jsx": "react"` dönüştürmek `tsconfig.json` için, `compilerOptions` ayarın dosyaya eklenmesi gerekir.

'./out/app.js' adresinde oluşturulan JavaScript dosyası, kodu içerir:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript projenizi yapılandırın

Dil hizmeti statik analizle desteklenmektedir, bu da IntelliSense sonuçlarını döndürmek ve diğer düzenleme özellikleri sağlamak için kaynak kodunuzu gerçekten yürütmeden analiz ettiği anlamına gelir.
Bu nedenle, proje bağlamınızda yer alan dosyaların miktarı ve boyutu ne kadar büyükse, çözümleme sırasında o kadar çok bellek ve CPU kullanılır.
Bu nedenle, proje şekliniz hakkında yapılan birkaç varsayılan varsayım vardır:

- `package.json`ve `bower.json` projeniz tarafından kullanılan ve varsayılan olarak otomatik tür edinme (ATA) dahil edilen bağımlılıkları listele
- Üst düzey `node_modules` bir klasör kitaplık kaynak kodu içerir ve içeriği varsayılan olarak proje bağlamından çıkarılır
- Her `.js`biri `.jsx` `.ts`, `.tsx` , , ve dosya muhtemelen kendi kaynak *dosyalarından* biridir ve proje bağlamında dahil edilmelidir

Çoğu durumda, projenizi açabilir ve varsayılan proje yapılandırmasını kullanarak harika bir deneyime sahip olabilirsiniz. Ancak, büyük veya farklı klasör yapıları olan projelerde, dil hizmetini yalnızca kendi kaynak dosyalarınıza daha iyi odaklanmak için daha fazla yapılandırmak istenebilir.

### <a name="override-defaults"></a>Varsayılanları geçersiz kılma

Proje kökünüze bir `tsconfig.json` dosya ekleyerek varsayılan yapılandırmayı geçersiz kılabilirsiniz.
A'nın `tsconfig.json` proje bağlamınızı işleyebilir birkaç farklı seçeneği vardır.
Bunlardan birkaçı aşağıda listelenmiştir, ancak mevcut tüm seçeneklerin tam seti için [şema deposuna bakın.](http://json.schemastore.org/tsconfig)

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

Aşağıdaki kurulum ile bir proje verilmiştir:

- projenin kaynak dosyaları`wwwroot/js`
- projenin lib dosyaları bulunmaktadır`wwwroot/lib`
- `bootstrap`, `jquery` `jquery-validation`, `jquery-validation-unobtrusive` , ve listelenen`bower.json`
- `kendo-ui`lib klasörüne el ile eklendi

![Klasör yapısı](../javascript/media/js-folderstructure.png)

Dil hizmetinin `tsconfig.json` yalnızca `js` klasördeki kaynak dosyalarınızı çözümlediğinden, ancak yine de klasörünüzdeki `.d.ts` `lib` kitaplıklar için dosyaları aldığından ve kullandığından emin olmak için aşağıdakileri kullanabilirsiniz.

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Sorun giderme JavaScript dil hizmeti aşağıdaki proje(ler) için devre dışı bırakıldı
Çok büyük miktarda içeriğe sahip bir JavaScript projesini açtığınızda, "JavaScript dil hizmeti aşağıdaki proje(ler)" için devre dışı bırakıldı" yazan bir ileti alabilirsiniz. JavaScript kaynağı çok büyük miktarda sahip olmanın en yaygın nedeni 20MB proje sınırını aşan kaynak kodu ile kütüphaneler dahil kaynak nedeniyle.

Projenizi en iyi duruma getirmenin `tsconfig.json` basit bir yolu, dil hizmetinin hangi dosyaların yoksayılabildiğini bilmesini sağlamak için proje kökünüze bir dosya eklemektir. Kitaplıkların depolandığı en yaygın dizinleri hariç tutmak için aşağıdaki örneği kullanın:

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

Uygun gördüğünüz gibi daha fazla dizin ekleyin. Diğer bazı örnekler arasında "satıcı" veya "wwwroot/lib" dizinleri sayılabilir.

> [!NOTE]
> Derleyici özelliği, `disableSizeLimit` 20MB onay sınırını devre dışı kullanabilirsiniz. Sınırı devre dışı bırakmak dil hizmetini çökebileceğinden, bu özelliği kullanırken özel önlemler alın.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015'ten Önemli Değişiklikler

Tamamen [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] yeni bir dil hizmeti özellikleri olarak, farklı veya önceki deneyimden yok olacak birkaç davranış vardır.
En önemli değişiklikler, VSDoc'un JSDoc ile değiştirilmesi, özel `.intellisense.js` uzantıların kaldırılması ve belirli kod desenleri için sınırlı IntelliSense'dir.

### <a name="no-more-references-or-_referencesjs"></a>Daha `///<references/>` fazla veya`_references.js`

Daha önce hangi dosyaların IntelliSense kapsamı içinde olduğunu herhangi bir anda anlamak oldukça karmaşıktı. Bazen tüm dosyalarınızın kapsam içinde olması istenirve diğer zamanlarda değildi ve bu da el ile başvuru yönetimini içeren karmaşık yapılandırmalara yol açmıştır. İleriye dönük olarak artık referans yönetimi hakkında düşünmeniz gerekmez ve böylece `_references.js` üçlü eğik çizgi referansları yorum veya dosyalargerekmez.

IntelliSense'in nasıl çalıştığı hakkında daha fazla bilgi için [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) sayfasına bakın.

### <a name="vsdoc"></a>VSDoc

Bazen VSDocs olarak da adlandırılan XML dokümantasyon yorumları, kaynak kodunuzu IntelliSense sonuçlarını yükseltmek için kullanılacak ek verilerle süslemek için daha önce kullanılabilir.
VSDoc artık yazmak daha kolay ve JavaScript için kabul edilen standart [JSDoc](https://jsdoc.app/about-getting-started.html) lehine desteklenir.

### <a name="intellisensejs-extensions"></a>`.intellisense.js`Uzantı -ları

Daha önce, üçüncü taraf kitaplıklar için özel tamamlama sonuçları eklemenize olanak tanıyan [IntelliSense uzantıları](https://msdn.microsoft.com/library/hh874692.aspx) nı yazabilirsiniz.
Bu uzantıları yazmak ve yüklemek ve onları başvurmak oldukça zordu hantal, bu yüzden ileriye doğru yeni dil hizmeti bu dosyaları desteklemez.
Daha kolay bir alternatif olarak, eski `.intellisense.js` uzantılarla aynı IntelliSense avantajlarını sağlamak için bir TypeScript tanım dosyası yazabilirsiniz.
Burada beyanname (`.d.ts`) dosya yazma [here](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)hakkında daha fazla bilgi edinebilirsiniz.

### <a name="unsupported-patterns"></a>Desteklenmeyen desenler

Yeni dil hizmeti yürütme altyapısı yerine statik çözümle güçlendirilmeolduğundan (farklar hakkında bilgi için [bu sorunu](https://github.com/Microsoft/TypeScript/issues/4789) okuyun), artık algılanamayacak birkaç JavaScript deleği vardır.
En yaygın desen "expando" desenidir.
Şu anda dil hizmeti, bildirimden sonra yapıştırılmış özelliklere sahip nesneler üzerinde IntelliSense sağlayamaz.
Örnek:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Nesne oluşturma sırasında özellikleri beyan ederek bu etrafında alabilirsiniz:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

JSDoc yorumunu aşağıdaki gibi de ekleyebilirsiniz:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
