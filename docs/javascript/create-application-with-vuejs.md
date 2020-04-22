---
title: Node.js kullanarak bir Vue.js uygulaması oluşturun
description: Vue.js çerçevesini kullanarak Visual Studio'da Düğüm.js uygulamaları oluşturabilirsiniz
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
ms.openlocfilehash: edf5307984b4efc00a7c83c84fe5cb87954a93dd
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744933"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Visual Studio için Node.js Tools kullanarak bir Vue.js uygulaması oluşturun

Visual Studio, JavaScript veya TypeScript'te [Vue.js](https://vuejs.org/) çerçevesi ile uygulama geliştirmeyi destekler.

Aşağıdaki yeni özellikler Visual Studio'da Vue.js uygulama geliştirmeyi desteklemektadır:

* *.vue* dosyalarındaki Komut Dosyası, Stil ve Şablon blokları için destek
* `lang` *.vue* dosyalarındaki özniteliğin tanınması
* Vue.js proje ve dosya şablonları

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio 2017 sürüm 15.8 veya daha sonraki bir sürümü yüklü ve **Node.js geliştirme** iş yükü olmalıdır.

    > [!IMPORTANT]
    > Bu makale, yalnızca Visual Studio 2017 sürüm 15.8'den başlayarak kullanılabilen özellikler gerektirir.

    ::: moniker range=">=vs-2019"
    Gerekli bir sürüm zaten yüklenmediyse Visual [Studio 2019'u](https://visualstudio.microsoft.com/downloads)yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. **Düğüm.js geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

* ASP.NET Core projesini oluşturmak için ASP.NET ve web geliştirme ve .NET Core platform lar arası geliştirme iş yüklerini yüklü yormuş olmalısınız.

* Düğüm.js çalışma saatini yüklemelisiniz.

    Yüklü değilseniz, [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yükleyin. Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındayüklü çalışma süresine başvurmak üzere yapılandırabilirsiniz. (Bir proje oluşturduktan sonra, proje düğümüne sağ tıklayın ve **Özellikler'i**seçin).

## <a name="create-a-vuejs-project-using-nodejs"></a>Node.js kullanarak bir Vue.js projesi oluşturun

Yeni bir proje oluşturmak için yeni Vue.js şablonlarını kullanabilirsiniz. Şablonun kullanımı başlamak için en kolay yoldur. Ayrıntılı adımlar [için ilk Vue.js uygulamanızı oluşturmak için Visual Studio'u kullanın'](../javascript/quickstart-vuejs-with-nodejs.md)a bakın.

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>ASP.NET Core ve Vue CLI ile bir Vue.js projesi oluşturun

Vue.js hızlı iskele projeleri için resmi bir CLI sağlar. Uygulamanızı oluşturmak için CLI'yi kullanmak istiyorsanız, geliştirme ortamınızı ayarlamak için bu makaledeki adımları izleyin.

> [!IMPORTANT]
> Bu adımlar zaten Vue.js çerçeve ile bazı deneyime sahip olduğunu varsayalım. Değilse, çerçeve hakkında daha fazla bilgi edinmek için [lütfen Vue.js](https://vuejs.org/) adresini ziyaret edin.

### <a name="create-a-new-aspnet-core-project"></a>Yeni bir ASP.NET Core projesi oluşturma

Bu örnekiçin, boş bir ASP.NET Çekirdek Uygulaması (C#) kullanırsınız. Ancak, çeşitli projeler ve programlama dilleri arasından seçim yapabilirsiniz.

#### <a name="create-an-empty-project"></a>Boş proje oluşturma

1. Visual Studio'u açın ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **asp.net**yazın, ardından yeni bir ASP.NET Core Web **Uygulaması oluştur'u**seçin. Görünen iletişim kutusunda, **istemci**adı uygulamasını yazın ve ardından **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde **Visual C#** seçeneğini genişletin ve **ardından Web'i**seçin. Orta bölmede, **Core Web Application ASP.NET**seçin , adı **istemci-app**yazın , ve sonra **Tamam**seçin.
    ::: moniker-end

    **ASP.NET Çekirdek Web Uygulaması** proje şablonu görmüyorsanız, ASP.NET ve web **geliştirme** iş yükünü ve . **Önce NET Core** geliştirme iş yükü. İş yükünü(ler) yüklemek için, **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** Aç bağlantısını tıklatın **(Dosya** > **Yeni** > **Proje'yi**seçin). Visual Studio Installer başlattı. Gerekli iş yüklerini seçin.

1. **Boş'u**seçin ve ardından **Tamam'ı**tıklatın.

    Visual Studio, Solution Explorer'da (sağ bölme) açılan projeyi oluşturur.

#### <a name="configure-the-project-startup-file"></a>Proje başlatma dosyasını yapılandırma

* *./Startup.cs*dosyasını açın ve Yapılandırma yöntemine aşağıdaki satırları ekleyin:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>vue CLI'yi yükleyin

Vue-cli npm modüllerini yüklemek için bir `npm install --g vue-cli` komut `npm install -g @vue/cli` istemi ve yazın veya sürüm 3.0 (şu anda beta da) açın.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>İskele vue CLI kullanarak yeni bir istemci uygulaması

1. Komut istemine gidin ve geçerli dizini proje kök klasörünüz olarak değiştirin.

1. Ek `vue init webpack client-app` soruları yanıtlamak istendiğinde adımları yazın ve izleyin.

    > [!NOTE]
    > *.vue* dosyaları için, dönüşüm yapmak için WebPack veya bir yükleyici ile benzer bir çerçeve kullanmanız gerekir. TypeScript ve Visual Studio *.vue* dosyalarını nasıl derlenen bilmez. Aynı sıfat, donatçıiçin de geçerlidir; TypeScript, ES2015 modüllerini (yani `import` ve `export` deyimleri) tarayıcıda yüklemek üzere tek bir son *.js* dosyasına nasıl dönüştürüldüğünü bilmiyor. Yine, WebPack burada en iyi seçimdir. Bu işlemi MSBuild'i kullanarak Visual Studio'nun içinden yönlendirmek için Visual Studio şablonundan başlamanız gerekir. Şu anda, Vue.js geliştirme in-the-box için ASP.NET bir şablon yoktur.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Web paketi yapılandırmasını, yerleşik dosyaları wwwroot'a çıktıracak şekilde değiştirin

* *./client-app/config/index.js*dosyasını açın ve `build.index` `build.assetsRoot` wwwroot yolunu değiştirin:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Bir yapı tetikleninher tetikleninher olduğunda istemci uygulamasını oluşturmak için projeyi göster

1. Visual Studio'da **Project** > **Properties** > **Build Events'e**gidin.

1. **Önceden yapılan olay komut satırında**, yazın. `npm --prefix ./client-app run build`

#### <a name="configure-webpacks-output-module-names"></a>Webpack'in çıktı modülü adlarını yapılandırma

* *./client-app/build/webpack.base.conf.js*dosyasını açın ve çıktı özelliğine aşağıdaki özellikleri ekleyin:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Vue CLI ile TypeScript desteği ekle

Bu adımlar şu anda beta vue-cli 3.0 gerektirir.

1. Komut istemine gidin ve geçerli dizini proje kökü klasörüne değiştirin.

1. Yazın `vue create client-app`ve ardından **Özellikleri El Ile Seçin.**

1. **Typescript'i**seçin ve ardından istenen diğer seçenekleri seçin.

1. Kalan adımları izleyin ve soruları yanıtlayın.

#### <a name="configure-a-vuejs-project-for-typescript"></a>TypeScript için Bir Vue.js projesini yapılandırma

1. *./client-app/tsconfig.json* dosyasını açın `noEmit:true` ve derleyici seçeneklerine ekleyin.

    Bu seçeneği ayarlayarak, Visual Studio'da her oluşturduğunuzda projenizi darmadağın etmekten kaçınırsınız.

1. Ardından, *./client-app/* dosyasında *bir vue.config.js* dosyası oluşturun ve aşağıdaki kodu ekleyin.

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

    Önceki kod webpaketini yapılandırır ve wwwroot klasörünü ayarlar.

#### <a name="build-with-vue-cli-30"></a>Vue-cli 3.0 ile inşa edin

Vue-cli 3.0 ile bilinmeyen bir sorun yapı işleminin otomatikleştirilmesiengelleyebilir. Wwwroot klasörünü her yenilemeye çalıştığınızda, istemci uygulaması `npm run build` klasöründeki komutu çalıştırmanız gerekir.

Alternatif olarak, ASP.NET proje özelliklerini kullanarak bir ön yapı olay olarak vue-cli 3.0 proje oluşturabilirsiniz. Projeyi sağ tıklatın, **Özellikler'i**seçin ve Yapı **sekmesine,** **Önceden Yapı olay komut satırı** metin kutusuna aşağıdaki komutları ekleyin.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Sınırlamalar

* `lang`öznitelik yalnızca JavaScript ve TypeScript dillerini destekler. Kabul edilen değerler şunlardır: js, jsx, tsx ve tsx.
* `lang`öznitelik şablon veya stil etiketleri ile çalışmıyor.
* *.vue* dosyalarındaki komut dosyası bloklarının hata ayıklanması, önceden işlenmiş yapısı nedeniyle desteklenmez.
* TypeScript *.vue* dosyalarını modül olarak tanımaz. TypeScript'e *.vue* dosyalarının nasıl göründüğünü söylemek için aşağıdaki gibi kod içeren bir dosyaya ihtiyacınız vardır (vue-cli 3.0 şablonu zaten bu dosyayı içerir).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Vue-cli 3.0 kullanırken komutu `npm run build` proje özelliklerinde önceden inşa olayı olarak çalıştırmak çalışmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Vue kılavuzu başlar](https://vuejs.org/v2/guide).
- [Vue CLI projesi](https://github.com/vuejs/vue-cli).
- [Webpack yapılandırma belgeleri](https://webpack.js.org/configuration/).
