---
title: JavaScript ve TypeScript birim testi
description: Visual Studio, Visual Studio için Node.js araçları kullanılarak JavaScript ve TypeScript kodu desteği sağlar
ms.date: 06/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: acac3eb306d12ff6976e19ae5dc1ad772691094c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289007"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Visual Studio 'da JavaScript ve TypeScript ile birim testi

Visual Studio Için Node.js araçları, bir komut istemine geçiş yapmanıza gerek kalmadan daha popüler JavaScript çerçevelerinden bazılarını kullanarak birim testleri yazmanızı ve çalıştırmanızı sağlar.

Desteklenen çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.io](https://jasmine.github.io/))
* Bant ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Çalıştırıcısı dışarı aktar (Bu Framework, Visual Studio için Node.js araçlarına özeldir)

En sevdiğiniz çerçeve desteklenmiyorsa, destek ekleme hakkında bilgi için bkz. [birim test çerçevesi için destek ekleme](#addingFramework) .

## <a name="write-unit-tests"></a>Birim testlerini yaz

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

Test Gezgini 'ni açtıktan sonra ( **Test**  >  **Windows**  >  **Test Gezgini**'ni seçin), Visual Studio Testleri bulur ve görüntüler. Testler başlangıçta gösterilmiyorsa, Listeyi yenilemek için projeyi yeniden derleyin.

![Test Gezgini](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> `outdir` `outfile` Test Gezgini, TypeScript dosyalarında birim testlerinizi bulamayacağından, *tsconfig.jsüzerinde*veya seçeneğini kullanmayın.

## <a name="run-tests"></a>Testleri çalıştırma

Testleri Visual Studio 2017 ' de veya komut satırından çalıştırabilirsiniz.

### <a name="run-tests-in-visual-studio-2017"></a>Visual Studio 2017 ' de testleri çalıştırma

Testleri test Gezgini içindeki **Tümünü Çalıştır** bağlantısına tıklayarak çalıştırabilirsiniz. Ya da, bir veya daha fazla test veya grup seçerek, sağ tıklayıp ve **Seçilen testleri** kısayol menüsünden Çalıştır ' ı seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve test Gezgini sonuçları otomatik olarak güncelleştirir ve gösterir. Ayrıca, seçili testlerde hata **Ayıkla seçili testleri**seçerek de hata ayıklaması yapabilirsiniz.

> [!Warning]
> Düğüm 8 + kullanan birim testlerinde hata ayıklama Şu anda yalnızca JavaScript test dosyaları için çalışır, TypeScript test dosyaları isabet kesme noktalarına başarısız olur. Geçici bir çözüm olarak, `debugger` anahtar sözcüğünü kullanır.

> [!NOTE]
> Profil oluşturma testlerini veya kod kapsamını Şu anda desteklemiyoruz.

### <a name="run-tests-from-the-command-line"></a>Komut satırından test çalıştırma

Aşağıdaki komutu kullanarak, Visual Studio 2017 için [Geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs) testlerini çalıştırabilirsiniz:

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

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Birim test çerçevesi için destek ekleme

JavaScript kullanarak bulma ve yürütme mantığını uygulayarak ek test çerçeveleri için destek ekleyebilirsiniz. Bunu, aşağıdaki test çerçevesinin adı ile bir klasör ekleyerek yapabilirsiniz:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Bu klasör, aşağıdaki iki işlevi dışarı aktaran aynı ada sahip bir JavaScript dosyası içermelidir:

* `find_tests`
* `run_tests`

Ve uygulamalarına yönelik iyi bir örnek için `find_tests` `run_tests` , Içindeki Mocha birimi test çerçevesinin uygulamasına bakın:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Kullanılabilir test çerçevelerini bulma işlemi Visual Studio başlangıcında oluşur. Visual Studio çalışırken bir çerçeve eklenirse, Framework 'ü algılamak için Visual Studio 'Yu yeniden başlatın. Ancak uygulamada değişiklik yaparken yeniden başlatmanız gerekmez.

## <a name="unit-tests-in-other-project-types"></a>Diğer proje türlerinde birim testleri
Yalnızca Node.js projelerinizde birim testlerini yazmak sınırlı değildir. TestFramework ve TestRoot özelliklerini herhangi bir C# veya Visual Basic projesine eklediğinizde, bu testler numaralandırılır ve test Gezgini penceresini kullanarak bunları çalıştırabilirsiniz.

Bunu etkinleştirmek için Çözüm Gezgini proje düğümüne sağ tıklayın, **Projeyi Kaldır**' ı seçin ve ardından **projeyi Düzenle**' yi seçin. Ardından proje dosyasında, bir özellik grubuna aşağıdaki iki öğeyi ekleyin.

> [!NOTE]
> Öğelerini eklemekte olduğunuz özellik grubunun belirtilen bir koşula sahip olmadığından emin olun.
> Bu beklenmeyen davranışlara neden olabilir.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Ardından, testlerinizi belirttiğiniz test kök klasörüne ekleyin ve test Gezgini penceresinde çalıştırmak için kullanılabilir olacaktır. Başlangıçta görünmüyorsa projeyi yeniden oluşturmanız gerekebilir.

### <a name="unit-test-net-core-and-net-standard"></a>Birim testi .NET Core ve .NET Standard
Yukarıdaki özelliklere ek olarak, [Microsoft. JavaScript. UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) NuGet paketini yüklemeniz ve özelliğini ayarlamanız gerekir:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Bazı test çerçeveleri, test algılaması için ek NPM paketleri gerektirebilir. Örneğin, jest, jest-Editor-destek NPM paketini gerektirir. Gerekirse, belirli bir çerçeveye ait belgelere bakın.
