---
title: Node.js ve React uygulaması oluşturma
description: bir Visual Studio şablonundan Node.js web uygulaması projesi oluşturmayı öğrenin.
ms.custom: vs-acquisition
ms.date: 09/14/2021
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
ms.openlocfilehash: 71ce14b60b3c935b06a4ea3fbdc1b7765ba3bc0b
ms.sourcegitcommit: da19ed1e48259b219c61c4cb9e98b006004a5766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128052982"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>öğretici: Visual Studio Node.js ve React uygulama oluşturma

Visual Studio, kolayca bir Node.js projesi oluşturabilir ve ıntellisense ve Node.js destekleyen diğer yerleşik özellikleri kullanabilirsiniz. bu öğreticide, bir Visual Studio şablonundan bir Node.js web uygulaması projesi oluşturacaksınız. Daha sonra, React kullanarak basit bir uygulama oluşturursunuz.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * NPM paketleri Ekle
> * uygulamanıza React kod ekleyin
> * Derleyin JSX
> * Hata ayıklayıcıyı iliştirme

Başlamadan önce, size bazı önemli kavramları tanıtmak için hızlı bir SSS aşağıda verilmiştir:

- **Node.js nedir?**
  
  Node.js, JavaScript kodunu yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

- **NPM nedir?**
  
  Node.js için varsayılan paket yöneticisi NPM 'dir. Paket Yöneticisi Node.js kaynak kodu kitaplıklarını yayımlamayı ve paylaşmayı kolaylaştırır. NPM Paket Yöneticisi kitaplık yükleme, güncelleştirme ve kaldırma işlemlerini basitleştirir.

- **React nedir?**
  
  React, kullanıcı arabirimi (uı) oluşturmak için bir ön uç çerçevesidir.

- **JSX nedir?**
  
  jsx, genellikle uı öğelerini anlatmak için React ile birlikte kullanılan bir JavaScript sözdizimi uzantısıdır. Bir tarayıcıda çalıştırılabilmesi için JSX Code 'u düz JavaScript 'e derleyin gerekir.

- **WebPack nedir?**

  Web paketi, JavaScript dosyalarını bir tarayıcıda çalışabilecek şekilde paketleyebilir ve ayrıca diğer kaynakları ve varlıkları dönüştürebilir veya paketleyebilir. WebPack, JSX veya TypeScript kodu düz JavaScript 'e derleyin için Babel veya TypeScript gibi bir derleyici belirtebilir.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici aşağıdaki önkoşulları gerektirir:

- Node.js geliştirme iş yükü yüklü Visual Studio.
  
  Henüz Visual Studio yüklemediyseniz:
  
  1. Visual Studio ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.
     
  1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve ardından **yükler**' i seçin.
     
     ![Visual Studio Yükleyicisi seçili düğüm j iş yükünü gösteren ekran görüntüsü.](media/quickstart-nodejs-workload.png)
  
  Visual Studio yüklüyse ancak Node.js iş yüküne ihtiyacınız varsa:
  
  1. Visual Studio ' **de araçlar**  >  **ve özellikler al**' a gidin.
     
  1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve iş yükünü indirmek ve yüklemek için **değiştir** ' i seçin.
  
