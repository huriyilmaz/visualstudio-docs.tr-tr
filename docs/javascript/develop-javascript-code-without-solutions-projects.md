---
title: Bir çözüm veya proje olmadan Visual Studio JavaScript kodu yazın
titleSuffix: ''
description: Visual Studio, proje dosyasına veya çözüm dosyasına bağımlılık olmadan kod oluşturmak için destek sağlar
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
ms.openlocfilehash: ae8b6fd52cd2469cf7562a199b952d388b463089
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549940"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Visual Studio'da çözüm veya proje olmadan JavaScript ve TypeScript kodu geliştirin

Visual Studio 2017'den başlayarak, bir kod klasörü açmanızı ve IntelliSense, arama, yeniden düzenleme, hata ayıklama ve daha fazlası gibi zengin düzenleyici desteğiyle çalışmaya hemen başlamanızı sağlayan [projeler veya çözümler olmadan kod geliştirebilirsiniz.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Bu özelliklere ek olarak, Visual Studio için Node.js Tools TypeScript dosyaları oluşturmak, npm paketlerini yönetmek ve npm komut dosyaları çalıştırmak için destek ekler.

Başlamak için araç çubuğundan **Dosya** > **Aç** > **Klasörünü** seçin. Solution Explorer klasördeki tüm dosyaları görüntüler ve düzenlemeye başlamak için dosyalardan herhangi birini açabilirsiniz. Arka planda Visual Studio, npm, build ve hata ayıklama özelliklerini etkinleştirmek için dosyaları dizinler.

> [!IMPORTANT]
> Bu makalede açıklanan nPM tümleştirmesi de dahil olmak üzere birçok özellik Visual Studio 2017 sürüm 15.8 veya daha sonraki sürümleri gerektirir. Visual Studio **Node.js geliştirme** iş yükü yüklü olmalıdır.

## <a name="npm-integration"></a>npm entegrasyonu

Açtığınız klasör bir *package.json* dosyası içeriyorsa, npm'ye özgü bir bağlam menüsü (kısayol menüsü) göstermek için *package.json'a* sağ tıklayabilirsiniz.

![çözüm explorer npm menü](../javascript/media/solution-explorer-npm-ctx.png)

Kısayol menüsünde, npm tarafından yüklenen paketleri, proje dosyasını kullanırken [npm paketlerini yönettiğiniz](npm-package-management.md) gibi yönetebilirsiniz.

Buna ek olarak, menü de `scripts` *package.json*öğesi tanımlanan komut dosyaları çalıştırmak için izin verir. Bu komut `PATH` dosyaları, ortam değişkeninde bulunan Düğüm.js sürümünü kullanır. Komut dosyaları yeni bir pencerede çalışır. Bu, yapı yürütmeveya komut dosyalarını çalıştırmanın harika bir yoludur.

## <a name="build-and-debug"></a>Oluşturma ve hata ayıklama

### <a name="packagejson"></a>package.json
Klasördeki *paket.json* bir `main` öğe belirtirse, Hata **Ayıklama** komutu *package.json*için sağ tıklama kısayol menüsünde kullanılabilir.
Bu tıklatıldığında, bağımsız değişken olarak belirtilen komut dosyası ile *node.exe* başlar.

### <a name="javascript-files"></a>JavaScript dosyaları
Bir dosyayı sağ tıklayarak ve kısayol menüsünden **Hata Ayıklama'yı** seçerek JavaScript dosyalarını hata ayıklayabilirsiniz. Bu, bağımsız değişken olarak bu JavaScript dosyası ile *node.exe* başlar.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript dosyaları ve tsconfig.json
Klasörde *tsconfig.json* yoksa, bu dosyayı oluşturmak ve hata ayıklamak için kısayol menü komutlarını görmek için bir TypeScript dosyasına sağ tıklayabilirsiniz. Bu komutları kullandığınızda, varsayılan seçenekleri ile *tsc.exe* kullanarak oluşturmak veya hata ayıklama. (Hata ayıklama yapmadan önce dosyayı oluşturmanız gerekir.)

> [!NOTE]
> TypeScript kodunu yazarken, 'de `C:\Program Files (x86)\Microsoft SDKs\TypeScript`yüklü olan en yeni sürümü kullanırız.

Klasörde *tsconfig.json* dosyası varsa, typescript dosyasını hata ayıklamak için bir menü komutunu görmek için TypeScript dosyasına sağ tıklayabilirsiniz. Seçenek yalnızca `outFile` *tsconfig.json'da*belirtilmemişse görüntülenir. Bir `outFile` belirtilmişse, *tsconfig.json'a* sağ tıklayarak ve doğru seçeneği seçerek bu dosyayı hata ayıklayabilirsiniz. Dosya `tsconfig.json` ayrıca derleyici seçeneklerini belirtmenize olanak tanıyan bir yapı seçeneği de sunar.

> [!NOTE]
> *Tsconfig.json* hakkında daha fazla bilgiyi [tsconfig.json TypeScript El Kitabı sayfasında](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)bulabilirsiniz.

## <a name="unit-tests"></a>Ünite Testleri
Visual Studio'da birim test entegrasyonunu paketinizde bir test kökü belirterek *etkinleştirebilirsiniz.json:*

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test koşucusu, hangi test çerçevesinin kullanılacağını belirlemek için yerel olarak yüklenen paketleri sıraya alır.
Desteklenen çerçevelerin hiçbiri tanınmıyorsa, test koşucusu Varsayılan olarak *ExportRunner'a*aktarılır. Desteklenen diğer çerçeveler şunlardır:
* Mocha ([mochajs.org](https://mochajs.org/))
* Yasemin ([Jasmine.github.io](https://jasmine.github.io/))
* Teyp ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

Test Gezgini'ni açtıktan sonra **(Windows** >  **Test** > **Gezgini Test**et seçeneğini seçin), Visual Studio testleri keşfeder ve görüntüler.

> [!NOTE]
> Test koşucusu yalnızca test kökündeki JavaScript dosyalarını sayısala, uygulamanız TypeScript'te yazılmışsa, bunları ilk oluşturmanız gerekir.
