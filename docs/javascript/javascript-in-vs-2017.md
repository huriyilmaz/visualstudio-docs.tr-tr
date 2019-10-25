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
monikerRange: vs-2017
ms.openlocfilehash: 653b2576b0076d02f2e18cedc6f9f9890fd98fe5
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888655"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017’de JavaScript

JavaScript, Visual Studio 'da birinci sınıf bir dildir. Visual Studio IDE'de JavaScript kodu yazarken standart düzenleme yardımlarının (kod parçacıkları, IntelliSense, vb.) çoğunu veya tümünü kullanabilirsiniz. Birçok uygulama türü ve hizmeti için JavaScript kodu yazabilirsiniz.

> [!NOTE]
> Microsoft 'un JavaScript API başvurusunu docs.microsoft.com adresinden MDN karşılıklarına yeniden yönlendirerek [MDN Web belgelerini](https://developer.mozilla.org/en-US/) Web 'in tek durağı olan bir geliştirme kaynağı haline getirme konusunda topluluk genelinde çaba harcadık. Ayrıntılar için bu [duyuruya](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)bakın.

## <a name="ES6"></a>ECMAScript 2015 (ES6) ve ötesi desteği

Visual Studio artık ECMAScript 2015/2016 gibi ECMAScript dil güncelleştirmelerine yönelik sözdizimini desteklemektedir.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015 nedir?