- Node.js çalışma zamanı yüklendi:
  
  Node.js çalışma zamanı yüklü değilse, [Node.js Web sitesinden LTS sürümünü yükleyebilirsiniz](https://nodejs.org/en/download/). LTS sürümü, diğer çerçeveler ve kitaplıklarla en iyi uyumluluğu içerir.
  
  Visual Studio Node.js iş yükünde Node.js araçları hem Node.js 32-bit hem de 64 bit mimari sürümlerini destekler. Visual Studio yalnızca bir sürüm gerektirir ve Node.js yükleyici tek seferde yalnızca bir sürümü destekler.
  
  Visual Studio genellikle yüklenen Node.js çalışma zamanını otomatik olarak algılar. Aksi takdirde, projenizi yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz:
  
  1. Bir proje oluşturduktan sonra, proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.
     
  1. **Özellikler** bölmesinde **Node.exe yolunu** , Node.js genel veya yerel bir yüklemesine başvuracak şekilde ayarlayın. Node.js projelerinizin her birinde yerel yorumlayıcı yolunu belirtebilirsiniz.

::: moniker range=">=vs-2022"
Bu öğretici Node.js 14.17.5 ile test edilmiştir.
::: moniker-end
::: moniker range="<=vs-2019"
Bu öğretici Node.js 12.6.2 ile test edilmiştir.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Node.js Web uygulaması projesi oluşturun.

::: moniker range=">=vs-2022"
1. Visual Studio açın ve başlangıç penceresini kapatmak için **Esc** tuşuna basın.
   
1. **CTRL** + **Q** tuşlarına basın, arama kutusuna *node.js* yazın ve açılan listeden **Web uygulaması-JavaScript Node.js boş** ' ı seçin.
   
   Bu öğretici TypeScript derleyicisini kullansa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.
   
   **Boş Node.js Web uygulaması** seçeneğini görmüyorsanız, Node.js geliştirme iş yükünü yüklemeniz gerekir. Yönergeler için bkz. [Önkoşullar](#prerequisites).
   
1. **Yeni projenizi yapılandırın** Iletişim kutusunda **Oluştur**' u seçin.
   
   Visual Studio yeni çözüm ve projeyi oluşturur ve sağ bölmede projeyi açar. *server.js* proje dosyası sol bölmedeki düzenleyicide açılır.
   
1. Sağ bölmedeki **Çözüm Gezgini** içindeki proje yapısına bakın.
   
   ![Çözüm Gezgini Node.js proje yapısını gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-project-structure.png)
   
   - En üst düzey, varsayılan olarak projenizle aynı ada sahip olan *çözümdür* (**1**). Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.
   
   - Projeniz (**2**) **yeni projenizi Yapılandır** iletişim kutusunda verdiğiniz adı kullanarak kalın renkle vurgulanır. Dosya sisteminde proje, proje klasörünüzdeki bir *. njsproj* dosyasıdır.
     
     Proje özelliklerini ve ortam değişkenlerini görmek ve ayarlamak için, **alt** + **ENTER** tuşuna basın veya projeye sağ tıklayıp bağlam menüsünden **Özellikler** ' i seçin. Diğer geliştirme araçlarıyla çalışabilirsiniz çünkü proje dosyası Node.js proje kaynağında özel değişiklikler yapmaz.
   
   - **NPM** düğümü (**3**) yüklü NPM paketlerini gösterir.
   
     NPM paketlerini aramak ve yüklemek için **NPM** düğümüne sağ tıklayın. Paketleri *Package. JSON* ' daki ayarları ve **NPM** düğümündeki sağ tıklama seçeneklerini kullanarak yükleyebilir ve güncelleştirebilirsiniz.
   
   - NPM, yerel olarak yüklenmiş paketlerin bağımlılıklarını ve sürümlerini yönetmek için *Package. JSON* dosyasını (**4**) kullanır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](npm-package-management.md).
   
   - Project dosyaları (**5**) proje düğümünün altında görünür. Proje başlangıç dosyası *server.js*, kalın olarak gösterilir.
     
     Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.
::: moniker-end
::: moniker range="vs-2019"
1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve sonra **Web uygulaması-JavaScript Node.js boş** seçeneğini belirleyin. (Bu öğretici TypeScript derleyicisini kullanıyor olsa da, adımlar **JavaScript** şablonuyla başlamanız gerekir.)
    
    Görüntülenen iletişim kutusunda **Oluştur**' u seçin.

    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi açar.

    ![Çözüm Gezgini Node.js projeyi gösteren ekran görüntüsü](media/tutorial-nodejs-react-project-structure.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler** ' i seçerek (veya **alt** Enter ' a basarak) projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz  +  . Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *Package. JSON* ' daki ayarları kullanarak paketleri yükleyip güncelleyebilir ve NPM düğümündeki Seçenekler ' e sağ tıklayın.

    (4) *Package. JSON* , NPM tarafından, yerel olarak yüklenen paketlere yönelik paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

    (5) *server.js* gibi Project dosyalar proje düğümünün altında görünür. *server.js* , proje başlangıç dosyasıdır ve bu nedenle **kalın** olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.
::: moniker-end
::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni uygulama iletişim kutusunun sol **bölmesinde JavaScript Project** genişletin ve ardından Yeni'yi **Node.js.**  Orta bölmede Boş uygulama web **Node.js' seçin,** **NodejsWebAppBlank adını** yazın ve tamam'ı **seçin.**

    Blank **Node.js Web Uygulaması** proje şablonunu görmüyorsanız, uygulama geliştirme işNode.js **eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi açar.

    ![Node.js projesini gösteren ekran Çözüm Gezgini](media/tutorial-nodejs-react-project-structure.png)

    (1) Yeni  Çalışma Alanı iletişim kutusunda verdiği adı kullanarak projeniz kalın **Project** vurgulanır. Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek (veya Alt Enter tuşuna basarak) projeyle **ilişkili özellikleri** ve ortam **değişkenlerini ayarlayın.**  +   Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm paketlerini bir iletişim kutusu kullanarak aramak ve yüklemek için npm düğümüne sağ tıklar veya *package.json'daki* ayarları kullanarak paketleri yükleyebilir ve güncelleştirin ve npm düğümünde sağ tıklayın.

    (4) *package.json,* npm tarafından yerel olarak yüklenmiş paketlerin paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5) Project gibi *server.js* proje düğümü altında gösterir. *server.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**
