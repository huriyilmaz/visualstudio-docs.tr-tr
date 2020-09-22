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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdb59c51fe38e3d2e3f2f1fd0b00db285b0de7f1
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739895"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017’de JavaScript

JavaScript, Visual Studio 'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türü ve hizmeti için JavaScript kodu yazabilirsiniz.

> [!NOTE]
> Microsoft 'un JavaScript API başvurusunu docs.microsoft.com adresinden MDN karşılıklarına yeniden yönlendirerek [MDN Web belgelerini](https://developer.mozilla.org/en-US/) Web 'in tek durağı olan bir geliştirme kaynağı haline getirme konusunda topluluk genelinde çaba harcadık. Ayrıntılar için bu [duyuruya](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)bakın.

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> ECMAScript 2015 (ES6) ve ötesi desteği

Visual Studio artık ECMAScript 2015/2016 gibi ECMAScript dil güncelleştirmelerine yönelik sözdizimini desteklemektedir.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015 nedir?

JavaScript hala bir programlama dili olarak gelişiyor ve [TC39](https://www.ecma-international.org/memento/tc39-m.htm) , güncelleştirme yapmaktan sorumlu bir komite.
ECMAScript 2015, JavaScript diline yönelik bir güncelleştirmedir ve yararlı yeni sözdizimi ve işlevselliği sunar. ES6 özellikleri hakkında ayrıntılı bilgi için [Bu](http://es6-features.org/#Constants) başvuru sitesine göz atın.

ECMAScript 2015 ' e yönelik desteğe ek olarak, Visual Studio ECMAScript 2016 ' yi de destekler ve kullanıma sunulduklarında ECMAScript 'in gelecek sürümleri için destek sağlar. TC39 ve ECMAScript 'teki en son değişikliklerle devam etmek için, [GitHub](https://github.com/tc39)'daki çalışmalarını izleyin.

### <a name="transpile-javascript"></a>Derleyin JavaScript

JavaScript 'le ilgili yaygın bir sorun, en son ES6 + dil özelliklerini kullanarak daha üretken olmanıza yardımcı olur, ancak çalışma zamanı ortamlarınız (genellikle tarayıcılar) bu yeni özellikleri henüz desteklemezler. Bu, hangi tarayıcıların hangi özellikleri desteklediğini (sıkıcı olabilecek) veya ES6 + kodunuzu hedef çalışma zamanlarının anlayacağı bir sürüme (genellikle ES5) dönüştürmek için bir yol olması gerektiği anlamına gelir. Kodunuzu çalışma zamanının anladığı sürüme dönüştürmek, genellikle "transpiling" olarak adlandırılır.

TypeScript 'in temel özelliklerinden biri, derleyin ES6 + Code to ES5 veya ES3 özelliğine sahiptir; böylece, en üretken olmanızı sağlayan kodu yazabilir, ancak yine de kodunuzun herhangi bir platformda çalıştırılmasını sağlayabilirsiniz. İçindeki JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] , TypeScript ile aynı dil hizmetini kullandığından, bu da ES6 + ' dan ES5 transpilation ' den faydalanabilir.

Transpilation önce ayarlanmadan önce, yapılandırma seçeneklerini anlamak gerekir.
TypeScript bir dosya aracılığıyla yapılandırılır `tsconfig.json` .
Böyle bir dosyanın yokluğunda, bazı varsayılan değerler kullanılır.
Uyumluluk nedenleriyle, Bu varsayılanlar yalnızca JavaScript dosyalarının (ve isteğe bağlı olarak) bulunduğu bağlamda farklıdır `.d.ts` .
JavaScript dosyalarını derlemek için bir `tsconfig.json` Dosya eklenmelidir ve bu seçeneklerden bazılarının açıkça ayarlanmış olması gerekir.

Tsconfig dosyası için gerekli ayarlar şunlardır:

- `allowJs`: Bu değerin, JavaScript dosyalarının tanınması için olarak ayarlanması gerekir `true` . Varsayılan değer `false` , TypeScript JavaScript 'e derlendiğinden ve derleyicinin henüz derlenmiş dosyaları içermemesi gerekir.
- `outDir`: Bu değer, yayımlanmış JavaScript dosyalarının algılanmadığı ve projeye dahil edilmesi için projeye dahil olmayan bir konuma ayarlanmalıdır (bkz `exclude` .).
- `module`: Modüller kullanılıyorsa, bu ayar derleyiciye, yayınlanan kodun hangi modül biçimini kullanması gerektiğini (örneğin `commonjs` , düğüm için veya Browserbelirt gibi paketleyiciler) söyler.
- `exclude`: Bu ayar, projeye hangi klasörlerin dahil edileceğini belirtir.
Çıkış konumunun yanı sıra veya gibi proje olmayan klasörler `node_modules` `temp` Bu ayara eklenmelidir.
- `enableAutoDiscovery`: Bu ayar, önceden özetlenen tanım dosyalarının otomatik olarak algılanmasını ve indirilmesini mümkün bir şekilde sunar.
- `compileOnSave`: Bu ayar, Visual Studio 'da kaynak dosyanın kaydedildiği her seferinde derlenmelidir derleyiciye bildirir.
- `typeAcquisition`: Bu ayarlar, otomatik tür alma davranışını denetler ( [Bu bölümde](../ide/javascript-intellisense.md#Auto)daha fazla açıklama)

JavaScript dosyalarını CommonJS modüllerine dönüştürmek ve bir klasöre yerleştirmek için `./out` aşağıdaki `tsconfig.json` dosyayı kullanabilirsiniz:

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

Ayarlar yerinde olduğunda, bir kaynak dosyası ( `./app.js` ) varsa ve birkaç ECMAScript 2015 Dil özelliği şu şekilde içeriyorsa:

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

Ardından `./out/app.js` , aşağıdaki gibi görünen ECMAScript 5 ' i (varsayılan) hedeflemek için bir dosya yayınlanır:

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

İçindeki JavaScript IntelliSense [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] , artık parametreler ve üye listeleri hakkında daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planda statik analiz kullanan TypeScript dil hizmeti tarafından sağlanır. Yeni IntelliSense deneyimi ve nasıl çalıştığı hakkında daha fazla bilgi [edinebilirsiniz.](../ide/javascript-intellisense.md)

## <a name="jsx-syntax-support"></a><a name="JSX"></a> JSX sözdizimi desteği

İçindeki JavaScript [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] , JSX sözdizimi için zengin desteğe sahiptir. JSX, JavaScript dosyaları içinde HTML etiketlerine izin veren bir sözdizimi kümesidir.

Aşağıdaki çizimde, TypeScript dosyasında tanımlanan bir yanıt verme bileşeni `comps.tsx` ve bundan sonra dosyadan kullanılan bu bileşen, `app.jsx` tamamlamalar için IntelliSense Ile ve JSX ifadeleri içindeki belgeler için tamamlandı.
Burada TypeScript 'e ihtiyacınız yoktur, bu özel örnek yalnızca bir TypeScript kodu içermesi için de olur.

![JSX sözdizimi](../javascript/media/js-react.png)

> [!NOTE]
> JSX sözdizimini yanıt verme çağrılarına dönüştürmek için, ayarın `"jsx": "react"` dosyasına eklenmesi gerekir `compilerOptions` `tsconfig.json` .

Derleme sonrasında './out/app.js ' konumunda oluşturulan JavaScript dosyası şu kodu içerir:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript projenizi yapılandırma

Dil hizmeti statik analizler tarafından desteklenir, bu da IntelliSense sonuçlarını döndürmek ve diğer özellikleri sağlamak amacıyla kaynak kodunuzu aslında çalıştırmadan analiz etmek zorunda kalmadan analiz eder.
Bu nedenle, proje bağlamınızın içerdiği dosyaların miktarı ve boyutu arttıkça, analiz sırasında daha fazla bellek ve CPU kullanılacaktır.
Bu nedenle, proje şekil'niz hakkında yapılan birkaç varsayılan varsayım vardır:

- `package.json` ve `bower.json` projeniz tarafından kullanılan liste bağımlılıkları ve varsayılan olarak otomatik tür alma (ata) içinde bulunur
- En üst düzey `node_modules` klasör, kitaplık kaynak kodunu içerir ve içeriği varsayılan olarak proje bağlamından çıkarılır
- Her `.js` biri, `.jsx` , `.ts` , ve `.tsx` dosya muhtemelen *kendi* kaynak dosyalarınıza ait ve proje bağlamına eklenmelidir

Çoğu durumda projenizi yalnızca açmanız ve varsayılan proje yapılandırmasını kullanarak harika deneyim sahibi olmanız mümkün olacaktır. Ancak, büyük veya farklı klasör yapılarına sahip olan projelerde, dil hizmetini yalnızca kendi kaynak dosyalarınıza daha iyi odaklanmak üzere daha fazla yapılandırmak istenebilir.

### <a name="override-defaults"></a>Geçersiz kılma Varsayılanları

Proje köküne bir dosya ekleyerek varsayılan yapılandırmayı geçersiz kılabilirsiniz `tsconfig.json` .
`tsconfig.json`, Proje bağlamını işleyebileceğiniz çeşitli farklı seçeneklere sahiptir.
Bunlardan bazıları aşağıda listelenmiştir, ancak kullanılabilir tüm seçeneklerin tam bir kümesi için [bkz. şema deposu](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Önemli `tsconfig.json` Seçenekler

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

- Projenin kaynak dosyaları `wwwroot/js`
- Projenin lib dosyaları `wwwroot/lib`
- `bootstrap`, `jquery` , `jquery-validation` , ve `jquery-validation-unobtrusive` içinde listelenmiştir `bower.json`
- `kendo-ui` el ile lib klasörüne eklendi

![Klasör yapısı](../javascript/media/js-folderstructure.png)

`tsconfig.json`Dil hizmetinin yalnızca klasördeki kaynak dosyalarınızı analiz ettiğinden emin olmak için aşağıdakileri kullanabilir `js` , ancak `.d.ts` klasördeki kitaplıklar için dosyaları getirir ve kullanır `lib` .

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

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Aşağıdaki projeler için JavaScript dil hizmeti 'nde sorun giderme devre dışı bırakıldı
Çok büyük miktarda içeriğe sahip bir JavaScript projesi açtığınızda, "JavaScript dil hizmeti şu projeler için devre dışı bırakıldı" iletisini okuyan bir ileti alabilirsiniz. Çok büyük bir JavaScript kaynağına sahip olmanın en yaygın nedeni, 20 MB 'lık bir proje sınırını aşan kaynak kodu olan kitaplıkların dahil olmasından kaynaklanır.

Projenizi en uygun hale getirmenin basit bir yolu, `tsconfig.json` dil hizmetinin hangi dosyaların yok sayılacak güvenli olduğunu bilmesini sağlamak için proje köküne bir dosya eklemektir. Kitaplıkların depolandığı en yaygın dizinleri dışlamak için aşağıdaki örneği kullanın:

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

Uygun gördüğünüz sürece daha fazla dizin ekleyin. Diğer bazı örnekler arasında "Vendor" veya "Wwwroot/lib" dizinleri bulunur.

> [!NOTE]
> Derleyici özelliği, `disableSizeLimit` 20 MB 'lık denetim sınırını devre dışı bırakmak için de kullanılabilir. Sınırın devre dışı bırakılması dil hizmetini kilitlemediğinden bu özelliği kullanırken özel önlemler alın.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015 ' den önemli değişiklikler

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]Tamamen yeni bir dil hizmeti özelliği olarak, önceki deneyimden farklı veya olmayan birkaç davranış vardır.
En önemli değişiklikler, VSDoc 'ın JSDoc ile değiştirilmesi, özel `.intellisense.js` uzantıların kaldırılması ve belirli kod desenleri için sınırlı IntelliSense ' in yerini alır.

### <a name="no-more-references-or-_referencesjs"></a>Daha fazla `///<references/>` veya `_references.js`

Daha önce, IntelliSense kapsamınızda hangi dosyaların olduğunu belirli bir anda anlamak oldukça karmaşıktır. Bazen tüm dosyalarınıza kapsam içinde ve diğer zamanlarda sahip olmak ve bu da el ile başvuru yönetimi içeren karmaşık yapılandırmalara yol açmasının istenmiş olması önerilir. Artık başvuru yönetimi hakkında düşünmenize gerek kalmaz, bu nedenle, Üçlü eğik çizgi başvuruları yorumlara veya dosyalara ihtiyacınız yoktur `_references.js` .

IntelliSense 'In nasıl çalıştığı hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](../ide/javascript-intellisense.md) sayfası.

### <a name="vsdoc"></a>VSDoc

Bazen VSDocs olarak adlandırılan XML belgesi Yorumları, daha önce IntelliSense sonuçlarını buatmak için kullanılacak ek verilerle kaynak kodunuzu süslemek için kullanılabilir.
VSDoc, yazma daha kolay olan [JSDoc](https://jsdoc.app/about-getting-started.html) için artık desteklenmiyor ve JavaScript için kabul edilen standart.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` uzantılardan

Daha önce, üçüncü taraf kitaplıklar için özel tamamlanma sonuçları eklemenize olanak tanıyan [IntelliSense uzantıları](../vs-2015/ide/extending-javascript-intellisense.md) yazabilirsiniz.
Bu uzantıların yazma ve yükleme ve bunlara başvurulması oldukça zordur, bu nedenle yeni dil hizmetinin iletilmesi bu dosyaları desteklemez.
Daha kolay bir alternatif olarak, eski uzantılarla aynı IntelliSense avantajlarını sağlamak için bir TypeScript tanım dosyası yazabilirsiniz `.intellisense.js` .
Burada bildirim ( `.d.ts` ) dosyası yazma hakkında daha fazla bilgi [here](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)edinebilirsiniz.

### <a name="unsupported-patterns"></a>Desteklenmeyen desenler

Yeni dil hizmeti bir yürütme altyapısı yerine statik analizler tarafından desteklenmediğinden (farklar hakkında bilgi edinmek için [Bu sorunu](https://github.com/Microsoft/TypeScript/issues/4789) okuyun), artık algılanamayan birkaç JavaScript deseni vardır.
En yaygın olarak kullanılan desenler "daha fazla" modeldir.
Şu anda dil hizmeti, bildirimde daha sonra bulunan özelliklere sahip nesneler üzerinde IntelliSense sağlayamaz.
Örneğin:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Nesne oluşturma sırasında özellikleri bildirerek bunu çözebilirsiniz:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Ayrıca, aşağıdaki gibi bir JSDoc açıklaması ekleyebilirsiniz:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```