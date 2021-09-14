---
title: Node.js ve React uygulaması oluşturma
description: bir Visual Studio şablonundan Node.js web uygulaması projesi oluşturmayı öğrenin.
ms.custom: vs-acquisition
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 55672b542bc2418cc1c5b2b7cf300072e8215695
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635902"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>öğretici: Visual Studio Node.js ve React uygulama oluşturma

Visual Studio kolayca Node.js bir proje oluşturmanıza ve ıntellisense ve Node.js destekleyen diğer yerleşik özelliklerle karşılaşmanızı sağlar. Visual Studio için bu öğreticide, bir Visual Studio şablonundan bir Node.js web uygulaması projesi oluşturacaksınız. Daha sonra, React kullanarak basit bir uygulama oluşturursunuz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * NPM paketleri Ekle
> * uygulamanıza React kod ekleyin
> * Derleyin JSX
> * Hata ayıklayıcıyı iliştirme

## <a name="before-you-begin"></a>Başlamadan önce

İşte size bazı önemli kavramlara yol açmaya yönelik hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafını yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPM nedir?

NPM, Node.js için varsayılan paket yöneticisidir. Paket Yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamasını ve paylaşmasını kolaylaştırır ve kitaplıkları yükleme, güncelleştirme ve kaldırmayı basitleştirecek şekilde tasarlanmıştır.

### <a name="what-is-react"></a>React nedir?

React, kullanıcı arabirimi oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

jsx, genellikle uı öğelerini anlatmak için React ile birlikte kullanılan bir JavaScript sözdizimi uzantısıdır. JSX kodu, bir tarayıcıda çalışmadan önce transpiled ile düz JavaScript olmalıdır.

### <a name="what-is-webpack"></a>WebPack nedir?

Web paketi, JavaScript dosyalarını bir tarayıcıda çalışabilecek şekilde paketler. Ayrıca diğer kaynakları ve varlıkları dönüştürebilir veya paketleyebilir. Genellikle Babel veya TypeScript gibi bir derleyicinin basit JavaScript 'e derleyin JSX veya TypeScript kodunu belirtmek için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    zaten 2017 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end

    iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanının yüklü olması gerekir.

    Bu öğretici sürüm 12.6.2 ile test edilmiştir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node.js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Node.js iş yüküne dahil olan Visual Studio Node.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyici yalnızca aynı anda yüklü olan birini destekler.

    genellikle Visual Studio, yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler** ' i seçin (veya **alt**  +  **ENTER** tuşuna basın) ve **Node.exe yolunu** ayarlayın. Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Node.js Web uygulaması projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve sonra **Web uygulaması-JavaScript Node.js boş** seçeneğini belirleyin. (Bu öğretici TypeScript derleyicisini kullanıyor olsa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.)
    
    Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni Project** iletişim kutusunun sol bölmesinde, **JavaScript**' i genişletin ve **Node.js**' ı seçin. Orta bölmede, **boş Node.js Web uygulaması**' nı seçin, **Nodejswebappblank** adını yazın ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi açar.

    ![Çözüm Gezgini Node.js proje](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler** ' i seçerek (veya **alt** Enter ' a basarak) projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz  +  . Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *Package. JSON* ' daki ayarları kullanarak paketleri yükleyip güncelleyebilir ve NPM düğümündeki Seçenekler ' e sağ tıklayın.

    (4) *Package. JSON* , NPM tarafından yerel olarak yüklenen paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek üzere kullanılan bir dosyadır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

    (5) *server.js* gibi Project dosyalar proje düğümünün altında görünür. *server.js* , proje başlangıç dosyasıdır ve bu nedenle **kalın** olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

## <a name="add-npm-packages"></a>NPM paketleri Ekle

Bu uygulama, doğru bir şekilde çalışması için birkaç NPM modülü gerektirir.

* tıkla
* tepki verme-Dom
* express
* path
* TS-yükleyici
* typescript
* Web paketi
* Web paketi-CLI

1. Çözüm Gezgini (sağ bölme) menüsünde, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

    **Yeni NPM paketlerini yükler** iletişim kutusunda, en güncel paket sürümünü yüklemeyi veya bir sürüm belirtmeyi seçebilirsiniz. Bu paketlerin güncel sürümünü yüklemeyi seçer, ancak daha sonra beklenmeyen hatalar halinde çalıştırırsanız, bu adımlarda daha sonra açıklanan paket sürümlerinin aynısını yüklemek isteyebilirsiniz.