::: moniker-end

## <a name="add-npm-packages"></a>npm paketleri ekleme

Bu uygulama, aşağıdaki npm modüllerini doğru şekilde çalıştırmayı gerektirir:

- Tepki
- react-dom
- express
- path
- ts-loader
- typescript
- Webpack
- webpack-cli

Paket yüklemek için:

1. Bu **Çözüm Gezgini** **npm** düğümüne sağ tıklayın ve Yeni **npm Paketleri Yükle'yi seçin.**
   
1. Yeni **npm Paketlerini Yükle iletişim kutusunda** **react** paketini arayın ve Paketi **Yükle'yi seçerek** yükleyin.

    ::: moniker range=">=vs-2022"
    ![Npm paketini yüklemeyi gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-install-package.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Npm paketini yüklemeyi gösteren ekran görüntüsü.](media/tutorial-nodejs-react-install-package.png)
    ::: moniker-end

    Yeni **npm Paketlerini Yükle iletişim** kutusunda, en güncel paket sürümünü yükleyebilir veya bir sürüm belirtebilirsiniz. Geçerli sürümleri yüklemeyi seçerseniz ancak daha sonra beklenmeyen hatayla karşılaşacaksanız, sonraki adımda listelenen tam paket sürümlerini yüklemeyi deneyin.

    Alt **bölmede** yer alan Visual Studio penceresinde paket yükleme ilerleme durumu gösterilir. Çıkışı **Görüntüle'yi** seçerek **veya**  >   **Ctrl** Alt O tuşlarına basarak Çıkış + **penceresini** + **açın.** Çıktı **penceresinin Çıktıyı** göster **alanında** **Npm'yi seçin.**

    Yüklendikten sonra **react paketi,** içinde **npm düğümü altında** **Çözüm Gezgini.**
    
    Projenin *package.json dosyası,* paket sürümü de dahil olmak üzere yeni paket bilgileriyle sonlanıyor.

Kullanıcı arabirimini kullanarak paketlerin geri kalanını tek tek aramak ve eklemek yerine, gerekli paket kodunu *package.json içine yapıştırabilirsiniz.*
    
1. bu **Çözüm Gezgini,** **package.json'u** Visual Studio açın. Dosyanın `dependencies` sonuna aşağıdaki bölümü ekleyin:

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

    Dosyada zaten bir bölüm `dependencies` varsa, önceki JSON koduyla değiştirin. *package.json* dosyasını kullanma hakkında daha fazla bilgi için bkz. [package.json yapılandırması.](configure-packages-with-package-json.md)

1. **Değişiklikleri kaydetmek için Ctrl** + **S**   >  **tuşlarına basın veya Dosya Kaydet package.json** öğesini seçin.

