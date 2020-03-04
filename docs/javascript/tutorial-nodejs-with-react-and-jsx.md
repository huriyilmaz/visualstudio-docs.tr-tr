---
title: Node. js ve tepki verme uygulaması oluşturma
description: Bu öğreticide, Visual Studio için Node. js Araçları ' nı kullanarak bir uygulama oluşturacaksınız
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f60cd71f1dda4e401acef1db9ccd8c5a0be2b961
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235099"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Visual Studio 'da Node. js ve tepki verme uygulaması oluşturma

Visual Studio, kolayca bir Node. js projesi oluşturmanıza, IntelliSense ve Node. js ' nin desteklediği diğer yerleşik özelliklerle karşılaşmanızı sağlar. Visual Studio için bu öğreticide, bir Visual Studio şablonundan bir Node. js web uygulaması projesi oluşturacaksınız. Daha sonra, yanıt verme kullanarak basit bir uygulama oluşturursunuz.

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * NPM paketleri Ekle
> * Uygulamanıza tepki verme kodu ekleme
> * Derleyin JSX
> * Hata ayıklayıcıyı iliştirme

## <a name="before-you-begin"></a>Başlamadan önce

İşte size bazı önemli kavramlara yol açmaya yönelik hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node. js nedir?

Node. js, JavaScript sunucu tarafını yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPM nedir?

NPM, Node. js için varsayılan paket yöneticisidir. Paket Yöneticisi, programcıların Node. js kitaplıklarının kaynak kodunu yayımlamasını ve paylaşmasını kolaylaştırır ve kitaplıkları yükleme, güncelleştirme ve kaldırma işlemlerini basitleştirmek üzere tasarlanmıştır.

### <a name="what-is-react"></a>Ne kadar tepki var?

Tepki verme, bir kullanıcı arabirimi oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX, genellikle UI öğelerini tanımlamaya tepki vererek kullanılan bir JavaScript sözdizimi uzantısıdır. JSX kodu, bir tarayıcıda çalışmadan önce transpiled ile düz JavaScript olmalıdır.

### <a name="what-is-webpack"></a>WebPack nedir?

