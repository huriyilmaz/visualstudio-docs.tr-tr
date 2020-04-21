---
title: Bir Düğüm.js ve Tepki uygulaması oluşturun
description: Bu eğitimde, Visual Studio için Node.js araçlarını kullanarak bir uygulama oluşturmak
ms.custom: mvc
ms.date: 4/20/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 265445306babf198c3d0063252846414a589a29c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649236"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Visual Studio'da Bir Düğüm.js ve React uygulaması oluşturun

Visual Studio kolayca bir Node.js proje oluşturmak ve Node.js destekleyen IntelliSense ve diğer yerleşik özellikleri deneyim sağlar. Visual Studio için bu öğreticide, Visual Studio şablonundan bir Düğüm.js web uygulama projesi oluşturursunuz. Ardından React'i kullanarak basit bir uygulama oluşturursunuz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * npm paketleri ekle
> * Uygulamanıza Tepki kodu ekleme
> * Transpile JSX
> * Hata ayıklama yı takma

## <a name="before-you-begin"></a>Başlamadan önce

Burada bazı anahtar kavramları tanıtmak için hızlı bir SSS's.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafını çalıştıran sunucu tarafındaki javascript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPm nedir?

npm, Node.js için varsayılan paket yöneticisidir. Paket yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamalarını ve paylaşmalarını kolaylaştırır ve kitaplıkların yüklenmesini, güncellenmesini ve yüklenmesini kolaylaştırmak için tasarlanmıştır.

### <a name="what-is-react"></a>React nedir?

Tepki, bir ui oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX, genellikle Yabancı Ay Öğelerini tanımlamak için React ile kullanılan bir JavaScript sözdizimi uzantısıdır. JSX kodu bir tarayıcıda çalıştırılabilmek için düz JavaScript'e aktarılmalıdır.

### <a name="what-is-webpack"></a>Web paketi nedir?

