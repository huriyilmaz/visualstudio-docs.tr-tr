---
title: çözüm veya proje olmadan Visual Studio JavaScript kodu yazma
titleSuffix: ''
description: Visual Studio bir proje dosyasında veya çözüm dosyasında bağımlılığı olmayan kod oluşturma desteği sağlar
ms.date: 09/24/2018
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
ms.openlocfilehash: f0d86db6369b33a7cc763b5567ff42ec88440e5f
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969300"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>çözüm veya proje olmadan Visual Studio JavaScript ve TypeScript kodu geliştirme

Visual Studio 2017 ' den başlayarak, [proje veya çözümler olmadan kod geliştirebilirsiniz](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md). bu, bir kod klasörü açmanıza ve ıntellisense, arama, yeniden düzenleme, hata ayıklama ve daha fazlası gibi zengin düzenleyici desteğiyle çalışmaya hemen başlayabilmenizi sağlar. bu özelliklere ek olarak, Visual Studio için Node.js araçları, TypeScript dosyaları oluşturmaya, npm paketlerini yönetmeye ve npm betikleri çalıştırmaya yönelik destek ekler.

Başlamak için araç çubuğundan **Dosya**  >  **Aç**  >  **klasörünü** seçin. Çözüm Gezgini klasördeki tüm dosyaları görüntüler ve düzenlemeden başlamak için herhangi bir dosyayı açabilirsiniz. arka planda, npm, derleme ve hata ayıklama özelliklerini etkinleştirmek için dosyaları dizine Visual Studio.

> [!IMPORTANT]
> bu makalede açıklanan, npm tümleştirmesi dahil özelliklerinin birçoğu, Visual Studio 2017 sürüm 15,8 veya sonraki sürümleri gerektirir. Visual Studio **Node.js geliştirme** iş yükünün yüklü olması gerekir.

## <a name="npm-integration"></a>npm tümleştirmesi

Açtığınız klasör bir *Package. JSON* dosyası içeriyorsa, NPM 'e özgü bir bağlam menüsü (kısayol menüsü) göstermek için *Package. JSON* öğesine sağ tıklayabilirsiniz.

![Çözüm Gezgini NPM menüsü](../javascript/media/solution-explorer-npm-ctx.png)

Kısayol menüsünde, NPM tarafından yüklenen paketleri, [NPM paketlerini](npm-package-management.md) bir proje dosyası kullanırken yönettiğiniz şekilde yönetebilirsiniz.

Ayrıca, menü, `scripts` *Package. JSON*' daki öğesinde tanımlanan betikleri çalıştırmanıza de olanak tanır. Bu betikler, ortam değişkeninde kullanılabilir Node.js sürümünü kullanacaktır `PATH` . Betikler yeni bir pencerede çalışır. Bu, derleme veya çalıştırma betikleri çalıştırmak için harika bir yoldur.

## <a name="build-and-debug"></a>Derleme ve hata ayıklama

### <a name="packagejson"></a>package.json
Klasördeki *Package. JSON* bir `main` öğesi belirtiyorsa, **Debug** komutu *Package. JSON* için sağ tıklama kısayol menüsünde kullanılabilir olacaktır.
Bunu tıklatmak, belirtilen komut dosyası bağımsız değişkeni olarak *node.exe* başlayacaktır.

### <a name="javascript-files"></a>JavaScript dosyaları
JavaScript dosyalarında hata ayıklama yaparak bir dosyaya sağ tıklayıp kısayol menüsünden **Hata Ayıkla** ' yı seçebilirsiniz. Bu, bağımsız değişkeni olarak bu JavaScript dosyası ile *node.exe* başlar.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript dosyaları ve tsconfig. JSON
Klasörde *tsconfig. JSON* dosyası yoksa, bu dosyayı derleyip hata ayıklamanın kısayol menü komutlarını görmek Için bir TypeScript dosyasına sağ tıklayabilirsiniz. Bu komutları kullandığınızda, varsayılan seçeneklerle *tsc.exe* kullanarak derleyin veya hata ayıklayın. (Hata ayıklayabilmeniz için önce dosyayı oluşturmanız gerekir.)

> [!NOTE]
> TypeScript kodu oluştururken ' de yüklü en yeni sürümü kullanıyoruz `C:\Program Files (x86)\Microsoft SDKs\TypeScript` .

Klasörde bir *tsconfig. JSON* dosyası varsa, bu TypeScript dosyasında hata ayıklamak üzere bir menü komutu görmek Için bir TypeScript dosyasına sağ tıklayabilirsiniz. Seçeneği yalnızca `outFile` *tsconfig. JSON* dosyasında belirtilen bir değer varsa görünür. Eğer `outFile` belirtilmişse, *tsconfig. JSON* öğesine sağ tıklayıp doğru seçeneği belirleyerek bu dosyada hata ayıklayabilirsiniz. Bu `tsconfig.json` Dosya Ayrıca, derleyici seçeneklerini belirtmenize izin veren bir yapı seçeneği sağlar.

> [!NOTE]
> Tsconfig *. JSON hakkında daha* fazla bilgiyi [tsconfig. JSON TypeScript el kitabı sayfasında](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)bulabilirsiniz.

## <a name="unit-tests"></a>Birim testleri
*package. json*' da bir test kökü belirterek Visual Studio birim testi tümleştirmesini etkinleştirebilirsiniz:

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
Desteklenen çerçevelerin hiçbiri tanınmazsa, Test Çalıştırıcısı varsayılan olarak *ExportRunner* olur. Desteklenen diğer çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.io](https://jasmine.github.io/))
* Bant ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

test gezgini 'ni açtıktan sonra ( **test**  >  **Windows**  >  **test gezginini** seçin), Visual Studio testleri bulur ve görüntüler.

> [!NOTE]
> Test Çalıştırıcısı yalnızca test kökündeki JavaScript dosyalarını numaralandıracaktır, çünkü uygulamanız TypeScript 'te yazılmışsa, önce bunları derlemeniz gerekir.