Web paketi, JavaScript dosyalarını bir tarayıcıda çalışabilecek şekilde paketler. Ayrıca diğer kaynakları ve varlıkları dönüştürebilir veya paketleyebilir. Genellikle Babel veya TypeScript gibi bir derleyicinin basit JavaScript 'e derleyin JSX veya TypeScript kodunu belirtmek için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. **Node. js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![Node.js iş yükü VS yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanı yüklü olması gerekir.

    Bu öğretici sürüm 10.16.0 ile test edilmiştir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node. js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Visual Studio 'daki Node. js Araçları, Node. js iş yüküne dahil edilmiştir, her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node. js yükleyicisi yalnızca aynı anda yüklü olan birini destekler.
    
    Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node. exe yolunu**ayarlayın). Node. js ' nin genel bir yüklemesini kullanabilir veya Node. js projelerinizdeki her bir yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Node. js web uygulaması projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node. js**yazın ve **boş Node. js web uygulaması-JavaScript**' i seçin. (Bu öğretici TypeScript derleyicisini kullanıyor olsa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.)
    
    Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede **boş Node. js web uygulaması**' nı seçin, **Nodejswebappblank**adını yazın ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node. js web uygulaması** proje şablonunu görmüyorsanız **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi açar.

    ![Çözüm Gezgini 'de Node. js projesi](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1), **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler**' i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz. Proje dosyası Node. js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *Package. JSON* ' daki ayarları kullanarak paketleri yükleyip güncelleyebilir ve NPM düğümündeki Seçenekler ' e sağ tıklayın.

    (4) *Package. JSON* , NPM tarafından yerel olarak yüklenen paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek üzere kullanılan bir dosyadır. Bu dosya hakkında daha fazla bilgi için bkz [. Package. JSON yapılandırması](../javascript/configure-packages-with-package-json.md)

    (5) *Server. js* gibi proje dosyaları proje düğümünün altında görünür. *Server. js* , proje başlangıç dosyasıdır ve bu nedenle **kalın**olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node. js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

## <a name="add-npm-packages"></a>NPM paketleri Ekle

Bu uygulama, doğru bir şekilde çalışması için birkaç NPM modülü gerektirir.

* react
* tepki verme-Dom
* çaba
* yol
* TS-yükleyici
* TypeScript
* Web paketi
* webpack-cli

1. Çözüm Gezgini (sağ bölme) menüsünde, projedeki **NPM** düğümüne sağ tıklayın ve **Yeni NPM paketleri yüklensin**' i seçin.

    **Yeni NPM paketlerini yükler** iletişim kutusunda, en güncel paket sürümünü yüklemeyi veya bir sürüm belirtmeyi seçebilirsiniz. Bu paketlerin geçerli sürümünü yüklemeyi seçer, ancak daha sonra beklenmeyen hatalar halinde çalıştırırsanız, bu adımlarda daha sonra açıklanan paket sürümlerinin aynısını yüklemeniz gerekebilir.

1. **Yeni NPM paketlerini yükler** iletişim kutusunda, yanıt verme paketini arayın ve paketi yüklemek Için **paketi yüklensin** ' i seçin.

    ![NPM paketlerini yükler](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Paketin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin ( **çıktıyı göster** alanından **NPM** ' yi seçin). Yüklendiğinde, paket **NPM** düğümünün altında görüntülenir.

    Projenin *Package. JSON* dosyası, paket sürümü de dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

1. Tek seferde paketleri aramak ve geri kalanını eklemek için Kullanıcı arabirimini kullanmak yerine, aşağıdaki kodu *Package. JSON*dosyasına yapıştırın. Bunu yapmak için, bu kodla bir `dependencies` bölümü ekleyin:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Boş şablon sürümünüzde zaten bir `dependencies` bölümü varsa, bunu önceki JSON kodu ile değiştirmeniz yeterlidir. Bu dosyanın kullanımı hakkında daha fazla bilgi için bkz. [Package. JSON yapılandırması](../javascript/configure-packages-with-package-json.md).

1. Değişiklikleri kaydedin.

1. Projenizde **NPM** düğümüne sağ tıklayın ve **NPM paketlerini Güncelleştir**' i seçin.

    Alt bölmede, paketlerin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıktıyı görmek için **Çıkış** penceresindeki çıktıyı **göster** alanında **NPM** ' yi seçtiğinizden emin olun.

    Çözüm Gezgini, yüklendikten sonra görüntülenen NPM modüllerdir.

    ![NPM paketleri](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Komut satırını kullanarak NPM paketlerini yüklemeyi tercih ediyorsanız, proje düğümüne sağ tıklayın ve **burada komut Istemi aç**' ı seçin. Paketleri yüklemek için standart Node. js komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları Ekle

Bu adımlarda, projenize dört yeni dosya eklersiniz.

* *App. TSX*
* *WebPack-config. js*
* *index. html*
* *tsconfig. JSON*

Bu basit uygulama için, proje köküne yeni proje dosyaları eklersiniz. (Çoğu uygulamalarda, genellikle dosyaları alt klasörlere ekler ve göreli yol başvurularını uygun şekilde ayarlayabilirsiniz.)

1. Çözüm Gezgini ' de proje **Nodejswebappblank** öğesine sağ tıklayın ve > **Yeni öğe** **Ekle** ' yi seçin.

1. **Yeni öğe Ekle** Iletişim kutusunda **TypeScript JSX dosyası**' nı seçin, *app. TSX*adını yazın ve **Ekle** veya **Tamam**' ı seçin.

1. *WebPack-config. js*eklemek için bu adımları tekrarlayın. TypeScript JSX dosyası yerine **JavaScript dosyası**' nı seçin.

1. Projeye *index. html* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **HTML dosyası**' nı seçin.

1. Projeye *tsconfig. json dosyasını* eklemek için aynı adımları yineleyin. JavaScript dosyası yerine **TYPESCRIPT JSON yapılandırma dosyası**' nı seçin.

## <a name="add-app-code"></a>Uygulama kodu ekle

1. *Server. js* ' ye açın ve mevcut kodu şu kodla değiştirin:

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

   Yukarıdaki kod Express kullanarak Node. js ' i Web uygulaması sunucunuz olarak başlatır. Bu kod, bağlantı noktasını proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar (varsayılan olarak, bağlantı noktası özelliklerde 1337 olarak yapılandırılır). Proje özelliklerini açmak için Çözüm Gezgini içinde projeye sağ tıklayın ve **Özellikler**' i seçin.

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

1. *İndex. html* dosyasını açın ve **Body** bölümünü şu kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML sayfası *App-Bundle. js*' yı, JSX ve yanıt kodu transpiled ' nı düz JavaScript 'e yükler. Şu anda, *App-Bundle. js* boş bir dosyadır. Sonraki bölümde, kodu derleyin için seçenekleri yapılandırırsınız.

## <a name="configure-webpack-and-typescript-compiler-options"></a>WebPack ve TypeScript derleyici seçeneklerini yapılandırma

Önceki adımlarda, *WebPack-config. js* ' yi projeye eklediniz. Ardından, Web paketi yapılandırma kodu ekleyin. Bir giriş dosyası (*app. TSX*) ve bir çıkış dosyası (*App-Bundle. js*) ve transpiling JSX ' i düz JavaScript 'e göre belirten bir basit Web paketi yapılandırması ekleyeceksiniz. Transpiling için bazı TypeScript derleyici seçeneklerini de yapılandırırsınız. Bu kod, WebPack ve TypeScript derleyicisine giriş olarak tasarlanan temel bir yapılandırmadır.

1. Çözüm Gezgini ' de, *WebPack-config. js* ' yi açın ve aşağıdaki kodu ekleyin.

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

1. *Tsconfig. JSON* dosyasını açın ve varsayılan kodu, TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

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

    ![WebPack 'i Çalıştır](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Yukarıdaki çıkış yerine herhangi bir hata görürseniz, uygulamanızın çalışması için önce bu hataları çözmeniz gerekir. NPM paket sürümleriniz Bu öğreticide gösterilen sürümlerden farklıysa, bu bir hata kaynağı olabilir. Hataları gidermenin bir yolu, önceki adımlarda gösterilen sürümlerin aynısını kullanmaktır. Ayrıca, bu paket sürümlerinden bir veya daha fazlası kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için *Package. JSON* kullanma hakkında daha fazla bilgi için bkz. [Package. JSON Configuration](../javascript/configure-packages-with-package-json.md).

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve > **var olan klasörü** **Ekle** ' yi seçin, sonra da *Dist* klasörünü seçip **Klasör Seç**' i seçin.

    Visual Studio, *App-Bundle. js* ve *App-Bundle. js. Map*içeren proje için *Dist* klasörünü ekler.

1. Transpiled JavaScript kodunu görmek için *App-Bundle. js* dosyasını açın.

1. Dışarıdan değiştirilen dosyaları yeniden yüklemeniz istenirse, **Tümüne Evet**' i seçin.

    ![Değiştirilen dosyaları yükle](../javascript/media/tutorial-nodejs-react-reload-files.png)

*App. TSX*üzerinde her değişiklik yaptığınızda WebPack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatik hale getirmek için, derleyin için JSX 'e bir derleme betiği ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX derleyin 'e derleme betiği ekleme

Visual Studio 2019 ' den başlayarak bir derleme betiği gereklidir. Transpiling JSX yerine, komut satırında (yukarıdaki bölümde gösterildiği gibi), Visual Studio 'dan oluştururken JSX derleyin sağlayabilirsiniz.

* *Package. JSON* ' i açın ve `dependencies` bölümünden sonra aşağıdaki bölümü ekleyin:

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Geçerli hata ayıklama hedefi olarak Microsoft Edge veya Chrome seçeneklerinden birini belirleyin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefi olarak Chrome seçin](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefi olarak Chrome seçin](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa, **Web tarayıcısı (BrowserName)** öğesini seçin > hata ayıklama hedefi açılır listesinden **Web tarayıcısı** ' nı seçin ve varsayılan tarayıcı hedefi olarak **Chrome** ' ı seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa **Web tarayıcısı (BrowserName)** hata ayıklama hedefi açılır listesinden **Google Chrome** > seçin ve varsayılan tarayıcı hedefi olarak **Chrome** ' ı seçin.
    ::: moniker-end

1. Uygulamayı çalıştırmak için **F5** tuşuna**basın (hata ayıklama** > **başlangıç hata ayıklaması**) veya yeşil ok düğmesi.

    Hata ayıklayıcının dinlediği bağlantı noktasını gösteren bir Node. js konsol penceresi açılır.

    Visual Studio, *Server. js*başlangıç dosyasını başlatarak uygulamayı başlatır.

    ![Tarayıcıda tepki verme](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Bir kesme noktası ayarlayın ve uygulamayı çalıştırın

1. *Server. js*' de, bir kesme noktası ayarlamak için `staticPath` bildiriminin solundaki cilt paya tıklayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir.

1. Uygulamayı çalıştırmak için **F5** tuşuna basın (**hata** ayıklama > hata **ayıklamayı Başlat**).

    Hata ayıklayıcı ayarladığınız kesme noktasında duraklatılır (geçerli ifade sarı olarak işaretlenir). Artık, şu anda kapsamda olan değişkenlerin üzerine giderek, **Yereller** ve **izleme** pencereleri gibi hata ayıklayıcı pencereleri kullanarak uygulamanızın durumunu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçları veya F12 araçlarını kullanmak istiyorsanız **F12**tuşuna basın. Bu araçları, DOM 'ı incelemek ve JavaScript konsolunu kullanarak uygulamayla etkileşim kurmak için kullanabilirsiniz.

1. Web tarayıcısını ve konsolunu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafı tepki verme kodunda bir kesme noktası ayarlama ve isabet

Önceki bölümde, hata ayıklayıcıyı sunucu tarafı Node. js koduna eklemiş olursunuz. Hata ayıklayıcıyı Visual Studio 'dan iliştirmek ve istemci tarafı tepki kodunda isabet kesme noktaları eklemek için, hata ayıklayıcının doğru süreci belirlemesine yardımcı olması gerekir. Bunu etkinleştirmenin bir yolu aşağıda verilmiştir.

### <a name="prepare-the-browser-for-debugging"></a>Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için, IDE veya Chrome 'da **Microsoft Edge Beta** adlı Microsoft Edge (Kmıum) kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome ' ı kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri tarayıcının hata ayıklama etkinken açılmasını önleyebilir. (Tarayıcı uzantıları çalışıyor olabilir ve tam hata ayıklama modunu engelleyebilir, bu nedenle beklenmedik Chrome örneklerini bulmak için Görev Yöneticisi 'Ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için tüm Chrome örneklerini de kapatın. Her iki tarayıcı de kmıum Code tabanını paylaştığından, bu en iyi sonuçları verir.
   ::: moniker-end

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için tüm Chrome örneklerini de kapatın. Her iki tarayıcı de kmıum Code tabanını kullandığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' den başlayarak, tarayıcı > başlatma sırasında `--remote-debugging-port=9222` bayrağını **hata ayıklama** araç çubuğundan ve sonra **Ekle** **' yi seçip** , sonra da **bağımsız değişkenler** alanında bayrağını ayarlayarak ayarlayabilirsiniz. Hata **ayıklamayla**hata ayıklama veya Chrome **ile kenar** gibi farklı bir kolay ad kullanın. Ayrıntılar için bkz. [sürüm notları](/visualstudio/releases/2019/release-notes-v16.2).

    ![Tarayıcınızı hata ayıklama etkinken açılacak şekilde ayarlama](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `msedge --remote-debugging-port=9222`

    veya,

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmıyor, bu nedenle boş bir tarayıcı sayfası alırsınız.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğe iliştirme

1. Visual Studio 'ya geçin ve kaynak kodunuzda *App-Bundle. js* ya da *app. TSX*olarak bir kesme noktası ayarlayın.

    *App-Bundle. js*için, aşağıdaki çizimde gösterildiği gibi `render()` işlevindeki kesme noktasını ayarlayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Transpiled *App-Bundle. js* dosyasında `render()` işlevini bulmak için **CTRL**+**F** (**Düzenle** > **Bul ve Değiştir** > **hızlı bul**) kullanın.

    *App. TSX*için, `return` deyimindeki `render()` işlevinin içinde kesme noktası ayarlayın.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Kesme noktasını *. TSX* dosyasında ( *App-Bundle. js*yerine) ayarlıyorsanız, *WebPack-config. js*' yi güncelleştirmeniz gerekir. Aşağıdaki kodu değiştirin:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    Bu kod ile:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Bu, Visual Studio 'da hata ayıklamayı etkinleştirmek için yalnızca geliştirme bir ayardır. Bu ayar, uygulamayı oluştururken *App-Bundle. js. Map*kaynak eşleme dosyasındaki oluşturulan başvuruları geçersiz kılmanızı sağlar. Varsayılan olarak, kaynak eşleme dosyasındaki WebPack başvuruları, Visual Studio 'Nun *app. TSX*kaynak dosyasını bulmasını önleyen *WebPack:///* önekini içerir. Özellikle, bu değişikliği yaptığınızda, *app. TSX*kaynak dosyasına yönelik başvuru, hata ayıklamayı sağlayan *WebPack:///./app.TSX* olarak *./app. TSX*olarak değiştirilir.

3. Visual Studio 'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl**+**F5** tuşuna**basın (hata ayıklama > ** **başlatın**).

    ::: moniker range=">=vs-2019"
    Kolay ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefi olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. **Işleme eklemek** > **Hata Ayıkla** ' yı seçin.

    > [!TIP]
    > Visual Studio 2017 ' den başlayarak, bu adımları izleyerek işleme ilk kez iliştirdikten sonra, **işlem için yeniden iliştir** > **Hata Ayıkla** ' yı seçerek aynı işleme hızlıca tekrar iliştirebilirsiniz.

5. **Işleme İliştir** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, arama sonuçlarını filtrelemek için hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge-ku)** için doğru hata ayıklayıcıyı seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de, **Ekle** alanına **WebKit Code** ' u seçin, arama sonuçlarını filtrelemek için filtre kutusuna **Chrome** yazın.
    ::: moniker-end

6. Doğru ana bilgisayar bağlantı noktasıyla (Bu örnekte localhost) tarayıcı işlemini seçin ve **Ekle**' yi seçin.

    Doğru tarayıcı örneğini seçmenize yardımcı olması için, **başlık** alanında bağlantı noktası (1337) de görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnekte bunun Microsoft Edge (Kmıum) tarayıcısı için nasıl göründüğü gösterilmektedir.

    ![İşleme İliştir](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme İliştir](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Visual Studio 'da DOM Gezgini ve JavaScript konsolu açıldığında hata ayıklayıcının doğru şekilde eklenmiş olduğunu bilirsiniz. Bu hata ayıklama araçları, Microsoft Edge için Chrome Geliştirici Araçları ve F12 araçlarına benzerdir.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcı iliştirilemez ve "işleme iliştirilemiyor" iletisini görürsünüz. İşlem geçerli durumda geçerli değil. ", tarayıcı hata ayıklama modunda başlatılmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi 'Ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modu engelleniyor olabilir.

7. Kesme noktası olan kod zaten yürütüldüğünden, kesme noktasına isabet etmek için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklalarken, değişkenlerin üzerine giderek ve hata ayıklayıcı pencerelerini kullanarak uygulamanızın durumunu inceleyebilirsiniz. Kod aracılığıyla (**F5**, **F10**ve **F11**) hata ayıklayıcıyı ilerleyebilirsiniz. Temel hata ayıklama özellikleri hakkında daha fazla bilgi için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

    Daha önce, ortamınız ve tarayıcı durumlarınızla birlikte, daha önce izlediğiniz adımlara bağlı olarak, *App-Bundle. js* ya da *app. TSX*içindeki eşleştirilmiş konumunda kesme noktasına ulaşırsınız. Her iki durumda da kodun içinde ilerleyebileceğiniz değişkenleri inceleyebilirsiniz.

   * *App. TSX* içindeki koda ayırmanız ve bunu yapamaması gerekiyorsa, hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi **işlemek için İliştir** ' i kullanın. Ortamınızın doğru ayarlandığından emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları da dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi kullanılarak). Tarayıcıyı hata ayıklama modunda başlattığınızdan emin olun.

      * Kaynak eşleme dosyanızın, Visual Studio hata ayıklayıcısının *app. TSX*' i bulmasını önleyen *./app.exe* ( *WebPack:///./app.TSX*değil) öğesine yönelik bir başvuru içerdiğinden emin olun.
       Alternatif olarak, *app. TSX* içindeki koda kesmeniz ve bunu yapamazsanız, *app. tsx*'teki `debugger;` Ifadesini kullanmayı deneyin veya Chrome Geliştirici Araçları (veya Microsoft Edge için F12 araçları) kesme noktaları ayarlayın.

   * *App-Bundle. js* ' deki kodu kesmeniz gerekiyorsa ve bunu yapamadığından, *App-Bundle. js. map*kaynak eşleme dosyasını kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)