1. **Yeni NPM paketlerini yükler** iletişim kutusunda, yanıt verme paketini arayın ve paketi yüklemek Için **paketi yüklensin** ' i seçin.

    ![NPM paketlerini yükler](../javascript/media/tutorial-nodejs-react-install-package.png)

    Paketin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin ( **çıktıyı göster** alanından **NPM** ' yi seçin). Yüklendiğinde, paket **NPM** düğümünün altında görüntülenir.

    Projenin *Package. JSON* dosyası, paket sürümü de dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

1. Tek seferde paketleri aramak ve geri kalanını eklemek için Kullanıcı arabirimini kullanmak yerine, aşağıdaki kodu *Package. JSON* dosyasına yapıştırın. Bunu yapmak için `dependencies` şu kodla bir bölüm ekleyin:

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

    `dependencies`Boş şablon sürümünüzde zaten bir bölüm varsa, bunu ÖNCEKI JSON kodu ile değiştirmeniz yeterlidir. Bu dosyanın kullanımı hakkında daha fazla bilgi için bkz. [Package. JSON yapılandırması](../javascript/configure-packages-with-package-json.md).

1. Değişiklikleri kaydedin.

1. Projenizde **NPM** düğümüne sağ tıklayın ve **NPM paketlerini yüklensin**' i seçin.

    Bu komut NPM install komutunu doğrudan çalıştırır.

    Alt bölmede, paketlerin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıktıyı görmek için **Çıkış** penceresindeki çıktıyı **göster** alanında **NPM** ' yi seçtiğinizden emin olun. (Pencereyi açmak için Görünüm'e **tıklayın**  >  **Ctrl**   +  Alt O **tuşlarına basın**  +  **veya çıkışa** basın.)

    Npm modülleri yüklendikten sonra Çözüm Gezgini burada görünür.

    ![npm paketleri](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Komut satırı kullanarak npm paketlerini yüklemek isterseniz proje düğümüne sağ tıklayın ve Burada Komut İstemi **Aç'ı seçin.** Paketleri yüklemek Node.js standart komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları ekleme

Bu adımlarda, projenize dört yeni dosya eklersiniz.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Bu basit uygulama için yeni proje dosyalarını proje köküne eklersiniz. (Çoğu uygulama için dosyaları genellikle alt klasörlere ekler ve göreli yol başvurularını buna göre ayarlarsiniz.)

1. Bu Çözüm Gezgini **NodejsWebAppBlank** projesine sağ tıklayın ve Yeni Öğe Ekle'yi seçin  >   **(veya Ctrl SHIFT** A  +    +  **tuşlarına basın).**

1. Yeni Öğe **Ekle iletişim kutusunda** **TypeScript JSX** dosyasını seçin, *app.tsx* adını yazın ve Ekle veya **Tamam'ı** **seçin.**

1. bu adımları tekrarlayın ve *webpack-config.js.* TypeScript JSX dosyası yerine **JavaScript dosyası'ı seçin.**

1. Aynı adımları tekrarlayın ve *projeyeindex.html* ekleyin. JavaScript dosyası yerine HTML dosyasını **seçin.**

1. Projeye *tsconfig.json eklemek için aynı* adımları tekrarlayın. JavaScript dosyası yerine **TypeScript JSON Yapılandırma dosyası'ı seçin.**

## <a name="add-app-code"></a>Uygulama kodu ekleme

1. Aşağıdaki *server.js* açın ve mevcut kodu aşağıdaki kodla değiştirin:

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

   Yukarıdaki kod, web uygulaması sunucunuz olarak Node.js express kullanır. Bu kod, bağlantı noktasını proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar (varsayılan olarak, bağlantı noktası özelliklerde 1337 olarak yapılandırılır). Proje özelliklerini açmak için, proje içinde projeye sağ tıklayın ve Çözüm Gezgini'yi **seçin.**

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

    Yukarıdaki kod, basit bir ileti görüntülemek için JSX React söz dizimi kullanır.

1. Aşağıdaki *index.html* açın ve **body** bölümünü aşağıdaki kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML *sayfası, JSXapp-bundle.js* içeren ve düz JavaScript'e React kodu içeren bir kod yükler. Şu *andaapp-bundle.js* boş bir dosyadır. Sonraki bölümde, kodun transpilesine geçiş yapmak için seçenekleri yapılandırabilirsiniz.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Webpack ve TypeScript derleyici seçeneklerini yapılandırma

Önceki adımlarda projeye *webpack-config.js* eklediniz. Ardından webpack yapılandırma kodunu ekleyin. JSX'i düz JavaScript'e paketlemek ve değiştirmek için bir giriş dosyası (*app.tsx*) ve bir çıkış dosyası (*app-bundle.js*) belirten basit bir web paketi yapılandırması eksersiniz. Transpiling için bazı TypeScript derleyici seçeneklerini de yapılandırabilirsiniz. Bu kod, webpack'e ve TypeScript derleyiciye giriş olarak amaçlanan temel bir yapılandırmadır.

1. Bu Çözüm Gezgini, *webpack-config.js* açın ve aşağıdaki kodu ekleyin.

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

    Webpack yapılandırma kodu, webpack'e JSX'i transpile etmek için TypeScript yükleyicisini kullanma talimatı sağlar.

1. *tsconfig.json'u* açın ve varsayılan kodu TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

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

## <a name="transpile-the-jsx"></a>JSX'i transpile

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.**

1. Komut isteminde aşağıdaki komutu yazın:

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Komut istemi penceresinde sonuç gösterilir.

    ![Webpack'i çalıştırma](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Önceki çıkış yerine herhangi bir hata görüyorsanız, bunları, uygulamanın çalışmadan önce çözümlemeniz gerekir. npm paketi sürümleriniz bu öğreticide gösterilen sürümlerden farklı ise, bu bir hata kaynağı olabilir. Hataları düzeltmenin bir yolu, önceki adımlarda gösterilen tam sürümleri kullanmaktır. Ayrıca, bu paket sürümlerinden biri veya daha fazlası kullanım dışı kaldı ve bir hatayla sonuçlanıyorsa, hataları düzeltmek için daha yeni bir sürüm yüklemeniz gerekir. npm paket sürümlerini *kontrol etmek için package.json* kullanma hakkında bilgi için bkz. [package.json yapılandırması.](../javascript/configure-packages-with-package-json.md)

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Var Olan Klasör Ekle'yi seçin, ardından  >   *dist klasörünü* seçin ve Klasör **Seç'i seçin.**

    Visual Studio,app-bundle.jsve *app-bundle.js.map'i* içeren  *dist* klasörünü projeye ekler.

1. JavaScript *app-bundle.js* görmek içinapp-bundle.js'yi açın.

1. Harici olarak değiştirilmiş dosyaları yeniden yüklemek istenirse, Evet'i **All (Tüm dosyalar) olarak seçin.**

    ![Değiştirilen dosyaları yükleme](../javascript/media/tutorial-nodejs-react-reload-files.png)

*app.tsx üzerinde her değişiklik* yaptığınız zaman webpack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatikleştirmek için JSX'i transpile etmek için bir derleme betiği ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX'i transpile etmek için derleme betiği ekleme

2019'Visual Studio başlayarak bir derleme betiği gerekir. JSX'i komut satırına (önceki bölümde gösterildiği gibi) çeviri yapmak yerine, JSX'i komut satırına Visual Studio.

* *package.json'ı* açın ve bölümünden sonra aşağıdaki bölümü `dependencies` ekleyin:

   ```json
   "scripts": {
    "build": "webpack-cli ./app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Geçerli hata **ayıklama hedefi olarak Web Sunucusu (Google Chrome)** veya Web Sunucusu **(Microsoft Edge)** seçeneğini kullanın.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefi olarak Chrome'u seçin](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefi olarak Chrome'u seçin](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Makinede Chrome mevcutsa ancak bir seçenek olarak göstermüyorsa, hata ayıklama hedefi açılan listesinden Birlikte Gözat'ı seçin ve varsayılan tarayıcı hedefi olarak Chrome'u seçin (Varsayılan Olarak **Ayarla'ya tıklayın).** 

1. Uygulamayı çalıştırmak için **F5** **(** Hata AyıklamaYı  >  **Başlat**) veya yeşil ok düğmesine basın.

    Hata Node.js dinleyen bağlantı noktasını gösteren bir konsol penceresi açılır.

    Visual Studio başlangıç dosyasını başlatarak uygulamayı başlatır ve *server.js.*

    ![Tarayıcıda React çalıştırma](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Kesme noktası ayarlama ve uygulamayı çalıştırma

1. Bu *server.js,* bir kesme noktası ayarlamak için bildirimin sol `staticPath` tarafından yer alan oluklara tıklayın:

    ![Visual Studio için Visual Studio penceresinin ekran server.js. Sol oluk içinde kırmızı bir nokta, staticPath bildirimi için bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

1. Uygulamayı çalıştırmak için **F5** tuşuna basın (**Hata**  >  **AyıklamaYı Başlat hata ayıklama).**

    Hata ayıklayıcı, ayar istediğiniz kesme noktası sırasında duraklatılır (geçerli deyim sarı olarak işaretlenir). Artık Yerel Ayarlar ve İzleme pencereleri gibi hata ayıklayıcı pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerine gelerek **uygulama durumunu** **inceleyebilirsiniz.**

1. Uygulamaya **devam etmek için F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçları veya F12 Araçları'Microsoft Edge **F12 tuşuna basın.** DoM'ları incelemek ve JavaScript Konsolu'nu kullanarak uygulamayla etkileşim kurmak için bu araçları kullanabilirsiniz.

1. Web tarayıcısını ve konsolunu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafında kesme noktası ayarlama ve React isabet

Önceki bölümde hata ayıklayıcıyı sunucu tarafı koda Node.js. Hata ayıklayıcıyı Visual Studio ve istemci tarafı kodda kesme noktalarına React için, hata ayıklayıcının doğru işlemi tanımlamaya yardımcı olması gerekir. Bunu etkinleştirmenin bir yolu şu şekildedir.

### <a name="prepare-the-browser-for-debugging"></a>Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için şu anda IDE Microsoft Edge de Chromium adlı **Microsoft Edge Beta** veya Chrome kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu önliyor olabilir, bu nedenle Beklenmeyen Chrome örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekir.)

   ::: moniker range=">=vs-2019"
   Bu Microsoft Edge (Chromium) chrome'un tüm örneklerini de kapatır. her iki tarayıcı da chromium kod tabanını paylaştığı için en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinleştirildiğinde tarayıcınızı başlatabilirsiniz.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, Hata Ayıklama araç çubuğundan `--remote-debugging-port=9222` **Gözat...**  >'yi ve ardından Ekle'yi seçerek ve ardından Bağımsız  Değişkenler alanında bayrağını ayarlayarak tarayıcı başlatma sırasında bayrağını ayarlayın. Hata Ayıklama ile Edge veya Hata Ayıklama ile **Chrome gibi** tarayıcı için farklı bir kolay **ad kullanın.** Ayrıntılar için bkz. [Sürüm Notları.](/visualstudio/releases/2019/release-notes-v16.2)

    ![Tarayıcınızı hata ayıklama etkin olarak açılacak şekilde ayarlayın](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Başlat **düğmesinden** Çalıştır Windows  açın (sağ tıklayın ve **Çalıştır'ı seçin)** ve aşağıdaki komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Başlat **düğmesinden** Çalıştır komutunu Windows **(sağ** tıklayın ve Çalıştır'ı **seçin)** ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmamıştır, bu nedenle boş bir tarayıcı sayfası açılır.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğine ekleme

1. Visual Studio'a geçiş ve ardından kaynak kodunda *app.tsx* *app-bundle.js* kesme noktası ayarlayın.

    Daha *app-bundle.js* için işlevinde kesme noktası `render()` aşağıdaki çizimde gösterildiği gibi ayarlayın:

    ![Uygulama için Visual Studio penceresinin ekran app-bundle.js. Sol oluk içinde kırmızı bir nokta, işleme işlevinde bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    İşlevi `render()` transpiled dosyada bulmak *app-bundle.js* **Ctrl** F ( Bul ve +  **Değiştir**  >  **Hızlı Bul)**  >  **tuşlarını kullanın.**

    *app.tsx* için işlevinin içindeki kesme `render()` noktası olan deyimini `return` ayarlayın.

    ![app.tsx için Visual Studio penceresinin ekran görüntüsü. Sol oluk içinde kırmızı bir nokta, işleme işlevinin dönüş deyiminde bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Kesme noktası *.tsx* dosyasında ayarıyorsanız (app-bundle.js *yerine),* kesme *webpack-config.js.* Aşağıdaki kodu değiştirin:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    yerine şu kodu yazın:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Bu, yalnızca geliştirme aşamasında hata ayıklamayı etkinleştiren bir Visual Studio. Bu ayar, uygulamayı oluşturulurken kaynak eşleme dosyasında oluşturulan başvuruları *(app-bundle.js.map)* geçersiz kılmaya olanak sağlar. Varsayılan olarak, kaynak eşleme dosyasındaki webpack  başvuruları *app.tsx* webpack:/// bulmasını engelleyen Visual Studio ön eklerini içerir. Bu değişikliği özellikle de *app.tsx* kaynak dosyasına yapılan başvuru, hata  ayıklamayı webpack:///./app.tsx *./app.tsx* olarak değiştirir.

3. Visual Studio'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl** F5 ( Hata Ayıklama Olmadan Başlat +    >  ) tuşlarına basın.

    ::: moniker range=">=vs-2019"
    Kolay bir adla bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Ekle hata**  >  **ayıkla'ya (veya** Ctrl Alt P   +  **tuşlarına**  +  **basın) seçin.**

    > [!TIP]
    > Visual Studio 2017'den başlayarak, bu adımları kullanarak işleme ilk kez iliştirilme işlemini tamamlayarak, İşleme Yeniden Ekle'de Hata Ayıkla'ya  >   (veya **Shift**  +  **Alt**  +  **P'ye** basarak) aynı işleme hızla yeniden iliştirebilirsiniz.

5. İşleme **Ekle iletişim** kutusunda, ekleyebilirsiniz tarayıcı örneklerinin filtrelenmiş bir listesini elde edin.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, Hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium)** için doğru hata  ayıklayıcıyı seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome veya **kenar** yazın. 
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de, 2017'de, Ekle  alanına **Webkit** kodu'u seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome yazın. 
    ::: moniker-end

6. Doğru konak bağlantı noktasıyla tarayıcı işlemini seçin (bu örnekte localhost) ve **Ekle'yi seçin.**

    Doğru tarayıcı örneğini seçmenize yardımcı olmak için  Başlık alanında bağlantı noktası (1337) de görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnek, bunun Microsoft Edge (Chromium) tarayıcısını nasıl göründüğünü gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM Gezgini ve JavaScript Konsolu açık olduğunda hata ayıklayıcının doğru şekilde ekli olduğunu Visual Studio. Bu hata ayıklama araçları Chrome Geliştirici Araçları ve F12 Tools'a benzer Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcısı eklenmezse ve "İşlem ekli değil. Bir işlem geçerli durumda yasal değildir." hata ayıklama modunda tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engel ediyor olabilir.

7. Kesme noktasıyla kod zaten yürütülür olduğundan, kesme noktasıyla bağlantı noktasıyla bağlantı için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kod (**F5**, F10 ve **F11)** adım adım ilerleyerek hata ayıklayıcıyı **ilerletebilirsiniz.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

    Kesme noktası, daha önce *hangi adımlarıapp-bundle.js* ortamınız ve tarayıcı durumunuz ile birlikte *app.tsx'te* veya eşlenmiş konumda olabilir. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

   * *app.tsx* dosyasındaki kodu kesmeniz gerekirse ve bunu yapamazsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi İşleme Ekle'ye kullanın.  Ortamınız doğru şekilde ayarlanmış olduğundan emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırmak için Chrome uzantıları dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi'ni kullanarak). Tarayıcıyı hata ayıklama modunda başlatın.

      * Kaynak eşleme dosyanız için *./app.tsx* başvurusu olduğundan ve *webpack:///./app.tsx'ye* başvuru içerir. Bu, Visual Studio hata ayıklayıcısının *app.tsx dosyasını bulmasını önler.*
       Alternatif olarak, *app.tsx'te* koda izin veremiyorsanız ve bunu yapamazsanız `debugger;` *app.tsx'te* deyimini kullanmayı deneyin veya Chrome Geliştirici Araçları'de (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlamayı deneyin.

   * app-bundle.js'de koda *app-bundle.js* ve bunu yapamazsanız, *app-bundle.js.map kaynak eşleme dosyasını kaldırın.*

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)
