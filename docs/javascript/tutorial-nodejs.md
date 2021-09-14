---
title: Node.js ve Express uygulaması oluşturma
description: Bu öğreticide, express web uygulaması çerçevesini kullanarak basit Node.js uygulama oluşturma hakkında bilgi Visual Studio.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635886"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Node.js express uygulaması oluşturma Visual Studio

Node.js express kullanarak Visual Studio geliştirme için bu öğreticide basit bir Node.js web uygulaması oluşturacak, kod ekser, IDE'nin bazı özelliklerini keşfeder ve uygulamayı çalıştırabilirsiniz. 

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod ekleme
> * IntelliSense kullanarak kodu düzenleme
> * Uygulamayı çalıştırma
> * Hata ayıklayıcısında bir kesme noktası isabeti

## <a name="before-you-begin"></a>Başlamadan önce

Bazı temel kavramları size tanıtan hızlı bir SSS'yi burada bulabilirsiniz.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafı yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>npm nedir?

npm, uygulamanın varsayılan paket Node.js. Paket yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamalarını ve paylaşmalarını kolaylaştırır ve kitaplıkları yüklemeyi, güncelleştirmeyi ve kaldırmayı basitleştirmek için tasarlanmıştır.

### <a name="what-is-express"></a>Express nedir?

Express, web uygulamaları derlemek için sunucu çerçevesi olarak Node.js bir web uygulaması çerçevesidir. Express, Pug (eski adı Jade) gibi bir kullanıcı arabirimi oluşturmak için farklı ön uç çerçeveleri seçmenize olanak sağlar. Pug bu öğreticide kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Uygulama ve Visual Studio geliştirme iş Node.js gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![VS YükleyicisiNode.js de iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js gerekir.

    Yüklü yoksa, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için [ LTS ](https://nodejs.org/en/download/) sürümünüNode.jsweb sitesinden yüklemenizi öneririz. Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır. Node.js iş yüküne dahil Visual Studio araçları her iki sürümü Node.js destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca birinin yüklü olduğunu destekler.
    
    Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanının başvurusu için yapılandırabilirsiniz (bir proje oluşturduk sonra proje düğümüne sağ tıklayın, Özellikler'i seçin veNode.exe **yolunu ayarlayın).** Bir yerel yorumlayıcının Node.js yüklemesini kullanabilir veya her bir yerel yorumlayıcının yolunu Node.js belirtebilirsiniz. 

    Bu öğretici 8.10.0 Node.js test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node.js oluşturma

Visual Studio projesinde tek bir uygulamanın dosyalarını *yönetir.* Proje kaynak kodunu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, bir Node.js ve express uygulaması için kod içeren basit bir projeyle başlayacaktır.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, **Node.js** yazın, ardından Yeni bir Temel Azure Node.js Express 4 uygulaması (JavaScript) oluştur'a tıklayın.  Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni Giriş iletişim kutusunun sol **bölmesinde JavaScript Project** genişletin ve ardından Yeni'yiNode.js.  **** Orta bölmede Temel Azure Node.js **Express 4 uygulamasını ve ardından Tamam'ı** **seçin.**
    ::: moniker-end
    Temel Azure Node.js **Express 4 uygulama** projesi şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi sağ bölmede açar. app.js proje dosyası düzenleyicide (sol bölme) açılır.

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1) Yeni  Çalışma Alanı iletişim kutusunda verdiği ad kullanılarak projeniz kalın **Project** vurgulanır. Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini **ayarlayın.** Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm paketlerini bir iletişim kutusu kullanarak aramak ve yüklemek için npm düğümüne sağ tıklar veya *package.json'daki* ayarları kullanarak paketleri yükleyebilir ve güncelleştirin ve npm düğümünde sağ tıklayın.

    (4) *package.json,* npm tarafından yerel olarak yüklenmiş paketlerin paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5) Project gibi *app.js* proje düğümü altında gösterir. *app.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**

1. **npm düğümünü** açın ve tüm gerekli npm paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklar ve Npm Paketlerini **Yükle'yi seçebilirsiniz.**

## <a name="add-some-code"></a>Kod ekleme

Uygulama, ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML'ye derlenmiş basit işaretleme kodunu kullanır. (Pug, 'de görünüm altyapısı *app.js.* içinde görünüm altyapısını ayar *app.js* `app.set('view engine', 'pug');` kodudur.)

1. Bu Çözüm Gezgini (sağ bölme) görünümler klasörünü ve ardından *index.pug'yi açın.*

1. İçeriği aşağıdaki işaretlemeyle değiştirin.

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

    Yukarıdaki kod, bir başlık ve karşılama iletisiyle dinamik olarak HTML sayfası oluşturmak için kullanılır. Sayfa, bir düğmeye her bastığınızda değişir bir görüntü görüntülemek için kod da içerir.

1. routes klasöründe *index.js.*

1. çağrısının önce aşağıdaki kodu `router.get` ekleyin:

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

    Bu kod, dinamik olarak oluşturulan HTML sayfasına aktaran bir veri nesnesi oluşturur.

1. İşlev `router.get` çağrısını aşağıdaki kodla değiştirin:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Yukarıdaki kod, Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfayı işler ve başlığı ve veri nesnesini sayfaya iletir. *Index.pug* dosyası burada, bir dosya çalıştırılamazken yük *index.js* belirtilir. *index.js* kodda varsayılan yol olarak *app.js* (gösterilmez) yapılandırılır.

    Uygulamanın çeşitli Visual Studio göstermek için, içeren kod sırasında kasıtlı bir hata `res.render` vardır. Uygulamanın çalışması için önce hatayı düzeltmelisiniz. Bunu bir sonraki bölümde yapacaksınız.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense, Visual Studio yardımcı olan bir araçtır.

1. Bu *index.js*, içeren kod satırına `res.render` gidin.

1. İmlecinizi `data` dize, tür ve IntelliSense'in altına yerleştirdikten sonra `: get` `getData` kodda daha önce tanımlanan işlev gösterilir. `getData` öğesini seçin.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Parantezleri işlev çağrısı yapmak için `getData()` ekleyin.

1. Önce virgül ( `,` ) kaldırıyor `"data"` ve ifadede yeşil söz dizimi vurgusu görüyorsunuz. Söz dizimi vurgulamanın üzerine gelin.

    ![Söz dizimi hatasını görüntüleme](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu iletinin son satırı, JavaScript yorumlayıcının virgül ( ) beklendiğini size `,` söyler.

1. Alt bölmede Hata Listesi **sekmesine tıklayın ve** bildirilen **sorunların türü olarak Derleme + IntelliSense'i** seçin.

    Uyarıyı ve açıklamayı dosya adı ve satır numarasıyla birlikte görüyorsunuz.

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

1. Hata ayıklama araç çubuğunda Web Sunucusu **(Google Chrome) veya Web Sunucusu (Microsoft Edge)** gibi hata ayıklama **hedefini seçin.**

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

    Başarılı bir dağıtımda, uygulamanız Azure App Service.'de çalışan bir tarayıcıda açılır. Bir görüntüyü görüntülemek için bir düğmeye tıklayın.

   ![Azure App Service'de çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Tebrikler, bu öğreticiyi tamamladıktan sonra!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [AngularJS dil hizmeti uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
