---
title: npm paketlerini yönetme
description: Visual Studio, Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0b4b699c01522878d83e59aadb2c6a54e9d7517f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760172"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio'da npm paketlerini yönetin

npm, Node.js uygulamalarınızda kullanılmak üzere paketleri yüklemenize ve yönetmenize olanak tanır. Visual Studio, npm ile etkileşimde bulunmayı ve ui veya doğrudan npm komutları vermeyi kolaylaştırır. NPM'ye aşina değilseniz ve daha fazla bilgi edinmek istiyorsanız, [npm belgelerine](https://docs.npmjs.com/)gidin.

NPM ile Visual Studio entegrasyonu proje türünüze bağlı olarak farklıdır.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasörü aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm proje kökünde *node_modules* klasörü ve *package.json* bekliyor. Uygulamanızın klasör yapısı farklıysa, Visual Studio'yı kullanarak npm paketlerini yönetmek istiyorsanız klasör yapınızı değiştirmeniz gerekir.

## <a name="nodejs-projects"></a>Düğüm.js projeleri

Node.js projeleri için aşağıdaki görevleri gerçekleştirebilirsiniz:
* [Solution Explorer'dan paketleri yükleme](#npmInstallWindow)
* [Solution Explorer'dan yüklü paketleri yönetme](#solutionExplorer)
* [Düğüm.js Etkileşimli Pencere'deki `.npm` komutu kullanın](#interactive)

Bu özellikler birlikte çalışır ve projedeki proje sistemi ve *package.json* dosyasıyla senkronize olur.

### <a name="prerequisites"></a>Ön koşullar

Projenize npm desteği eklemek için **Düğüm.js geliştirme** iş yükünün ve Düğüm.js çalışma zamanının yüklü olması gerekir. Ayrıntılı adımlar için [bkz.](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json)

> [!NOTE]
> Varolan Node.js projeleri için, projenizde npm'yi etkinleştirmek için **Varolan Düğüm.js kodu** çözüm şablonundan veya [Açık klasör (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) proje türünü kullanın.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Solution Explorer'dan paket yükleme (Node.js)

Node.js projeleri için npm paketlerini yüklemenin en kolay yolu npm paket yükleme penceresinden geçer. Bu pencereye erişmek için projedeki **npm** düğümüne sağ tıklayın ve **Yeni npm Paketleri Yükle'yi**seçin.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Çözüm gezgininden yeni npm paketi yükleme" border="true":::

Bu pencerede bir paket arayabilir, seçenekleri belirtebilir ve yükleyebilirsiniz.

![npm paketini ara](../javascript/media/search-package.png)

* **Bağımlılık türü** - **Standart,** **Geliştirme**ve **İsteğe Bağlı** paketler arasında seçim. Standart, paketin çalışma zamanı bağımlılığı olduğunu belirtirken, Geliştirme paketin yalnızca geliştirme sırasında gerekli olduğunu belirtir.
* **package.json ekle** - Önerilir. Bu yapılandırılabilir seçenek amortismana tabidir.
* **Seçili sürüm** - Yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer npm bağımsız değişkenleri** - Diğer standart npm bağımsız değişkenlerini belirtin. Örneğin, sürüm listesinde bulunmayan belirli `@~0.8` bir sürümü yüklemek gibi bir sürüm değeri girebilirsiniz.

Yüklemenin ilerlemesini **Çıkış** **penceresinden npm** çıkışında görebilirsiniz. Bu işlem biraz zaman alabilir.

![npm çıktı](../javascript/media/npm-output.png)

> [!TIP]
> Arama sorgusunu ilgilendiğiniz kapsamda ön satarak kapsamlı paketleri arayabilirsiniz, örneğin `@types/mocha` mocha için TypeScript tanım dosyalarını aramak için yazın. Ayrıca, TypeScript için tür tanımları yüklerken, npm bağımsız değişken alanına `@ts2.6` ekleyerek hedeflediğiniz TypeScript sürümünü belirtebilirsiniz.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Yüklü paketleri Çözüm Gezgini'nde yönetme (Node.js)

npm paketleri Solution Explorer'da gösterilir. **npm** düğümü altındaki girişler *package.json* dosyasındaki bağımlılıkları taklit ediyor.

![npm paketini ara](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu

* ![Yüklü paket](../javascript/media/installed-npm.png) - Yüklendi ve package.json listelenen
* ![Yabancı paket](../javascript/media/extraneous-npm.png) - Yüklü, ancak açıkça package.json listelenen değil
* ![Eksik paket](../javascript/media/missing-npm.png) - Yüklü değil, ancak package.json listelenen

::: moniker range=">=vs-2019"
Aşağıdaki eylemlerden birini yapmak için **npm** düğümüne sağ tıklayın:

* **Yeni npm Paketleri yükleyin** Yeni paketler yüklemek için UI'yi açar.
* **npm Paketleri yükleyin** *paket.json*listelenen tüm paketleri yüklemek için npm yükleme komutunu çalıştırAr. (Çalışır `npm install`.)
* **npm Paketlerini Güncelleştir** *Paketleri paket.json'da*belirtilen semver aralığına göre en son sürümlere günceller. (Çalışır `npm update --save`.). Semver aralıkları genellikle "~" veya "^" kullanılarak belirtilir. Daha fazla bilgi için, [package.json yapılandırma.](../javascript/configure-packages-with-package-json.md)

Aşağıdaki eylemlerden birini yapmak için bir paket düğümüne sağ tıklayın:

* **npm Paketi(ler) yükleyin** *package.json*listelenen paket sürümünü yüklemek için npm yükleme komutunu çalıştırAr. (Çalışır `npm install`.)
* **güncelleme npm Paketi(ler)** *Paketi paket.json'da*belirtilen semver aralığına göre en son sürüme güncelleştirir. (Çalıştır `npm update --save`.) Semver aralıkları genellikle "~" veya "^" kullanılarak belirtilir.
* **npm Paketi(ler) kaldır** Paketi kaldırır ve *package.json* (Çalışır `npm uninstall --save`.) kaldırır
::: moniker-end
::: moniker range="vs-2017"
Aşağıdaki eylemlerden birini yapmak için bir paket düğümüne veya **npm** düğümüne sağ tıklayın:
* *paket.json'da* listelenen **eksik paketleri yükleyin**
* **npm paketlerini** en son sürüme güncelleştirin
* **Paketi kaldırın** ve *package.json'dan* kaldırın
::: moniker-end

>[!NOTE]
> npm paketleriyle ilgili sorunları çözmeye yardımcı olmak için [sorun giderme](#troubleshooting-npm-packages)konusuna bakın.

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Düğüm.js İnteraktif Pencere'deki .npm komutunu (Node.js) kullanın

NPM `.npm` komutlarını yürütmek için Düğüm.js Interactive Window'daki komutu da kullanabilirsiniz. Pencereyi açmak için Solution Explorer'da projeyi sağ tıklatın ve **Node.js Etkileşimli Pencereaç'ı**seçin.

Pencerede, bir paket yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`

 > [!Tip]
 > Varsayılan olarak, npm projenizin ev dizininde yürütülür. Çözümünüzde birden çok proje varsa, projenin adını veya yolunu parantez içinde belirtin.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projenizde bir package.json dosyası yoksa, `.npm init -y` varsayılan girişleri olan yeni bir package.json dosyası oluşturmak için kullanın.

 ## <a name="aspnet-core-projects"></a>ASP.NET Çekirdek projeleri

ASP.NET Core projeleri gibi projeler için, projenize npm desteğini entegre edebilir ve paketleri yüklemek için npm'yi kullanabilirsiniz.
* [Projeye npm desteği ekleme](#npmAdd)
* [paket.json kullanarak paketleri yükleyin](#npmInstallPackage)

>[!NOTE]
> ASP.NET Core projeleri için, istemci tarafındaki JavaScript ve CSS dosyalarını yüklemek için npm yerine [Kitaplık Yöneticisi](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) veya iplik de kullanabilirsiniz.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Projeye npm desteği ekleme (ASP.NET Core)

Projenizde zaten bir *package.json* dosyası yoksa, projeye bir *package.json* dosyası ekleyerek npm desteğini etkinleştirmek için bir dosya ekleyebilirsiniz.

1. Node.js yüklü yoksa, dış çerçeveler ve kütüphaneler ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yüklemenizi öneririz.

   npm Node.js gerektirir.

1. *package.json* dosyasını eklemek için Solution Explorer'daki projeyi sağ tıklatın ve**Yeni Öğe** **Ekle'yi** > seçin. **npm Yapılandırma Dosyası'nı**seçin, varsayılan adı kullanın ve **Ekle'yi**tıklatın.

   ![Projenize package.json ekle](../javascript/media/npm-add-package-json.png)

   Listelenen npm Configuration File'ı görmüyorsanız, Node.js geliştirme araçları yüklenmez. **Düğüm geliştirme** iş yükünü eklemek için Visual Studio Yükleyicisini kullanabilirsiniz. Sonra önceki adımı tekrarlayın.

1. `dependencies` *package.json'un*bir veya `devDependencies` daha fazla npm paketini ekleyin. Örneğin, dosyaya aşağıdakileri ekleyebilirsiniz:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Dosyayı kaydettiğinizde Visual Studio, Solution Explorer'daki **Bağımlılıklar / npm** düğümü altında paketi ekler. Düğümü görmüyorsanız, **package.json'a** sağ tıklayın ve **Paketleri Geri Yükle'yi**seçin.

>[!NOTE]
> Bazı senaryolarda, Solution Explorer yüklü npm paketleri için doğru durumu göstermeyebilir. Daha fazla bilgi için bkz. [Sorun giderme](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>package.json (ASP.NET Core) kullanarak paketleri yükleyin

NPM dahil projeler için, kullanarak `package.json`npm paketleri yapılandırabilirsiniz. Çözüm Gezgini'ndeki npm düğümüne sağ tıklayın ve **Open package.json'u**seçin.

![npm paketini ara](../javascript/media/npm-add-package.png)

in in *package.json'daki* IntelliSense, bir npm paketinin belirli bir sürümünü seçmenize yardımcı olur.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="npm paket sürümünü seçin" border="true":::

Dosyayı kaydettiğinizde Visual Studio, Solution Explorer'daki **Bağımlılıklar / npm** düğümü altında paketi ekler. Düğümü görmüyorsanız, **package.json'a** sağ tıklayın ve **Paketleri Geri Yükle'yi**seçin.

Bir paketi yüklemek birkaç dakika sürebilir. **Çıkış** penceresinde **npm** çıkışına geçerek paket yüklemesinde ilerlemeyi denetleyin.

![npm çıktı](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Sorun giderme npm paketleri

* npm Node.js gerektirir Eğer Node.js yüklü yoksa, dış çerçeveler ve kütüphaneler ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yüklemenizi öneririz.

* Node.js projeleri için, npm desteği için **Node.js geliştirme** iş yükünün yüklü olması gerekir.

* Bazı senaryolarda, Solution Explorer [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorun nedeniyle yüklü npm paketleri için doğru durumu göstermeyebilir. Örneğin, paket yüklendiğinde yüklü değilmiş gibi görünebilir. Çoğu durumda, *package.json'u*silerek Solution Explorer'ı güncelleştirebilirsiniz, Visual Studio'yu yeniden başlatabilir ve bu makalede daha önce açıklandığı gibi *package.json* dosyasını yeniden ekleyebilirsiniz. Veya paketleri yüklerken, yükleme durumunu doğrulamak için npm Çıktı penceresini kullanabilirsiniz.

* Uygulamanızı yaparken veya TypeScript kodunu aktarırken herhangi bir hata görürseniz, olası bir hata kaynağı olarak npm paket uyumsuzluklarını kontrol edin. Hataları belirlemeye yardımcı olmak için, paketleri yüklerken npm Çıktı penceresini kontrol edin, bu makalede daha önce açıklandığı gibi. Örneğin, bir veya daha fazla npm paket sürümü amortismana uğradıysa ve bir hataya yol açarsa, hataları düzeltmek için daha yeni bir sürüm yüklemeniz gerekebilir. npm paket sürümlerini kontrol etmek için *package.json* kullanma hakkında daha fazla bilgi için [package.json yapılandırmasına](../javascript/configure-packages-with-package-json.md)bakın.

