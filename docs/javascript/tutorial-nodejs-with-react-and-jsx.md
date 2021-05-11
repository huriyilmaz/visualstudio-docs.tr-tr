---
title: Node.js oluşturma ve uygulama tepki verme
description: Visual Studio şablonundan Node.js Web uygulaması projesi oluşturmayı öğrenin.
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 80516adffcb058d6ce28751e7a9f30002ca3a640
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729305"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Visual Studio 'da Node.js oluşturma ve uygulama tepki verme

Visual Studio, kolayca bir Node.js projesi oluşturmanıza ve IntelliSense ve Node.js destekleyen diğer yerleşik özelliklerle karşılaşmanızı sağlar. Visual Studio için bu öğreticide, Visual Studio şablonundan bir Node.js Web uygulaması projesi oluşturacaksınız. Daha sonra, yanıt verme kullanarak basit bir uygulama oluşturursunuz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * NPM paketleri Ekle
> * Uygulamanıza tepki verme kodu ekleme
> * Derleyin JSX
> * Hata ayıklayıcıyı iliştirme

## <a name="before-you-begin"></a>Başlamadan önce

İşte size bazı önemli kavramlara yol açmaya yönelik hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafını yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPM nedir?

NPM, Node.js için varsayılan paket yöneticisidir. Paket Yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamasını ve paylaşmasını kolaylaştırır ve kitaplıkları yükleme, güncelleştirme ve kaldırmayı basitleştirecek şekilde tasarlanmıştır.

### <a name="what-is-react"></a>Ne kadar tepki var?

Tepki verme, bir kullanıcı arabirimi oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX, genellikle UI öğelerini tanımlamaya tepki vererek kullanılan bir JavaScript sözdizimi uzantısıdır. JSX kodu, bir tarayıcıda çalışmadan önce transpiled ile düz JavaScript olmalıdır.

### <a name="what-is-webpack"></a>Webpack nedir?

webpack, JavaScript dosyalarını bir tarayıcıda çalıştıracak şekilde paketler. Ayrıca diğer kaynakları ve varlıkları da dönüştürebilirsiniz veya paketler. JSX veya TypeScript kodunu düz JavaScript'e transpile etmek için genellikle Babel veya TypeScript gibi bir derleyici belirtmek için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Uygulama ve Visual Studio geliştirme iş Node.js gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![VS YükleyicisiNode.js de iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js yüklü olmalıdır.

    Bu öğretici 12.6.2 sürümüyle test edilmiştir.

    Yüklü yoksa, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için [ LTS ](https://nodejs.org/en/download/) sürümünüNode.jsweb sitesinden yüklemenizi öneririz. Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır. Node.js iş yüküne dahil Visual Studio araçları her Node.js sürümleri destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca birinin yüklü olduğunu destekler.

    Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanlarına başvuracak şekilde yapılandırabilirsiniz (proje oluşturduk sonra proje düğümüne sağ tıklayın, Özellikler'i seçin **(veya** **Alt** Enter tuşuna basın) veNode.exe  +   **yolunu ayarlayın).** Bir yerel yorumlayıcının Node.js yüklemesini kullanabilir veya her bir yerel yorumlayıcının yolunu Node.js belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir web Node.js projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve sonra **Web uygulaması-JavaScript Node.js boş** seçeneğini belirleyin. (Bu öğretici TypeScript derleyicisini kullanıyor olsa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.)
    
    Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde **JavaScript**' i ve ardından **Node.js**' yi seçin. Orta bölmede, **boş Node.js Web uygulaması**' nı seçin, **Nodejswebappblank** adını yazın ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi açar.

    ![Çözüm Gezgini Node.js proje](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1), **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler** ' i seçerek (veya **alt** Enter ' a basarak) projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz  +  . Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *package.js* ' deki ayarları ve NPM düğümündeki sağ tıklama seçenekleri ' ni kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

    (4) *package.js,* npm tarafından yerel olarak yüklenmiş paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5)server.js *gibi* proje dosyaları proje düğümü altında gösterir. *server.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**

## <a name="add-npm-packages"></a>npm paketleri ekleme

Bu uygulamanın doğru çalışması için bir dizi npm modülü gerekir.

* Tepki
* react-dom
* express
* path
* ts-loader
* typescript
* Webpack
* webpack-cli