JavaScript hala bir programlama dili olarak gelişiyor ve [TC39](https://www.ecma-international.org/memento/tc39-m.htm) , güncelleştirme yapmaktan sorumlu bir komite.
ECMAScript 2015, JavaScript diline yönelik bir güncelleştirmedir ve yararlı yeni sözdizimi ve işlevselliği sunar. ES6 özellikleri hakkında ayrıntılı bilgi için [Bu](http://es6-features.org/#Constants) başvuru sitesine göz atın.

ECMAScript 2015 ' e yönelik desteğe ek olarak, Visual Studio ECMAScript 2016 ' yi de destekler ve kullanıma sunulduklarında ECMAScript 'in gelecek sürümleri için destek sağlar. TC39 ve ECMAScript 'teki en son değişikliklerle devam etmek için, [GitHub](https://github.com/tc39)'daki çalışmalarını izleyin.

### <a name="transpile-javascript"></a>Derleyin JavaScript

JavaScript 'le ilgili yaygın bir sorun, en son ES6 + dil özelliklerini kullanarak daha üretken olmanıza yardımcı olur, ancak çalışma zamanı ortamlarınız (genellikle tarayıcılar) bu yeni özellikleri henüz desteklemezler. Bu, hangi tarayıcıların hangi özellikleri desteklediğini (sıkıcı olabilecek) veya ES6 + kodunuzu hedef çalışma zamanlarının anlayacağı bir sürüme (genellikle ES5) dönüştürmek için bir yol olması gerektiği anlamına gelir. Kodunuzu çalışma zamanının anladığı sürüme dönüştürmek, genellikle "transpiling" olarak adlandırılır.

TypeScript 'in temel özelliklerinden biri, derleyin ES6 + Code to ES5 veya ES3 özelliğine sahiptir; böylece, en üretken olmanızı sağlayan kodu yazabilir, ancak yine de kodunuzun herhangi bir platformda çalıştırılmasını sağlayabilirsiniz. [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] içindeki JavaScript, TypeScript ile aynı dil hizmetini kullandığından, ES6 + ile ES5 transpilation avantajlarından de yararlanabilir.

Transpilation önce ayarlanmadan önce, yapılandırma seçeneklerini anlamak gerekir.
TypeScript bir `tsconfig.json` dosyası aracılığıyla yapılandırılır.
Böyle bir dosyanın yokluğunda, bazı varsayılan değerler kullanılır.
Uyumluluk nedenleriyle, Bu varsayılanlar yalnızca JavaScript dosyalarının (ve isteğe bağlı olarak `.d.ts` dosyalarının) bulunduğu bağlamda farklıdır.
JavaScript dosyalarını derlemek için bir `tsconfig.json` dosyası eklenmelidir ve bu seçeneklerden bazılarının açıkça ayarlanmış olması gerekir.

Tsconfig dosyası için gerekli ayarlar şunlardır:

- `allowJs`: Bu değerin, JavaScript dosyalarının tanınması için `true` olarak ayarlanması gerekir. Varsayılan değer `false`, çünkü TypeScript JavaScript 'e derlenir ve derleyici henüz derlenen dosyaları içermemelidir.
- `outDir`: Bu değer, yayımlanmış JavaScript dosyalarının algılanmadığı ve projeye dahil edilmesi için projeye dahil olmayan bir konuma ayarlanmalıdır (bkz. `exclude`).
- `module`: modüller kullanılıyorsa, bu ayar derleyiciye, yayınlanan kodun hangi modül biçimini kullanması gerektiğini bildirir (örneğin, düğüm için `commonjs` veya Browserbelirt gibi paketleyiciler).
- `exclude`: Bu ayar, projeye hangi klasörlerin dahil edileceğini belirtir.
Çıkış konumunun yanı sıra `node_modules` veya `temp`gibi proje olmayan klasörler bu ayara eklenmelidir.
- `enableAutoDiscovery`: Bu ayar, tanım dosyalarının daha önce özetlenen otomatik olarak algılanmasını ve indirilmesini mümkün bir şekilde sunar.
- `compileOnSave`: Bu ayar, Visual Studio 'da kaynak dosyanın kaydedildiği her seferinde derlenmelidir derleyiciye bildirir.
- `typeAcquisition`: Bu ayar kümesi, otomatik tür alma davranışını denetler ( [Bu bölümde](/visualstudio/ide/javascript-intellisense#Auto)daha fazla açıklama)

JavaScript dosyalarını CommonJS modüllerine dönüştürmek ve bir `./out` klasöre yerleştirmek için aşağıdaki `tsconfig.json` dosyasını kullanabilirsiniz:

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

Ayarlar yerinde olduğunda, bir kaynak dosyası (`./app.js`) varsa ve birkaç ECMAScript 2015 Dil özelliği şu şekilde içeriyorsa:

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

Ardından, aşağıdaki gibi görünen ECMAScript 5 ' i (varsayılan) hedefleyen `./out/app.js` bir dosya yayınlanır:

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

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] içindeki JavaScript IntelliSense artık parametreler ve üye listeleri hakkında daha fazla bilgi görüntüler. Bu yeni bilgiler, kodunuzu daha iyi anlamak için arka planda statik analiz kullanan TypeScript dil hizmeti tarafından sağlanır. Yeni IntelliSense deneyimi ve nasıl çalıştığı hakkında daha fazla bilgi [edinebilirsiniz.](/visualstudio/ide/javascript-intellisense/)

## <a name="JSX"></a>JSX sözdizimi desteği

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] JavaScript, JSX sözdizimi için zengin desteğe sahiptir. JSX, JavaScript dosyaları içinde HTML etiketlerine izin veren bir sözdizimi kümesidir.

Aşağıdaki çizimde `comps.tsx` TypeScript dosyasında tanımlanan bir yanıt verme bileşeni gösterilmektedir ve ardından bu bileşen, `app.jsx` dosyasından kullanılan bu bileşen, tamamlamalar ve JSX ifadeleri içindeki belgeler için IntelliSense ile tamamlandı.
Burada TypeScript 'e ihtiyacınız yoktur, bu özel örnek yalnızca bir TypeScript kodu içermesi için de olur.

![JSX sözdizimi](../javascript/media/js-react.png)

> [!NOTE]
> JSX sözdizimini yanıt verme çağrılarına dönüştürmek için, `"jsx": "react"` ayarı `tsconfig.json` dosyasında `compilerOptions` eklenmelidir.

Derleme sonrasında './out/appnjs ' konumunda oluşturulan JavaScript dosyası şu kodu içermelidir:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript projenizi yapılandırma

Dil hizmeti statik analizler tarafından desteklenir, bu da IntelliSense sonuçlarını döndürmek ve diğer özellikleri sağlamak amacıyla kaynak kodunuzu aslında çalıştırmadan analiz etmek zorunda kalmadan analiz eder.
Bu nedenle, proje bağlamınızın içerdiği dosyaların miktarı ve boyutu arttıkça, analiz sırasında daha fazla bellek ve CPU kullanılacaktır.
Bu nedenle, proje şekil'niz hakkında yapılan birkaç varsayılan varsayım vardır:

- projeniz tarafından kullanılan ve varsayılan olarak `package.json` ve `bower.json` liste bağımlılıkları otomatik tür Alım (ATA) içine eklenmiştir
- Üst düzey `node_modules` klasörü, kitaplık kaynak kodunu içerir ve içeriği varsayılan olarak proje bağlamından çıkarılır
- Tüm diğer `.js`, `.jsx`, `.ts`ve `.tsx` dosyası muhtemelen *kendi* kaynak dosyalarınıza ait ve proje bağlamına dahil olmalıdır

Çoğu durumda projenizi yalnızca açmanız ve varsayılan proje yapılandırmasını kullanarak harika deneyim sahibi olmanız mümkün olacaktır. Ancak, büyük veya farklı klasör yapılarına sahip olan projelerde, dil hizmetini yalnızca kendi kaynak dosyalarınıza daha iyi odaklanmak üzere daha fazla yapılandırmak istenebilir.

### <a name="override-defaults"></a>Geçersiz kılma Varsayılanları

Proje köküne bir `tsconfig.json` dosyası ekleyerek varsayılan yapılandırmayı geçersiz kılabilirsiniz.
`tsconfig.json`, proje bağlamını işleyebileceğiniz çeşitli farklı seçeneklere sahiptir.
Bunlardan bazıları aşağıda listelenmiştir, ancak kullanılabilir tüm seçeneklerin tam bir kümesi için [bkz. şema deposu](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Önemli `tsconfig.json` seçenekleri

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
- `bootstrap`, `jquery`, `jquery-validation`ve `jquery-validation-unobtrusive` `bower.json` listelenmiştir
- `kendo-ui` lib klasörüne el ile eklendi

![Klasör yapısı](../javascript/media/js-folderstructure.png)

Dil hizmetinin yalnızca `js` klasöründeki kaynak dosyalarınızı analiz ettiğinden emin olmak için aşağıdaki `tsconfig.json` kullanabilirsiniz, ancak yine de `lib` klasörünüzdeki kitaplıkların `.d.ts` dosyalarını getirir ve kullanır.

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

Projenizi en uygun hale getirmenin basit bir yolu, dil hizmetinin hangi dosyaların yok sayılacak güvenli olduğunu bilmesini sağlamak için proje köküne bir `tsconfig.json` dosyası eklemektir. Kitaplıkların depolandığı en yaygın dizinleri dışlamak için aşağıdaki örneği kullanın:

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
> `disableSizeLimit` derleyici özelliği, 20 MB 'lık denetim sınırını devre dışı bırakmak için de kullanılabilir. Sınırın devre dışı bırakılması dil hizmetini kilitlemediğinden bu özelliği kullanırken özel önlemler alın.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015 ' den önemli değişiklikler

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] tamamen yeni bir dil hizmeti olarak, önceki deneyimden farklı veya olmayan bazı davranışlar vardır.
En önemli değişiklikler, VSDoc 'ın JSDoc ile değiştirilmesi, özel `.intellisense.js` uzantılarının kaldırılması ve belirli kod desenleri için sınırlı IntelliSense ' in yerini alır.

### <a name="no-more-references-or-_referencesjs"></a>Daha fazla `///<references/>` veya `_references.js`

Daha önce, IntelliSense kapsamınızda hangi dosyaların olduğunu belirli bir anda anlamak oldukça karmaşıktır. Bazen tüm dosyalarınıza kapsam içinde ve diğer zamanlarda sahip olmak ve bu da el ile başvuru yönetimi içeren karmaşık yapılandırmalara yol açmasının istenmiş olması önerilir. Artık başvuru yönetimi hakkında düşünmenize gerek kalmaz, bu nedenle üç eğik çizgi başvuruları açıklamalara veya `_references.js` dosyalarına gerek kalmaz.

IntelliSense 'In nasıl çalıştığı hakkında daha fazla bilgi için bkz. [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) sayfası.

### <a name="vsdoc"></a>VSDoc

Bazen VSDocs olarak adlandırılan XML belgesi Yorumları, daha önce IntelliSense sonuçlarını buatmak için kullanılacak ek verilerle kaynak kodunuzu süslemek için kullanılabilir.
VSDoc, yazma daha kolay olan [JSDoc](https://jsdoc.app/about-getting-started.html) için artık desteklenmiyor ve JavaScript için kabul edilen standart.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` uzantıları

Daha önce, üçüncü taraf kitaplıklar için özel tamamlanma sonuçları eklemenize olanak tanıyan [IntelliSense uzantıları](https://msdn.microsoft.com/library/hh874692.aspx) yazabilirsiniz.
Bu uzantıların yazma ve yükleme ve bunlara başvurulması oldukça zordur, bu nedenle yeni dil hizmetinin iletilmesi bu dosyaları desteklemez.
Daha kolay bir alternatif olarak, eski `.intellisense.js` Uzantılarıyla aynı IntelliSense avantajlarını sağlamak için bir TypeScript tanım dosyası yazabilirsiniz.
Bildirim (`.d.ts`) [dosya yazma hakkında](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)daha fazla bilgi edinebilirsiniz.

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