webpack, JavaScript dosyalarını bir tarayıcıda çalıştırabilmeleri için paketler. Ayrıca, diğer kaynakları ve varlıkları dönüştürebilir veya paketleyebilir. Genellikle, Düz JavaScript JSX veya TypeScript kodu transpile Babel veya TypeScript gibi bir derleyici belirtmek için kullanılır.

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio yüklü ve Node.js geliştirme iş yükünü yüklü olmalıdır.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'yi henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. **Düğüm.js geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

    ![VS Yükleyici'de Düğüm.js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Düğüm.js çalışma saatini yüklemelisiniz.

    Bu öğretici sürüm 12.6.2 ile test edilmiştir.

    Yüklü değilse, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için LTS sürümünü [Node.js](https://nodejs.org/en/download/) web sitesinden yüklemenizi öneririz. Node.js 32-bit ve 64-bit mimariler için inşa edilmiştir. Visual Studio'daki Düğüm.js iş yüküne dahil olan Düğüm.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca bir tanenin yüklenmesini destekler.
    
    Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındayüklü çalışma süresine başvuru yapacak şekilde yapılandırabilirsiniz (proje oluşturduktan sonra, proje düğümüne sağ tıklayın, **Özellikler'i**seçin ve **Düğüm.exe yolunu**ayarlayın). Node.js'nin genel yüklemesini kullanabilir veya Node.js projelerinizin her birinde yerel bir yorumlayıcıya giden yolu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Düğüm.js web uygulama projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Düğüm.js**yazın, ardından **Boş Düğüm.js Web Uygulaması - JavaScript'i**seçin. (Bu öğretici, TypeScript derleyicisini kullansa da, adımlar **JavaScript** şablonuyla başlamanızı gerektirir.)
    
    Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **JavaScript**genişletmek, sonra **Node.js**seçin. Orta bölmede, **Boş Düğüm.js Web Uygulaması**seçin , adını **NodejsWebAppBlank**yazın, sonra **Tamam**seçin.
    ::: moniker-end
    **Boş Düğüm.js Web Uygulaması** proje şablonu görmüyorsanız, Düğüm **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

    Visual Studio yeni bir çözüm oluşturur ve projenizi açar.

    ![Çözüm Gezgini'nde Düğüm.js projesi](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) **Yeni Proje** iletişim kutusunda vermiş olduğunuz adı kullanarak projeniz **kalın** olarak vurgulanır. Dosya sisteminde, bu proje proje klasörünüzde bir *.njsproj* dosyası yla temsil edilir. Projeyle ilişkili özellikleri ve ortam değişkenlerini, projeyi sağ tıklatarak ve **Özellikler'i**seçerek ayarlayabilirsiniz. Proje dosyası Düğüm.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla yuvarlama yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projeile aynı ada sahip bir çözüm vardır. Diskteki *bir .sln* dosyasıyla temsil edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. NPM düğümlerini aramak ve bir iletişim kutusu kullanarak npm paketlerini yüklemek veya *paketleri package.json'daki* ayarları ve npm düğümündeki sağ tıklatma seçeneklerini kullanarak yüklemek ve güncellemek için npm düğümüne sağ tıklayabilirsiniz.

    (4) *package.json* yerel olarak yüklenmiş paketler için paket bağımlılıkları ve paket sürümleri yönetmek için npm tarafından kullanılan bir dosyadır. Bu dosya hakkında daha fazla bilgi için [package.json yapılandırması](../javascript/configure-packages-with-package-json.md)

    (5) *server.js* gibi proje dosyaları proje düğümüaltında gösterir. *server.js* proje başlangıç dosyasıdır ve bu yüzden **kalın**olarak görünür. Projedeki bir dosyayı sağ tıklayarak ve **Node.js başlangıç dosyası olarak**Ayarla'yı seçerek başlangıç dosyasını ayarlayabilirsiniz.

## <a name="add-npm-packages"></a>npm paketleri ekle

Bu uygulama, doğru çalışması için bir dizi npm modülü gerektirir.

* Tepki
* tepki-dom
* express
* yol
* ts-yükleyici
* typescript
* Webpack
* webpack-cli

1. Solution Explorer'da (sağ bölme), projedeki **npm** düğümüne sağ tıklayın ve **Yeni npm Paketlerini Yükle'yi**seçin.

    Yeni **npm Paketleri Yükle** iletişim kutusunda, en güncel paket sürümünü yüklemeyi veya bir sürüm belirtmeyi seçebilirsiniz. Bu paketlerin geçerli sürümünü yüklemeyi seçerseniz, ancak daha sonra beklenmeyen hatalarla karşılaştıysanız, daha sonra bu adımlarda açıklanan tam paket sürümlerini yüklemek isteyebilirsiniz.

1. Yeni **npm Paketleri Yükle** iletişim kutusunda, tepki paketini arayın ve yüklemek için **Paketi Yükle'yi** seçin.

    ![npm paketleri yükleyin](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Paketi yükleme de ilerlemeyi görmek için **Çıktı** penceresini seçin (alandan **çıktıyı göster'de** **Npm'yi** seçin). Yüklendiğinde, paket **npm** düğümüaltında görünür.

    Projenin *package.json* dosyası, paket sürümünü de içeren yeni paket bilgileriyle güncelleştirilir.

1. UI'yi aramak ve paketlerin geri kalanını teker teker eklemek için kullanmak yerine, aşağıdaki kodu *package.json'a*yapıştırın. Bunu yapmak için, `dependencies` bu kodu içeren bir bölüm ekleyin:

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    Boş şablonunuzun `dependencies` sürümünde zaten bir bölüm varsa, önceki JSON koduyla değiştirmeniz. Bu dosyanın kullanımı hakkında daha fazla bilgi için [package.json yapılandırmasına](../javascript/configure-packages-with-package-json.md)bakın.

1. Değişiklikleri kaydedin.

1. Projenizde **npm** düğümüne sağ tıklayın ve **NPm Paketlerini Yükle'yi**seçin.

    Bu komut npm yükleme komutunu doğrudan çalıştırın.

    Alt bölmede, paketleri yükleme de ilerleme görmek için **Çıktı** penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen göremeyebilirsiniz. Çıktıyı görmek için, **Çıktı** penceresindeki **alandan çıktıyı göster'de** **Npm'i** seçtiğinizden emin olun.

    Burada yüklendikten sonra Solution Explorer'da göründükleri gibi npm modülleri verem.

    ![npm paketleri](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Komut satırını kullanarak npm paketleri yüklemeyi tercih ederseniz, proje düğümüne sağ tıklayın ve **Burada Komut İstemin'i Aç'ı**seçin. Paketleri yüklemek için standart Node.js komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları ekleme

Bu adımlarda, projenize dört yeni dosya eklersiniz.

* *app.tsx*
* *webpack-config.js*
* *Index.html*
* *tsconfig.json*

Bu basit uygulama için, proje köküne yeni proje dosyaları eklersiniz. (Çoğu uygulamada, genellikle dosyaları alt klasörlere ekler ve göreli yol başvurularını buna göre ayarlarsınız.)

1. Solution Explorer'da, Proje **NodejsWebAppBlank'a** sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin.

1. Yeni **Öğe Ekle** iletişim kutusunda, **TypeScript JSX dosyasını**seçin, *app.tsx*adını yazın ve **Ekle** veya **Tamam'ı**seçin.

1. *Webpack-config.js*eklemek için bu adımları tekrarlayın. TypeScript JSX dosyası yerine **JavaScript dosyayı**seçin.

1. *Projeye index.html* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **HTML dosyayı**seçin.

1. Projeye *tsconfig.json* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **TypeScript JSON Configuration dosyayı**seçin.

## <a name="add-app-code"></a>Uygulama kodu ekleme

1. *Server.js'yi* açın ve varolan kodu aşağıdaki kodla değiştirin:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Önceki kod, Web uygulama sunucunuz olarak Düğüm.js başlatmak için Express kullanır. Bu kod, bağlantı noktasını proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar (varsayılan olarak, bağlantı noktası özelliklerde 1337 olarak yapılandırılır). Proje özelliklerini açmak için Solution Explorer'da projeyi sağ tıklatın ve **Özellikler'i**seçin.

1. *app.tsx'i* açın ve aşağıdaki kodu ekleyin:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Önceki kod, basit bir iletiyi görüntülemek için JSX sözdizimini ve Tepki'yi kullanır.

1. *index.html'i* açın ve **gövde** bölümünü aşağıdaki kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML sayfası, düz JavaScript'e aktarılan JSX ve React kodunu içeren *app-bundle.js*yükler. Şu *anda, app-bundle.js* boş bir dosyadır. Sonraki bölümde, seçenekleri kodu transpile olacak şekilde yapılandırırsınız.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Web paketi ve TypeScript derleyici seçeneklerini yapılandırma

Önceki adımlarda projeye *webpack-config.js* eklediniz. Ardından, webpack yapılandırma kodu ekleyin. JSX'i düz JavaScript'e aktarmak ve aktarmak için bir giriş dosyası *(app.tsx)* ve bir çıkış dosyası *(app-bundle.js)* belirten basit bir web paketi yapılandırması eklersiniz. Aktarma için, bazı TypeScript derleyici seçeneklerini de yapılandırırsınız. Bu kod, webpack ve TypeScript derleyicisine giriş olarak tasarlanmış temel bir yapılandırmadır.

1. Solution Explorer'da *webpack-config.js'i* açın ve aşağıdaki kodu ekleyin.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Webpack yapılandırma kodu, webpack'e JSX'i transpile etmek için TypeScript yükleyicisini kullanmasını bildirir.

1. *Tsconfig.json'u* açın ve varsayılan kodu TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* kaynak dosya olarak belirtilir.

## <a name="transpile-the-jsx"></a>Transpile the JSX

1. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve **Burada Komut İstemin'i Aç'ı**seçin.

1. Komut isteminde aşağıdaki komutu yazın:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Komut istemi penceresi sonucu gösterir.

    ![Web paketini çalıştırın](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Önceki çıktı yerine herhangi bir hata görürseniz, uygulamanız çalışmadan önce bunları çözmeniz gerekir. npm paket sürümleriniz bu öğreticide gösterilen sürümlerden farklıysa, bu bir hata kaynağı olabilir. Hataları düzeltmenin bir yolu, önceki adımlarda gösterilen tam sürümleri kullanmaktır. Ayrıca, bu paket sürümlerinden biri veya birkaçı amortismana kalınmışsa ve bir hataya yol açarsa, hataları düzeltmek için daha yeni bir sürüm yüklemeniz gerekebilir. npm paket sürümlerini kontrol etmek için *package.json* kullanma hakkında daha fazla bilgi için [package.json yapılandırmasına](../javascript/configure-packages-with-package-json.md)bakın.

1. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve**Varolan Klasörü** **Ekle'yi** > seçin, ardından *dist* klasörünü seçin ve **Klasörü Seç'i**seçin.

    Visual *Studio, app-bundle.js* ve *app-bundle.js.map*içeren projeye *dist* klasörünü ekler.

1. Aktarılan JavaScript kodunu görmek için *app-bundle.js'yi* açın.

1. Harici olarak değiştirilen dosyaları yeniden yüklemek **istenirse, Tümüne Evet'i**seçin.

    ![Değiştirilmiş dosyaları yükleme](../javascript/media/tutorial-nodejs-react-reload-files.png)

*app.tsx'te*her değişiklik yaptığınızda, webpack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatikleştirmek için, JSX'i aşmak için bir yapı komut dosyası ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX'i transpileetmek için yapı komut dosyası ekleme

Visual Studio 2019'dan itibaren bir yapı komut dosyası gereklidir. Komut satırında JSX'i aktarmak yerine (önceki bölümde gösterildiği gibi), Visual Studio'dan bina yaparken JSX'i aktarabilirsiniz.

* *Open package.json* ve `dependencies` bölümden sonra aşağıdaki bölümü ekleyin:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Geçerli hata ayıklama hedefi olarak Microsoft Edge veya Chrome'u seçin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefi olarak Chrome'u seçin](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefi olarak Chrome'u seçin](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Chrome makinenizde kullanılabilse, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedef açılır listesinden **Web Tarayıcısı** **'nı (tarayıcı adı)** > seçin ve varsayılan tarayıcı hedefi olarak **Chrome'u** seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Chrome makinenizde kullanılabilse, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedef açılır listesinden **Web Tarayıcısı (tarayıcı adı)** > **Google Chrome'u** seçin ve varsayılan tarayıcı hedefi olarak **Chrome'u** seçin.
    ::: moniker-end

1. Uygulamayı çalıştırmak için **F5** **(Hata** > **Ayıklama Başlatma Hata Ayıklama)** düğmesine veya yeşil ok düğmesine basın.

    Hata ayıklamanın dinlediği bağlantı noktasını gösteren bir Düğüm.js konsol penceresi açılır.

    Visual Studio başlangıç dosyası, *server.js*başlatarak uygulama başlar.

    ![Tarayıcıda Tepki'yi Çalıştır](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Bir kesme noktası ayarlayın ve uygulamayı çalıştırın

1. *server.js'de,* bir kesme noktası ayarlamak `staticPath` için bildirimin solundaki olukta tıklayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösterir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz.

1. Uygulamayı çalıştırmak için **F5** **(Hata** > **Ayıklama Hata Ayıklama)** tuşuna basın.

    Hata ayıklama ayarladığınız kesme noktasında duraklar (geçerli deyim sarı yla işaretlenir). Artık, **Yerel Halk** ve **İzle** pencereleri gibi hata ayıklama pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerinde gezinerek uygulama durumunuzu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçlarını veya F12 Araçlarını kullanmak istiyorsanız **F12**tuşuna basın. Bu araçları, JAVAScript Konsolu'nu kullanarak DOM'u incelemek ve uygulamayla etkileşimde kalmak için kullanabilirsiniz.

1. Web tarayıcısını ve konsolu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafındaki Tepki kodunda bir kesme noktası ayarlama ve çarpma

Önceki bölümde, hata ayıklayıcıyı sunucu tarafındaki Düğüm.js koduna iliştirdin. Görsel Studio'dan hata ayıklayıcıyı eklemek ve istemci tarafındaki Tepki kodundaki kesme noktalarını vurmak için hata ayıklayıcının doğru işlemi belirlemek için yardıma ihtiyacı vardır. Bunu etkinleştirmenin bir yolu da budur.

### <a name="prepare-the-browser-for-debugging"></a>Tarayıcıyı hata ayıklama için hazırlayın

::: moniker range=">=vs-2019"
Bu senaryo için, şu anda IDE'de **Microsoft Edge Beta** veya Chrome olarak adlandırılan Microsoft Edge (Krom) kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome'u kullanın.
::: moniker-end

1. Hedef tarayıcının tüm pencerelerini kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinken tarayıcının açılmasını engelleyebilir. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engelliyor olabilir, bu nedenle Chrome'un beklenmeyen örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Chromium) için, Chrome'un tüm örneklerini de kapatın. Her iki tarayıcı da krom kod tabanını paylaştığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, `--remote-debugging-port=9222` Hata **Ayıklama** araç çubuğundan > **Gözat'ı** seçerek tarayıcı lansmanında bayrağı ayarlayabilir, ardından **Ekle'yi**seçerek ve **ardından Bağımsızlar** alanında bayrağı ayarlayabilirsiniz. **Hata Ayıklama ile Edge** veya Hata **Ayıklama ile Chrome**gibi tarayıcı için farklı bir dostu ad kullanın. Ayrıntılar [için, Yayın Notları'na](/visualstudio/releases/2019/release-notes-v16.2)bakın.

    ![Hata ayıklama etkinken tarayıcınızı açacak şekilde ayarlayın](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayın ve **Çalıştır'ı**seçin ) ve aşağıdaki komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **Start** düğmesinden **Çalıştır** komutunu açın (sağ tıklayın ve **Çalıştır'ı**seçin ) ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkinken başlatır.

    Uygulama henüz çalışmıyor, bu nedenle boş bir tarayıcı sayfası elde elabilirsiniz.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklamayı istemci tarafındaki komut dosyasına ekleme

1. Visual Studio'ya geçin ve ardından kaynak kodunuzda *app-bundle.js* veya *app.tsx*bir kesme noktası ayarlayın.

    *app-bundle.js*için, aşağıdaki resimde `render()` gösterildiği gibi işlevdeki kesme noktasını ayarlayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    `render()` Aktarılan *app-bundle.js* dosyasındaki işlevi bulmak için **Ctrl**+**F** **(Hızlı** > **Bul'u Bul ve Değiştir** > **Quick Find**) kullanın.

    *app.tsx*için, `render()` işlev içindeki kesme noktasını `return` deyimüzerinde ayarlayın.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. *.tsx* dosyasındaki kesme noktasını ayarlıyorsanız *(app-bundle.js*yerine), *webpack-config.js'yi*güncelleştirmeniz gerekir. Aşağıdaki kodu değiştirin:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    bu kod ile:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Bu, Visual Studio'da hata ayıklamayı etkinleştirmek için yalnızca geliştirme ayarıdır. Bu ayar, uygulamayı oluştururken kaynak harita dosyasında, *app-bundle.js.map'te*oluşturulan başvuruları geçersiz kılmanızı sağlar. Varsayılan olarak, kaynak harita dosyasındaki web paketi başvuruları, Visual Studio'nun kaynak dosya, *app.tsx'i*bulmasını engelleyen *webpack:///* önekini içerir. Özellikle, bu değişikliği yaptığınızda, kaynak dosya, *app.tsx,* başvuru *webpack:///./app.tsx* 'den *./app.tsx,* hata ayıklama sağlayan değiştirilir.

3. Visual Studio'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin ve uygulamayı tarayıcıda çalıştırmak için **Ctrl**+**F5** 'e **(Hata Ayıklama** > Olmadan**Hata Ayıklama)** basın.

    ::: moniker range=">=vs-2019"
    Uygun bir ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Hata Ayıklama** > **Ekle'yi**seçin.

    > [!TIP]
    > Visual Studio 2017'den başlayarak, bu adımları izleyerek işleme ilk kez bağlandığınızda, İşleme Hata**Ayıklama'yı** **Debug** > seçerek aynı işleme hızlı bir şekilde yeniden bağlanabilirsiniz.

5. **İşleme Ekle** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, arama sonuçlarını filtrelemek için filtre kutusuna **ekle** alanında hedef tarayıcınız **JavaScript (Chrome)** **chrome** veya **edge** **JavaScript (Microsoft Edge - Chromium)** için doğru hata ayıklayıcıyı seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de, Alana **Ekle'de** **Webkit kodunu** seçin, arama sonuçlarına filtre lemek için filtre kutusuna **krom** yazın.
    ::: moniker-end

6. Doğru ana bilgisayar bağlantı noktası (bu örnekte localhost) ile tarayıcı işlemini seçin ve **Ekle'yi**seçin.

    Bağlantı noktası (1337), doğru tarayıcı örneğini seçmenize yardımcı olmak için **Başlık** alanında da görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnek, bunun Microsoft Edge (Krom) tarayıcısını nasıl kullandığını gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Hata ayıklamanın, VISUAL Studio'da DOM Explorer ve JavaScript Konsolu açıldığında doğru şekilde iliştirdiğini biliyorsunuz. Bu hata ayıklama araçları, Microsoft Edge için Chrome Geliştirici Araçları ve F12 Araçları'na benzer.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklama eklenmiyorsa ve "İşleme eklenemiyor. Geçerli durumda bir işlem yasal değildir.", hata ayıklama modunda tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engelliyor olabilir.

7. Kesme noktası olan kod zaten yürütüldolduğundan, kesme noktasına basmak için tarayıcı sayfanızı yenileyin.

    Hata ayıklamada duraklatılırken, değişkenlerin üzerinde gezinerek ve hata ayıklama pencerelerini kullanarak uygulama durumunuzu inceleyebilirsiniz. Hata ayıklayıcıyı koda **(F5**, **F10**ve **F11)** basarak ilerletebilirsiniz. Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [hata ayıklama](../debugger/debugger-feature-tour.md)ilk bakışta bakın.

    Ortam ve tarayıcı durumunuzla birlikte daha önce hangi adımları izlediğinize bağlı olarak *app-bundle.js* veya *app.tsx'teki*eşlenen konumundaki kesme noktasına ulaşabilirsiniz. Her iki şekilde de, kod üzerinden adım ve değişkenleri inceleyebilirsiniz.

   * *app.tsx'te* koda girmeniz gerekiyorsa ve bunu yapamıyorsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi **İşleme Ekle'yi** kullanın. Ortamınızın doğru ayarlandığınızdan emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları (Görev Yöneticisi'ni kullanarak) dahil olmak üzere tüm tarayıcı örneklerini kapattınız. Tarayıcıyı hata ayıklama modunda başlattığınızdan emin olun.

      * Kaynak harita dosyanızın *./app.tsx'e* bir başvuru içerdiğinden emin olun, *webpack:///./app.tsx*değil, Visual Studio hata ayıklayıcısının *app.tsx'i*bulmasını engeller.
       Alternatif olarak, *app.tsx'te* koda girmeniz gerekiyorsa ve bunu yapamıyorsanız, `debugger;` bildirimi *app.tsx'te*kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları'nda (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlayın.

   * *App-bundle.js'de* kod alabilmeniz gerekiyorsa ve bunu yapamıyorsanız, kaynak harita dosyasını, *app-bundle.js.map'i*kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux Uygulama Hizmetine dağıtın](../javascript/publish-nodejs-app-azure.md)