1. Yeni Çözüm Gezgini (sağ bölme) altında, projedeki **npm** düğümüne sağ tıklayın ve Yeni **npm Paketleri Yükle'yi seçin.**

    Yeni **npm Paketlerini Yükle iletişim** kutusunda, en güncel paket sürümünü yükleyebilir veya bir sürüm belirtebilirsiniz. Bu paketlerin geçerli sürümünü yüklemeyi seçerseniz, ancak daha sonra beklenmeyen hatalarla karşılaşacaksanız, bu adımların sonraki adımlarında açıklanan tam paket sürümlerini yüklemek iyi olabilir.

1. Yeni **npm Paketlerini Yükle iletişim kutusunda** react paketini arayın ve Paketi **Yükle'yi seçerek** yükleyin.

    ![npm paketlerini yükleme](../javascript/media/tutorial-nodejs-react-install-package.png)

    Paketi **yüklemenin** ilerlemesini görmek için Çıkış penceresini seçin (Çıktıyı göster alanında **Npm'yi** seçin).  Paket yüklendikten sonra **npm** düğümü altında görünür.

    Projenin dosya *package.js,* paket sürümü de dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

1. Tek seferde paketleri aramak ve geri kalanını eklemek için Kullanıcı arabirimini kullanmak yerine, aşağıdaki kodu *üzerinepackage.js* yapıştırın. Bunu yapmak için `dependencies` şu kodla bir bölüm ekleyin:

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

    `dependencies`Boş şablon sürümünüzde zaten bir bölüm varsa, bunu ÖNCEKI JSON kodu ile değiştirmeniz yeterlidir. Bu dosyanın kullanımı hakkında daha fazla bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).

1. Değişiklikleri kaydedin.

