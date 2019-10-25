---
title: Visual Studio 'da çözüm veya proje olmadan JavaScript kodu yazma
titleSuffix: ''
description: Visual Studio, bir proje dosyası veya çözüm dosyası üzerinde bağımlılığını olmadan kod oluşturma desteği sağlar
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 288cb11d3e6ae3917f5fcc6ec9ed242549908576
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888648"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Visual Studio 'da çözüm veya proje olmadan JavaScript ve TypeScript kodu geliştirme

Visual Studio 2017 ' den başlayarak, [Proje veya çözümler olmadan kod geliştirebilirsiniz](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md). Bu, kod klasörünü açmanıza ve IntelliSense, arama, yeniden düzenleme, hata ayıklama ve daha fazlası gibi zengin düzenleyici desteğiyle çalışmaya hemen başlayabilmenizi sağlar. Bu özelliklere ek olarak Visual Studio için Node.js Araçları, TypeScript dosyaları oluşturmaya, NPM paketlerini yönetmeye ve NPM betikleri çalıştırmaya yönelik destek ekler.

Başlamak için araç çubuğundan **dosya** >  > **klasörünü** **Aç** ' ı seçin. Çözüm Gezgini klasördeki tüm dosyaları görüntüler ve düzenlemeden başlamak için herhangi bir dosyayı açabilirsiniz. Arka planda, Visual Studio, NPM, derleme ve hata ayıklama özelliklerini etkinleştirmek için dosyaları dizinliyor.

> [!IMPORTANT]
> Bu makalede açıklanan, npm tümleştirmesi dahil özelliklerinin birçoğu, Visual Studio 2017 sürüm 15,8 veya sonraki sürümleri gerektirir.

## <a name="npm-integration"></a>npm tümleştirmesi

Açtığınız klasör bir *Package. JSON* dosyası içeriyorsa, NPM 'e özgü bir bağlam menüsü (kısayol menüsü) göstermek için *Package. JSON* öğesine sağ tıklayabilirsiniz.

![Çözüm Gezgini NPM menüsü](../javascript/media/solution-explorer-npm-ctx.png)

Kısayol menüsünde, NPM tarafından yüklenen paketleri, [NPM paketlerini](npm-package-management.md) bir proje dosyası kullanırken yönettiğiniz şekilde yönetebilirsiniz.

Ayrıca, menü, *Package. JSON*' de `scripts` öğesinde tanımlanan betikleri çalıştırmanıza de olanak tanır. Bu betikler, `PATH` ortam değişkeninde bulunan Node. js sürümünü kullanır. Betikler yeni bir pencerede çalışır. Bu, derleme veya çalıştırma betikleri çalıştırmak için harika bir yoldur.

## <a name="build-and-debug"></a>Derleme ve hata ayıklama

### <a name="packagejson"></a>Package. JSON
Klasördeki *Package. JSON* bir `main` öğesi belirtiyorsa, **Debug** komutu *Package. JSON*için sağ tıklama kısayol menüsünde kullanılabilir olacaktır.
Bunu tıklatmak, *Node. exe* ' yi belirtilen betiğe bağımsız değişken olarak başlatacak.

### <a name="javascript-files"></a>JavaScript dosyaları
JavaScript dosyalarında hata ayıklama yaparak bir dosyaya sağ tıklayıp kısayol menüsünden **Hata Ayıkla** ' yı seçebilirsiniz. Bu, *Node. exe* ' yi bağımsız değişkeni olarak bu JavaScript dosyası ile başlatır.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript dosyaları ve tsconfig. JSON
Klasörde *tsconfig. JSON* dosyası yoksa, bu dosyayı derleyip hata ayıklamanın kısayol menü komutlarını görmek Için bir TypeScript dosyasına sağ tıklayabilirsiniz. Bu komutları kullandığınızda, *TSC. exe* ' yi varsayılan seçenekleriyle kullanarak derler veya hata ayıklayın. (Hata ayıklayabilmeniz için önce dosyayı oluşturmanız gerekir.)

> [!NOTE]
> TypeScript kodu oluştururken, `C:\Program Files (x86)\Microsoft SDKs\TypeScript`' de yüklü en yeni sürümü kullanıyoruz.

Klasörde bir *tsconfig. JSON* dosyası varsa, bu TypeScript dosyasında hata ayıklamak üzere bir menü komutu görmek Için bir TypeScript dosyasına sağ tıklayabilirsiniz. Seçenek yalnızca *tsconfig. JSON*dosyasında belirtilen `outFile` yoksa görüntülenir. Bir `outFile` belirtilirse, *tsconfig. JSON* öğesine sağ tıklayıp doğru seçeneği belirleyerek bu dosyada hata ayıklayabilirsiniz. `tsconfig.json` dosyası, derleyici seçeneklerini belirtmenize izin veren bir yapı seçeneği de sağlar.

> [!NOTE]
> Tsconfig *. JSON hakkında daha* fazla bilgiyi [tsconfig. JSON TypeScript el kitabı sayfasında](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)bulabilirsiniz.

## <a name="unit-tests"></a>Birim testleri
*Package. JSON*' da bir test kökü belirterek Visual Studio 'da birim testi tümleştirmesini etkinleştirebilirsiniz:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test Çalıştırıcısı, hangi test çerçevesinin kullanılacağını belirleyen yerel olarak yüklenen paketleri numaralandırır.
Desteklenen çerçevelerin hiçbiri tanınmazsa, Test Çalıştırıcısı varsayılan olarak *ExportRunner*olur. Desteklenen diğer çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.io](https://jasmine.github.io/))
* Bant ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

Test Gezgini 'ni açtıktan sonra ( **test** > **Windows** > **Test Gezgini**' ni seçin), Visual Studio Testleri bulur ve görüntüler.

> [!NOTE]
> Test Çalıştırıcısı yalnızca test kökündeki JavaScript dosyalarını numaralandıracaktır, çünkü uygulamanız TypeScript 'te yazılmışsa, önce bunları derlemeniz gerekir.
