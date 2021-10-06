---
title: npm paketlerini yönetme
description: Visual Studio, Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur
ms.custom: seodec18
ms.date: 10/1/2021
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
ms.openlocfilehash: 46b5284f91fdce4b073f8ac7b8e78569b353452c
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129560925"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio'de npm paketlerini yönetme

npm hem uygulama hem de uygulama yönetimi uygulamalarında kullanmak üzere paketleri Node.js ASP.NET Core sağlar. Visual Studio npm ile etkileşim kurmayı ve kullanıcı arabirimi aracılığıyla veya doğrudan npm komutları çıkararak bunu kolaylaştırır. npm hakkında bilginiz yoksa ve daha fazla bilgi edinmek için [npm belgelerine gidin.](https://docs.npmjs.com/)

Visual Studio npm tümleştirmesi proje türünüze bağlı olarak farklıdır.
::: moniker range=">=vs-2022"
* [CLI tabanlı projeler (.esproj)](#cli-based-project-esproj)
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasör aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

::: moniker range="<=vs-2019"
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasör aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

> [!Important]
> npm proje *kökünde node_modules* *ve package.json* klasörünü bekler. Uygulamanın klasör yapısı farklı ise, npm paketlerini Visual Studio kullanarak yönetmek için klasör yapınızı Visual Studio.

::: moniker range=">=vs-2022"
## <a name="cli-based-project-esproj"></a>CLI tabanlı proje (.esproj)

Visual Studio 2022 Preview 4'ten başlayarak, npm paket yöneticisi CLI tabanlı projelerde kullanılabilir, bu nedenle artık ASP.NET Core projeleri için NuGet paketlerini indirmeye benzer şekilde npm modüllerini indirebilirsiniz. Ardından *package.json kullanarak paketleri* değiştirebilir ve silebilirsiniz.

Paket yöneticisini açmak için Çözüm Gezgini projenizin **npm düğümüne** sağ tıklayın.

:::image type="content" source="../javascript/media/vs-2022/npm-packages-open-manager-esproj.png" alt-text="Paket yöneticisini Çözüm Gezgini" border="true":::

Ardından, npm paketlerini arayabilir, birini seçin ve Paketi Yükle'yi **seçerek yükleyin.** 

:::image type="content" source="../javascript/media/vs-2022/npm-packages-install-esproj.png" alt-text="esproj için yeni npm paketi yükleme" border="true":::
::: moniker-end

## <a name="nodejs-projects"></a>Node.js projeleri

Bu Node.js için aşağıdaki görevleri gerçekleştirebilirsiniz:
* [Paketlerden Çözüm Gezgini](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini](#solutionExplorer)
* [Node.js `.npm` Interactive Window'da komutunu kullanın](#interactive)

Bu özellikler birlikte çalışır ve proje sistemiyle ve projede *package.json* dosyasıyla eşitlenir.

### <a name="prerequisites"></a>Önkoşullar

Projenize npm **Node.js için** Node.js iş yükünün ve Node.js çalışma zamanının yüklü olması gerekir. Ayrıntılı adımlar için [bkz. Bir Node.js oluşturma.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json)

> [!NOTE]
> Mevcut Node.js projelerinde npm'yi **etkinleştirmek için Mevcut Node.js** kod çözümünden şablonunu veya Klasör aç [(Node.js) proje](../javascript/develop-javascript-code-without-solutions-projects.md) türünü kullanın.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Çözüm Gezgini(Node.js) paketi yükleme

Daha Node.js için npm paketlerini yüklemenin en kolay yolu npm paketi yükleme penceresidir. Bu pencereye erişmek için projedeki **npm düğümüne** sağ tıklayın ve Yeni **npm Paketleri Yükle'yi seçin.**

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Node.jsiçin yeni npm paketi Node.js" border="true":::

Bu pencerede bir paket arayabilir, seçenekleri belirtebilirsiniz ve yükleyebilirsiniz.

![Yeni npm Paketlerini Yükle iletişim kutusunun ekran görüntüsü. Azure 2.2.1-preview paketi seçilidir ve bu paketin ayrıntıları ve seçenekleri gösterilir.](../javascript/media/search-package.png)

* **Bağımlılık türü -** Standart, **Geliştirme** ve **İsteğe Bağlı** paketler arasında **seçim.** Standart, paketin bir çalışma zamanı bağımlılığı olduğunu belirtirken Geliştirme, paketin yalnızca geliştirme sırasında gerekli olduğunu belirtir.
* **package.json'a ekle** - Önerilir. Bu yapılandırılabilir seçenek kullanım dışıdır.
* **Seçili sürüm** - Yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer npm bağımsız değişkenleri** - Diğer standart npm bağımsız değişkenlerini belirtin. Örneğin, sürüm listesinde mevcut olan belirli bir `@~0.8` sürümü yüklemek için gibi bir sürüm değeri girebilirsiniz.

Yüklemenin ilerlemesini Çıkış penceresinde **npm** çıkışında  görebilirsiniz (pencereyi açmak için Çıkışı Görüntüle'yi seçin veya  >   Ctrl Alt O   +  **tuşlarına**  +  **basın).** Bu işlem biraz zaman alabilir.

![npm çıktısı](../javascript/media/npm-output.png)

> [!TIP]
> Arama sorgusunu ilgilendiğin kapsamla (örneğin, mocha için TypeScript tanım dosyalarını aramak için) yazarak kapsamlı paketleri `@types/mocha` arayabilirsiniz. Ayrıca, TypeScript için tür tanımlarını yüklerken npm bağımsız değişken alanına ekleyerek hedefle istediğiniz TypeScript `@ts2.6` sürümünü belirtebilirsiniz.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Çözüm Gezgini'de yüklü paketleri yönetme (Node.js)

npm paketleri, Çözüm Gezgini. npm düğümü **altındaki girdiler** *package.json* dosyasındaki bağımlılıkları taklit ediyor.

![npm paketlerinin yükleme Çözüm Gezgini gösteren npm düğümünün ekran görüntüsü.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu

* ![Yüklü paket](../javascript/media/installed-npm.png) - package.json'da yüklü ve listelenmiş
* ![Fazlalık paket ](../javascript/media/extraneous-npm.png) - Package.json'da yüklü ancak açıkça listelenmiyor
* ![Eksik paket](../javascript/media/missing-npm.png) - Yüklü değil, ancak package.json içinde listelenmiş

::: moniker range=">=vs-2019"
Aşağıdaki eylemlerden birini yapmak için **npm** düğümüne sağ tıklayın:

* **Yeni npm Paketleri Yükleme** Yeni paketleri yüklemek için kullanıcı arabirimini açar.
* **npm Paketlerini yükleme** *package.json* içinde listelenen tüm paketleri yüklemek için npm install komutunu çalıştırır. `npm install`(Çalıştırır.)
* **npm Paketlerini güncelleştirme** Package.json içinde belirtilen semantik sürüm (SemVer) aralığına göre paketleri *en son sürümlere göre günceller.* `npm update --save`(çalıştırır.). SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir. Daha fazla bilgi için [package.json yapılandırması.](../javascript/configure-packages-with-package-json.md)

Aşağıdaki eylemlerden birini yapmak için paket düğümüne sağ tıklayın:

* **npm Paketlerini yükleme** *package.json* içinde listelenen paket sürümünü yüklemek için npm install komutunu çalıştırır. `npm install`(Çalıştırır.)
* **npm Paketlerini güncelleştirme** package.json içinde belirtilen SemVer aralığına göre paketi en son *sürüme günceller.* `npm update --save`(Çalıştırın.) SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir.
* **npm Paketlerini kaldırma** Paketi kaldırır ve *package.json'dan kaldırır* (Çalıştırır.) `npm uninstall --save`
::: moniker-end
::: moniker range="vs-2017"
Aşağıdaki eylemlerden birini yapmak için bir **paket düğümüne** veya npm düğümüne sağ tıklayın:
*  *package.json* içinde listelenen eksik paketleri yükleme
* **npm paketlerini en son** sürüme güncelleştirme
* **Paketi kaldırma ve** *package.json'dan kaldırma*
::: moniker-end

>[!NOTE]
> npm paketleriyle ilgili sorunları çözme konusunda yardım için bkz. Sorun [giderme.](#troubleshooting-npm-packages)

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Node.js Interactive Window 'da .npm komutunu kullanın (Node.js)

Npm komutlarını yürütmek `.npm` için etkileşimli Node.js penceresinde komutunu da kullanabilirsiniz. Pencereyi açmak için, Çözüm Gezgini'de projeye sağ tıklayın ve Etkileşimli **Node.js** Aç'ı seçin **(veya Ctrl**  +  **K**, **N tuşlarına basın).**

Pencerede, bir paket yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`

 > [!Tip]
 > Varsayılan olarak, npm projenizin giriş dizininde yürütülür. Çözümde birden çok projeniz varsa köşeli ayraç içinde projenin adını veya yolunu belirtin.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projeniz package.json dosyası içeriyorsa, varsayılan girişlere sahip yeni `.npm init -y` bir package.json dosyası oluşturmak için kullanın.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core projeleri

Yönetim projeleri gibi ASP.NET Core projeniz için npm desteğini tümleştirebilirsiniz ve paketleri yüklemek için npm kullanabilirsiniz.
* [Projeye npm desteği ekleme](#npmAdd)
* [package.json kullanarak paketleri yükleme](#npmInstallPackage)

>[!NOTE]
> Daha ASP.NET Core, istemci tarafı JavaScript ve CSS dosyalarını yüklemek için npm yerine [Kitaplık](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) Yöneticisi'ni veya yarn'i de kullanabilirsiniz.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Projeye npm desteği ekleme (ASP.NET Core)

Projeniz zaten *package.json* dosyası eklemezse, projeye *package.json* dosyası ekleyerek npm desteğini etkinleştirmek için bir dosya eklediniz.

1. Yüklü bir Node.js, dış çerçeveler ve kitaplıklarla en iyi uyumluluk [ içinNode.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yüklemenizi öneririz.

   npm için Node.js.

1. *package.json dosyasını eklemek* için, dosyanın içinde projeye sağ tıklayın Çözüm Gezgini Öğe Ekle'yi  >   seçin (veya Ctrl SHIFT A   +    +  **tuşlarına basın).** **npm Yapılandırma Dosyası'yı seçin,** varsayılan adı kullanın ve Ekle'ye **tıklayın.**

   ![Projenize package.json ekleme](../javascript/media/npm-add-package-json.png)

   NPM yapılandırma dosyasını listede görmüyorsanız, Node.js geliştirme araçları yüklenmez. **Node.js geliştirme** iş yükünü eklemek için Visual Studio Yükleyicisi kullanabilirsiniz. Ardından önceki adımı yineleyin.

1. `dependencies` `devDependencies` *Package. JSON*' nin veya bölümüne bir veya daha fazla NPM paketi ekleyin. Örneğin, aşağıdakileri dosyasına ekleyebilirsiniz:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

dosyayı kaydettiğinizde Visual Studio, paketi Çözüm Gezgini içindeki **Dependencies/npm** düğümüne ekler. Düğümü görmüyorsanız **Package. JSON** öğesine sağ tıklayın ve **paketleri geri yükle**' yi seçin.

>[!NOTE]
> Bazı senaryolarda, yüklü NPM paketleri için doğru durumu gösteremeyebilir Çözüm Gezgini. Daha fazla bilgi için bkz. [Sorun giderme](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Package. JSON (ASP.NET Core) kullanarak paket yükler

NPM 'nin dahil olduğu projeler için kullanarak NPM paketlerini yapılandırabilirsiniz `package.json` . Çözüm Gezgini NPM düğümüne sağ tıklayın ve **Package. JSON öğesini aç**' ı seçin.

![NPM düğümü seçili Çözüm Gezgini ekran görüntüsü. Sağ tıklama bağlam menüsü açık ve paket aç. JSON seçilidir.](../javascript/media/npm-add-package.png)

*Package. JSON* içinde IntelliSense, NPM paketinin belirli bir sürümünü seçmenize yardımcı olur.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="NPM paket sürümünü seçin" border="true":::

dosyayı kaydettiğinizde Visual Studio, paketi Çözüm Gezgini içindeki **Dependencies/npm** düğümüne ekler. Düğümü görmüyorsanız **Package. JSON** öğesine sağ tıklayın ve **paketleri geri yükle**' yi seçin.

Bir paketin yüklenmesi birkaç dakika sürebilir. **Çıkış** penceresindeki **NPM** çıktısına geçerek paket yüklemesinde ilerleme durumunu denetleyin.

![NPM çıkışı](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>NPM paketlerinde sorun giderme

* NPM Node.js için Node.js yüklü değilse, dışarıdaki çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

* Node.js projelerinde, NPM desteği için **Node.js geliştirme** iş yükünün yüklü olması gerekir.

* Bazı senaryolarda, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorundan dolayı yüklü NPM paketleri için doğru durumu gösteremeyebilir Çözüm Gezgini. Örneğin, paket yüklendiğinde yüklü değil olarak görünebilir. çoğu durumda, bu makalenin önceki kısımlarında açıklandığı gibi package *. json*' ı silerek Çözüm Gezgini güncelleştirebilir, Visual Studio yeniden başlatarak ve *package. json* dosyasını yeniden ekleyebilirsiniz. Ya da paketleri yüklerken, yükleme durumunu doğrulamak için NPM çıkış penceresini kullanabilirsiniz.

* bazı ASP.NET Core senaryolarda, projeyi derledikten sonra Çözüm Gezgini npm düğümü görünür olmayabilir. Düğümü yeniden görünür hale getirmek için proje düğümüne sağ tıklayın ve **Project kaldır** ' ı seçin. Ardından proje düğümüne sağ tıklayın ve **Project yeniden yükle**' yi seçin.

* Uygulamanızı veya transpiling TypeScript kodunuzu oluştururken herhangi bir hata görürseniz olası hata kaynakları olarak NPM paket uyumsuzluklarını denetleyin. Hataları belirlemede yardımcı olması için, bu makalede daha önce açıklandığı gibi paketleri yüklerken NPM çıkış penceresini kontrol edin. Örneğin, bir veya daha fazla NPM paket sürümü kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için *Package. JSON* kullanma hakkında daha fazla bilgi için bkz. [Package. JSON Configuration](../javascript/configure-packages-with-package-json.md).
