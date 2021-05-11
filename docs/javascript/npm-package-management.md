---
title: npm paketlerini yönetme
description: Visual Studio, Node.js paket yöneticisini (npm) kullanarak paketleri yönetmenize yardımcı olur
ms.custom: seodec18
ms.date: 02/23/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2fcf1bd9e9ef5c3ff0663cf12684e6e638d1e5e4
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729292"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio'de npm paketlerini yönetme

npm, uygulama uygulamalarınızı yönetmek için paketleri yüklemenize ve yönetmenize Node.js sağlar. Visual Studio npm ile etkileşim kurmayı ve kullanıcı arabirimi aracılığıyla veya doğrudan npm komutları çıkararak bunu kolaylaştırır. npm hakkında bilginiz yoksa ve daha fazla bilgi edinmek için [npm belgelerine gidin.](https://docs.npmjs.com/)

Visual Studio npm tümleştirmesi proje türünüze bağlı olarak farklıdır.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Klasör aç (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm, *node_modules* klasörünü bekler *package.jskök* dizinde görünür. Uygulamanın klasör yapısı farklı ise, npm paketlerini farklı bir klasör kullanarak yönetmek için klasör yapınızı Visual Studio.

## <a name="nodejs-projects"></a>Node.js projeleri

Bu Node.js için aşağıdaki görevleri gerçekleştirebilirsiniz:
* [Paketlerden Çözüm Gezgini](#npmInstallWindow)
* [Yüklü paketleri Çözüm Gezgini](#solutionExplorer)
* [Node.js `.npm` Interactive Window'da komutunu kullanın](#interactive)

Bu özellikler birlikte çalışır ve proje sistemiyle eşitlenir ve *package.jsdosyada* yer alan dosyayla eşitlenir.

### <a name="prerequisites"></a>Önkoşullar

Projenize npm **Node.js eklemek** için Node.js geliştirme iş yükünün ve Node.js çalışma zamanının yüklü olması gerekir. Ayrıntılı adımlar için [bkz. Bir Node.js oluşturma.](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json)

> [!NOTE]
> Mevcut Node.js projelerinde npm'yi **etkinleştirmek için Mevcut Node.js** kod çözümünden şablonunu veya Klasör aç [(Node.js) proje](../javascript/develop-javascript-code-without-solutions-projects.md) türünü kullanın.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Paket yükleme Çözüm Gezgini (Node.js)

Daha Node.js için npm paketlerini yüklemenin en kolay yolu npm paketi yükleme penceresidir. Bu pencereye erişmek için, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Çözüm Gezgini 'nden yeni NPM paketi 'ni yükler" border="true":::

Bu pencerede bir paket arayabilir, Seçenekler belirtebilir ve yükleyebilirsiniz.

![Yeni NPM paketleri Kur iletişim kutusunun ekran görüntüsü. Azure 2.2.1-Preview paketi seçilidir ve bu pakete ilişkin ayrıntılar ve seçenekler gösterilir.](../javascript/media/search-package.png)

* **Bağımlılık türü** - **Standart**, **geliştirme** ve **isteğe bağlı** paketler arasında tercih edin. Standart, paketin bir çalışma zamanı bağımlılığı olduğunu belirtir ancak geliştirme sırasında paketin yalnızca geliştirme sırasında gerekli olduğunu belirtir.
* **package.jsiçin önerilen ' ye ekleyin** . Bu yapılandırılabilir seçeneği kullanım dışıdır.
* **Seçili sürüm** -yüklemek istediğiniz paketin sürümünü seçin.
* **Diğer NPM bağımsız değişkenleri** -diğer standart NPM bağımsız değişkenlerini belirtin. Örneğin, `@~0.8` sürümler listesinde kullanılamayan belirli bir sürümü yüklemek için gibi bir sürüm değeri girebilirsiniz.

Yükleme işleminin ilerleme durumunu **Çıkış** penceresinde görebilirsiniz (pencereyi açmak  için çıktıyı **görüntüle**' yi seçin  >   veya **CTRL**  +  **alt**  +  **O** tuşlarına basın). Bu işlem biraz zaman alabilir.

![NPM çıkışı](../javascript/media/npm-output.png)

> [!TIP]
> Arama sorgusunu ilgilendiğiniz kapsama göre ön bekleyen paketler için arama yapabilirsiniz, örneğin, `@types/mocha` Mocha Için TypeScript tanım dosyalarını aramak için yazın. Ayrıca, TypeScript için tür tanımlarını yüklerken, `@ts2.6` NPM bağımsız değişkeni alanına ekleyerek hedeflediğiniz TypeScript sürümünü belirtebilirsiniz.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Çözüm Gezgini yüklü paketleri yönetme (Node.js)

NPM paketleri Çözüm Gezgini gösterilmektedir. **NPM** düğümündeki girdiler dosyadaki *package.js* bağımlılıkları taklit ediyor.

![NPM paketlerinin yükleme durumunu gösteren Çözüm Gezgini NPM düğümünün ekran görüntüsü.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Paket durumu

* ![Yüklü paket](../javascript/media/installed-npm.png) - Yüklü ve package.jslistelenir
* ![Fazlalık paket ](../javascript/media/extraneous-npm.png) - Yüklü, ancak açık olarak listede package.jsdeğil
* ![Eksik paket](../javascript/media/missing-npm.png) - Yüklü değil, ancak package.jslistelenir

::: moniker range=">=vs-2019"
Aşağıdaki eylemlerden birini yapmak için **npm** düğümüne sağ tıklayın:

* **Yeni npm Paketleri Yükleme** Yeni paketleri yüklemek için kullanıcı arabirimini açar.
* **npm Paketlerini yükleme** 'de listelenen tüm paketleri yüklemek için npm install *komutunupackage.jsçalıştırır.* `npm install`(Çalıştırır.)
* **npm Paketlerini güncelleştirme** üzerinde belirtilen semantik sürüm (SemVer) aralığına göre paketleri en *son sürümlerepackage.jsgüncelleştirme.* `npm update --save`(çalıştırır.). SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir. Daha fazla bilgi için [package.jshakkında bilgi edinebilirsiniz.](../javascript/configure-packages-with-package-json.md)

Aşağıdaki eylemlerden birini yapmak için paket düğümüne sağ tıklayın:

* **npm Paketlerini yükleme** 'de listelenen paket sürümünü yüklemek için npm *install komutunupackage.jsçalıştırır.* `npm install`(Çalıştırır.)
* **npm Paketlerini güncelleştirme** paketi, üzerinde belirtilen SemVer aralığına göre en son sürüme *package.js.* `npm update --save`(Çalıştırın.) SemVer aralıkları genellikle "~" veya "^" kullanılarak belirtilir.
* **npm Paketlerini kaldırma** Paketi kaldırır ve üzerindepackage.js *kaldırır* `npm uninstall --save` (Çalıştırır.)
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

Ayrıca, `.npm` NPM komutlarını yürütmek için Node.js etkileşimli penceresindeki komutunu da kullanabilirsiniz. Pencereyi açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Node.js etkileşimli pencereyi aç** ' ı (veya **CTRL**  +  **K**, **N**) seçin.

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
> ASP.NET Core projeleri için, istemci tarafı JavaScript ve CSS dosyalarını yüklemek üzere NPM yerine [Kitaplık Yöneticisi](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) 'ni veya Yarn 'yi de kullanabilirsiniz.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Bir projeye NPM desteği ekleme (ASP.NET Core)

Projeniz zaten bir *package.js* dosyası içermiyorsa, projeye dosya *package.js* ekleyerek NPM desteğini etkinleştirmek üzere bir tane ekleyebilirsiniz.

1. Yüklü Node.js yoksa, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

   npm için Node.js.

1. Dosyadapackage.js *eklemek için,* dosyanın içinde projeye sağ tıklayın Çözüm Gezgini Öğe Ekle'yi  >   seçin (veya Ctrl SHIFT A   +    +  **tuşlarına basın).** **npm Yapılandırma Dosyası'yı seçin,** varsayılan adı kullanın ve Ekle'ye **tıklayın.**

   ![Projenize package.jsekleme](../javascript/media/npm-add-package-json.png)

   npm Yapılandırma Dosyası'nın listelenmiş olduğunu görmüyorsanız Node.js araçları yüklü değildir. Geliştirme iş yükünü Visual Studio Yükleyicisi eklemek için **Node.js kullanabilirsiniz.** Ardından önceki adımı tekrarlayın.

1. üzerinde bir veya daha fazla npm paketipackage.js`dependencies` `devDependencies` dahil *edin.* Örneğin, dosyaya aşağıdakini eklersiniz:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Dosyayı kaydediyorsanız, Visual Studio dosyasındaki **Bağımlılıklar / npm** düğümü altına Çözüm Gezgini. Düğümü görmüyorsanız, Düğüm'e sağ tıklayın vepackage.jsGeri **Yükle'yi seçin.** 

>[!NOTE]
> Bazı senaryolarda, Çözüm Gezgini npm paketleri için doğru durumu gösterebebilirsiniz. Daha fazla bilgi için bkz. [Sorun giderme](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>üzerinde package.jskullanarak paketleri yükleme (ASP.NET Core)

npm içeren projeler için kullanarak npm paketlerini `package.json` yapılandırabilirsiniz. içinde npm düğümüne sağ tıklayın ve Çözüm Gezgini **Aç'ı package.jsseçin.**

![npm düğümünün Çözüm Gezgini ekran görüntüsü. Sağ tıklama bağlam menüsü açılır ve Açık package.jsaçılır.](../javascript/media/npm-add-package.png)

*package.js'daki* IntelliSense, npm paketinin belirli bir sürümünü seçmenize yardımcı olur.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="npm paketi sürümünü seçin" border="true":::

Dosyayı kaydediyorsanız, Visual Studio dosyasındaki **Bağımlılıklar / npm** düğümü altına Çözüm Gezgini. Düğümü görmüyorsanız, **üzerindepackage.js** sağ tıklayın ve **paketleri geri yükle**' yi seçin.

Bir paketin yüklenmesi birkaç dakika sürebilir. **Çıkış** penceresindeki **NPM** çıktısına geçerek paket yüklemesinde ilerleme durumunu denetleyin.

![NPM çıkışı](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>NPM paketlerinde sorun giderme

* NPM Node.js için Node.js yüklü değilse, dışarıdaki çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz.

* Node.js projelerinde, NPM desteği için **Node.js geliştirme** iş yükünün yüklü olması gerekir.

* Bazı senaryolarda, [burada](https://github.com/aspnet/Tooling/issues/479)açıklanan bilinen bir sorundan dolayı yüklü NPM paketleri için doğru durumu gösteremeyebilir Çözüm Gezgini. Örneğin, paket yüklendiğinde yüklü değil olarak görünebilir. Çoğu durumda, *package.js* Çözüm Gezgini güncelleştirebilir, Visual Studio 'yu yeniden başlatarak ve bu makalede daha önce anlatıldığı gibi *package.js* dosyaya yeniden ekleyebilirsiniz. Ya da paketleri yüklerken, yükleme durumunu doğrulamak için NPM çıkış penceresini kullanabilirsiniz.

* Bazı ASP.NET Core senaryolarda, Projeyi derledikten sonra Çözüm Gezgini NPM düğümü görünür olmayabilir. Düğümü yeniden görünür hale getirmek için proje düğümüne sağ tıklayın ve **Projeyi Kaldır** ' ı seçin. Ardından proje düğümüne sağ tıklayın ve **projeyi yeniden yükle**' yi seçin.

* Uygulamanızı veya transpiling TypeScript kodunuzu oluştururken herhangi bir hata görürseniz olası hata kaynakları olarak NPM paket uyumsuzluklarını denetleyin. Hataları belirlemede yardımcı olması için, bu makalede daha önce açıklandığı gibi paketleri yüklerken NPM çıkış penceresini kontrol edin. Örneğin, bir veya daha fazla NPM paket sürümü kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için *üzerindepackage.js* kullanma hakkında bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).
