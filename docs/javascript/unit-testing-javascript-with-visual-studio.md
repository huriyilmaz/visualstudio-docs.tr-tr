---
title: JavaScript ve TypeScript birim testi
description: Visual Studio, Visual Studio için Node.js araçlarını kullanarak JavaScript ve TypeScript kodu desteği sağlar
ms.date: 09/20/2021
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
ms.openlocfilehash: c2a11d163416febf50bb1c4947a069733dd8ae21
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129560886"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Visual Studio 'de birim testi JavaScript ve TypeScript

bir komut istemine geçiş gerektirmeden daha popüler JavaScript çerçevelerinden bazılarını kullanarak Visual Studio birim testlerini yazabilir ve çalıştırabilirsiniz. hem Node.js hem de ASP.NET Core projeleri desteklenir.

Desteklenen çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.io](https://jasmine.github.io/))
* Bant ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Çalıştırıcısı dışarı aktar (Bu çerçeve, Visual Studio için Node.js araçlara özeldir)

ASP.NET Core ve JavaScript ya da TypeScript için bkz. [ASP.NET Core için birim testleri yazma ](#write-unit-tests-for-aspnet-core).

En sevdiğiniz çerçeve desteklenmiyorsa, destek ekleme hakkında bilgi için bkz. [birim test çerçevesi için destek ekleme](#addingFramework) .

::: moniker range=">=vs-2022"
## <a name="write-unit-tests-for-a-cli-based-project-esproj"></a>CLı tabanlı bir proje (. esproj) için birim testleri yazma

Visual Studio 2022 ' de desteklenen clı tabanlı projeler Test gezgini ile çalışır. jest, React ve vue projeleri için yerleşik test çerçevesidir ve Angular projeler için Karma ve jasmine kullanılır. Varsayılan olarak, her bir çerçeve tarafından sunulan varsayılan testleri, ayrıca yazdığınız ek testleri çalıştırabileceksiniz.  Yalnızca test Gezgini 'nde **Çalıştır** düğmesine basın. Test Gezgini zaten açık değilse, menü çubuğunda **Test**  >  **Test Gezgini** ' ni seçerek bunu bulabilirsiniz.

Node.js geliştirme iş yükü, CLı tabanlı projelere yönelik birim testini desteklemek için gereklidir.

Mocha ve bant test kitaplıkları da desteklenir. Bunlardan birini kullanmak için Package. json ' daki varsayılan test kitaplığını uygun test kitaplığının paketine değiştirmeniz yeterlidir.
::: moniker-end

## <a name="write-unit-tests-in-a-nodejs-project"></a>Node.js projesindeki birim testlerini yazma

Projenize birim testleri eklemeden önce, kullanmayı planladığınız çerçevenin projenizde yerel olarak yüklü olduğundan emin olun. Bu, [NPM paket yükleme penceresi](npm-package-management.md#npmInstallWindow)kullanılarak kolayca yapılır.

Projenize birim testleri eklemenin tercih edilen yolu, projenizde bir *Test* klasörü oluşturup proje özelliklerinde test kökü olarak ayarlanıyor. Ayrıca, kullanmak istediğiniz test çerçevesini de seçmeniz gerekir.

![Test kökünü ve test çerçevesini ayarla](../javascript/media/unit-test-project-properties.png)

**Yeni öğe Ekle** iletişim kutusunu kullanarak projenize basit boş testler ekleyebilirsiniz. Aynı projede hem JavaScript hem de TypeScript desteklenir.

![Yeni birim testi Ekle](../javascript/media/unit-test-add-new-item.png)

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

Proje özelliklerinde birim testi seçeneklerini ayarlamadıysanız, **Özellikler** penceresindeki **test çerçevesi** özelliğinin birim test dosyalarınız için doğru test çerçevesine ayarlandığından emin olmanız gerekir. Bu, birim test dosyası şablonları tarafından otomatik olarak gerçekleştirilir.

![Test çerçevesi](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Birim testi seçenekleri tek tek dosyalar için ayarlar üzerinde tercih edilir.

test gezgini 'ni açtıktan sonra ( **test**  >  **Windows**  >  **test gezginini** seçin), Visual Studio testleri bulur ve görüntüler. Testler başlangıçta gösterilmiyorsa, Listeyi yenilemek için projeyi yeniden derleyin.

![Test Gezgini](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> TypeScript için, `outdir` `outfile` Test Gezgini birim testlerinizi bulamayacağından *tsconfig. JSON* içinde or seçeneğini kullanmayın.

## <a name="run-tests-nodejs"></a>Testleri Çalıştır (Node.js)

testleri Visual Studio veya komut satırından çalıştırabilirsiniz.

### <a name="run-tests-in-visual-studio"></a>Visual Studio Testleri çalıştırma

::: moniker range=">=vs-2019"
Testleri test Gezgini içindeki **Tümünü Çalıştır** bağlantısına tıklayarak çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ tıklayıp ve kısayol menüsünden **Çalıştır** ' ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve test Gezgini sonuçları otomatik olarak güncelleştirir ve gösterir. Ayrıca, sağ tıklayıp **Hata Ayıkla**' yı seçerek seçili testlerde hata ayıklaması de yapabilirsiniz.
::: moniker-end
::: moniker range="vs-2017"
Testleri test Gezgini içindeki **Tümünü Çalıştır** bağlantısına tıklayarak çalıştırabilirsiniz. Ya da, bir veya daha fazla test veya grup seçerek, sağ tıklayıp ve **Seçilen testleri** kısayol menüsünden Çalıştır ' ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve test Gezgini sonuçları otomatik olarak güncelleştirir ve gösterir. Ayrıca, seçili testlerde hata **Ayıkla seçili testleri** seçerek de hata ayıklaması yapabilirsiniz.
::: moniker-end

TypeScript için, birim testleri oluşturulan JavaScript koduna karşı çalıştırılır.

> [!NOTE]
> Çoğu TypeScript senaryosunda, TypeScript kodunda bir kesme noktası ayarlayarak, test Gezgini 'nde bir teste sağ tıklayıp **Hata Ayıkla**' yı seçerek bir birim testinde hata ayıklaması yapabilirsiniz. Kaynak haritaları kullanan bazı senaryolar gibi daha karmaşık senaryolarda, TypeScript kodunda kesme noktalarına vurmadan zorluk yaşayabilirsiniz. Geçici bir çözüm olarak, `debugger` anahtar sözcüğünü kullanmayı deneyin.

> [!NOTE]
> Profil oluşturma testlerini veya kod kapsamını Şu anda desteklemiyoruz.

### <a name="run-tests-from-the-command-line"></a>Komut satırından test çalıştırma

aşağıdaki komutu kullanarak [Visual Studio için Geliştirici Komut İstemi](../ide/reference/command-prompt-powershell.md) testleri çalıştırabilirsiniz:

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
> *vstest.console.exe* bulunamadığını belirten bir hata alırsanız, normal bir komut istemi değil Geliştirici komut istemi açtığınızdan emin olun.

## <a name="write-unit-tests-for-aspnet-core"></a>ASP.NET Core için birim testleri yazma

1. bir ASP.NET Core projesi oluşturun ve TypeScript desteği ekleyin.

   örnek bir proje için bkz. [TypeScript ile ASP.NET Core uygulaması oluşturma](../javascript/tutorial-aspnet-with-typescript.md). birim testi desteği için, standart bir ASP.NET Core projesi şablonuyla başlamasını öneririz.

   npm typescript paketi yerine typescript desteği eklemek için NuGet paketini kullanın.

1. [Microsoft. JavaScript. unittest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) NuGet paketini yükler

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Project kaldır**' ı seçin.

   *. Csproj* dosyası Visual Studio açılmalıdır.

1. Aşağıdaki öğeleri öğesindeki *. csproj* dosyasına ekleyin `PropertyGroup` .

   Bu örnek, test çerçevesi olarak Mocha 'yi belirtir. Bunun yerine jest, Tape veya Jasmine belirtebilirsiniz.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot`Öğesi, birim testlerinizin proje kökünün *testler* klasöründe olacağını belirtir.

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Project yeniden yükle**' yi seçin.

1. [ASP.NET Core projeleri](../javascript/npm-package-management.md#aspnet-core-projects)altındaki npm paket yönetimi makalesinde açıklandığı şekilde npm desteği ekleyin.

   Bu, NPM desteği için Node.js çalışma zamanının yüklenmesini ve proje kökünde *Package. JSON* ' i eklemeyi gerektirir.

1. *Package. JSON*' da, bağımlılıklar altında istediğiniz NPM paketini ekleyin.

   Örneğin, Mocha için aşağıdakileri kullanabilirsiniz:

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Jest gibi bazı birim testi çerçeveleri ek NPM paketleri gerektirir. Jest için aşağıdaki JSON 'u kullanın:

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > Bazı senaryolarda Çözüm Gezgini, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorun nedeniyle NPM düğümünü gösteremeyebilir. npm düğümünü görmeniz gerekiyorsa projeyi (projeye sağ tıklayıp **Project kaldır**' ı seçin) ve ardından npm düğümü yeniden görüntülenmesini sağlamak için projeyi yeniden yükleyebilirsiniz.

1. Sınanacak kodu ekleyin.

   [TypeScript ile ASP.NET Core uygulaması oluşturma](tutorial-aspnet-with-typescript.md)bölümünde açıklanan örneği kullanıyorsanız, *komut dosyaları* klasöründe bulunan *library. ts* dosyasının sonuna aşağıdaki kodu ekleyin.

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   TypeScript için, birim testleri oluşturulan JavaScript koduna karşı çalıştırılır.

1. Birim testlerinizi proje kökündeki *testler* klasörüne ekleyin.

   Örneğin, bu örnekte Mocha veya jest gibi test çerçevesinden eşleşen doğru belge sekmesini seçerek aşağıdaki kodu kullanabilirsiniz. Bu kod, adlı bir işlevi sınar `getData` .

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

1. test gezgini 'ni açın ( **test**  >  **Windows**  >  **test gezgini**) seçin ve testleri bulur ve görüntüler Visual Studio. Testler başlangıçta gösterilmiyorsa, Listeyi yenilemek için projeyi yeniden derleyin.

   ![Test Gezgini test keşfi](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > TypeScript için, `outfile` Test Gezgini birim testlerinizi bulamayacağından *tsconfig. JSON* içinde seçeneğini kullanmayın. `outdir`Seçeneğini kullanabilirsiniz, ancak ve gibi yapılandırma dosyalarının `package.json` `tsconfig.json` Proje kökünde olmasını sağlayabilirsiniz.

## <a name="run-tests-aspnet-core"></a>Testleri Çalıştır (ASP.NET Core)

::: moniker range=">=vs-2019"
Testleri test Gezgini içindeki **Tümünü Çalıştır** bağlantısına tıklayarak çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ tıklayıp ve kısayol menüsünden **Çalıştır** ' ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve test Gezgini sonuçları otomatik olarak güncelleştirir ve gösterir. Ayrıca, sağ tıklayıp **Hata Ayıkla**' yı seçerek seçili testlerde hata ayıklaması de yapabilirsiniz.
::: moniker-end
::: moniker range="vs-2017"
Testleri test Gezgini içindeki **Tümünü Çalıştır** bağlantısına tıklayarak çalıştırabilirsiniz. Ya da bir veya daha fazla test veya grup seçerek, sağ  tıklar ve kısayol menüsünden Seçili Testleri Çalıştır'ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini otomatik olarak güncelleştirmesi ve sonuçları gösterir. Ayrıca Seçili Testlerde Hata Ayıkla seçeneğini kullanarak seçili **testlerde de hata ayıklandırıcısı.**
::: moniker-end

TypeScript için birim testleri, oluşturulan JavaScript kodunda çalışır.

![Test Gezgini sonuçları](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> Çoğu TypeScript senaryosunda, TypeScript kodunda bir kesme noktası ayarp Test Gezgini'nde bir teste sağ tıklar ve Hata ayıkla'ya tıklayarak birim testinde **hata ayıkabilirsiniz.** Kaynak eşlemeleri kullanan bazı senaryolar gibi daha karmaşık senaryolarda TypeScript kodunda kesme noktalarına inebilirsiniz. Geçici bir çözüm olarak anahtar sözcüğünü kullanmayı `debugger` deneyin.

> [!NOTE]
> Şu anda profil oluşturma testlerini veya kod kapsamayı desteklemez.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Birim testi çerçevesi için destek ekleme

JavaScript kullanarak bulma ve yürütme mantığını kullanarak ek test çerçeveleri için destek ekleyebilirsiniz.

> [!NOTE]
> Daha ASP.NET Core destek eklemek NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) NuGet paketini projenize ekleyin.

Bunu yapmak için aşağıdakiler altında test çerçevesinin adına sahip bir klasör eklersiniz:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Klasörü bir ASP.NET Core `NodeJsTools` projesinde görmüyorsanız, Node.js kullanarak Visual Studio Yükleyicisi. Bu iş yükü, JavaScript ve TypeScript birim testi desteği içerir.

Bu klasörün, aşağıdaki iki işlevi dışarı aktaran aynı adla bir JavaScript dosyası içermesi gerekir:

* `find_tests`
* `run_tests`

ve uygulamalarına iyi bir örnek için, içinde Mocha birim testi `find_tests` `run_tests` çerçevesinin uygulamasına bakın:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Kullanılabilir test çerçevelerinin bulunması en Visual Studio gerçekleşir. Çerçeve çalışırken bir çerçeve Visual Studio, çerçeveyi algılamak Visual Studio yeniden başlatın. Ancak uygulamada değişiklik yaparken yeniden başlatmanız gerek değildir.

## <a name="unit-tests-in-net-framework"></a>.NET Framework'da birim testleri

Yalnızca kendi proje ve projelerinde birim testleri yazmakla Node.js ASP.NET Core olmaz. TestFramework ve TestRoot özelliklerini herhangi bir C# veya Visual Basic projesine eklerken, bu testler numaralara eklir ve Test Gezgini penceresini kullanarak bunları çalıştırabilirsiniz.

Bunu etkinleştirmek için, proje düğümünde proje düğümüne sağ tıklayın, Çözüm Gezgini kaldır'ı  **Project'yi** seçin ve sonra da Project. Ardından proje dosyasında, bir özellik grubuna aşağıdaki iki öğeyi ekleyin.

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

Yukarıdaki özelliklere ek olarak, [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) NuGet paketini de yüklemeniz ve özelliğini ayarlamalısiniz:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Bazı test çerçeveleri, test algılama için ek npm paketleri gerektirir. Örneğin jest, jest-editor-support npm paketini gerektirir. Gerekirse, belirli bir çerçevenin belgelerini inceleyin.
