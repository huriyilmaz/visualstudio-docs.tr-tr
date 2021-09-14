---
title: JavaScript ve TypeScript'i birim testi
description: Visual Studio, Node.js Tools for Visual Studio kullanarak JavaScript ve TypeScript kodu için destek birimi testi Visual Studio
ms.date: 03/18/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ee04b9e3a49af86780bc9702de5d5c128dae2173
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635870"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>JavaScript ve TypeScript'i Visual Studio

Komut istemine geçmek zorunda kalmadan Visual Studio JavaScript çerçevelerinden bazılarını kullanarak birim testleri yazabilir ve çalıştırabilirsiniz. Hem Node.js hem ASP.NET Core projeleri de desteklene.

Desteklenen çerçeveler:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Bant ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Dışarı Aktarma Çalıştırıcısı (bu çerçeve Node.js Araçları'Visual Studio)

JavaScript ASP.NET Core TypeScript için bkz. ASP.NET Core için [birim testleri yazma. ](#write-unit-tests-for-aspnet-core)

Sık kullanılan çerçeveniz desteklenmiyorsa, destek ekleme [hakkında bilgi için bkz.](#addingFramework) Birim testi çerçevesi için destek ekleme.

## <a name="write-unit-tests-in-a-nodejs-project"></a>Node.js projesinde birim testleri yazma

Projenize birim testleri eklemeden önce kullanmayı planlamış olduğu çerçevenin projenize yerel olarak yüklü olduğundan emin olun. npm paketi yükleme penceresini [kullanarak bunu yapmak kolaydır.](npm-package-management.md#npmInstallWindow)

Projenize birim testleri eklemenin tercih edilen yolu, projeniz içinde *bir testler* klasörü oluşturmak ve bunu proje özelliklerinde test kökü olarak ayar yapmaktır. Ayrıca kullanmak istediğiniz test çerçevesini de seçmeniz gerekir.

![Test kökünü ve test çerçevesini ayarlama](../javascript/media/unit-test-project-properties.png)

Yeni Öğe Ekle iletişim kutusunu kullanarak projenize basit boş **testler bırakabilirsiniz.** Aynı projede hem JavaScript hem de TypeScript desteği vardır.

![Yeni birim testi ekleme](../javascript/media/unit-test-add-new-item.png)

Mocha birim testi için aşağıdaki kodu kullanın:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Proje özelliklerinde birim testi seçeneklerini ayarlamadısanız, Özellikler **penceresindeki Test** Framework  özelliğinin birim testi dosyalarınız için doğru test çerçevesine ayarlanmış olduğundan emin olun. Bu işlem birim testi dosyası şablonları tarafından otomatik olarak yapılır.

![Test Çerçevesi](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Birim testi seçenekleri, tek tek dosyaların ayarlarına göre tercihi alır.

Test Gezgini'ni açtıktan sonra **(Test**  >  **Gezgini Windows'ni**  >  seçin), Visual Studio testlerini keşfeder ve görüntüler. Testler başlangıçta göster görünmüyorsa, listeyi yenilemek için projeyi yeniden oluştur.

![Test Gezgini](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Test Gezgini birim testlerinizi bulamaz olduğundan TypeScript için `outdir` `outfile` *tsconfig.json'da* veya seçeneğini kullanmayın.

## <a name="run-tests-nodejs"></a>Testleri çalıştırma (Node.js)

Testleri komut Visual Studio çalıştırabilirsiniz.

### <a name="run-tests-in-visual-studio"></a>Visual Studio'da testleri çalıştırma

::: moniker range=">=vs-2019"
Test Gezgini'nde Tüm Çalıştır **bağlantısına tıklayarak** testleri çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ tıklar ve kısayol menüsünden **Çalıştır'ı seçerek** testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini otomatik olarak güncelleştirmesi ve sonuçları gösterir. Ayrıca, seçili testlerde hata ayıklamak için sağ tıklar ve Hata ayıkla'ya **tıklar ve öğesini de seçersiniz.**
::: moniker-end
::: moniker range="vs-2017"
Test Gezgini'nde Tüm Çalıştır **bağlantısına tıklayarak** testleri çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ  tıklar ve kısayol menüsünden Seçili Testleri Çalıştır'ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini otomatik olarak güncelleştirmesi ve sonuçları gösterir. Ayrıca Seçili Testlerde Hata Ayıkla seçeneğini kullanarak seçili **testlerde de hata ayıklandırıcısı.**
::: moniker-end

TypeScript için birim testleri, oluşturulan JavaScript kodunda çalışır.

> [!NOTE]
> Çoğu TypeScript senaryosunda, TypeScript kodunda bir kesme noktası ayarp Test Gezgini'nde bir teste sağ tıklar ve Hata ayıkla'ya tıklayarak birim testinde **hata ayıkabilirsiniz.** Kaynak eşlemeleri kullanan bazı senaryolar gibi daha karmaşık senaryolarda TypeScript kodunda kesme noktalarına inebilirsiniz. Geçici bir çözüm olarak anahtar sözcüğünü kullanmayı `debugger` deneyin.

> [!NOTE]
> Şu anda profil oluşturma testlerini veya kod kapsamayı desteklemez.

### <a name="run-tests-from-the-command-line"></a>Komut satırından test çalıştırma

Aşağıdaki komutu kullanarak Geliştirici Komut İstemi [Visual Studio](../ide/reference/command-prompt-powershell.md) çalıştırabilirsiniz:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Bu komut aşağıdakine benzer bir çıktı gösterir:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Dosyanın buluna olmadığını belirten *vstest.console.exe,* normal bir komut istemi değil Geliştirici Komut İstemi emin olun.

## <a name="write-unit-tests-for-aspnet-core"></a>ASP.NET Core için birim testleri yazma

1. Yeni bir ASP.NET Core oluşturun ve TypeScript desteği ekleyin.

   Örnek bir proje için [bkz. TypeScript ile ASP.NET Core uygulama oluşturma.](../javascript/tutorial-aspnet-with-typescript.md) Birim testi desteği için standart bir proje şablonuyla ASP.NET Core öneririz.

   npm NuGet paketi yerine TypeScript desteği eklemek için NuGet paketini kullanın.

1. [Microsoft.JavaScript.UnitTest NuGet paketini yükleme](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Yüklemeden **kaldır'ı Project.**

   *.csproj dosyası,* dosyanın içinde Visual Studio.

1. Aşağıdaki öğeleri öğesinde *.csproj* dosyasına `PropertyGroup` ekleyin.

   Bu örnek, test çerçevesi olarak Mocha'yı belirtir. Bunun yerine Jest, Bant veya Jasmine belirtesiniz.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot`öğesi, birim testlerinin proje kökünde *testler* klasöründe olacağını belirtir.

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Yeniden Yükle'yi **Project.**

1. npm paket yönetimi makalesinde açıklandığı gibi npm desteğini [projelerini ASP.NET Core ekleyin.](../javascript/npm-package-management.md#aspnet-core-projects)

   Bunun için npm desteği için Node.js çalışma zamanının yüklemesi ve proje köküne *package.json* eklemesi gerekir.

1. *package.json içinde,* bağımlılıklar altına istediğiniz npm paketini ekleyin.

   Örneğin mocha için aşağıdakini kullanabilirsiniz:

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Jest gibi bazı birim testi çerçeveleri için ek npm paketleri gerekir. Jest için aşağıdaki JSON'u kullanın:

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > Bazı senaryolarda, Çözüm Gezgini bilinen bir sorun nedeniyle npm düğümünü [gösteremeyebilecektir.](https://github.com/aspnet/Tooling/issues/479) npm düğümünü görüyorsanız, projeyi kaldır (projeye sağ tıklar ve Yüklemeden kaldır'ı **Project)** ve sonra npm düğümünün yeniden görünmesini yapmak için projeyi yeniden yükleyin.

1. Test etmek için kod ekleyin.

   [TypeScript](tutorial-aspnet-with-typescript.md)ile bir ASP.NET Core uygulaması oluşturma konusunda açıklanan örneği kullanıyorsanız, scripts klasöründeki *library.ts* dosyasının sonuna aşağıdaki *kodu* ekleyin.

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   TypeScript için birim testleri, oluşturulan JavaScript kodunda çalışır.

1. Birim testlerinizi proje *kökünde testler* klasörüne ekleyin.

   Örneğin, bu örnekte Mocha veya Jest gibi test çerçevenize uygun doğru belge sekmesini seçerek aşağıdaki kodu kullanabilirsiniz. Bu kod adlı bir işlevi test `getData` etti.

   # <a name="mocha"></a>[Mocha](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[Jest](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. Test Gezgini'ni açın **(Test**  >  **Gezgini'Windows**  >  **Test Gezgini'ni** seçin) Visual Studio testlerini keşfeder ve görüntüler. Testler başlangıçta göster görünmüyorsa, listeyi yenilemek için projeyi yeniden oluştur.

   ![Test Gezgini test bulma](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > Test Gezgini birim testlerinizi bulamaz olduğundan TypeScript için `outfile` *tsconfig.json'da* seçeneğini kullanmayın. seçeneğini `outdir` kullanabilirsiniz, ancak ve gibi yapılandırma dosyalarının proje `package.json` `tsconfig.json` kökünde olduğundan emin olun.

## <a name="run-tests-aspnet-core"></a>Testleri çalıştırma (ASP.NET Core)

::: moniker range=">=vs-2019"
Test Gezgini'nde Tüm Çalıştır **bağlantısına tıklayarak** testleri çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ tıklar ve kısayol menüsünden **Çalıştır'ı seçerek** testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini otomatik olarak güncelleştirmesi ve sonuçları gösterir. Ayrıca, seçili testlerde hata ayıklamak için sağ tıklar ve Hata ayıkla'ya **tıklar ve öğesini de seçersiniz.**
::: moniker-end
::: moniker range="vs-2017"
Test Gezgini'nde Tüm Çalıştır **bağlantısına tıklayarak** testleri çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ  tıklar ve kısayol menüsünden Seçili Testleri Çalıştır'ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini otomatik olarak güncelleştirmesi ve sonuçları gösterir. Ayrıca Seçili Testlerde Hata Ayıkla seçeneğini kullanarak seçili **testlerde de hata ayıklandırıcısı.**
::: moniker-end

TypeScript için birim testleri, oluşturulan JavaScript kodunda çalışır.

![Test Gezgini sonuçları](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> Çoğu TypeScript senaryosunda, TypeScript kodunda bir kesme noktası ayarp Test Gezgini'nde bir teste sağ tıklar ve Hata ayıkla'ya tıklayarak birim testinde **hata ayıkabilirsiniz.** Kaynak eşlemeleri kullanan bazı senaryolar gibi daha karmaşık senaryolarda TypeScript kodunda kesme noktalarına inebilirsiniz. Geçici bir çözüm olarak anahtar sözcüğünü kullanmayı `debugger` deneyin.

> [!NOTE]
> Şu anda profil oluşturma testlerini veya kod kapsamayı desteklemez.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Birim testi çerçevesi için destek ekleme

JavaScript kullanarak bulma ve yürütme mantığını kullanarak ek test çerçeveleri için destek ekleyebilirsiniz. Bunu yapmak için aşağıdakiler altında test çerçevesinin adına sahip bir klasör eklersiniz:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Bu klasörün, aşağıdaki iki işlevi dışarı aktaran aynı adla bir JavaScript dosyası içermesi gerekir:

* `find_tests`
* `run_tests`

ve uygulamalarına iyi bir örnek için, içinde Mocha birim testi `find_tests` `run_tests` çerçevesinin uygulamasına bakın:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Kullanılabilir test çerçevelerinin bulunması en Visual Studio gerçekleşir. Çerçeve çalışırken bir çerçeve Visual Studio çerçeveyi algılamak için Visual Studio yeniden başlatın. Ancak uygulamada değişiklik yaparken yeniden başlatmanız gerek değildir.

## <a name="unit-tests-in-net-framework"></a>.NET Framework'da birim testleri

Yalnızca kendi proje ve projelerinde birim testleri yazmakla Node.js ASP.NET Core olmaz. TestFramework ve TestRoot özelliklerini herhangi bir C# veya Visual Basic projesine eklerken, bu testler numaralara eklir ve Test Gezgini penceresini kullanarak bunları çalıştırabilirsiniz.

Bunu etkinleştirmek için, proje düğümünde proje düğümüne sağ tıklayın, Çözüm Gezgini **kaldır'ı Project'yi** seçin ve ardından **Project.** Ardından proje dosyasında, bir özellik grubuna aşağıdaki iki öğeyi ekleyin.

> [!IMPORTANT]
> Öğeleri eklemekte olduğunu özellik grubunun belirtilen bir koşula sahip olduğundan emin olun.
> Bu beklenmeyen davranışa neden olabilir.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Ardından, testlerinizi belirttiğiniz test kök klasörüne ekleyin ve Test Gezgini penceresinde çalıştırabilirsiniz. Başlangıçta görünmüyorsa projeyi yeniden oluşturmanız gerekir.

## <a name="unit-test-net-core-and-net-standard"></a>Birim testi .NET Core ve .NET Standard

Yukarıdaki özelliklere ek olarak, [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) NuGet paketini de yüklemeniz ve özelliğini ayarlamamız gerekir:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Bazı test çerçeveleri, test algılama için ek npm paketleri gerektirir. Örneğin jest, jest-editor-support npm paketini gerektirir. Gerekirse, belirli bir çerçevenin belgelerini inceleyin.
