---
title: Node.js oluşturma ve uygulama tepki verme
description: Bu öğreticide, Visual Studio için Node.js araçları 'nı kullanarak bir uygulama oluşturacaksınız
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c6813e0ad482bb211269c9da3950842dda7f6abd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81760089"
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

### <a name="what-is-webpack"></a>WebPack nedir?

Web paketi, JavaScript dosyalarını bir tarayıcıda çalışabilecek şekilde paketler. Ayrıca diğer kaynakları ve varlıkları dönüştürebilir veya paketleyebilir. Genellikle Babel veya TypeScript gibi bir derleyicinin basit JavaScript 'e derleyin JSX veya TypeScript kodunu belirtmek için kullanılır.

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio yüklü ve Node.js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak zaten Visual Studio 'ya sahipseniz **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanının yüklü olması gerekir.

    Bu öğretici sürüm 12.6.2 ile test edilmiştir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node.js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Visual Studio 'daki Node.js araçları, Node.js iş yüküne dahil edilmiştir, her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyici yalnızca aynı anda yüklü olan birini destekler.
    
    Genel olarak, Visual Studio yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node.exe yolunu**ayarlayın). Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Node.js Web uygulaması projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js**yazın ve sonra **Web uygulaması-JavaScript Node.js boş**seçeneğini belirleyin. (Bu öğretici TypeScript derleyicisini kullanıyor olsa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.)
    
    Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde **JavaScript**' i ve ardından **Node.js**' yi seçin. Orta bölmede, **boş Node.js Web uygulaması**' nı seçin, **Nodejswebappblank**adını yazın ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi açar.

    ![Çözüm Gezgini Node.js proje](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1), **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler**' i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz. Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *package.js* ' deki ayarları ve NPM düğümündeki sağ tıklama seçenekleri ' ni kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

    (4) *package.json* , NPM tarafından yerel olarak yüklenen paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek üzere kullanılan bir dosyadır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

    (5) *server.js* gibi proje dosyaları proje düğümünün altında görünür. *server.js* , proje başlangıç dosyasıdır ve bu nedenle **kalın**olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

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

    Projenin dosyadaki *package.js* , paket sürümü de dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

1. Tek seferde paketleri aramak ve geri kalanını eklemek için Kullanıcı arabirimini kullanmak yerine, aşağıdaki kodu * üzerinepackage.js*yapıştırın. Bunu yapmak için `dependencies` şu kodla bir bölüm ekleyin:

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

    Alt bölmede, paketlerin yüklenmesiyle ilgili ilerleme durumunu görmek için **Çıkış** penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıktıyı görmek için **Çıkış** penceresindeki çıktıyı **göster** alanında **NPM** ' yi seçtiğinizden emin olun.

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

1. Çözüm Gezgini ' de proje **nodejswebappblank** öğesine sağ tıklayın ve yeni öğe **Ekle**' yi seçin  >  **New Item**.

1. **Yeni öğe Ekle** Iletişim kutusunda **TypeScript JSX dosyası**' nı seçin, *app. TSX*adını yazın ve **Ekle** veya **Tamam**' ı seçin.

1. *webpack-config.js*eklemek için bu adımları tekrarlayın. TypeScript JSX dosyası yerine **JavaScript dosyası**' nı seçin.

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

    Bu HTML sayfası, JSX ve transpiled kodunu düz JavaScript 'e içeren *app-bundle.js*yükler. Şu anda *app-bundle.js* boş bir dosyadır. Sonraki bölümde, kodu derleyin için seçenekleri yapılandırırsınız.

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

    Yukarıdaki çıkış yerine herhangi bir hata görürseniz, uygulamanızın çalışması için önce bu hataları çözmeniz gerekir. NPM paket sürümleriniz Bu öğreticide gösterilen sürümlerden farklıysa, bu bir hata kaynağı olabilir. Hataları gidermenin bir yolu, önceki adımlarda gösterilen sürümlerin aynısını kullanmaktır. Ayrıca, bu paket sürümlerinden bir veya daha fazlası kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için * üzerindepackage.js* kullanma hakkında bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve **Add**  >  **var olan klasörü**Ekle ' yi seçtikten sonra, *dağ* klasörünü seçip **Klasör Seç**' i seçin.

    Visual Studio, *app-bundle.js* ve *app-bundle.js. Map*içeren proje için *Dist* klasörünü ekler.