1. Bu **Çözüm Gezgini** projenizin **npm** düğümüne sağ tıklayın ve Npm Paketlerini **Yükle'yi seçin.**

    Bu komut, *packages.json* içinde listelenen tüm paketleri yüklemek için npm install komutunu doğrudan çalıştırır.

    Yüklemenin **ilerlemesini** görmek için alt bölmede Çıkış penceresini seçin. Yükleme birkaç dakika sürebilir ve sonuçları hemen görmeyebilirsiniz. Çıkış penceresindeki Çıkış çıkışını göster alanında  **Npm'yi** seçin. 

    Yüklemeden sonra, npm modülleri Çözüm Gezgini'daki **npm** **düğümünde görünür.**

    ::: moniker range=">=vs-2022"
    ![Yüklü npm paketlerini gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-npm-modules-installed.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Yüklü npm paketlerini gösteren ekran görüntüsü.](media/tutorial-nodejs-react-npm-modules-installed.png)
    ::: moniker-end

    > [!NOTE]
    > Komut satırı kullanarak npm paketlerini de yükleyebilirsiniz. Bu **Çözüm Gezgini** proje adına sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.** Paketleri yüklemek Node.js standart komutlarını kullanın.

## <a name="add-project-files"></a>Proje dosyaları ekleme

Ardından projenize dört yeni dosya ekleyin.

- *app.tsx*
- *webpack-config.js*
- *index.html*
- *tsconfig.json*

Bu basit uygulama için yeni proje dosyalarını proje köküne eklersiniz. Çoğu uygulama için, dosyaları alt klasörlere ekler ve göreli yol başvurularını buna göre ayarlarsiniz.

1. Bu **Çözüm Gezgini** proje adını seçin ve **Ctrl** Shift A tuşlarına basın veya proje adına sağ tıklar ve Yeni Öğe +  +  **Ekle'yi**  >  **seçin.**

1. Yeni Öğe **Ekle iletişim kutusunda** **TypeScript JSX Dosyası'ı seçin,** *app.tsx* adını yazın ve Ekle veya **Tamam'ı** **seçin.**

1. webpack-config.jsadlı bir **JavaScript dosyası** *eklemek için buwebpack-config.js.*

1. index.htmladlı bir **HTML dosyası** *eklemek için buindex.html.*

1. *tsconfig.json* adlı **bir TypeScript JSON Yapılandırma Dosyası** eklemek için bu adımları tekrarlayın.

## <a name="add-app-code"></a>Uygulama kodu ekleme

1. Burada **Çözüm Gezgini'** **server.js** açın ve mevcut kodu aşağıdaki kodla değiştirin:

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

   Yukarıdaki kod, web uygulaması sunucunuz olarak Node.js express kullanır. Kod, bağlantı noktasını varsayılan olarak 1337 olan proje özelliklerinde yapılandırılan bağlantı noktası numarasına ayarlar. Proje özelliklerini açmamız gerekirse, proje içinde proje adına sağ tıklayın ve **Çözüm Gezgini'yi** **seçin.**

1. **app.tsx'i** açın ve aşağıdaki kodu ekleyin:

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

    Yukarıdaki kod JSX söz dizimi kullanır ve React görüntülemek için kullanılır.

1. Aşağıdaki **index.html** açın ve `body` bölümünü aşağıdaki kodla değiştirin:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Bu HTML *sayfası, JSXapp-bundle.js* içeren ve düz JavaScript'e React kodu içeren bir kod yükler. Şu *andaapp-bundle.js* boş bir dosyadır. Sonraki bölümde, kodun transpilesine geçiş yapmak için seçenekleri yapılandırabilirsiniz.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Webpack ve TypeScript derleyici seçeneklerini yapılandırma

Ardından, webpack yapılandırma kodunu uygulamasına *webpack-config.js.* JSX'i düz JavaScript'e paketlemek ve değiştirmek için bir giriş dosyası, *app.tsx* ve *app-bundle.js* çıkış dosyası belirten basit bir web paketi yapılandırması eklersiniz. Transpiling için bazı TypeScript derleyici seçeneklerini de yapılandırabilirsiniz. Bu temel yapılandırma kodu, webpack'e ve TypeScript derleyiciye giriş bilgileridir.

1. Bu **Çözüm Gezgini'** **webpack-config.js** açın ve aşağıdaki kodu ekleyin.

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

