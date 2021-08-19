---
title: Node.js ve React oluşturma
description: Visual Studio şablonundan Node.js web uygulaması projesi Visual Studio öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077783"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Öğretici: Node.js'da React uygulama Visual Studio

Visual Studio, kolayca bir Node.js proje oluşturmanıza ve IntelliSense'i ve bu projeyi destekleyen diğer yerleşik özellikleri Node.js. Bu öğreticide, Visual Studio şablondan Node.js web uygulaması projesi Visual Studio oluşturabilirsiniz. Ardından, React kullanarak basit bir uygulama React.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * npm paketleri ekleme
> * Uygulamanıza React kodu ekleme
> * Transpile JSX
> * Hata ayıklayıcıyı ekleme

## <a name="before-you-begin"></a>Başlamadan önce

Bazı temel kavramları size tanıtan hızlı bir SSS'yi burada bulabilirsiniz.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafı yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>npm nedir?

npm, uygulamanın varsayılan paket Node.js. Paket yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamalarını ve paylaşmalarını kolaylaştırır ve kitaplıkları yüklemeyi, güncelleştirmeyi ve kaldırmayı basitleştirmek için tasarlanmıştır.

### <a name="what-is-react"></a>Hangi React?

React kullanıcı arabirimi oluşturmak için bir ön uç çerçevesidir.

### <a name="what-is-jsx"></a>JSX nedir?

JSX, genellikle kullanıcı arabirimi öğelerini açıklamak için React bir JavaScript söz dizimi uzantısıdır. Bir tarayıcıda çalıştırılamadan önce JSX kodunun düz JavaScript'e transpilesi gerekir.

### <a name="what-is-webpack"></a>Webpack nedir?

