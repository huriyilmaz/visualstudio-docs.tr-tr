---
title: npm paketlerini yönetme
description: Visual Studio, Node.js paket yöneticisini (NPM) kullanarak paketleri yönetmenize yardımcı olur
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1269049adad3fe2d26caa79721452f7f313e60d5
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739908"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio 'da NPM paketlerini yönetme

NPM, Node.js uygulamalarınızda kullanım için paketleri yüklemenize ve yönetmenize olanak sağlar. Visual Studio, NPM ile etkileşimde bulunmayı kolaylaştırır ve Kullanıcı arabirimi veya doğrudan aracılığıyla NPM komutları verebilir. NPM 'yi tanımıyorsanız ve daha fazla bilgi edinmek istiyorsanız [NPM belgelerine](https://docs.npmjs.com/)gidin.

NPM ile Visual Studio tümleştirmesi, proje türüne göre farklılık fark edilir.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasörü aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> NPM *node_modules* klasörü ve proje kökünde *package.js* bekliyor. Uygulamanızın klasör yapısı farklıysa, Visual Studio 'Yu kullanarak NPM paketlerini yönetmek istiyorsanız klasör yapınızı değiştirmelisiniz.

## <a name="nodejs-projects"></a>Node.js projeleri

Node.js projeleri için aşağıdaki görevleri gerçekleştirebilirsiniz:
* [Paketleri Çözüm Gezgini 'dan yükler](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini yönetin](#solutionExplorer)
* [`.npm`Node.js etkileşimli penceresinde komutunu kullanın](#interactive)

Bu özellikler birlikte çalışarak proje sistemiyle ve projedeki *package.js* dosya ile eşitlenir.

### <a name="prerequisites"></a>Ön koşullar

Projenize NPM desteği eklemek için **Node.js geliştirme** iş yükü ve Node.js çalışma zamanının yüklü olması gerekir. Ayrıntılı adımlar için bkz. [Node.js projesi oluşturma](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> Mevcut Node.js projeleri için, projenizde NPM 'yi etkinleştirmek üzere **mevcut Node.js kodu** çözüm şablonunu veya [açık klasör (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) proje türünü kullanın.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Paketleri Çözüm Gezgini 'den (Node.js) yükler

Node.js projeleri için NPM paketlerini yüklemenin en kolay yolu NPM paketi yükleme penceresidir. Bu pencereye erişmek için, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Çözüm Gezgini 'nden yeni NPM paketi 'ni yükler" border="true":::

Bu pencerede bir paket arayabilir, Seçenekler belirtebilir ve yükleyebilirsiniz.

![NPM paketi ara](../javascript/media/search-package.png)

* **Bağımlılık türü** - **Standart**, **geliştirme**ve **isteğe bağlı** paketler arasında tercih edin. Standart, paketin bir çalışma zamanı bağımlılığı olduğunu belirtir ancak geliştirme sırasında paketin yalnızca geliştirme sırasında gerekli olduğunu belirtir.
* **package.jsiçin önerilen ' ye ekleyin** . Bu yapılandırılabilir seçeneği kullanım dışıdır.
* **Seçili sürüm** -yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer NPM bağımsız değişkenleri** -diğer standart NPM bağımsız değişkenlerini belirtin. Örneğin, `@~0.8` sürümler listesinde kullanılamayan belirli bir sürümü yüklemek için gibi bir sürüm değeri girebilirsiniz.

Yükleme işleminin ilerlemesini **Çıkış** penceresindeki **NPM** çıktısına bakabilirsiniz. Bu işlem biraz zaman alabilir.

![NPM çıkışı](../javascript/media/npm-output.png)

> [!TIP]
> Arama sorgusunu ilgilendiğiniz kapsama göre ön bekleyen paketler için arama yapabilirsiniz, örneğin, `@types/mocha` Mocha Için TypeScript tanım dosyalarını aramak için yazın. Ayrıca, TypeScript için tür tanımlarını yüklerken, `@ts2.6` NPM bağımsız değişkeni alanına ekleyerek hedeflediğiniz TypeScript sürümünü belirtebilirsiniz.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Çözüm Gezgini yüklü paketleri yönetme (Node.js)

NPM paketleri Çözüm Gezgini gösterilmektedir. **NPM** düğümündeki girdiler dosyadaki *package.js* bağımlılıkları taklit ediyor.

![NPM paketi ara](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu

* ![Paket yüklendi](../javascript/media/installed-npm.png) -package.js' de yüklendi ve listede listelendi
* ![Yabancı paket ](../javascript/media/extraneous-npm.png) -yüklü, ancak package.jsüzerinde açıkça listelenmemiş
* ![Paket eksik](../javascript/media/missing-npm.png) -Yüklenmedi, ancak üzerinde package.jslistelendi

::: moniker range=">=vs-2019"
Aşağıdaki eylemlerden birini gerçekleştirmek için **NPM** düğümüne sağ tıklayın:

* **Yeni NPM paketleri 'Ni yükler** Yeni paketleri yüklemek için Kullanıcı arabirimini açar.
* **NPM paketlerini yükler** * Üzerindepackage.js*listelenen tüm paketleri yüklemek için NPM install komutunu çalıştırır. (Çalıştırır `npm install` .)
* **NPM paketlerini Güncelleştir** , Paketi en son sürümlere, *package.jsüzerinde*belirtilen anlamsal sürüm oluşturma (semver) aralığına göre güncelleştirir. (Çalıştırır `npm update --save` .). Semver aralıkları genellikle "~" veya "^" kullanılarak belirtilir. Daha fazla bilgi için, [ yapılandırmapackage.js](../javascript/configure-packages-with-package-json.md).

Aşağıdaki eylemlerden birini gerçekleştirmek için bir paket düğümüne sağ tıklayın:

* **NPM paketlerini yükler** *package.js*' de listelenen paket sürümünü yüklemek için NPM install komutunu çalıştırır. (Çalıştırır `npm install` .)
* **NPM paketlerini Güncelleştir** *package.json*' da belirtilen semver aralığına göre paketi en son sürüme güncelleştirir. (Çalıştır `npm update --save` .) Semver aralıkları genellikle "~" veya "^" kullanılarak belirtilir.
* **NPM paketlerini kaldır** Paketi kaldırır ve * üzerindepackage.js* kaldırır (çalışır `npm uninstall --save` .)
::: moniker-end
::: moniker range="vs-2017"
Aşağıdaki eylemlerden birini gerçekleştirmek için bir paket düğümüne veya **NPM** düğümüne sağ tıklayın:
* *Üzerindepackage.js* listelenen **eksik paketleri yükler**
* **NPM paketlerini** en son sürüme Güncelleştir
* **Bir paketi kaldır** ve *üzerindepackage.js* kaldır
::: moniker-end

>[!NOTE]
> NPM paketleriyle ilgili sorunları çözmeye yardımcı olması için bkz. [sorun giderme](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Node.js etkileşimli penceresinde. NPM komutunu kullanın (Node.js)

Ayrıca, `.npm` NPM komutlarını yürütmek için Node.js etkileşimli penceresindeki komutunu da kullanabilirsiniz. Pencereyi açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Node.js etkileşimli pencere aç**' ı seçin.

Penceresinde, bir paket yüklemek için aşağıdaki gibi komutları kullanabilirsiniz:

`.npm install azure@4.2.3`

 > [!Tip]
 > Varsayılan olarak NPM, projenizin giriş dizininde yürütülür. Çözümünüzde birden çok projeniz varsa, köşeli ayraçlar içinde projenin adını veya yolunu belirtin.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Projeniz dosya package.jsiçermiyorsa, `.npm init -y` dosya üzerinde varsayılan girdilerle yeni bir package.jsoluşturmak için kullanın.

 ## <a name="aspnet-core-projects"></a>ASP.NET Core projeleri

ASP.NET Core projeleri gibi projeler için, projenizde NPM desteğini tümleştirebilir ve NPM kullanarak paketleri yükleyebilirsiniz.
* [Bir projeye NPM desteği ekleme](#npmAdd)
* [package.jskullanarak paket yüklemesi](#npmInstallPackage)

>[!NOTE]
> ASP.NET Core projeleri için, istemci tarafı JavaScript ve CSS dosyalarını yüklemek üzere NPM yerine [Kitaplık Yöneticisi](/aspnet/core/client-side/libman/?view=aspnetcore-3.1) 'ni veya Yarn 'yi de kullanabilirsiniz.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Bir projeye NPM desteği ekleme (ASP.NET Core)

Projeniz zaten bir *package.js* dosyası içermiyorsa, projeye dosya *package.js* ekleyerek NPM desteğini etkinleştirmek üzere bir tane ekleyebilirsiniz.

1. Yüklü Node.js yoksa, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

   NPM Node.js gerektiriyor.

1. Dosyaya *package.js* eklemek için Çözüm Gezgini projeye sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin. **NPM yapılandırma dosyasını**seçin, varsayılan adı kullanın ve **Ekle**' ye tıklayın.

   ![Projenize package.jsekleyin](../javascript/media/npm-add-package-json.png)

   NPM yapılandırma dosyasını listede görmüyorsanız, Node.js geliştirme araçları yüklenmez. **Node.js geliştirme** iş yükünü eklemek için Visual Studio yükleyicisi kullanabilirsiniz. Ardından önceki adımı yineleyin.

1. `dependencies` `devDependencies` *package.jsüzerindeki*veya bölümüne bir veya daha fazla NPM paketi ekleyin. Örneğin, aşağıdakileri dosyasına ekleyebilirsiniz:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Dosyayı kaydettiğinizde, Visual Studio Paketi Çözüm Gezgini içindeki **Dependencies/NPM** düğümüne ekler. Düğümü görmüyorsanız, ** üzerindepackage.js** sağ tıklayın ve **paketleri geri yükle**' yi seçin.

>[!NOTE]
> Bazı senaryolarda, yüklü NPM paketleri için doğru durumu gösteremeyebilir Çözüm Gezgini. Daha fazla bilgi için bkz. [Sorun giderme](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>package.js(ASP.NET Core) kullanarak paket yükler

NPM 'nin dahil olduğu projeler için kullanarak NPM paketlerini yapılandırabilirsiniz `package.json` . Çözüm Gezgini NPM düğümüne sağ tıklayın ve **package.jsaç**' ı seçin.

![NPM paketi ara](../javascript/media/npm-add-package.png)

*Üzerindepackage.js* IntelliSense, NPM paketinin belirli bir sürümünü seçmenize yardımcı olur.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="NPM paket sürümünü seçin" border="true":::

Dosyayı kaydettiğinizde, Visual Studio Paketi Çözüm Gezgini içindeki **Dependencies/NPM** düğümüne ekler. Düğümü görmüyorsanız, ** üzerindepackage.js** sağ tıklayın ve **paketleri geri yükle**' yi seçin.

Bir paketin yüklenmesi birkaç dakika sürebilir. **Çıkış** penceresindeki **NPM** çıktısına geçerek paket yüklemesinde ilerleme durumunu denetleyin.

![NPM çıkışı](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>NPM paketlerinde sorun giderme

* NPM Node.js için Node.js yüklü değilse, dışarıdaki çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

* Node.js projelerinde, NPM desteği için **Node.js geliştirme** iş yükünün yüklü olması gerekir.

* Bazı senaryolarda, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorundan dolayı yüklü NPM paketleri için doğru durumu gösteremeyebilir Çözüm Gezgini. Örneğin, paket yüklendiğinde yüklü değil olarak görünebilir. Çoğu durumda, *package.js*Çözüm Gezgini güncelleştirebilir, Visual Studio 'yu yeniden başlatarak ve bu makalede daha önce anlatıldığı gibi *package.js* dosyaya yeniden ekleyebilirsiniz. Ya da paketleri yüklerken, yükleme durumunu doğrulamak için NPM çıkış penceresini kullanabilirsiniz.

* Uygulamanızı veya transpiling TypeScript kodunuzu oluştururken herhangi bir hata görürseniz olası hata kaynakları olarak NPM paket uyumsuzluklarını denetleyin. Hataları belirlemede yardımcı olması için, bu makalede daha önce açıklandığı gibi paketleri yüklerken NPM çıkış penceresini kontrol edin. Örneğin, bir veya daha fazla NPM paket sürümü kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için * üzerindepackage.js* kullanma hakkında bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).
