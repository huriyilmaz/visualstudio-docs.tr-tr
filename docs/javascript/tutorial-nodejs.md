---
title: Node.js ve Express uygulaması oluşturma
description: Bu öğreticide, Visual Studio Hızlı Web uygulaması çerçevesini kullanarak basit bir Node.js uygulaması oluşturmayı öğrenin.
ms.date: 03/25/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: dae63215fe41d42f1a20f5d21e7c51e05163281a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027987"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Visual Studio Node.js ve Express uygulaması oluşturma

Node.js ve Express kullanarak Visual Studio geliştirmeye yönelik bu öğreticide, basit bir Node.js web uygulaması oluşturur, bazı kodlar ekler, ıde 'nin bazı özelliklerini keşfedebilir ve uygulamayı çalıştırırsınız. 

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod ekleme
> * Kodu düzenlemek için IntelliSense kullanma
> * Uygulamayı çalıştırma
> * Hata ayıklayıcıda bir kesme noktasına isabet edin

## <a name="before-you-begin"></a>Başlamadan önce

İşte size bazı önemli kavramlara yol açmaya yönelik hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafını yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPM nedir?

NPM, Node.js için varsayılan paket yöneticisidir. Paket Yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamasını ve paylaşmasını kolaylaştırır ve kitaplıkları yükleme, güncelleştirme ve kaldırmayı basitleştirecek şekilde tasarlanmıştır.

### <a name="what-is-express"></a>Express nedir?

Express, Web uygulamaları oluşturmak için Node.js için sunucu çerçevesi olarak kullanılan bir Web uygulaması çerçevesidir. Express, Pug (eskiden Jade olarak adlandırılır) gibi bir kullanıcı arabirimi oluşturmak için farklı ön uç çerçeveleri seçmenize olanak sağlar. Pug Bu öğreticide kullanılır.

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

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node.js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Node.js iş yüküne dahil olan Visual Studio Node.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyici yalnızca aynı anda yüklü olan birini destekler.
    
    genellikle Visual Studio, yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node.exe yolunu** ayarlayın). Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz. 

    Bu öğretici Node.js 8.10.0 ile test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node.js projesi oluştur

