---
title: npm paketlerini yönetme
description: Visual Studio, Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur.
ms.date: 12/20/2021
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
ms.openlocfilehash: 5f6c21f0ec4d972bf09c9c291e128c9517dbdfc1
ms.sourcegitcommit: aa5e295b9e3fc8e287f3ae2b6224f41e7d4ee833
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2021
ms.locfileid: "135437279"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio NPM paketlerini yönetme

npm, hem Node.js hem de ASP.NET Core uygulamalarda kullanım için paketleri yüklemenize ve yönetmenize olanak sağlar. Visual Studio, npm ile etkileşimde bulunmayı ve kullanıcı arabirimi aracılığıyla npm komutları vermesini kolaylaştırır. NPM 'yi tanımıyorsanız ve daha fazla bilgi edinmek istiyorsanız [NPM belgelerine](https://docs.npmjs.com/)gidin.

npm ile tümleştirme Visual Studio proje türüne bağlı olarak farklılık açmış.
::: moniker range=">=vs-2022"
* [CLı tabanlı projeler (. esproj)](#cli-based-project-esproj)
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasörü aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

::: moniker range="<=vs-2019"
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasörü aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)
::: moniker-end

> [!Important]
> NPM, proje kökünde *node_modules* klasörü ve *Package. JSON* bekliyor. Uygulamanızın klasör yapısı farklıysa, Visual Studio kullanarak NPM paketlerini yönetmek istiyorsanız klasör yapınızı değiştirmelisiniz.

::: moniker range=">=vs-2022"
## <a name="cli-based-project-esproj"></a>CLı tabanlı proje (. esproj)

Visual Studio 2022 Preview 4 ' te başlayarak, npm paket yöneticisi clı tabanlı projeler için kullanılabilir, bu sayede, artık npm modüllerini ASP.NET Core projelerine yönelik NuGet paketlerini karşıdan yükleme yöntemine benzer şekilde indirebilirsiniz. Ardından *paket. JSON* ' u kullanarak paketleri değiştirebilir ve silebilirsiniz.

Paket Yöneticisi 'ni Çözüm Gezgini açmak için, projenizdeki **NPM** düğümüne sağ tıklayın.

:::image type="content" source="../javascript/media/vs-2022/npm-packages-open-manager-esproj.png" alt-text="Çözüm Gezgini Paket Yöneticisi 'ni açın" border="true":::

Ardından, NPM paketlerini arayabilir, bir tane seçebilir ve **paketi Kur**' u seçerek yükleyebilirsiniz. 

:::image type="content" source="../javascript/media/vs-2022/npm-packages-install-esproj.png" alt-text="Esproj için yeni NPM paketi 'ni yükler" border="true":::
::: moniker-end

## <a name="nodejs-projects"></a>Node.js projeleri

Node.js projeler (. njsproj) için aşağıdaki görevleri gerçekleştirebilirsiniz:

* [Paketleri Çözüm Gezgini 'dan yükler](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini yönetin](#solutionExplorer)
* [`.npm`Node.js etkileşimli penceresinde komutunu kullanın](#interactive)

Bu özellikler birlikte çalışarak proje sistemiyle ve projedeki *Package. JSON* dosyasıyla eşitlenir.

### <a name="prerequisites"></a>Önkoşullar

Projenize NPM desteği eklemek için **Node.js geliştirme** iş yükü ve Node.js çalışma zamanının yüklü olması gerekir. Ayrıntılı adımlar için bkz. [Node.js projesi oluşturma](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Mevcut Node.js projeleri için, projenizde NPM 'yi etkinleştirmek üzere **mevcut Node.js kodu** çözüm şablonunu veya [açık klasör (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) proje türünü kullanın.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Paketleri Çözüm Gezgini 'den (Node.js) yükler

Node.js projeleri için NPM paketlerini yüklemenin en kolay yolu NPM paketi yükleme penceresidir. Bu pencereye erişmek için, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Node.jsiçin yeni NPM paketi yüklensin " border="true":::

Bu pencerede bir paket arayabilir, Seçenekler belirtebilir ve yükleyebilirsiniz.

![Yeni NPM paketleri Kur iletişim kutusunun ekran görüntüsü.](../javascript/media/search-package.png)

* **Bağımlılık türü** - **Standart**, **geliştirme** ve **isteğe bağlı** paketler arasında tercih edin. Standart, paketin bir çalışma zamanı bağımlılığı olduğunu belirtir ancak geliştirme sırasında paketin yalnızca geliştirme sırasında gerekli olduğunu belirtir.
* **Package. JSON öğesine ekleyin** -önerilir. Bu yapılandırılabilir seçeneği kullanım dışıdır.
* **Seçili sürüm** -yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer NPM bağımsız değişkenleri** -diğer standart NPM bağımsız değişkenlerini belirtin. Örneğin, `@~0.8` sürümler listesinde kullanılamayan belirli bir sürümü yüklemek için gibi bir sürüm değeri girebilirsiniz.

Yükleme işleminin ilerleme durumunu **Çıkış** penceresinde görebilirsiniz (pencereyi açmak  için çıktıyı **görüntüle**' yi seçin  >   veya **CTRL**  +  **alt**  +  **O** tuşlarına basın). Bu işlem biraz zaman alabilir.

![NPM çıkışı](../javascript/media/npm-output.png)

> [!TIP]
> Arama sorgusunu ilgilendiğiniz kapsama göre ön bekleyen paketler için arama yapabilirsiniz, örneğin, `@types/mocha` Mocha Için TypeScript tanım dosyalarını aramak için yazın. Ayrıca, TypeScript için tür tanımlarını yüklerken, `@ts2.6` NPM bağımsız değişkeni alanına ekleyerek hedeflediğiniz TypeScript sürümünü belirtebilirsiniz.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Çözüm Gezgini yüklü paketleri yönetme (Node.js)

NPM paketleri Çözüm Gezgini gösterilmektedir. **NPM** düğümündeki girişler *Package. JSON* dosyasındaki bağımlılıkları taklit ediyor.

![NPM paketlerinin yükleme durumunu gösteren Çözüm Gezgini NPM düğümünün ekran görüntüsü.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu

* ![Paket yüklendi](../javascript/media/installed-npm.png) -Package. JSON içinde yüklendi ve listelendi
* ![Yabancı paket ](../javascript/media/extraneous-npm.png) -yüklü, ancak Package. JSON içinde açıkça listelenmemiş
* ![Paket eksik](../javascript/media/missing-npm.png) -Yüklenmedi, ancak Package. JSON içinde listelendi

::: moniker range=">=vs-2019"
Aşağıdaki eylemlerden birini gerçekleştirmek için **NPM** düğümüne sağ tıklayın:

* **Yeni NPM paketleri 'Ni yükler** Yeni paketleri yüklemek için Kullanıcı arabirimini açar.
* **NPM paketlerini yükler** *Package. JSON*' da listelenen tüm paketleri yüklemek için NPM install komutunu çalıştırır. (Çalıştırır `npm install` .)
* **NPM paketlerini Güncelleştir** Paketleri *Package. JSON* içinde belirtilen anlam sürümü oluşturma (semver) aralığına göre en son sürümlere güncelleştirir. (Çalıştırır `npm update --save` .). SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir. Daha fazla bilgi için [Package. JSON yapılandırması](../javascript/configure-packages-with-package-json.md).

Aşağıdaki eylemlerden birini gerçekleştirmek için bir paket düğümüne sağ tıklayın:

* **NPM paketlerini yükler** *Package. JSON*' da listelenen paket sürümünü yüklemek için NPM install komutunu çalıştırır. (Çalıştırır `npm install` .)
* **NPM paketlerini Güncelleştir** Paketi *Package. JSON*' da belirtilen semver aralığına göre en son sürüme güncelleştirir. (Çalıştır `npm update --save` .) SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir.
* **NPM paketlerini kaldır** Paketi kaldırır ve *Package. JSON* ' dan kaldırır (çalıştırır `npm uninstall --save` .)
::: moniker-end
::: moniker range="vs-2017"
Aşağıdaki eylemlerden birini gerçekleştirmek için bir paket düğümüne veya **NPM** düğümüne sağ tıklayın:
* *Package. JSON* içinde listelenen **eksik paketleri yükler**
* **NPM paketlerini** en son sürüme Güncelleştir
* **Bir paketi kaldırın** ve *Package. JSON* öğesinden kaldırın
::: moniker-end

>[!NOTE]
> NPM paketleriyle ilgili sorunları çözmeye yardımcı olması için bkz. [sorun giderme](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Node.js etkileşimli penceresinde. NPM komutunu kullanın (Node.js)

Ayrıca, `.npm` NPM komutlarını yürütmek için Node.js etkileşimli penceresindeki komutunu da kullanabilirsiniz. Pencereyi açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Node.js etkileşimli pencereyi aç** ' ı (veya **CTRL**  +  **K**, **N**) seçin.

Penceresinde, bir paket yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`

 > [!Tip]
 > Varsayılan olarak NPM, projenizin giriş dizininde yürütülür. Çözümünüzde birden çok projeniz varsa, köşeli ayraçlar içinde projenin adını veya yolunu belirtin.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projeniz bir Package. JSON dosyası içermiyorsa, `.npm init -y` varsayılan girdilerle yeni bir Package. JSON dosyası oluşturmak için kullanın.

## <a name="aspnet-core-projects"></a>ASP.NET Core projeleri

ASP.NET Core projeleri gibi projeler için, projenizde npm desteğini tümleştirebilir ve npm kullanarak paketleri yükleyebilirsiniz.
* [Bir projeye NPM desteği ekleme](#npmAdd)
* [Package. JSON kullanarak paket yükler](#npmInstallPackage)

>[!NOTE]
> ASP.NET Core projeleri için, istemci tarafı JavaScript ve CSS dosyalarını yüklemek üzere npm yerine [kitaplık yöneticisi](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) 'ni veya yarn 'yi de kullanabilirsiniz.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Bir projeye NPM desteği ekleme (ASP.NET Core)

Projeniz zaten bir *Package. JSON* dosyası içermiyorsa, projeye bir *Package. JSON* dosyası ekleyerek NPM desteğini etkinleştirmek üzere bir tane ekleyebilirsiniz.

1. Yüklü Node.js yoksa, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

   NPM Node.js gerektiriyor.

1. *Package. JSON* dosyasını eklemek için Çözüm Gezgini ' de projeye sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin (veya **CTRL**  +  **+ SHIFT** tuşuna basın  +  ). NPM dosyasını bulmak için arama kutusunu kullanın, **NPM yapılandırma dosyasını** seçin, varsayılan adı kullanın ve **Ekle**' ye tıklayın.

   ![Projenize Package. JSON ekleyin](../javascript/media/npm-add-package-json.png)

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

NPM 'nin dahil olduğu projeler için kullanarak NPM paketlerini yapılandırabilirsiniz `package.json` . Doğrudan açın `package.json` ya da Çözüm Gezgini NPM düğümüne sağ tıklayıp **Package. JSON öğesini aç**' ı seçin.

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