webpack, JavaScript dosyalarını bir tarayıcıda çalıştıracak şekilde paketler. Ayrıca diğer kaynakları ve varlıkları da dönüştürebilirsiniz veya paketler. JSX veya TypeScript kodunu düz JavaScript'e transpile etmek için genellikle Babel veya TypeScript gibi bir derleyici belirtmek için kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Uygulama ve Visual Studio iş yükünün yüklü Node.js gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![Node.js Yükleyicisi'ne iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js gerekir.

    Bu öğretici 12.6.2 sürümüyle test edilmiştir.

    Yüklü yoksa, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için [ LTS ](https://nodejs.org/en/download/) sürümünüNode.jsweb sitesinden yüklemenizi öneririz. Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır. Node.js iş yüküne dahil Visual Studio araçları her Node.js destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca birinin yüklü olduğunu destekler.

    Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanlarına başvuracak şekilde yapılandırabilirsiniz (proje oluşturduk sonra proje düğümüne sağ tıklayın, Özellikler'i seçin **(veya** **Alt** Enter tuşuna basın) veNode.exe yolunu  +   **ayarlayın).** Bir yerel yorumlayıcının Node.js yüklemesini kullanabilir veya her bir yerel yorumlayıcının yolunu Node.js belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir web Node.js projesi oluşturun.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, **Node.js** yazın ve boş Node.js Web Uygulaması **- JavaScript'i seçin.** (Bu öğretici TypeScript derleyicisi kullanıyor olsa da, adımlar JavaScript şablonuyla **başlamayı** gerektirir.)
    
    Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni uygulama iletişim kutusunun sol **bölmesinde JavaScript Project** genişletin ve ardından Yeni'yiNode.js.  **** Orta bölmede Boş uygulama web **Node.js' seçin,** **NodejsWebAppBlank** adını yazın ve tamam'ı **seçin.**
    ::: moniker-end
    Blank **Node.js Web Uygulaması proje** şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **gerekir.** Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi açar.

    ![Node.js projesini Çözüm Gezgini](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Yeni  Çalışma Alanı iletişim kutusunda verdiği ad kullanılarak projeniz kalın Project **vurgulanır.** Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek (veya Alt Enter tuşuna basarak) projeyle **ilişkili özellikleri** ve ortam **değişkenlerini ayarlayın.**  +   Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm düğümünü sağ tıklar ve npm paketlerini bir iletişim kutusu kullanarak arayabilir ve yükleyebilir ya da *npm* düğümündepackage.js'daki ayarları kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

    (4) *package.js,* npm tarafından yerel olarak yüklenmiş paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5) Project gibi *server.js* proje düğümü altında gösterir. *server.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**

## <a name="add-npm-packages"></a>npm paketleri ekleme

Bu uygulamanın doğru şekilde çalışması için bir dizi npm modülü gerekir.

* Tepki
* react-dom
* express
* path
* ts-loader
* typescript
* Webpack
* webpack-cli

1. Yeni Çözüm Gezgini (sağ bölme) altında, projedeki **npm** düğümüne sağ tıklayın ve Yeni **npm Paketleri Yükle'yi seçin.**

    Yeni **npm Paketlerini Yükle iletişim** kutusunda, en güncel paket sürümünü yükleyebilir veya bir sürüm belirtebilirsiniz. Bu paketlerin geçerli sürümünü yüklemeyi seçerseniz ancak daha sonra beklenmeyen hatalarla karşılaşacaksanız, bu adımların sonraki adımlarında açıklanan tam paket sürümlerini yüklemek iyi olabilir.

1. Yeni **npm Paketlerini Yükle iletişim kutusunda** react paketini arayın ve Paketi **Yükle'yi seçerek** yükleyin.

    ![npm paketlerini yükleme](../javascript/media/tutorial-nodejs-react-install-package.png)

    Paketi **yüklemenin** ilerlemesini görmek için Çıkış penceresini seçin (Çıktıyı göster alanında **Npm'yi** seçin).  Paket yüklendikten sonra **npm** düğümü altında görünür.

    Projenin dosya *package.jspaketi,* paket sürümü de dahil olmak üzere yeni paket bilgileriyle güncelleştirilir.

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

    Paketlerin yükleme ilerlemesini **görmek için** alt bölmede Çıkış penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıkışı görmek için Çıkış penceresindeki Çıkış çıkışını göster alanında  **Npm'yi** seçin.  (Pencereyi açmak için Görünüm'e **tıklayın**  >  **Ctrl**   +  Alt O **tuşlarına basın**  +  **veya çıkışa** basın.)

    Npm modülleri yüklendikten sonra Çözüm Gezgini burada görünür.

    ![npm paketleri](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Komut satırı kullanarak npm paketlerini yüklemek isterseniz proje düğümüne sağ tıklayın ve Komut İstemi'ne Buradan **Aç'ı seçin.** Paketleri yüklemek Node.js standart komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları ekleme

Bu adımlarda, projenize dört yeni dosya eklersiniz.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Bu basit uygulama için yeni proje dosyalarını proje köküne eklersiniz. (Çoğu uygulama için dosyaları genellikle alt klasörlere ekler ve göreli yol başvurularını buna göre ayarlarsiniz.)

1. Bu Çözüm Gezgini **NodejsWebAppBlank** projesine sağ tıklayın ve Yeni Öğe Ekle'yi  >   seçin (veya Ctrl SHIFT A   +    +  **tuşlarına basın).**

1. Yeni Öğe **Ekle iletişim kutusunda** **TypeScript JSX** dosyasını seçin, *app.tsx* adını yazın ve Ekle veya **Tamam'ı** **seçin.**

1. bu adımları tekrarlayın *ve* webpack-config.js. TypeScript JSX dosyası yerine **JavaScript dosyası'ı seçin.**

1. Aynı adımları tekrarlayın ve *projeyeindex.html'yi* ekleyin. JavaScript dosyası yerine HTML dosyasını **seçin.**

1. Projeye yeni birtsconfig.js *eklemek için* aynı adımları tekrarlayın. JavaScript dosyası yerine **TypeScript JSON Yapılandırma dosyası'ı seçin.**

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

   Yukarıdaki kod, web uygulaması sunucunuz olarak Node.js express kullanır. Bu kod, bağlantı noktasını proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar (varsayılan olarak, bağlantı noktası özelliklerde 1337 olarak yapılandırılır). Proje özelliklerini açmak için, proje içinde projeye sağ tıklayın Çözüm Gezgini'yi **seçin.**

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

1. l *index.htmaçın* ve body **bölümünü** aşağıdaki kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML *sayfasıapp-bundle.js* JSX'i içeren ve düz JavaScript'e React kodu içeren dosyasını yükler. Şu *andaapp-bundle.js* boş bir dosyadır. Sonraki bölümde, kodu transpile etmek için seçenekleri yapılandırabilirsiniz.

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

1. Aşağıdaki *tsconfig.jsaçın* ve varsayılan kodu TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

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

    *app.tsx,* kaynak dosya olarak belirtilir.

## <a name="transpile-the-jsx"></a>JSX'i transpile

1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.**

1. Komut isteminde aşağıdaki komutu yazın:

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Komut istemi penceresinde sonuç gösterilir.

    ![Webpack'i çalıştırma](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Önceki çıkış yerine herhangi bir hata görüyorsanız, bunları, uygulamanın çalışmadan önce çözümlemeniz gerekir. npm paketi sürümleriniz bu öğreticide gösterilen sürümlerden farklı ise, bu bir hata kaynağı olabilir. Hataları düzeltmenin bir yolu, önceki adımlarda gösterilen tam sürümleri kullanmaktır. Ayrıca, bu paket sürümlerinden biri veya daha fazlası kullanım dışı kaldı ve bir hatayla sonuçlanıyorsa, hataları düzeltmek için daha yeni bir sürüm yüklemeniz gerekir. npm paket sürümlerini *package.jsiçin* üzerinde uygulama kullanma hakkında bilgi için [bkz.package.jsyapılandırma.](../javascript/configure-packages-with-package-json.md)

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

1. Bu *server.js* içinde bildirimin sol tarafından sol tarafta yer alan oluklara `staticPath` tıklar ve bir kesme noktası ayarlayın:

    ![Uygulama için Visual Studio penceresinin ekran server.js. Sol oluk içinde kırmızı bir nokta, staticPath bildirimi için bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

1. Uygulamayı çalıştırmak için **F5** tuşuna basın (**Hata Ayıklamayı**  >  **Başlatma hata ayıklaması).**

    Hata ayıklayıcı, ayar istediğiniz kesme noktası sırasında duraklatılır (geçerli deyim sarı olarak işaretlenir). Artık Yerel Ayarlar ve İzleme pencereleri gibi hata ayıklayıcı pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerine gelerek **uygulama** durumunu **inceleyebilirsiniz.**

1. Uygulamaya **devam etmek için F5** tuşuna basın.

1. Microsoft Edge için Chrome Geliştirici Araçları veya F12 Araçları'Microsoft Edge **F12 tuşuna basın.** DoM'ları incelemek ve JavaScript Konsolu'nu kullanarak uygulamayla etkileşim kurmak için bu araçları kullanabilirsiniz.

1. Web tarayıcısını ve konsolunu kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafında kesme noktası ayarlama ve React isabet

Önceki bölümde hata ayıklayıcıyı sunucu tarafı koda Node.js. Hata ayıklayıcısını istemci Visual Studio kesme noktalarına isabet etmek ve React hata ayıklayıcının doğru işlemi tanımlaması için yardıma ihtiyacı vardır. Bunu etkinleştirmenin bir yolu şu şekildedir.

### <a name="prepare-the-browser-for-debugging"></a>Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için şu anda IDE Microsoft Edge de Chromium adlı **Microsoft Edge Beta** veya Chrome'u kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu önliyor olabilir, bu nedenle Beklenmeyen Chrome örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekir.)

   ::: moniker range=">=vs-2019"
   Bu Microsoft Edge (Chromium) chrome'un tüm örneklerini de kapatır. Her iki tarayıcı da chromium kod tabanını paylaştığı için en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinleştirildiğinde tarayıcınızı başlatabilirsiniz.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, Hata Ayıklama araç çubuğundan `--remote-debugging-port=9222` **Gözat...** >'yi  ve ardından Ekle'yi seçerek ve ardından  Bağımsız Değişkenler alanında bayrağı ayarlayarak tarayıcı başlatma sırasında bayrağını ayarlayın. Tarayıcı için Hata Ayıklama ile **Edge** veya Hata Ayıklama ile Chrome gibi **farklı bir kolay ad kullanın.** Ayrıntılar için bkz. [Sürüm Notları.](/visualstudio/releases/2019/release-notes-v16.2)

    ![Tarayıcınızı hata ayıklama etkin olarak açılacak şekilde ayarlama](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

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

    Bu *app-bundle.js* için işlevinde kesme noktası `render()` aşağıdaki çizimde gösterildiği gibi ayarlayın:

    ![Uygulama için Visual Studio penceresinin ekran app-bundle.js. Sol oluk içinde kırmızı bir nokta, işleme işlevinde bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    İşlevi `render()` transpiledapp-bundle.js bulmak için **Ctrl** F ( Bul ve +  **Değiştir**  >  **Hızlı Bul) tuşlarını**  >  **kullanın.**

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

    Bu, yalnızca geliştirme aşamasında hata ayıklamayı etkinleştiren bir Visual Studio. Bu ayar, uygulamayı oluşturulurken kaynak eşleme dosyasında oluşturulan başvuruları *(app-bundle.js.map)* geçersiz kılmaya olanak sağlar. Varsayılan olarak, kaynak eşleme dosyasındaki webpack  başvuruları, *app.tsx* Visual Studio bulmasını engelleyen webpack:/// ön eklerini içerir. Bu değişikliği özellikle *de, app.tsx* kaynak dosyasına yapılan başvuru,  hata ayıklamayı sağlayan *webpack:///./app.tsx ./app.tsx* olarak değiştirilir.

3. Visual Studio'de hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl** F5 ( Hata Ayıklama Olmadan Başlat +    >  ) tuşlarına basın.

    ::: moniker range=">=vs-2019"
    Kolay bir adla bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

4. İşleme **Ekle hata**  >  **ayıkla'ya seçin** (veya Ctrl Alt P   +  **tuşlarına**  +  **basın).**

    > [!TIP]
    > Visual Studio 2017'den başlayarak, bu adımları kullanarak işleme ilk kez iliştirilme işlemini tamamlayarak, İşleme Yeniden Ekle'de Hata Ayıkla'ya  >   (veya **Shift**  +  **Alt**  +  **P'ye** basarak) aynı işleme hızla yeniden iliştirebilirsiniz.

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
    Aşağıdaki örnek, bunun Microsoft Edge (Chromium) tarayıcısını nasıl göründüğünü gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM Gezgini ve JavaScript Konsolu açık olduğunda hata ayıklayıcının doğru şekilde ekli olduğunu Visual Studio. Bu hata ayıklama araçları, chrome için Geliştirici Araçları F12 Araçları'Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcısı eklenmezse ve "İşleme eklenemiyor. Bir işlem geçerli durumda yasal değildir." hata ayıklama modunda tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engel ediyor olabilir.

7. Kesme noktasıyla kod zaten yürütülür olduğundan, kesme noktasıyla bağlantı noktasıyla bağlantı için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kod (**F5**, F10 ve **F11)** adım adım ilerleyerek hata ayıklayıcıyı **ilerletebilirsiniz.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

    Daha önce hangi adımları takip *ettiğine ve ortamınız ve tarayıcı durumunuza* bağlı olarak,app-bundle.jsveya *app.tsx'te* eşlenmiş konumu içinde kesme noktasıyla isabetleyebilirsiniz. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

   * *app.tsx* dosyasındaki kodu kesmeniz gerekirse ve bunu yapamazsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi İşleme Ekle'ye kullanın.  Ortamınız doğru şekilde ayarlanmış olduğundan emin olun:

      * Tarayıcıyı hata ayıklama modunda çalıştırmak için Chrome uzantıları dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi'ni kullanarak). Tarayıcıyı hata ayıklama modunda başlatın.

      * Kaynak eşleme dosyanız için *./app.tsx* başvurusu olduğundan ve *webpack:///./app.tsx'ye* başvuru içerir. Bu, Visual Studio hata ayıklayıcısının *app.tsx dosyasını bulmasını önler.*
       Alternatif olarak, *app.tsx'te* koda izin veremiyorsanız ve bunu yapamazsanız `debugger;` *app.tsx'te* deyimini kullanmayı deneyin veya Bunun yerine Chrome Geliştirici Araçları'de (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlamayı deneyin.

   * app-bundle.jskodunda kesmeye  ihtiyacınız varsa ve bunu yapamazsanız, *app-bundle.js.map kaynak eşleme dosyasını kaldırın.*

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)