1. Projenizde **NPM** düğümüne sağ tıklayın ve **NPM paketlerini yüklensin**' i seçin.

    Bu komut NPM install komutunu doğrudan çalıştırır.

    Alt bölmede, paketlerin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıktıyı görmek için **Çıkış** penceresindeki çıktıyı **göster** alanında **NPM** ' yi seçtiğinizden emin olun. (Pencereyi açmak için **Görünüm**  >  ' ü seçin. **Çıktı** veya **CTRL**  +  **alt**  +  **O** tuşlarına basın.)

    Çözüm Gezgini, yüklendikten sonra görüntülenen NPM modüllerdir.

    ![NPM paketleri](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Komut satırını kullanarak NPM paketlerini yüklemeyi tercih ediyorsanız, proje düğümüne sağ tıklayın ve **burada komut Istemi aç**' ı seçin. Paketleri yüklemek için standart Node.js komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları Ekle

Bu adımlarda, projenize dört yeni dosya eklersiniz.

* *App. TSX*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Bu basit uygulama için, proje köküne yeni proje dosyaları eklersiniz. (Çoğu uygulamalarda, genellikle dosyaları alt klasörlere ekler ve göreli yol başvurularını uygun şekilde ayarlayabilirsiniz.)

1. Çözüm Gezgini ' de proje **nodejswebappblank** öğesine sağ tıklayın ve yeni öğe **Ekle**' yi seçin  >   (veya **CTRL**  +  **+ SHIFT**  +  **A** tuşlarına basın).

1. **Yeni öğe Ekle** Iletişim kutusunda **TypeScript JSX dosyası**' nı seçin, *app. TSX* adını yazın ve **Ekle** veya **Tamam**' ı seçin.

1. *webpack-config.js* eklemek için bu adımları tekrarlayın. TypeScript JSX dosyası yerine **JavaScript dosyası**' nı seçin.

1. Projeye *index.html* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **HTML dosyası**' nı seçin.

1. Projeye *tsconfig.js* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **TYPESCRIPT JSON yapılandırma dosyası**' nı seçin.

## <a name="add-app-code"></a>Uygulama kodu ekle

1. *server.js* açın ve mevcut kodu şu kodla değiştirin:

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

   Yukarıdaki kod, Web uygulaması sunucunuz olarak Node.js başlatmak için Express 'ı kullanır. Bu kod, bağlantı noktasını proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar (varsayılan olarak, bağlantı noktası özelliklerde 1337 olarak yapılandırılır). Proje özelliklerini açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Özellikler**' i seçin.

1. *App. TSX* ' i açın ve aşağıdaki kodu ekleyin:

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

    Yukarıdaki kod JSX söz dizimini kullanır ve basit bir ileti göstermek için tepki verir.

1. *index.html* 'yi açın ve **Body** bölümünü aşağıdaki kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML sayfası, JSX ve transpiled kodunu düz JavaScript 'e içeren *app-bundle.js* yükler. Şu anda *app-bundle.js* boş bir dosyadır. Sonraki bölümde, kodu derleyin için seçenekleri yapılandırırsınız.

## <a name="configure-webpack-and-typescript-compiler-options"></a>WebPack ve TypeScript derleyici seçeneklerini yapılandırma

Önceki adımlarda projeye *webpack-config.js* eklediniz. Ardından, Web paketi yapılandırma kodu ekleyin. Paketleme ve transpiling JSX için bir giriş dosyası (*app. TSX*) ve bir çıkış dosyası (*app-bundle.js*) belirten basit bir Web paketi yapılandırması ekleyerek düz JavaScript 'e ekleyeceksiniz. Transpiling için bazı TypeScript derleyici seçeneklerini de yapılandırırsınız. Bu kod, WebPack ve TypeScript derleyicisine giriş olarak tasarlanan temel bir yapılandırmadır.

1. Çözüm Gezgini ' de *webpack-config.js* açın ve aşağıdaki kodu ekleyin.

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

    WebPack yapılandırma kodu, WebPack 'in JSX derleyin için TypeScript yükleyicisini kullanmasını söyler.

1. *tsconfig.js* açın ve varsayılan kodu, TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

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

    *app. TSX* , kaynak dosya olarak belirtilir.

## <a name="transpile-the-jsx"></a>JSX derleyin

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve ardından **komut Istemi aç**' ı seçin.

1. Komut isteminde aşağıdaki komutu yazın:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Komut istemi penceresi sonucu gösterir.

    ![WebPack 'i Çalıştır](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Yukarıdaki çıkış yerine herhangi bir hata görürseniz, uygulamanızın çalışması için önce bu hataları çözmeniz gerekir. NPM paket sürümleriniz Bu öğreticide gösterilen sürümlerden farklıysa, bu bir hata kaynağı olabilir. Hataları gidermenin bir yolu, önceki adımlarda gösterilen sürümlerin aynısını kullanmaktır. Ayrıca, bu paket sürümlerinden bir veya daha fazlası kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için *üzerindepackage.js* kullanma hakkında bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Var Olan Klasör Ekle'yi seçin, ardından  >   *dist klasörünü* seçin ve Klasör **Seç'i seçin.**

    Visual Studio,app-bundle.jsve *app-bundle.js.map'i içeren*  *dist* klasörünü projeye ekler.

1. JavaScript *app-bundle.js* görmek içinapp-bundle.js'yi açın.

1. Harici olarak değiştirilmiş dosyaları yeniden yüklemek istenirse, Evet'i **All (Tüm dosyalar) olarak seçin.**

    ![Değiştirilen dosyaları yükleme](../javascript/media/tutorial-nodejs-react-reload-files.png)

*app.tsx üzerinde her değişiklik* yaptığınız zaman webpack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatikleştirmek için JSX'i transpile etmek için bir derleme betiği ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX'i transpile etmek için derleme betiği ekleme

2019'Visual Studio başlayarak bir derleme betiği gerekir. JSX'i komut satırına (önceki bölümde gösterildiği gibi) çeviri yapmak yerine, JSX'i komut satırına Visual Studio.

* Aşağıdaki *package.jsaçın* ve bölümünden sonra aşağıdaki bölümü `dependencies` ekleyin:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
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

    Chrome makineniz üzerinde kullanılabilir ancak seçenek olarak göstermüyorsa, hata ayıklama hedefi açılan listesinden Birlikte Gözat'ı seçin ve varsayılan tarayıcı hedefi olarak Chrome'u seçin (Varsayılan Olarak **Ayarla'ya tıklayın).** 

1. Uygulamayı çalıştırmak için **F5** **(** Hata AyıklamaYı  >  **Başlat**) veya yeşil ok düğmesine basın.

    Hata Node.js dinleyen bağlantı noktasını gösteren bir konsol penceresi açılır.

    Visual Studio başlangıç dosyasını başlatarak uygulamayı başlatır ve *server.js.*

    ![React'i tarayıcıda çalıştırma](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Bir kesme noktası ayarlayın ve uygulamayı çalıştırın

1. *server.js*, `staticPath` bir kesme noktası ayarlamak için bildirimin solundaki cilt payın içine tıklayın:

    ![server.js için Visual Studio Code penceresinin ekran görüntüsü. Sol cilt Paydaki kırmızı nokta, staticPath bildirimi için bir kesme noktası ayarlandığını gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

1. Uygulamayı çalıştırmak için **F5** tuşuna basın (**hata ayıklama**  >  **başlatma hata ayıklaması**).

    Hata ayıklayıcı ayarladığınız kesme noktasında duraklatılır (geçerli ifade sarı olarak işaretlenir). Artık, şu anda kapsamda olan değişkenlerin üzerine giderek, **Yereller** ve **izleme** pencereleri gibi hata ayıklayıcı pencereleri kullanarak uygulamanızın durumunu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçları veya F12 araçlarını kullanmak istiyorsanız **F12** tuşuna basın. Bu araçları, DOM 'ı incelemek ve JavaScript konsolunu kullanarak uygulamayla etkileşim kurmak için kullanabilirsiniz.

1. Web tarayıcısını ve konsolunu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafı tepki verme kodunda bir kesme noktası ayarlama ve isabet

Önceki bölümde, hata ayıklayıcıyı sunucu tarafı Node.js koduna eklemiş olursunuz. Hata ayıklayıcıyı Visual Studio 'dan iliştirmek ve istemci tarafı tepki kodunda isabet kesme noktaları eklemek için, hata ayıklayıcının doğru süreci belirlemesine yardımcı olması gerekir. Bunu etkinleştirmenin bir yolu aşağıda verilmiştir.

### <a name="prepare-the-browser-for-debugging"></a>Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için, IDE veya Chrome 'da **Microsoft Edge Beta** adlı Microsoft Edge (Kmıum) kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome ' ı kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu önliyor olabilir, bu nedenle Beklenmeyen Chrome örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekir.)

   ::: moniker range=">=vs-2019"
   Bu Microsoft Edge (Chromium) chrome'un tüm örneklerini de kapatır. her iki tarayıcı da chromium kod tabanını paylaştığı için en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinleştirildiğinde tarayıcınızı başlatabilirsiniz.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, Hata Ayıklama araç çubuğundan `--remote-debugging-port=9222` **Gözat...**  >'yi ve ardından Ekle'yi seçerek ve ardından Bağımsız  Değişkenler alanında bayrağını ayarlayarak tarayıcı başlatma sırasında bayrağını ayarlayın. Tarayıcı için Hata Ayıklama ile **Edge** veya Hata Ayıklama ile Chrome gibi **farklı bir kolay ad kullanın.** Ayrıntılar için bkz. [Sürüm Notları.](/visualstudio/releases/2019/release-notes-v16.2)

    ![Tarayıcınızı hata ayıklama etkin olarak açılacak şekilde ayarlama](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, **Windows** **Başlat düğmesinden** Çalıştır komutunu açın (sağ tıklayın ve **Çalıştır'ı seçin)** ve aşağıdaki komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows Başlat **düğmesinden** Çalıştır komutunu **açın** (sağ tıklayın ve Çalıştır'ı **seçin)** ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmamıştır, bu nedenle boş bir tarayıcı sayfası açılır.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğine ekleme

1. Visual Studio'a geçiş ve ardından kaynak kodunda *app.tsx* *app-bundle.js* kesme noktası ayarlayın.

    Daha *app-bundle.js* için işlevinde kesme `render()` noktası aşağıdaki çizimde gösterildiği gibi ayarlayın:

    ![Uygulama için Visual Studio penceresinin ekran app-bundle.js. Sol oluk içinde kırmızı bir nokta, işleme işlevinde bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    `render()`İşlevi transpiled *app-bundle.js* dosyasında bulmak için **CTRL** + **F** 'yi (**Düzenle**  >  **Bul ve Değiştir**  >  **hızlı bul**) kullanın.

    *App. TSX* için, deyimindeki kesme noktasını işlevin içinde ayarlayın `render()` `return` .

    ![App. TSX için Visual Studio Code penceresinin ekran görüntüsü. Sol cilt Paydaki kırmızı nokta, render işlevinin Return ifadesinde bir kesme noktası ayarlandığını gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Kesme noktasını *. TSX* dosyasında ( *app-bundle.js* yerine) ayarlıyorsanız, *webpack-config.js* güncelleştirmeniz gerekir. Aşağıdaki kodu değiştirin:

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

    Bu, Visual Studio 'da hata ayıklamayı etkinleştirmek için yalnızca geliştirme bir ayardır. Bu ayar, uygulamayı oluştururken *app-bundle.js. Map* dosyasında kaynak eşleme dosyasındaki oluşturulan başvuruları geçersiz kılmanıza olanak tanır. Varsayılan olarak, kaynak eşleme dosyasındaki WebPack başvuruları, Visual Studio 'Nun *app. TSX* kaynak dosyasını bulmasını önleyen *WebPack:///* önekini içerir. Özellikle, bu değişikliği yaptığınızda, *app. TSX* kaynak dosyasına yönelik başvuru, hata ayıklamayı sağlayan *WebPack:///./app.TSX* olarak *./app. TSX* olarak değiştirilir.

3. Visual Studio 'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin ve  + uygulamayı tarayıcıda çalıştırmak için CTRL **F5** tuşuna basın (**hata ayıklama**  >  **olmadan Başlat**).

    ::: moniker range=">=vs-2019"
    Kolay ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefi olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Ekle hata ayıkla**' yı seçin  >   (veya **CTRL**  +  **alt**  +  **P** tuşlarına basın).

    > [!TIP]
    > Visual Studio 2017 ' den itibaren, bu adımları izleyerek işleme ilk kez iliştirdikten sonra, işlem için **hata ayıklamayı** yeniden iliştirme ' yi seçerek aynı işleme hızlıca yeniden iliştirebilirsiniz  >   (veya **SHIFT**  +  **alt**  +  **P**' ye basabilirsiniz).

5. **Işleme İliştir** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, Hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium)** için doğru  hata ayıklayıcıyı  seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome veya kenar yazın. 
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de, Ekle alanında **Webkit** kodu'u  seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome yazın. 
    ::: moniker-end

6. Doğru konak bağlantı noktasıyla tarayıcı işlemini seçin (bu örnekte localhost) ve **Ekle'yi seçin.**

    Doğru tarayıcı örneğini seçmenize yardımcı olmak için  Başlık alanında bağlantı noktası (1337) de görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnekte bunun Microsoft Edge (Chromium) tarayıcısında nasıl göründüğünü gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM Gezgini ve JavaScript Konsolu açık olduğunda hata ayıklayıcının doğru şekilde ekli olduğunu Visual Studio. Bu hata ayıklama araçları, chrome için Geliştirici Araçları F12 Araçları'Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcısı eklenmezse ve "İşleme eklenemiyor. Bir işlem geçerli durumda yasal değildir." hata ayıklama modunda tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engel ediyor olabilir.

7. Kesme noktasıyla kod zaten yürütülür olduğundan, kesme noktasıyla bağlantı noktası için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kod (**F5**, F10 ve **F11)** adım adım ilerleyerek hata ayıklayıcıyı **ilerletebilirsiniz.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

    Kesme noktası, daha önce *hangi adımlarıapp-bundle.js* ortamınız ve tarayıcı durumunuz bağlı olarak *app.tsx'te* veya eşlenmişapp-bundle.js'de isabet edersiniz. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

   * *App. TSX* içindeki koda ayırmanız ve bunu yapamaması gerekiyorsa, hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi **işlemek için İliştir** ' i kullanın. Ortamınızın doğru ayarlandığından emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları da dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi kullanılarak). Tarayıcıyı hata ayıklama modunda başlattığınızdan emin olun.

      * Kaynak eşleme dosyanızın, Visual Studio hata ayıklayıcısının *app. TSX*' i bulmasını önleyen *./app.exe* ( *WebPack:///./app.TSX* değil) öğesine yönelik bir başvuru içerdiğinden emin olun.
       Alternatif olarak, *app. TSX* içindeki koda bir kod kesmeniz ve bunu yapamazsanız, `debugger;` *app. TSX* içindeki ifadesini kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları (veya Microsoft Edge için F12 araçları) kesme noktaları ayarlayın.

   * *app-bundle.js* kodu kesmeniz gerekiyorsa ve bunu yapamadığından, *app-bundle.js. map* kaynak eşleme dosyasını kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)