1. **tsconfig.json'u** açın ve içeriğini TypeScript derleyici seçeneklerini belirten aşağıdaki kodla değiştirin:

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

    Kod, kaynak dosya *olarak app.tsx* dosyasını belirtir.

1. Tüm **değişiklikleri kaydetmek için Ctrl** + **Shift** + **S**   >  **tuşlarına basın veya Dosya Hepsini** Kaydet'i seçin.

## <a name="transpile-the-jsx"></a>JSX'i transpile

1. Bu **Çözüm Gezgini** proje adına sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.**

1. Komut istemine aşağıdaki webpack komutunu girin:

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Komut istemi penceresinde sonuç gösterilir.

    ![Webpack komutunu çalıştırmanın sonuçlarını gösteren ekran görüntüsü.](media/tutorial-nodejs-react-run-webpack-cmd.png)

    Önceki çıkış yerine herhangi bir hata görüyorsanız, bunları, uygulamanın çalışmadan önce çözümlemeniz gerekir. npm paketi sürümleriniz bu öğreticinin belirtilen sürümlerinden farklı ise hatalara neden olabilir. Hataları düzeltmenin bir yolu, önceki adımda gösterilen tam sürümleri kullanmaktır.
    
    Ayrıca, bir veya daha fazla paket sürümü kullanım dışı kaldı ve bir hatayla sonuçlanıyorsa, hataları düzeltmek için daha yeni bir sürüm yüklemeniz gerekir. npm paket sürümlerini *kontrol etmek için package.json* kullanma hakkında bilgi için bkz. [package.json yapılandırması.](../javascript/configure-packages-with-package-json.md)

1. Uygulama **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Var Olan Klasörü   >  **Ekle'yi seçin.**

1. *dist klasörünü ve* ardından Klasör **Seç'i seçin.**

    Visual Studio,app-bundle.jsve *app-bundle.js.map* içeren  *dist* klasörünü projeye ekler.

1. JavaScript *app-bundle.js* görmek içinapp-bundle.js'yi açın.

1. Harici olarak değiştirilmiş dosyaların yeniden yük isteyip olmadığı sorsa, Evet'i **All (Tüm dosyalar) olarak seçin.**

    ![Değiştirilen dosyaların yüklenip yüklenmey istemini gösteren ekran görüntüsü.](media/tutorial-nodejs-react-reload-files.png)

*app.tsx üzerinde her değişiklik yaptığınız* zaman webpack komutunu yeniden çalıştırmanız gerekir. Bu adımı otomatikleştirmek için, JSX'i transpile etmek için bir derleme betiği ekleyin.

### <a name="add-a-build-script-to-transpile-the-jsx"></a>JSX'i transpile etmek için derleme betiği ekleme

Visual Studio 2019 Visual Studio sürümleri için derleme betiği gerekir. Önceki bölümde gösterildiği gibi JSX'i komut satırına çeviri yapmak yerine JSX'i komut satırına Visual Studio.

1. *package.json'ı* açın ve bölümünden sonra aşağıdaki bölümü `dependencies` ekleyin:

   ```json
   "scripts": {
    "build": "webpack-cli ./app.tsx --config webpack-config.js"
   }
   ```

