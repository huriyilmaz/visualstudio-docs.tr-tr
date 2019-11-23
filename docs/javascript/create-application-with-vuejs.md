---
title: Node.js kullanarak bir Vue.js uygulaması oluşturma
description: Vue.js framework kullanarak Visual Studio'da Node.js uygulamaları oluşturun
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: af781f5735a3539d8b0e2d098bb9252bc60193fc
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180274"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Visual Studio için node.js araçları kullanarak Vue.js uygulama oluşturma

Visual Studio, [Vue. js](https://vuejs.org/) çerçevesiyle JavaScript ya da TypeScript içindeki uygulama geliştirmeyi destekler.

Aşağıdaki yeni özellikleri, Visual Studio'da Vue.js uygulama geliştirmeyi destekler:

* Betik, stil ve şablon bloklarında desteği *.vue* dosyaları
* Tanıma `lang` özniteliği *.vue* dosyaları
* VUE.js proje ve dosya şablonları

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio 2017 sürüm 15,8 veya sonraki bir sürümün yüklü olması ve **Node. js geliştirme** iş yüküne sahip olmanız gerekir.

    > [!IMPORTANT]
    > Bu makale, yalnızca Visual Studio 2017 sürüm 15,8 ' den başlayarak kullanılabilen özellikleri gerektirir.

    ::: moniker range=">=vs-2019"
    Gerekli bir sürüm yüklü değilse, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' i yükleme.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

* ASP.NET Core projesi oluşturmak için ASP.NET ve web geliştirme ve .NET Core çoklu platform geliştirme iş yükleri yüklü olması gerekir.

* Node.js çalışma zamanı yüklü olması gerekir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz. (Bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

## <a name="create-a-vuejs-project-using-a-template"></a>Bir şablon kullanarak Vue.js projesi oluşturma

Yeni bir proje oluşturmak için yeni Vue.js şablonları kullanabilirsiniz. Şablon kullanımı başlamanın en kolay yoludur. Ayrıntılı adımlar için bkz. [ilk Vue.js uygulamanızı oluşturmak için Visual Studio](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core ve Vue CLI ile bir Vue.js projesi oluşturma

VUE.js hızla yapı iskelesi projeleri için resmi bir CLI sağlar. Uygulamanızı oluşturmak için CLI'yı kullanmak istiyorsanız, geliştirme ortamınızı ayarlamak için bu makaledeki adımları izleyin.

> [!IMPORTANT]
> Bu adımları biraz deneyim Vue.js framework ile zaten sahip olduğunuzu varsaymaktadır. Aksi takdirde, lütfen [Vue.js](https://vuejs.org/) altyapısı hakkında daha fazla bilgi edinmek için.

### <a name="create-a-new-aspnet-core-project"></a>Yeni bir ASP.NET Core projesi oluşturma

Bu örnekte, boş bir ASP.NET Core uygulaması (C#) kullanın. Ancak, çeşitli projeler ve programlama dilleri arasından seçebilirsiniz.

#### <a name="create-an-empty-project"></a>Boş bir proje oluşturun

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **asp.net**yazıp **Yeni ASP.NET Core Web uygulaması oluştur**' u seçin. Görüntülenen iletişim kutusunda, **istemci uygulaması**adını yazın ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** ' i genişletin ve ardından **Web**' i seçin. Orta bölmede **ASP.NET Core Web uygulaması**' nı seçin, **istemci uygulaması**adını yazın ve ardından **Tamam**' ı seçin.
    ::: moniker-end

    Görmüyorsanız **ASP.NET Core Web uygulaması** proje şablonu, yüklemelisiniz **ASP.NET ve web geliştirme** iş yükü ve. **NET Core** geliştirme iş yükü ilk. Workload(s) yüklemek için tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu (seçin **dosya**  >  **Yeni** > **proje**). Visual Studio Yükleyicisi'ni başlatır. Gerekli iş yüklerini seçin.

1. Seçin **boş**ve ardından **Tamam**.

    Visual Studio Çözüm Gezgini'nde (sağ bölme) açar Proje oluşturur.

#### <a name="configure-the-project-startup-file"></a>Proje başlangıç dosyasını yapılandırın

* Dosyayı açmak *./Startup.cs*ve yapılandırma yöntemine aşağıdaki satırları ekleyin:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>' % S'vue CLI yükleme

CLI vue npm modülünü yüklemek için bir komut istemi açıp `npm install --g vue-cli` veya `npm install -g @vue/cli` (şu anda beta sürümündeki) sürüm 3.0 için.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>İskele vue CLI kullanarak yeni bir istemci uygulaması

1. Komut istemine gidin ve geçerli dizini, proje kök klasörüne değiştirin.

1. Tür `vue init webpack client-app` ve ek soruları yanıtlamak için istendiğinde adımları izleyin.

    > [!NOTE]
    > *. Vue* dosyaları için, dönüştürme yapmak Için WebPack veya bir yükleyiciyle benzer bir çerçeve kullanmanız gerekir. TypeScript ve Visual Studio, *. Vue* dosyalarını derlemeyi bilmez. Aynı paket paketleme için de geçerlidir; TypeScript, ES2015 modüllerinin (yani, `import` ve `export` deyimlerinin) tarayıcıya yüklenecek tek bir son *. js* dosyasına nasıl dönüştürüleceğini bilmez. Burada, WebPack burada en iyi seçenektir. MSBuild kullanarak bu işlemi Visual Studio 'Nun içinden bir sürücüye yönlendirmek için Visual Studio şablonundan başlamanız gerekir. Mevcut olduğunda, yerleşik Vue. js geliştirme için ASP.NET şablonu yoktur.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Web yapılandırmasını wwwroot oluşturulmuş dosyaları çıkış değiştirin

* *./Client-App/config/Index.js*dosyasını açın ve `build.index` değiştirin ve Wwwroot yolu olarak `build.assetsRoot`:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Her derleme tetiklendiğinde istemci uygulamasını derlemek için projeyi belirtin

1. Visual Studio'da Git **proje** > **özellikleri** > **Build Events**.

1. Üzerinde **derleme öncesi olay komut satırı**, türü `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Web'ın çıktı modül adlarını yapılandırın

* *./Client-App/Build/WebPack.Base.conf.js*dosyasını açın ve çıkış özelliğine aşağıdaki özellikleri ekleyin:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI ile TypeScript desteği eklendi

Bu adımlar vue-şu anda beta sürümünde olan CLI 3.0 gerektirir.

1. Komut istemine gidin ve geçerli dizin proje kök klasörüyle değiştirin.

1. Tür `vue create client-app`ve ardından **özellikleri el ile seçin**.

1. Seçin **Typescript**ve ardından diğer istenen seçenekleri belirleyin.

1. Kalan adımları izleyin ve soruları yanıtlayın.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript için Vue.js proje yapılandırma

1. *./Client-App/tsconfig.exe* dosyasını açın ve derleyici seçeneklerine `noEmit:true` ekleyin.

    Bu seçenek ayarlayarak, projenizi Visual Studio'da derleyin her zaman karmaşık hale getirmekten kaçının.

1. Sonra, *./Client-App/* içinde *Vue. config. js* dosyası oluşturun ve aşağıdaki kodu ekleyin.

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

    Yukarıdaki kod, Web yapılandırır ve wwwroot klasörü ayarlar.

#### <a name="build-with-vue-cli-30"></a>VUE-cli 3.0 ile derleme

Vue-CLI 3,0 ile ilgili bilinmeyen bir sorun, yapı sürecinin otomatikleştirilmesine engel olabilir. Wwwroot klasörünü yenilemeye her seferinde, komutunu istemci uygulaması klasöründe `npm run build` çalıştırmanız gerekir.

Alternatif olarak, ASP.NET proje özelliklerini kullanarak Vue-CLI 3,0 projesini derleme öncesi bir olay olarak oluşturabilirsiniz. Projeye sağ tıklayın, **Özellikler**' i seçin ve **derleme sekmesine, derleme** **öncesi olay komut satırı** metin kutusuna aşağıdaki komutları ekleyin.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Sınırlamalar

* `lang` öznitelik yalnızca, JavaScript ve TypeScript dilleri de destekler. Kabul edilen değerler şunlardır: js, jsx, ts ve tsx.
* `lang` öznitelik, şablon veya stil etiketler ile çalışmaz.
* Hata ayıklamayı engelleyen *.vue* dosyaları, önceden işlenmiş doğası nedeniyle desteklenmiyor.
* TypeScript tanımıyor *.vue* modülleri olarak dosyaları. TypeScript ne söylemek için aşağıdaki gibi bir kod içeren bir dosyayı duyduğunuz *.vue* dosyaları aramak gibi (vue-cli 3.0 şablonu bu dosya zaten içerir).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Komutu çalıştırmadan `npm run build` proje özelliklerinde bir derleme öncesi olay vue-cli 3.0 kullanırken işe yaramazsa gibi.

## <a name="see-also"></a>Ayrıca bkz.

- [Vue Başlarken Kılavuzu](https://vuejs.org/v2/guide).
- [Vue CLI projesi](https://github.com/vuejs/vue-cli).
- [Web paketi yapılandırma belgeleri](https://webpack.js.org/configuration/).