1. Transpiled JavaScript kodunu görmek için *app-bundle.js* açın.

1. Dışarıdan değiştirilen dosyaları yeniden yüklemeniz istenirse, **Tümüne Evet**' i seçin.

    ![Değiştirilen dosyaları yükle](../javascript/media/tutorial-nodejs-react-reload-files.png)

*App. TSX*üzerinde her değişiklik yaptığınızda WebPack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatik hale getirmek için, derleyin için JSX 'e bir derleme betiği ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX derleyin 'e derleme betiği ekleme

Visual Studio 2019 ' den başlayarak bir derleme betiği gereklidir. Transpiling JSX yerine, komut satırında (yukarıdaki bölümde gösterildiği gibi), Visual Studio 'dan oluştururken JSX derleyin sağlayabilirsiniz.

* *package.js* açın ve bölümden sonra aşağıdaki bölümü ekleyin `dependencies` :

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Geçerli hata ayıklama hedefi olarak **Web sunucusu (Google Chrome)** ya da **Web sunucusu (Microsoft Edge)** seçin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefi olarak Chrome seçin](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefi olarak Chrome seçin](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedefi açılır listesinden **Araştır** ' ı seçin ve varsayılan tarayıcı hedefi olarak Chrome ' u seçin ( **Varsayılan olarak ayarla**' yı seçin).

1. Uygulamayı çalıştırmak için **F5** (**hata**ayıklama  >  **başlatma hata**ayıklama) veya yeşil ok düğmesine basın.

    Hata ayıklayıcının dinlediği bağlantı noktasını gösteren bir Node.js konsol penceresi açılır.

    Visual Studio, *server.js*başlangıç dosyasını başlatarak uygulamayı başlatır.

    ![Tarayıcıda tepki verme](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Tarayıcı penceresini kapatın.

1. Konsol penceresini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Bir kesme noktası ayarlayın ve uygulamayı çalıştırın

1. *server.js*, `staticPath` bir kesme noktası ayarlamak için bildirimin solundaki cilt payın içine tıklayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

1. Uygulamayı çalıştırmak için **F5** tuşuna basın (**hata ayıklama**  >  **başlatma hata ayıklaması**).

    Hata ayıklayıcı ayarladığınız kesme noktasında duraklatılır (geçerli ifade sarı olarak işaretlenir). Artık, şu anda kapsamda olan değişkenlerin üzerine giderek, **Yereller** ve **izleme** pencereleri gibi hata ayıklayıcı pencereleri kullanarak uygulamanızın durumunu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçları veya F12 araçlarını kullanmak istiyorsanız **F12**tuşuna basın. Bu araçları, DOM 'ı incelemek ve JavaScript konsolunu kullanarak uygulamayla etkileşim kurmak için kullanabilirsiniz.

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

   Diğer tarayıcı örnekleri tarayıcının hata ayıklama etkinken açılmasını önleyebilir. (Tarayıcı uzantıları çalışıyor olabilir ve tam hata ayıklama modunu engelleyebilir, bu nedenle beklenmedik Chrome örneklerini bulmak için Görev Yöneticisi 'Ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için tüm Chrome örneklerini de kapatın. Her iki tarayıcı de kmıum Code tabanını paylaştığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' den başlayarak, `--remote-debugging-port=9222` **hata ayıklama** araç çubuğundan **.** .. > ve ardından **Ekle**' yi seçerek ve sonra da **bağımsız değişkenler** alanında bayrağını ayarlayarak tarayıcı başlatma sırasında bayrağı ayarlayabilirsiniz. Hata **ayıklamayla**hata ayıklama veya Chrome **ile kenar** gibi farklı bir kolay ad kullanın. Ayrıntılar için bkz. [sürüm notları](/visualstudio/releases/2019/release-notes-v16.2).

    ![Tarayıcınızı hata ayıklama etkinken açılacak şekilde ayarlama](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `msedge --remote-debugging-port=9222`

    veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmıyor, bu nedenle boş bir tarayıcı sayfası alırsınız.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğe iliştirme

1. Visual Studio 'ya geçin ve kaynak kodunuzda *app-bundle.js*  ya da *app. TSX*arasında bir kesme noktası ayarlayın.

    *app-bundle.js*için, `render()` işlevde aşağıdaki çizimde gösterildiği gibi bir kesme noktası ayarlayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    `render()`İşlevi transpiled *app-bundle.js* dosyasında bulmak için **CTRL** + **F** 'yi (**Düzenle**  >  **Bul ve Değiştir**  >  **hızlı bul**) kullanın.

    *App. TSX*için, deyimindeki kesme noktasını işlevin içinde ayarlayın `render()` `return` .

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Kesme noktasını *. TSX* dosyasında ( *app-bundle.js*yerine) ayarlıyorsanız, *webpack-config.js*güncelleştirmeniz gerekir. Aşağıdaki kodu değiştirin:

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

    Bu, Visual Studio 'da hata ayıklamayı etkinleştirmek için yalnızca geliştirme bir ayardır. Bu ayar, uygulamayı oluştururken *app-bundle.js. Map*dosyasında kaynak eşleme dosyasındaki oluşturulan başvuruları geçersiz kılmanıza olanak tanır. Varsayılan olarak, kaynak eşleme dosyasındaki WebPack başvuruları, Visual Studio 'Nun *app. TSX*kaynak dosyasını bulmasını önleyen *WebPack:///* önekini içerir. Özellikle, bu değişikliği yaptığınızda, *app. TSX*kaynak dosyasına yönelik başvuru, hata ayıklamayı sağlayan *WebPack:///./app.TSX* olarak *./app. TSX*olarak değiştirilir.

3. Visual Studio 'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin ve **Ctrl** + uygulamayı tarayıcıda çalıştırmak için CTRL**F5** tuşuna basın (**hata ayıklama**  >  **olmadan Başlat**).

    ::: moniker range=">=vs-2019"
    Kolay ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefi olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Ekle hata ayıkla**öğesini seçin  >  **Attach to Process**.

    > [!TIP]
    > Visual Studio 2017 ' den başlayarak, bu adımları izleyerek işleme ilk kez iliştirdikten sonra, **Debug**  >  **işlemek için**hata ayıklama yeniden iliştirme ' yi seçerek aynı işleme hızlıca tekrar iliştirebilirsiniz.

5. **Işleme İliştir** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, arama sonuçlarını filtrelemek için hedef **edge** tarayıcınız, **JavaScript (Chrome)** veya **chrome** **JavaScript (Microsoft Edge-ku)** için doğru hata ayıklayıcıyı **Attach to** seçin.
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

    Daha önce, ortamınız ve tarayıcı durumlarınızla birlikte, daha önce izlediğiniz adımlara bağlı olarak, *app-bundle.js* ya da *app. TSX*içindeki eşleştirilmiş konumunda kesme noktasına ulaşırsınız. Her iki durumda da kodun içinde ilerleyebileceğiniz değişkenleri inceleyebilirsiniz.

   * *App. TSX* içindeki koda ayırmanız ve bunu yapamaması gerekiyorsa, hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi **işlemek için İliştir** ' i kullanın. Ortamınızın doğru ayarlandığından emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları da dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi kullanılarak). Tarayıcıyı hata ayıklama modunda başlattığınızdan emin olun.

      * Kaynak eşleme dosyanızın, Visual Studio hata ayıklayıcısının *app. TSX*' i bulmasını önleyen *./app.exe* ( *WebPack:///./app.TSX*değil) öğesine yönelik bir başvuru içerdiğinden emin olun.
       Alternatif olarak, *app. TSX* içindeki koda bir kod kesmeniz ve bunu yapamazsanız, `debugger;` *app. TSX*içindeki ifadesini kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları (veya Microsoft Edge için F12 araçları) kesme noktaları ayarlayın.

   * *app-bundle.js* kodu kesmeniz gerekiyorsa ve bunu yapamadığından, *app-bundle.js. map*kaynak eşleme dosyasını kaldırın.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)
