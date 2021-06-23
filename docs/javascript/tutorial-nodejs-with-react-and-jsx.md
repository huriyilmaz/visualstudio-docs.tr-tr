---
title: Node.js ve React uygulaması oluşturma
description: Visual Studio şablonu Node.js ndan bir web uygulaması projesi Visual Studio öğrenin.
ms.custom: vs-acquisition
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
ms.openlocfilehash: 3299f38e99c6b96cacd3c3661937a29bdec3c93d
ms.sourcegitcommit: 809fff25b7701882c899c639eeb6da38ad4fb88a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2021
ms.locfileid: "112550707"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Node.js ve React uygulaması Visual Studio

Visual Studio kolayca bir Node.js oluşturmanızı ve IntelliSense'i ve diğer yerleşik özellikleri deneyimleyemenizi Node.js. Bu öğreticide, Visual Studio şablondan Node.js web uygulaması projesi Visual Studio oluşturabilirsiniz. Ardından React kullanarak basit bir uygulama oluşturabilirsiniz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * npm paketleri ekleme
> * Uygulamanıza React kodu ekleme
> * JSX'i transpile
> * Hata ayıklayıcıyı ekleme

## <a name="before-you-begin"></a>Başlamadan önce

Bazı temel kavramları size tanıtan hızlı bir SSS'yi burada bulabilirsiniz.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js JavaScript sunucu tarafı yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>npm nedir?

npm, uygulamanın varsayılan paket Node.js. Paket yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamalarını ve paylaşmalarını kolaylaştırır ve kitaplıkları yüklemeyi, güncelleştirmeyi ve kaldırmayı basitleştirmek için tasarlanmıştır.

### <a name="what-is-react"></a>React nedir?

