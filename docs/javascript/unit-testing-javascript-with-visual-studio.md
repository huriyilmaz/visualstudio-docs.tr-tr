---
title: Unit test JavaScript ve TypeScript
description: Visual Studio, Visual Studio için Düğüm.js Araçlarını kullanarak JavaScript ve TypeScript kodunu test eden destek birimi sağlar
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 792c74a3b5da5ed6528fa3919a0c60625d1a38ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77071953"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Unit Test JavaScript ve TypeScript Visual Studio

Visual Studio için Node.js Tools komut istemine geçmenize gerek kalmadan daha popüler JavaScript çerçevelerinden bazılarını kullanarak birim testleri yazmanızı ve çalıştırmanızı sağlar.

Desteklenen çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Yasemin ([Jasmine.github.io](https://jasmine.github.io/))
* Teyp ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* İhracat Runner (Bu çerçeve Visual Studio için Düğüm.js Araçlar özeldir)

> [!WARNING]
> Teyp'deki bir sorun şu anda Teyp testlerinin çalışmasını engelliyor. [PR #361](https://github.com/substack/tape/pull/361) birleştirilirse, sorun çözülmelidir.

Sık kullanılan çerçeveniz desteklenmiyorsa, destek ekleme hakkında bilgi [için birim test çerçevesi için destek ekle'ye](#addingFramework) bakın.

## <a name="write-unit-tests"></a>Ünite testleri yazma

Projenize birim testleri eklemeden önce, kullanmayı planladığınız çerçevenin projenizde yerel olarak yüklendiğinden emin olun. Bu [npm paket yükleme penceresi](npm-package-management.md#npmInstallWindow)kullanarak yapmak kolaydır.

Projenize birim testleri eklemenin tercih edilen yolu, projenizde bir *test* klasörü oluşturmak ve bunu proje özelliklerinde test kökü olarak ayarlamaktır. Ayrıca kullanmak istediğiniz test çerçevesini seçmeniz gerekir.

![Test kökünü ve test çerçeveni ayarlama](../javascript/media/unit-test-project-properties.png)

**Yeni Öğe Ekle** iletişim kutusunu kullanarak projenize basit boş testler ekleyebilirsiniz. JavaScript ve TypeScript aynı projede desteklenir.

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

Proje özelliklerindeki birim test seçeneklerini ayarlamadıysanız, **Özellikler** penceresindeki **Test Çerçevesi** özelliğinin birim test dosyalarınız için doğru test çerçevesine ayarlı olduğundan emin olmalısınız. Bu birim test dosyası şablonları tarafından otomatik olarak yapılır.

![Test Çerçevesi](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Birim test seçenekleri tek tek dosyaların ayarları üzerinde tercih alır.

Test Gezgini'ni açtıktan sonra **(Windows** >  **Test** > **Gezgini Test**et seçeneğini seçin), Visual Studio testleri keşfeder ve görüntüler. Testler başlangıçta görünmüyorsa, listeyi yenilemek için projeyi yeniden oluşturun.

![Test Gezgini](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> `outdir` `outfile` *Tsconfig.json'da*veya seçeneği kullanmayın, çünkü Test Gezgini birim testlerinizi TypeScript dosyalarında bulamayacak.

## <a name="run-tests"></a>Testleri çalıştırma

Testleri Visual Studio 2017'de veya komut satırından çalıştırabilirsiniz.

### <a name="run-tests-in-visual-studio-2017"></a>Visual Studio 2017'de testler çalıştırın

Test Gezgini'ndeki **Tümleri Çalıştır** bağlantısını tıklatarak testleri çalıştırabilirsiniz. Veya, bir veya daha fazla test veya grup seçerek, sağ tıklatarak ve kısayol menüsünden **Seçili Testleri Çalıştır'ı** seçerek testleri çalıştırabilirsiniz. Testler arka planda çalışır ve Test Gezgini sonuçları otomatik olarak güncelleştirir ve gösterir. Ayrıca, **Hata Ayıklama Seçili Testleri**seçerek seçili testleri hata ayıklama da yapabilirsiniz.

> [!Warning]
> Düğüm 8+ kullanarak birim testlerini ayıklama şu anda yalnızca JavaScript test dosyaları için çalışır, TypeScript test dosyaları kesme noktalarına ulaşamaz. Geçici çözüm olarak `debugger` anahtar sözcüğü kullanın.

> [!NOTE]
> Şu anda profil oluşturma testlerini veya kod kapsamını destekliyoruz.

### <a name="run-tests-from-the-command-line"></a>Komut satırından test çalıştırma

Testleri Visual Studio 2017 için [Geliştirici Komut Komut Ustem'den](/dotnet/framework/tools/developer-command-prompt-for-vs) aşağıdaki komutu kullanarak çalıştırabilirsiniz:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Bu komut, aşağıdakilere benzer çıktıyı gösterir:

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
> *vstest.console.exe'nin* bulunamayacağını belirten bir hata alırsanız, düzenli bir komut istemi değil Geliştirici Komut Istem'ini açtığınıza emin olun.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Birim test çerçevesi için destek ekleme

JavaScript kullanarak bulma ve yürütme mantığını uygulayarak ek test çerçeveleri için destek ekleyebilirsiniz. Bunu, aşağıdakiler altında test çerçevesinin adını içeren bir klasör ekleyerek yaparsınız:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Bu klasör, aşağıdaki iki işlevi dışa aktaran aynı ada sahip bir JavaScript dosyası içermelidir:

* `find_tests`
* `run_tests`

İyi bir örnek `find_tests` ve `run_tests` uygulamalar için, Mocha birim test çerçevesi için uygulamaya bakın:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Kullanılabilir test çerçevelerinin keşfi Visual Studio başlangıcında gerçekleşir. Visual Studio çalışırken bir çerçeve eklenirse, çerçeveyi algılamak için Visual Studio'yu yeniden başlatın. Ancak uygulamada değişiklik yaparken yeniden başlatmanız gerekmez.

## <a name="unit-tests-in-other-project-types"></a>Diğer proje türlerinde birim testleri
Sadece Node.js projelerinizde birim testleri yazmakla sınırlı değildir. Herhangi bir C# veya Visual Basic projesine TestFramework ve TestRoot özelliklerini eklediğinizde, bu testler numaralandırılır ve bunları Test Gezgini penceresini kullanarak çalıştırabilirsiniz.

Bunu etkinleştirmek için, Çözüm Gezgini'ndeki proje düğümüne sağ tıklayın, **Project'i Boşalt'ı**ve ardından **Project'i Edit'i**seçin. Ardından proje dosyasında, aşağıdaki iki öğeyi bir özellik grubuna ekleyin.

> [!NOTE]
> Öğeleri eklediğiniz özellik grubunun belirtilen bir koşul olmadığından emin olun.
> Bu beklenmeyen davranışlara neden olabilir.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Ardından, testlerinizi belirttiğiniz test kökü klasörüne ekleyin ve bunlar Test Gezgini penceresinde çalıştırılabilebilirsiniz. Başlangıçta görünmüyorlarsa, projeyi yeniden oluşturmanız gerekebilir.

### <a name="unit-test-net-core-and-net-standard"></a>Ünite testi .NET Çekirdek ve .NET Standardı
Yukarıdaki özelliklere ek olarak, Ayrıca NuGet paketi [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) yüklemeniz ve özelliği ayarlamak gerekir:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Bazı test çerçeveleri, test algılaması için ek npm paketleri gerektirebilir. Örneğin, jest jest-editor-destek npm paketi gerektirir. Gerekirse, belirli bir çerçeve için belgeleri denetleyin.
