---
title: Vue.js kullanarak bir Node.js
description: Vue.js Node.js kullanarak Visual Studio uygulamaları Vue.js oluşturabilirsiniz
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: <= vs-2019
ms.openlocfilehash: 24ee3dbc8a3a91eaa7176bb0e9971940203ff694
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094201"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Node.js tools for Vue.js kullanarak bir Vue.js uygulaması Visual Studio

Visual Studio JavaScript veya [TypeScript'teVue.js](https://vuejs.org/) çerçevesiyle uygulama geliştirmeyi destekler.

Aşağıdaki yeni özellikler, Vue.js uygulama geliştirmeyi Visual Studio:

* *.vue* dosyalarında Betik, Stil ve Şablon blokları desteği
* `lang` *.vue dosyalarında özniteliğinin tanınması*
* Vue.js ve dosya şablonlarını kullanma

## <a name="prerequisites"></a>Önkoşullar

* 2017 Visual Studio 15.8 veya sonraki bir sürümün yüklü olması ve geliştirme iş **yükününNode.js gerekir.**

    > [!IMPORTANT]
    > Bu makale, yalnızca 2017 sürüm 15.8'Visual Studio başlayarak kullanılabilir özellikler gerektirir.

    ::: moniker range=">=vs-2019"
    Gerekli bir sürüm zaten yüklü değilse, [2019'Visual Studio yükleyin.](https://visualstudio.microsoft.com/downloads)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklü Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

* ASP.NET Core projesini oluşturmak için ASP.NET ve web geliştirme ve .NET Core platformlar arası geliştirme iş yüklerinin yüklü olması gerekir.

* Node.js çalışma Node.js yüklü olmalıdır.

    Yüklü yoksa,Node.jsweb sitesinden LTS [ sürümünü ](https://nodejs.org/en/download/) yükleyin. Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanının başvurusu için yapılandırabilirsiniz. (Bir proje oluşturduk sonra proje düğümüne sağ tıklayın ve Özellikler'i **seçin).**

## <a name="create-a-vuejs-project-using-nodejs"></a>Vue.js kullanarak bir Vue.js projesi Node.js

Yeni proje oluşturmak için Vue.js şablonlarını kullanabilirsiniz. Şablonu kullanmak, kullanmaya başlamanın en kolay yoludur. Ayrıntılı adımlar için [bkz. İlk Visual Studio uygulama oluşturmak için Vue.js kullanma.](../javascript/quickstart-vuejs-with-nodejs.md)

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core ve Vue CLI ile Vue.js proje oluşturma

Vue.js hızla yapı iskelesi için resmi bir CLI sağlar. Cli kullanarak uygulama oluşturmak için kullanmak için bu makaledeki adımları izleyin ve geliştirme ortamınızı ayarlayın.

> [!IMPORTANT]
> Bu adımlarda, Vue.js framework ile ilgili deneyime sahip Vue.js varsayılacaktır. Yoksa çerçeve hakkında daha [ fazlaVue.js](https://vuejs.org/) için lütfenVue.jsziyaret edin.

### <a name="create-a-new-aspnet-core-project"></a>Yeni bir ASP.NET Core oluşturma

Bu örnekte, boş bir uygulama ASP.NET Core (C#) kullanırsınız. Ancak, çeşitli projelerden ve programlama dillerinden birini seçebilirsiniz.

#### <a name="create-an-empty-project"></a>Boş proje oluşturma

* Yeni Visual Studio ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** **Web uygulaması yazın,** dil **olarak C#** seçin, ardından Boş **ASP.NET Core'ı seçin** ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **client-app** adını ve ardından Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni Uygulama İletişim Kutusu iletişim **kutusunun sol Project** Visual **C#** öğesini genişletin ve Ardından **Web'i seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core seçin,** **client-app** adını yazın ve tamam'ı **seçin.**

    Boş **'u** seçin ve ardından Tamam'a **tıklayın.**

    Visual Studio projeyi oluşturur ve bu işlem Çözüm Gezgini bölmede açılır.
    ::: moniker-end

    **ASP.NET Core Web Uygulaması** proje şablonunu görmüyorsanız, ASP.NET ve web **geliştirme iş yükünü** yüklemeniz gerekir. **Önce NET Core** geliştirme iş yükü. İş yüklerini yüklemek için  Yeni Visual Studio Yükleyicisi iletişim kutusunun sol bölmesindeki  Aç bağlantısına Project (Dosya Yeni   >    >  **Dosya'yı Project).** Uygulama Visual Studio Yükleyicisi başlatıyor. Gerekli iş yüklerini seçin.

#### <a name="configure-the-project-startup-file"></a>Proje başlangıç dosyasını yapılandırma

* *./Startup.cs dosyasını açın* ve Configure yöntemine aşağıdaki satırları ekleyin:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>vue CLI'sini yükleme

vue-cli npm modülünü yüklemek için bir komut istemi açın ve veya `npm install --g vue-cli` `npm install -g @vue/cli` sürüm 3.0 (şu anda beta sürümündedir) yazın.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>vue CLI'sini kullanarak yeni bir istemci uygulaması iskelesi

1. Komut isteminize gidin ve geçerli dizini proje kök klasörünüz olarak değiştirebilirsiniz.

1. Ek `vue init webpack client-app` soruları yanıtlamak için istendiğinde yazın ve adımları izleyin.

    > [!NOTE]
    > *.vue dosyaları* için, dönüştürmeyi yapmak için Bir yükleyici ile WebPack veya benzer bir çerçeve kullan gerekir. TypeScript ve Visual Studio .vue dosyalarının nasıl *derlen bir şey olduğunu* bilmiyor. Aynı durum, iş için de doğrudur; TypeScript, ES2015 modüllerini (ve deyimleri) tarayıcıda yüklemek için tek bir son.jsdosyaya nasıl `import` `export` dönüştüreceklerini  bilmiyor. Burada da en iyi seçenek WebPack'tir. Bu işlemi Visual Studio kullanarak MSBuild için bir şablondan Visual Studio gerekir. Şu anda, ASP.NET geliştirme için Vue.js şablon yoktur.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Web paketi yapılandırmasını, yerleşik dosyaların çıktısını wwwroot olarak almak için değiştirme

* *./client-app/config/index.js* dosyasını açın ve ve dosyasını `build.index` `build.assetsRoot` wwwroot yolu olarak değiştirebilirsiniz:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Derleme her tetiklendiğinde istemci uygulamasını derlemek için projeyi belirt

1. Bu Visual Studio Özellikler Derleme **Olayları'Project'ye**  >    >  **gidin.**

1. Derleme **öncesi olay komut satırına** `npm --prefix ./client-app run build` yazın.

#### <a name="configure-webpacks-output-module-names"></a>Webpack'in çıkış modülü adlarını yapılandırma

* *./client-app/build/webpack.base.conf.js* dosyasını açın ve çıktı özelliğine aşağıdaki özellikleri ekleyin:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI ile TypeScript desteği ekleme

Bu adımlar için şu anda beta sürümünde olan vue-cli 3.0 gerekir.

1. Komut isteminize gidin ve geçerli dizini proje kök klasörü olarak değiştirebilirsiniz.

1. yazın `vue create client-app` ve ardından Özellikleri el ile **seç'i seçin.**

1. **Typescript 'i** ve ardından istenen diğer seçenekleri belirleyin.

1. Kalan adımları izleyin ve sorulara yanıt verin.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript Vue.js projesini yapılandırma

1. *./client-app/tsconfig.jsdosyasını açın* ve derleyici `noEmit:true` seçeneklerine ekleyin.

    Bu seçeneği ayar olarak, projenizi her derlemede karmaşık hale Visual Studio.

1. *Ardından./client-app/* vue.config.jsbir dosya oluşturun ve aşağıdaki kodu ekleyin. 

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

    Yukarıdaki kod webpack'i yapılandırarak wwwroot klasörünü ayarlar.

#### <a name="build-with-vue-cli-30"></a>vue-cli 3.0 ile derleme

vue-cli 3.0 ile ilgili bilinmeyen bir sorun derleme işleminin otomatikleşmesini önleyebildi. wwwroot klasörünü yenilemeye her denemeniz için `npm run build` komutu client-app klasöründe çalıştırmamız gerekir.

Alternatif olarak, proje özelliklerini kullanarak vue-cli 3.0 projesini derleme öncesi ASP.NET olarak da derleme öncesi olay olarak derlemeniz gerekir. Projeye sağ tıklayın, Özellikler'i seçin ve Derleme  sekmesindeki Derleme öncesi olay komut satırı metin kutusuna **aşağıdaki komutları** ekleyin.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Sınırlamalar

* `lang` özniteliği yalnızca JavaScript ve TypeScript dillerini destekler. Kabul edilen değerler: js, jsx, ts ve tsx.
* `lang` özniteliği şablon veya stil etiketleriyle çalışmıyor.
* Önceden işlenme yapısı *nedeniyle .vue* dosyalarında betik bloklarında hata ayıklama desteklenmiyor.
* TypeScript , *.vue dosyalarını* modül olarak tanımaz. TypeScript'e *.vue* dosyalarının nasıl olduğunu söylemek için aşağıdaki gibi bir kod içeren bir dosyaya ihtiyacınız vardır (vue-cli 3.0 şablonu bu dosyayı zaten içerir).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Komutunu proje özelliklerinde derleme öncesi olay olarak çalıştırma, `npm run build` vue-cli 3.0 kullanılırken çalışmıyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Vue ile çalışmaya başlama kılavuzu.](https://vuejs.org/v2/guide)
- [Vue CLI projesi](https://github.com/vuejs/vue-cli).
- [Webpack yapılandırma belgeleri.](https://webpack.js.org/configuration/)