React, kullanıcı arabirimi oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX, genellikle Kullanıcı arabirimi öğelerini açıklamak için React ile birlikte kullanılan bir JavaScript söz dizimi uzantısıdır. Bir tarayıcıda çalıştırılamadan önce JSX kodunun düz JavaScript'e transpilesi gerekir.

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
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, **Node.js** yazın ve boş Node.js Web Uygulaması **- JavaScript'i seçin.** (Bu öğretici TypeScript derleyicisi kullanıyor olsa da, adımlar JavaScript şablonuyla **başlamayı** gerektirir.)
    
    Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Proje'yi**  >    >  **seçin.** Yeni Proje iletişim kutusunun sol **bölmesinde** **JavaScript'i** genişletin ve ardından Yeni **Proje'Node.js.** Orta bölmede Boş uygulama web **Node.js' seçin,** **NodejsWebAppBlank adını yazın** ve tamam'ı **seçin.**
    ::: moniker-end
    Blank **Node.js Web Uygulaması** proje şablonunu görmüyorsanız, uygulama geliştirme işNode.js **eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi açar.

    ![Node.js projesini Çözüm Gezgini](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Yeni Proje **iletişim** kutusunda verdiği ad kullanılarak projeniz kalın **olarak vurgulanır.** Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek (veya Alt Enter tuşuna basarak) projeyle **ilişkili özellikleri** ve ortam **değişkenlerini ayarlayın.**  +   Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde, varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm düğümünü sağ tıklar ve npm paketlerini bir iletişim kutusu kullanarak arayabilir ve  yükleyebilir veya npm düğümündepackage.js'daki ayarları kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

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

1. Kullanıcı arabirimini kullanarak paketlerin geri kalanını tek tek aramak ve eklemek yerine aşağıdaki kodupackage.js *yapıştırın.* Bunu yapmak için şu `dependencies` kodla bir bölüm ekleyin:

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

    Boş şablon `dependencies` sürümünüzde zaten bir bölüm varsa, bunu önceki JSON koduyla değiştirmeniz gerekir. Bu dosyanın kullanımı hakkında daha fazla bilgi için [bkz.package.jsyapılandırma.](../javascript/configure-packages-with-package-json.md)

1. Değişiklikleri kaydedin.

1. Projenizin **npm düğümüne** sağ tıklayın ve Npm Paketlerini **Yükle'yi seçin.**

    Bu komut npm install komutunu doğrudan çalıştırır.

    Paketlerin yükleme ilerlemesini **görmek için** alt bölmede Çıkış penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen göreyemebilirsiniz. Çıkışı görmek için Çıkış penceresindeki Çıkış çıkışını göster alanında  **Npm'yi** seçin.  (Pencereyi açmak için **Görünüm**  >  ' ü seçin. **Çıktı** veya **CTRL**  +  **alt**  +  **O** tuşlarına basın.)

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

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Komut istemi penceresi sonucu gösterir.

    ![WebPack 'i Çalıştır](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Yukarıdaki çıkış yerine herhangi bir hata görürseniz, uygulamanızın çalışması için önce bu hataları çözmeniz gerekir. NPM paket sürümleriniz Bu öğreticide gösterilen sürümlerden farklıysa, bu bir hata kaynağı olabilir. Hataları gidermenin bir yolu, önceki adımlarda gösterilen sürümlerin aynısını kullanmaktır. Ayrıca, bu paket sürümlerinden bir veya daha fazlası kullanım dışı bırakılmış ve bir hatayla sonuçlanmışsa, hataları onarmak için daha yeni bir sürüm yüklemeniz gerekebilir. NPM paket sürümlerini denetlemek için *üzerindepackage.js* kullanma hakkında bilgi için bkz. [package.jsyapılandırma](../javascript/configure-packages-with-package-json.md).

1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve   >  **var olan klasörü** Ekle ' yi seçtikten sonra, *dağ* klasörünü seçip **Klasör Seç**' i seçin.

    Visual Studio, *app-bundle.js* ve *app-bundle.js. Map* içeren proje için *Dist* klasörünü ekler.

1. Transpiled JavaScript kodunu görmek için *app-bundle.js* açın.

1. Dışarıdan değiştirilen dosyaları yeniden yüklemeniz istenirse, **Tümüne Evet**' i seçin.

    ![Değiştirilen dosyaları yükle](../javascript/media/tutorial-nodejs-react-reload-files.png)

*App. TSX* üzerinde her değişiklik yaptığınızda WebPack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatik hale getirmek için, derleyin için JSX 'e bir derleme betiği ekleyin.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX derleyin 'e derleme betiği ekleme

Visual Studio 2019 ' den başlayarak bir derleme betiği gereklidir. Transpiling JSX yerine, komut satırında (yukarıdaki bölümde gösterildiği gibi), Visual Studio 'dan oluştururken JSX derleyin sağlayabilirsiniz.

* *package.js* açın ve bölümden sonra aşağıdaki bölümü ekleyin `dependencies` :

   ```json
   "scripts": {
    "build": "webpack-cli ./app.tsx --config webpack-config.js"
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

1. Uygulamayı çalıştırmak için **F5** (**hata** ayıklama  >  **başlatma hata** ayıklama) veya yeşil ok düğmesine basın.

    Hata ayıklayıcının dinlediği bağlantı noktasını gösteren bir Node.js konsol penceresi açılır.

    Visual Studio, *server.js* başlangıç dosyasını başlatarak uygulamayı başlatır.

    ![Tarayıcıda tepki verme](../javascript/media/tutorial-nodejs-react-running-react.png)

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

   Diğer tarayıcı örnekleri tarayıcının hata ayıklama etkinken açılmasını önleyebilir. (Tarayıcı uzantıları çalışıyor olabilir ve tam hata ayıklama modunu engelleyebilir, bu nedenle beklenmedik Chrome örneklerini bulmak için Görev Yöneticisi 'Ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için tüm Chrome örneklerini de kapatın. Her iki tarayıcı de kmıum Code tabanını paylaştığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

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

    Daha *app-bundle.js* için işlevinde kesme noktası `render()` aşağıdaki çizimde gösterildiği gibi ayarlayın:

    ![Uygulama için Visual Studio penceresinin ekran app-bundle.js. Sol oluk içinde kırmızı bir nokta, işleme işlevinde bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    İşlevi `render()` transpiled dosyada  bulmakapp-bundle.js **Ctrl** F ( Bul ve +  **Değiştir**  >  **Hızlı Bul)**  >  **tuşlarını kullanın.**

    *app.tsx* için işlevinin içindeki kesme `render()` noktası için deyimini `return` ayarlayın.

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

    Bu, yalnızca geliştirme aşamasında hata ayıklamayı etkinleştiren bir Visual Studio. Bu ayar, uygulamayı oluşturulurken kaynak eşleme dosyasında oluşturulan başvuruları *(app-bundle.js.map)* geçersiz kılmaya olanak sağlar. Varsayılan olarak, kaynak eşleme dosyasındaki webpack  başvuruları webpack:/// ön eklerini içerir ve bu da *Visual Studio app.tsx dosyasını bulmasını ön ekidir.* Bu değişikliği özellikle *de, app.tsx* kaynak dosyasına yapılan başvuru,  hata ayıklamayı sağlayan *webpack:///./app.tsx./app.tsx* olarak değiştirilir.

3. Visual Studio'de hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl** F5 ( Hata Ayıklama Olmadan Başlat +    >  ) tuşlarına basın.

    ::: moniker range=">=vs-2019"
    Kolay bir adla bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Ekle hata**  >  **ayıkla'ya seçin** (veya Ctrl Alt P   +  **tuşlarına**  +  **basın).**

    > [!TIP]
    > Visual Studio 2017'den başlayarak, bu adımları kullanarak işleme ilk kez iliştirilme işlemini tamamlayarak, İşleme Yeniden Ekle'de Hata Ayıkla'ya  >   (veya **Shift**  +  **Alt**  +  **P'ye** basarak) aynı işleme hızlıca yeniden iliştirebilirsiniz.

5. İşleme **Ekle iletişim** kutusunda, ekleyebilirsiniz tarayıcı örneklerinin filtrelenmiş bir listesini elde edin.

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

    Hata ayıklayıcıda duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kod ( F5 , **F10** ve **F11**) adım adım ilerleyerek hata ayıklayıcıyı **ilerletebilirsiniz.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

    Kesme noktası, daha önce *hangi adımlarıapp-bundle.js* ortamınız ve tarayıcı durumunuz bağlı olarak *app.tsx'te* veya eşlenmişapp-bundle.js'de isabet edersiniz. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

   * *app.tsx* dosyasındaki kodu kesmeniz gerekirse ve bunu yapamazsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi İşleme Ekle'ye kullanın.  Ortamınız doğru şekilde ayarlanmış olduğundan emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırmak için Chrome uzantıları dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi'ni kullanarak). Tarayıcıyı hata ayıklama modunda başlatın.

      * Kaynak eşleme dosyanız için *./app.tsx* başvurusu olduğundan ve *webpack:///./app.tsx'ye* başvuru içerir. Bu, Visual Studio hata ayıklayıcısının *app.tsx dosyasını bulmasını önler.*
       Alternatif olarak, *app.tsx'te* koda giremiyorsanız ve bunu yapamazsanız `debugger;` *app.tsx'te* deyimini kullanmayı deneyin veya Chrome Geliştirici Araçları'de (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlamayı deneyin.

   * app-bundle.js'da koda *app-bundle.js* ve bunu yapamazsanız, *app-bundle.js.map kaynak eşleme dosyasını kaldırın.*

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)