1. Yaptığınız değişiklikleri kaydedin.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Hata Ayıklama **araç çubuğunda,** hata ayıklama hedefi **olarak Web Sunucusu (Microsoft Edge)** veya **Web Sunucusu (Google Chrome)** öğesini seçin.

    ::: moniker range=">=vs-2022"
    ![Hata ayıklama hedefi olarak Microsoft Edge seçmeyi gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="=vs-2019"
    ![Hata ayıklama hedefi olarak Chrome'u seçmeyi gösteren ekran görüntüsü.](media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefi olarak Chrome'u seçmeyi gösteren ekran görüntüsü.](media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Tercih ettiğiniz hata ayıklama hedefinin makinede kullanılabilir olduğunu biliyorsanız ancak bir  seçenek olarak görünmüyorsa, hata ayıklama hedefi açılan listesinden Birlikte Gözat'ı seçin. Listeden varsayılan tarayıcı hedefini seçin ve Varsayılan olarak **Ayarla'ya tıklayın.**

1. Uygulamayı çalıştırmak için **F5** tuşuna basın, yeşil ok düğmesini seçin veya Hata Ayıklamayı   >  **Başlat'ı seçin.**

    Hata Node.js dinleme bağlantı noktasını gösteren bir konsol penceresi açılır.

    Visual Studio başlangıç dosyasını başlatarak uygulamayı başlatır ve *server.js.*

    ![Tarayıcıda çalışan React gösteren ekran görüntüsü.](media/tutorial-nodejs-react-running-react.png)

1. Tarayıcıyı ve konsol pencerelerini kapatın.

## <a name="set-a-breakpoint-and-run-the-app"></a>Kesme noktası ayarlama ve uygulamayı çalıştırma

Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, çalışan Visual Studio askıya alınması gereken yeri gösterir. Ardından değişken değerlerini, bellek davranışını veya bir kod dallarının çalıştırıp çalışmamalarını gözlemlersiniz.

1. Bu *server.js,* bir kesme noktası ayarlamak için bildirimin sol `staticPath` tarafından yer alan oluklara tıklayın:

    ::: moniker range=">=vs-2022"
    ![dot js sunucusunda staticPath bildirimi için ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-set-breakpoint.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![dot js sunucusunda staticPath bildirimi için ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/tutorial-nodejs-react-set-breakpoint.png)
    ::: moniker-end

1. Uygulamayı çalıştırmak için **F5** tuşuna basın veya Hata AyıklamaYı   >  **Başlat'ı seçin.**

    Hata ayıklayıcısı, geçerli deyimi vurgulanmış şekilde, ayarlanmış kesme noktası sırasında duraklatılır. Artık Yerel Ayarlar ve İzleme pencereleri gibi hata ayıklayıcı pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerine gelerek **uygulama durumunu** **inceleyebilirsiniz.**

1. Uygulamayı çalıştırmaya devam etmek için F5 tuşuna **basın,** Hata Ayıklama **araç** çubuğunda Devam'ı **seçin** veya Devam'da **Hata Ayıkla'ya**  >  **tıklayın.**

   Microsoft Edge için Chrome Geliştirici Araçları veya F12 Araçları'Microsoft Edge **F12 tuşuna basın.** JavaScript Konsolu'nu kullanarak DOM'ı incelemek ve uygulamayla etkileşim kurmak için bu araçları kullanabilirsiniz.

1. Tarayıcıyı ve konsol pencerelerini kapatın.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>İstemci tarafı kodda kesme noktası ayarlama ve React isabet

Önceki bölümde hata ayıklayıcıyı sunucu tarafı koda Node.js. hata ayıklayıcısını istemci tarafı koda eklemek React kesme noktalarına isabet etmek için, hata ayıklayıcıyı doğru işleme eklemeniz gerekir. Burada bir tarayıcıyı etkinleştirmenin ve hata ayıklama işlemi eklemenin bir yolu vardır.

### <a name="enable-the-browser-for-debugging"></a>Hata ayıklama için tarayıcıyı etkinleştirme

::: moniker range=">=vs-2019"
Microsoft Edge veya Google Chrome kullanabilirsiniz. Hedef tarayıcı için tüm pencereleri kapatın. Daha Microsoft Edge chrome'un tüm örneklerini de kapatın. Her iki tarayıcı da kod Chromium paylaştığı için, her iki tarayıcının da kapatılması en iyi sonuçları verir.

Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. Tarayıcı uzantıları tam hata ayıklama modunu önleyebildi. Çalışan tüm Chrome örneklerini bulmak ve sona ererken Görev Yöneticisi'ni kullanabilirsiniz.

Hata ayıklama etkinken tarayıcınızı başlatmak için:

1. Hata **Ayıklama araç çubuğundaki** açılan listeden Birlikte **Gözat'ı** seçin. 
   
1. Tercih ettiğiniz **tarayıcı vurgulanmış** şekilde Birlikte Gözat ekranında Ekle'yi **seçin.**
   
1. Bağımsız Değişkenler *alanına --remote-debugging-port=9222* **bayrağını** girin.
   
1. Tarayıcıya Hata ayıklama ile *Edge* veya hata ayıklama ile Chrome gibi yeni bir *kolay ad* girin ve tamam'ı **seçin.**
   
1. Birlikte Gözat **ekranında Gözat'ı** **seçin.**

    ![Hata ayıklama etkinleştirilmiş bir Edge tarayıcısı oluşturmayı gösteren ekran görüntüsü.](media/tutorial-nodejs-react-edge-with-debugging.png)

- Alternatif olarak, Başlat düğmesine **sağ** tıklayarak Çalıştır Windows **açabilir ve** şunları girebilirsiniz:
  
  `msedge --remote-debugging-port=9222`
  
  veya
  
  `chrome.exe --remote-debugging-port=9222`
::: moniker-end

::: moniker range="vs-2017"
Bu senaryo için Chrome kullanın.

1. Tüm Chrome tarayıcı pencerelerini kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. Tarayıcı uzantıları tam hata ayıklama modunu önleyebildi. Çalışan tüm Chrome örneklerini bulmak için Görev Yöneticisi'ni açabilirsiniz.

2. Hata ayıklama etkinleştirildiğinde tarayıcınızı başlatabilirsiniz.

    Başlat **düğmesinin** Çalıştır Windows **açın** (sağ tıklayın ve **Çalıştır'ı seçin)** ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
::: moniker-end

Tarayıcı hata ayıklama etkin olarak başlar. Uygulama henüz çalışmamıştır, bu nedenle tarayıcı sayfası boştur.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğine ekleme

1. Visual Studio düzenleyicisinde,app-bundle.js *veya app.tsx kaynak kodunda bir kesme noktası* ayarlayın. 

    - Daha *app-bundle.js* için işlevinde kesme noktası `render()` ayarlayın. İşleviapp-bundle.jsbulmak `render()` *için* **Ctrl** F tuşlarına basın veya Bul ve Değiştir Hızlı Bul'ı düzenle'yi seçin ve +  arama   >    >  alanına *işleme* girin.

      ::: moniker range=">=vs-2022"
      ![app-bundle dot js içinde işleme işlevinde ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-set-breakpoint-client-code.png)
      ::: moniker-end
      ::: moniker range="<=vs-2019"
      ![app-bundle dot js içinde işleme işlevinde ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/tutorial-nodejs-react-set-breakpoint-client-code.png)
      ::: moniker-end

    - *app.tsx* için işlevinin içindeki kesme `render()` noktası olan deyimini `return` ayarlayın.

      ::: moniker range=">=vs-2022"
      ![Uygulama nokta t s x'te işleme işlevinin dönüş deyiminde ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-react-set-breakpoint-tsx-file.png)
      ::: moniker-end
      ::: moniker range="<=vs-2019"
      ![Uygulama nokta t s x'te işleme işlevinin dönüş deyiminde ayarlanmış bir kesme noktası gösteren ekran görüntüsü.](media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)
      ::: moniker-end

      *app.tsx'te* kesme noktası ayarlanırsa, aşağıdaki *koduwebpack-config.js* ve değişikliklerinizi kaydetmek için de bu kesme noktası güncelleştirildi.

      Bu kodu değiştirin:

      ```javascript
      output: {
          filename: "./app-bundle.js",
      },
      ```

      Yerine şu kodu yazın:

      ```javascript
      output: {
          filename: "./app-bundle.js",
          devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
      },
      ```

      Bu yalnızca geliştirme ayarı, hata ayıklamayı Visual Studio. Varsayılan olarak, kaynak eşleme dosyasındaki webpack başvuruları, *webpack:///* *app.tsx* dosyasını bulmasını Visual Studio ön eklerini içerir. Bu ayar, uygulamayı oluşturulurken kaynak eşleme dosyasında oluşturulan *başvuruları (app-bundle.js.map)* geçersiz kılar. Özel olarak, bu ayar kaynak dosyanın başvurus webpack:///./app.tsx hata *ayıklamayı* sağlayan *./app.tsx* olarak değiştirir.

1. Visual Studio'de hata ayıklama hedefi olarak hedef tarayıcınızı seçin ve **ardından Ctrl** F5 tuşlarına basın veya Hata Ayıklama Olmadan Başlat'ı seçerek uygulamayı +    >  tarayıcıda çalıştırın.

    ::: moniker range=">=vs-2019"
    Kolay bir adla hata ayıklama özellikli bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bu tarayıcıyı seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

1. İşleme **Ekle hata**  >  **ayıkla'ya veya** **Ctrl** Alt P + **tuşlarına** + **basın.**

    > [!TIP]
    > İşleme ilk kez iliştirilme işleminin ardından, İşleme Yeniden Ekle'de Hata Ayıkla'ya veya Shift Alt P'ye basarak aynı işleme hızla  >    + **yeniden** + **iliştirin.**

1. İşleme **Ekle iletişim** kutusunda, ekleyebilirsiniz tarayıcı örneklerinin filtrelenmiş bir listesini elde edin.

    ::: moniker range=">=vs-2019"
    Hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium) için** doğru hata ayıklayıcının, Ekle alanında **göründüğünden emin** olun. Sonuçları *filtrelemek* *için* filtre kutusuna chrome veya edge yazın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017'Visual Studio 2017'de, **Ekle alanında Webkit** **kodunu** seçin. Arama **sonuçlarını** filtrelemek için filtre kutusuna chrome yazın.
    ::: moniker-end

1. Bu örnekte doğru konak bağlantı noktası **localhost olan tarayıcı** işlemini seçin. Doğru işlemi seçmenize yardımcı olmak için Başlık alanında  **1337** veya **localhost** bağlantı noktası da görünebilir.

1. **Ekle'yi seçin.**

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnekte, Microsoft Edge **tarayıcısı için** İşleme Ekle penceresi gösterilir.

    ![İşleme ekle iletişim kutusunu gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle iletişim kutusunu gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Hata ayıklayıcı doğru şekilde ekleniyorsa, DOM Gezgini ve JavaScript Konsolu Visual Studio. Bu hata ayıklama araçları Chrome Geliştirici Araçları ve F12 Tools for Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcısı eklenmezse ve işleme **eklenemiyor iletisiyle karşılaşabilirsiniz. Bir işlem geçerli durumda yasal değildir.**, tarayıcıyı hata ayıklama modunda başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engel ediyor olabilir.

1. Kesme noktasıyla kod zaten yürütülür olduğundan, kesme noktasıyla bağlantı noktasıyla bağlantı için tarayıcı sayfanızı yenileyin.

    Ortamınıza, tarayıcı durumuna ve daha önce hangi adımları takip ettiğine  bağlı olarak,app-bundle.jsveya *app.tsx'te* eşlenmiş konumu ile kesme noktasıyla karşınıza çıktı. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

    Hata ayıklayıcı duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kodda adım adım ilerlerken  **F11 tuşuna basın** veya Adım Adımında Hata Ayıkla'ya veya  >   **F10'a** basın ya da Üzerinden Hata Ayıkla'ya   >  **basın.** Kodu çalıştırmaya devam etmek için **F5 tuşuna basın veya Devam'ı** **seçin.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

   - *app.tsx'te* koda ara ve ardından,  önceki adımlarda açıklandığı gibi hata ayıklayıcıyı eklemek için İşleme Ekle'yi kullanarak yeniden deneyin. Ortamınız doğru şekilde ayarlanmış olduğundan emin olun:

      - Görev Yöneticisi'ni kullanarak Chrome uzantıları dahil olmak üzere tüm tarayıcı örneklerini kapatın. Tarayıcıyı hata ayıklama modunda başlatın.

      - Kaynak eşleme dosyanız için *./app.tsx* başvurusu olduğundan ve *webpack:///./app.tsx'ye* başvuru olduğundan emin olun. Bu, Visual Studio hata ayıklayıcısının *app.tsx dosyasını bulmasını önler.*

     Veya app.tsx içinde deyimini kullanmayı deneyin veya Bunun yerine Chrome Geliştirici Araçları veya `debugger;` F12 Tools'ta kesme Microsoft Edge ayarlayın.

   - app-bundle.js'de koda *gireapp-bundle.js,* *app-bundle.js.map kaynak eşleme dosyasını kaldırın.*

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)