Visual Studio *projedeki* tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, Node.js ve Express uygulaması için kod içeren basit bir proje ile başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve ardından **Yeni temel Azure Node.js Express 4 uygulaması oluştur** (JavaScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni Project** iletişim kutusunun sol bölmesinde, **JavaScript**' i genişletin ve **Node.js**' ı seçin. Orta bölmede **temel Azure Node.js Express 4 uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Temel Azure Node.js Express 4 uygulama** projesi şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar. *app.js* proje dosyası düzenleyicide açılır (sol bölme).

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler**' i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz. Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *package.js* ' deki ayarları ve NPM düğümündeki sağ tıklama seçenekleri ' ni kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

    (4) *package.json* , NPM tarafından yerel olarak yüklenen paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek üzere kullanılan bir dosyadır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

    (5) *app.js* gibi Project dosyalar proje düğümünün altında görünür. *app.js* , proje başlangıç dosyasıdır ve bu nedenle **kalın** olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

1. **NPM** düğümünü açın ve tüm gerekli NPM paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **NPM paketlerini yükleyebilirsiniz**' i seçebilirsiniz.

## <a name="add-some-code"></a>Kod ekleme

Uygulama ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML 'ye derlenen basit biçimlendirme kodunu kullanır. (Pug, *app.js* içinde Görünüm altyapısı olarak ayarlanır. *app.js* içinde görünüm altyapısını ayarlayan kod `app.set('view engine', 'pug');` .)

1. Çözüm Gezgini (sağ bölme) menüsünde, görünümler klasörünü açın ve *index. Pug* öğesini açın.

1. İçeriği aşağıdaki biçimlendirme ile değiştirin.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Yukarıdaki kod, bir başlık ve hoş geldiniz iletisiyle bir HTML sayfasını dinamik olarak oluşturmak için kullanılır. Sayfada Ayrıca bir düğmeye bastığınızda değişen bir görüntüyü görüntüleyen kod de yer alır.

1. Yollar klasöründe *index.js* açın.

1. Çağrısının önüne aşağıdaki kodu ekleyin `router.get` :

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Bu kod, dinamik olarak oluşturulan HTML sayfasına geçirdiğiniz bir veri nesnesi oluşturur.

1. `router.get`İşlev çağrısını aşağıdaki kodla değiştirin:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Yukarıdaki kod, Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfayı, başlık ve veri nesnesini sayfaya geçirerek oluşturur. *İndex. Pug* dosyası, *index.js* çalıştığında yüklenecek sayfa olarak belirtilir. *index.js* , *app.js* kodunda varsayılan yol olarak yapılandırılır (gösterilmez).

    Visual Studio çeşitli özelliklerini göstermek için, içeren kod satırında bir bilinçli hatası vardır `res.render` . Uygulamanın çalıştırılabilmesi için sonraki bölümde yaptığınız hatayı çözmeniz gerekir.

## <a name="use-intellisense"></a>IntelliSense kullanma

ıntellisense, kod yazarken size yardımcı olan bir Visual Studio aracıdır.

1. *index.js* içinde, içeren kod satırına gidin `res.render` .

1. İmlecinizi dizenin arkasına koyun `data` , yazın `: get` ve IntelliSense `getData` kodda daha önce tanımlanan işlevi gösterir. `getData` öğesini seçin.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Bir işlev çağrısı yapmak için ayraçları ekleyin `getData()` .

1. Önce virgül ( `,` ) işareti kaldırın `"data"` ve ifadede yeşil söz dizimi vurgulamasını görürsünüz. Söz dizimi vurgulamanın üzerine gelin.

    ![Sözdizimi görüntüleme hatası](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu iletinin son satırı, JavaScript yorumlayıcının virgül ( ) beklendiğini size `,` söyler.

1. Alt bölmede Hata Listesi **sekmesine tıklayın ve** bildirilen **sorunların türü olarak Derleme + IntelliSense'i** seçin.

    Dosya adı ve satır numarasıyla birlikte uyarı ve açıklamayı da görüyorsunuz.

    ![Hata listesini görüntüleme](../javascript/media/tutorial-nodejs-error-list.png)

1. önce virgül ( ) ekleyerek `,` kodu `"data"` düzeltin.

    Düzeltilmiş olduğunda, kod satırı şu şekilde görünüyor: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Bir sonraki adım, hata ayıklayıcının ekli olduğu Visual Studio çalıştıracak. Bunu yapmadan önce bir kesme noktası ayarlay gerekir.

1. Bu *index.js,* bir kesme noktası ayarlamak için aşağıdaki kod satırı öncesinde sol olukluna tıklayın:

    `res.render('index', { title: 'Express', "data": getData() });`

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Hata ayıklama araç çubuğunda Web Sunucusu **(Google Chrome)** veya Web Sunucusu **(Microsoft Edge) gibi hata ayıklama hedefini seçin.**

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefini seçin](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefini seçin](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Makinede Chrome mevcutsa ancak bir seçenek olarak göstermüyorsa, hata ayıklama hedefi açılan listesinden Birlikte Gözat'ı seçin ve varsayılan tarayıcı hedefi olarak Chrome'u seçin (Varsayılan Olarak **Ayarla'ya tıklayın).** 

1. Uygulamayı **çalıştırmak için F5** '**e**(  >  **Hata AyıklamaYı** Başlat ) basın.

    Hata ayıklayıcı, ayar istediğiniz kesme noktası üzerinde duraklatılır. Artık uygulama durumunu inceebilirsiniz.

1. `getData`DataTip'te özelliklerini görmek için üzerine gelin

    ![Değişkenleri inceleme](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Devam **etmek için F5** (**Devam Hata**  >  **Ayıkla**) tuşuna basın.

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde başlık olarak "Express" ve ilk paragrafta "Express'e Hoş Geldiniz" ifadesini görebilirsiniz.

1. Farklı görüntüler görüntülemek için düğmelere tıklayın.

    ![Tarayıcıda çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="optional-publish-to-azure-app-service"></a>(İsteğe bağlı) Azure App Service'de yayımlama

1. Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin.**

   ![Azure App Service’e yayımlama](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure App Service.**

    App Service **iletişim** kutusunda Azure hesabınızla oturum açabilirsiniz ve mevcut Azure aboneliklerine bağlanabilirsiniz.

1. Abonelik seçmek, kaynak grubu seçmek veya oluşturmak, app service düzlemi seçmek veya oluşturmak için kalan adımları izleyin ve ardından Azure'da yayımlamanız istendiğinde adımları izleyin. Daha ayrıntılı yönergeler için bkz. [Web dağıtımı kullanarak Azure web sitesinde yayımlama.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. Çıktı **penceresi,** Azure'a dağıtım ilerlemesini gösterir.

    Başarılı bir dağıtımda, uygulamanız Azure App Service. Bir görüntüyü görüntülemek için bir düğmeye tıklayın.

   ![Azure App Service'da çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Tebrikler, bu öğreticiyi tamamladıktan sonra!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [AngularJS dil hizmeti uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
