---
title: Çözüm veya proje olmadan Visual Studio JavaScript kodu yazma
titleSuffix: ''
description: Visual Studio proje dosyasına veya çözüm dosyasına bağımlılık olmadan kod oluşturma desteği sağlar
ms.custom: seodec18
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
ms.openlocfilehash: c1cad687f73af5eb59f23a2d176e5b8facd3da40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028026"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Çözüm veya proje olmadan Visual Studio JavaScript ve TypeScript kodu geliştirme

Visual Studio 2017'den başlayarak, [](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)bir kod klasörü açıp IntelliSense, arama, yeniden düzenleme, hata ayıklama ve daha fazlası gibi zengin düzenleyici desteğiyle hemen çalışmaya başlamanızı sağlayan, projeleri veya çözümleri olmayan kod geliştirebilirsiniz. Node.js Tools for Visual Studio, bu özelliklere ek olarak TypeScript dosyaları oluşturma, npm paketlerini yönetme ve npm betiklerini çalıştırma desteği ekler.

Çalışmaya başlamanız için araç **çubuğundan**  >    >  **Dosya Klasör Aç'ı** seçin. Çözüm Gezgini klasördeki tüm dosyaları görüntüler ve düzenlemeye başlamak için dosyalardan herhangi birini açabilirsiniz. Arka planda, Visual Studio, derleme ve hata ayıklama özelliklerini etkinleştirmek için dosyaları dizinler.

> [!IMPORTANT]
> Npm tümleştirmesi de dahil olmak üzere bu makalede açıklanan özelliklerin birçoğu, 2017 Visual Studio 15.8 veya sonraki sürümleri gerektirir. Geliştirme Visual Studio **Node.js iş** yükünün yüklü olması gerekir.

## <a name="npm-integration"></a>npm tümleştirmesi

Açık klasör bir *dosyada* package.jsiçeriyorsa, npm'ye *özgü bir bağlampackage.js* (kısayol menüsü) göstermek için aç'a sağ tıklarsınız.

![Çözüm Gezgini'de npm menüsü](../javascript/media/solution-explorer-npm-ctx.png)

Kısayol menüsünde npm tarafından yüklenmiş paketleri, proje dosyası kullanırken npm paketlerini [yönetmekle](npm-package-management.md) aynı şekilde yönetebilirsiniz.

Ayrıca menü, öğesinde tanımlanan betikleri üzerinde birpackage.js`scripts` *sağlar.* Bu betikler, ortam değişken Node.js betiklerin `PATH` sürümünü kullanır. Betikler yeni bir pencerede çalıştır. Bu, derleme veya çalıştırma betiklerini yürütmek için harika bir yol sağlar.

## <a name="build-and-debug"></a>Derleme ve hata ayıklama

### <a name="packagejson"></a>package.json
Klasördeki *package.js* öğesi belirtirse, hata ayıkla komutu, üzerinde belirtilen öğenin sağ tıklama `main` kısayol menüsündepackage.js *kullanılabilir.* 
Bu düğmeye *tıklar* node.exebağımsız değişkeni olarak belirtilen betikle çalışmaya başlar.

### <a name="javascript-files"></a>JavaScript dosyaları
Bir dosyaya sağ tıklar ve kısayol menüsünden Hata ayıkla'yı seçerek JavaScript **dosyalarında** hata ayıkabilirsiniz. Bu *node.exe* JavaScript dosyasıyla bağımsız değişkeni olarak başlar.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript dosyaları ve tsconfig.jsdosyaları
Klasörde herhangi *birtsconfig.js* yoksa, bu dosyayı derlemek ve hata ayıklamak için kısayol menüsü komutlarını görmek için TypeScript dosyasına sağ tıklarsınız. Bu komutları kullanırken, varsayılan seçenekleri kullanarak derlemetsc.exe *hata* ayıklarsınız. (Hata ayıklamadan önce dosyayı derlemelisiniz.)

> [!NOTE]
> TypeScript kodu oluşturmada, 'de yüklü en yeni sürümü `C:\Program Files (x86)\Microsoft SDKs\TypeScript` kullanıyoruz.

Klasörde bir *tsconfig.jsdosyası* varsa TypeScript dosyasına sağ tıklar ve bu TypeScript dosyasında hata ayıklaması yapmak için menü komutunu ekleyebilirsiniz. Seçeneği yalnızca üzerinde belirtilen içinde `outFile` *belirtilmemişsetsconfig.jsgörünür.* belirtilirse, dosyanın hata ayıklaması için sağ tıklartsconfig.js`outFile` ve doğru seçeneği belirtebilirsiniz.  Dosya, `tsconfig.json` derleyici seçeneklerini belirtmenize olanak sağlayan bir derleme seçeneği de sağlar.

> [!NOTE]
> Hakkında daha fazla bilgi için *tsconfig.jstypescript* [tsconfig.jssayfasında bulabilirsiniz.](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

## <a name="unit-tests"></a>Birim Testleri
üzerinde bir test kökü belirterek Visual Studio testi tümleştirmeyi *package.js:*

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test çalıştırıcısı, hangi test çerçevesini kullanmak üzere yerel olarak yüklenmiş paketleri numaralandırıyor.
Desteklenen çerçevelerden hiçbiri tanınmıyorsa, test çalıştırıcı varsayılan olarak *ExportRunner 'ı kullanır.* Desteklenen diğer çerçeveler:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Bant ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

Test Gezgini'ni açtıktan sonra **(Test**  >  **Gezgini Windows'ni**  >  seçin), Visual Studio testlerini keşfeder ve görüntüler.

> [!NOTE]
> Test çalıştırıcısı, javascript dosyalarını yalnızca test kökünde numaralar; eğer uygulamanız TypeScript'te yazılmışsa önce bu dosyaları derlemeniz gerekir.
