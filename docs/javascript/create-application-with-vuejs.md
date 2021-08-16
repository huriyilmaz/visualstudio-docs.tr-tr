---
title: Node.js kullanarak Vue.js uygulaması oluşturma
description: Vue.js çerçevesini kullanarak Visual Studio Node.js uygulamalar oluşturabilirsiniz
ms.custom: seodec18
ms.date: 07/06/2018
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
monikerRange: <= vs-2019
ms.openlocfilehash: e9f67334dfc6f0fb586638a8f9a93148fed4bb33b134066c92a6606f9e506e3c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371158"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Visual Studio için Node.js araçları kullanarak Vue.js uygulaması oluşturma

Visual Studio, JavaScript veya TypeScript içinde [Vue.js](https://vuejs.org/) framework ile uygulama geliştirmeyi destekler.

Aşağıdaki yeni özellikler Visual Studio ' de uygulama geliştirmeyi Vue.js destekler:

* *. Vue* dosyalarında betik, stil ve şablon blokları için destek
* `lang` *. Vue* dosyalarındaki özniteliğin tanınması
* Vue.js proje ve dosya şablonları

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 sürüm 15,8 veya daha sonraki bir sürümün yüklü olması ve **Node.js geliştirme** iş yüküne sahip olmanız gerekir.

    > [!IMPORTANT]
    > bu makale yalnızca Visual Studio 2017 sürüm 15,8 ' den başlayarak kullanılabilen özellikleri gerektirir.

    ::: moniker range=">=vs-2019"
    gerekli bir sürüm yüklü değilse, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' i yükleme.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.
    ::: moniker-end

    iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

* ASP.NET Core projesi oluşturmak için, ASP.NET ve web geliştirme ve .net Core platformlar arası geliştirme iş yüklerinin yüklü olması gerekir.

* Node.js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz. genellikle Visual Studio, yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasında yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz. (Bir proje oluşturduktan sonra, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin).

## <a name="create-a-vuejs-project-using-nodejs"></a>Node.js kullanarak Vue.js projesi oluşturma

Yeni Vue.js şablonlarını kullanarak yeni bir proje oluşturabilirsiniz. Şablon kullanımı, başlamak için en kolay yoldur. ayrıntılı adımlar için bkz. [ilk Vue.js uygulamanızı oluşturmak için Visual Studio kullanma](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core ve vue clı ile Vue.js projesi oluşturma

Vue.js hızla dolandırıcılamalı projeler için resmi CLı sağlar. Uygulamanızı oluşturmak için CLı 'yı kullanmak istiyorsanız, geliştirme ortamınızı ayarlamak için bu makaledeki adımları izleyin.

> [!IMPORTANT]
> Bu adımlarda Vue.js Framework ile zaten bir deneyim olduğunu varsaymaktadır. Aksi takdirde, Framework hakkında daha fazla bilgi edinmek için lütfen [Vue.js](https://vuejs.org/) ziyaret edin.

### <a name="create-a-new-aspnet-core-project"></a>yeni bir ASP.NET Core projesi oluştur

bu örnekte, boş bir ASP.NET Core uygulaması (C#) kullanırsınız. Ancak, çeşitli projeler ve programlama dilleri arasından seçim yapabilirsiniz.

#### <a name="create-an-empty-project"></a>Boş bir proje oluştur

* Visual Studio açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. **web uygulaması** yazın, dil **olarak C#** ' ı seçin, sonra **ASP.NET Core boş**' ı seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, proje **istemcisi-uygulaması**' nı adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni Project** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin, ardından **Web**' i seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin, **istemci uygulaması** adını yazın ve ardından **tamam**' ı seçin.

    **Boş**' ı seçin ve ardından **Tamam**' a tıklayın.

    Visual Studio, Çözüm Gezgini (sağ bölme) açılan projeyi oluşturur.
    ::: moniker-end

    **ASP.NET Core web uygulaması** proje şablonunu görmüyorsanız, **ASP.NET ve web geliştirme** iş yükünü ve ' yi yüklemelisiniz. Önce **NET Core** geliştirme iş yükü. iş yüklerini yüklemek için **yeni Project** iletişim kutusunun sol bölmesindeki **aç Visual Studio Yükleyicisi** bağlantısına tıklayın ( **dosya**  >  **yeni**  >  **Project**' nı seçin). Visual Studio Yükleyicisi başlatılır. Gerekli iş yüklerini seçin.

#### <a name="configure-the-project-startup-file"></a>Proje başlangıç dosyasını yapılandırma

* *./Startup.cs* dosyasını açın ve configure yöntemine aşağıdaki satırları ekleyin:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Vue CLı 'yı yükler

Vue-CLI NPM modülünü yüklemek için bir komut istemi açın ve `npm install --g vue-cli` `npm install -g @vue/cli` sürüm 3,0 (Şu anda beta sürümünde) yazın.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Vue CLı kullanarak yeni bir istemci uygulaması oluşturma

1. Komut istemine gidin ve geçerli dizini proje kök klasörünüz olarak değiştirin.

1. `vue init webpack client-app`Ek soruları yanıtlamak için sorulduğunda yazın ve adımları izleyin.

    > [!NOTE]
    > *. Vue* dosyaları için, dönüştürme yapmak Için WebPack veya bir yükleyiciyle benzer bir çerçeve kullanmanız gerekir. TypeScript ve Visual Studio, *. vue* dosyalarını derlemeyi bilmez. Aynı paket paketleme için de geçerlidir; TypeScript, ES2015 modüllerini (yani, `import` ve `export` deyimlerini) tarayıcıya yüklemek için tek bir son *.js* dosyasına nasıl dönüştürebileceğinizi bilmez. Burada, WebPack burada en iyi seçenektir. bu işlemi MSBuild kullanarak Visual Studio içinden kullanmak için, bir Visual Studio şablonundan başlamanız gerekir. mevcut olduğunda, yerleşik Vue.js geliştirme için ASP.NET şablonu yoktur.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Web paketi yapılandırmasını, oluşturulan dosyaları Wwwroot 'a çıkarmak için değiştirin

* *./Client-App/config/index.js* dosyasını açın ve `build.index` ve ile `build.assetsRoot` Wwwroot yolunu değiştirin:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Her derleme tetiklendiğinde istemci uygulamasını derlemek için projeyi belirtin

1. Visual Studio, **Project**  >  **özellikleri**  >  **derleme olayları**' na gidin.

1. **Oluşturma öncesi olay komut satırı** üzerinde yazın `npm --prefix ./client-app run build` .

#### <a name="configure-webpacks-output-module-names"></a>WebPack 'in çıkış modülü adlarını yapılandırma

* *./Client-App/Build/webpack.base.conf.js* dosyasını açın ve çıkış özelliğine aşağıdaki özellikleri ekleyin:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLı ile TypeScript desteği ekleme

Bu adımlar, şu anda beta 'da olan Vue-CLI 3,0 gerektirir.

1. Komut istemine gidin ve geçerli dizini proje kök klasörüyle değiştirin.

1. Yazın `vue create client-app` ve ardından **el ile seçim özellikleri**' ni seçin.

1. **TypeScript**' i seçin ve ardından istediğiniz diğer seçenekleri belirleyin.

1. Kalan adımları izleyin ve soruları yanıtlayın.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript için Vue.js projesi yapılandırma

1. *./Client-App/tsconfig.js* dosyasını açın ve `noEmit:true` derleyici seçeneklerine ekleyin.

    Bu seçeneği ayarlayarak, Visual Studio her seferinde projenizi derlemenize engel olursunuz.

1. Sonra, *./Client-App/* içinde bir *vue.config.js* dosyası oluşturun ve aşağıdaki kodu ekleyin.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Yukarıdaki kod Web paketini yapılandırır ve Wwwroot klasörünü ayarlar.

#### <a name="build-with-vue-cli-30"></a>Vue ile derleme-CLI 3,0

Vue-CLI 3,0 ile ilgili bilinmeyen bir sorun, yapı sürecinin otomatikleştirilmesine engel olabilir. Wwwroot klasörünü yenilemeyi her seferinde, komutunu `npm run build` istemci-uygulama klasöründe çalıştırmanız gerekir.

alternatif olarak, ASP.NET projesi özelliklerini kullanarak vue-clı 3,0 projesini derleme öncesi bir olay olarak oluşturabilirsiniz. Projeye sağ tıklayın, **Özellikler**' i seçin ve **derleme sekmesine, derleme** **öncesi olay komut satırı** metin kutusuna aşağıdaki komutları ekleyin.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Sınırlamalar

* `lang` öznitelik yalnızca JavaScript ve TypeScript dillerini destekler. Kabul edilen değerler şunlardır: JS, JSX, TS ve TSX.
* `lang` öznitelik, şablon veya stil etiketleriyle çalışmıyor.
* *. Vue* dosyalarında hata ayıklama betiği blokları, ön işlenmiş doğası nedeniyle desteklenmiyor.
* TypeScript *. Vue* dosyalarını modüller olarak tanımıyor. TypeScript 'e nasıl göründüğünü söylemek için aşağıdaki gibi bir kod içeren bir dosyaya ihtiyacınız vardır *. Vue* -CLI 3,0 şablonu bu dosyayı zaten içeriyor).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Komut, `npm run build` proje özelliklerinde oluşturma öncesi olay olarak çalıştırıldığında, Vue-clı 3,0 kullanılırken çalışmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Vue Başlarken Kılavuzu](https://vuejs.org/v2/guide).
- [Vue CLI projesi](https://github.com/vuejs/vue-cli).
- [Web paketi yapılandırma belgeleri](https://webpack.js.org/configuration/).
