---
title: Node.js ve Express uygulaması oluşturma
description: Bu öğreticide, express web uygulaması çerçevesini kullanarak basit Node.js uygulama oluşturma hakkında bilgi Visual Studio.
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2bca688977187071b5530911f9aa975e10ceef99
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306533"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Node.js'de express uygulaması Visual Studio

Node.js ve Express kullanarak Visual Studio geliştirme için bu öğreticide basit bir Node.js web uygulaması oluşturacak, kod ekser, IDE'nin bazı özelliklerini keşfeder ve uygulamayı çalıştırabilirsiniz. 

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

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

Node.js JavaScript sunucu tarafı yürüten bir sunucu tarafı JavaScript çalışma zamanı ortamıdır.

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

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![VS YükleyicisiNode.js de iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js yüklü olmalıdır.

    Yüklü yoksa, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için [ LTS ](https://nodejs.org/en/download/) sürümünüNode.jsweb sitesinden yüklemenizi öneririz. Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır. Node.js iş yüküne dahil Visual Studio araçları her Node.js sürümleri destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca birinin yüklü olduğunu destekler.
    
    Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanının başvurusu için yapılandırabilirsiniz (proje oluşturduk sonra proje düğümüne sağ tıklayın, Özellikler'i seçin veNode.exe **yolunu ayarlayın).** Bir yerel yorumlayıcının Node.js yüklemesini kullanabilir veya her bir yerel yorumlayıcının yolunu Node.js belirtebilirsiniz. 

    Bu öğretici 8.10.0 Node.js test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node.js oluşturma

Visual Studio projesinde tek bir uygulamanın dosyalarını *yönetir.* Proje kaynak kodunu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, bir Node.js express uygulaması için kod içeren basit bir projeyle başlayacaktır.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın,Node.jsyazın, ardından Yeni bir Temel Azure Node.js Express 4 uygulaması (JavaScript) oluştur'a tıklayın. ****  Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Proje'yi**  >    >  **seçin.** Yeni Proje iletişim kutusunun sol **bölmesinde** **JavaScript'i** genişletin ve ardından Yeni **Proje'Node.js.** Orta bölmede Temel Azure Express **4 Node.js'ı ve ardından** Tamam'ı **seçin.**
    ::: moniker-end
    Temel Azure Node.js **Express 4 uygulama** projesi şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **gerekir.** Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi sağ bölmede açar. app.js proje dosyası düzenleyicide (sol bölme) açılır.

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1) Yeni Proje **iletişim** kutusunda verdiği ad kullanılarak projeniz kalın **olarak vurgulanır.** Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini **ayarlayın.** Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde, varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm düğümünü sağ tıklar ve npm paketlerini bir iletişim kutusu kullanarak arayabilir ve  yükleyebilir veya npm düğümündepackage.js'daki ayarları kullanarak paketleri yükleyebilir ve güncelleştirebilirsiniz.

    (4) *package.js,* npm tarafından yerel olarak yüklenmiş paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5)app.js *gibi* proje dosyaları proje düğümü altında gösterir. *app.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**

1. **npm düğümünü** açın ve tüm gerekli npm paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklar ve Npm Paketlerini **Yükle'yi seçebilirsiniz.**

## <a name="add-some-code"></a>Kod ekleme

Uygulama, ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML'ye derlenmiş basit işaretleme kodunu kullanır. (Pug, içinde görünüm altyapısı olarak *app.js.* görünüm altyapısını ayarlarken kod *app.js* `app.set('view engine', 'pug');` olur.)

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

    Yukarıdaki kod Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfayı işler ve başlığı ve veri nesnesini sayfaya iletir. *Index.pug* dosyası burada, bir dosya çalıştırılamazken yük *index.js* belirtilir. *index.js* kodda varsayılan yol olarak *yapılandırılırapp.js* (gösterilmez).

    Uygulamanın çeşitli Visual Studio göstermek için, içeren kod sırasında kasıtlı bir hata `res.render` vardır. Uygulamanın çalışması için önce hatayı düzeltmelisiniz. Bunu bir sonraki bölümde yapacaksınız.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense, Visual Studio yardımcı olan bir araçtır.

1. Içinde *index.js*, içeren kod satırına `res.render` gidin.

1. İmlecinizi `data` dize, tür ve IntelliSense'in altına yerleştirdikten sonra `: get` `getData` kodda daha önce tanımlanan işlev gösterilir. `getData` öğesini seçin.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Parantezleri işlev çağrısı yapmak için `getData()` ekleyin.

1. Önce virgül ( `,` ) kaldırıyor `"data"` ve ifadede yeşil söz dizimi vurgusu görüyorsunuz. Söz dizimi vurgulamanın üzerine gelin.

    ![Söz dizimi hatasını görüntüleme](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu iletinin son satırı JavaScript yorumlayıcı 'nın bir virgül () beklediğine bildirir `,` .

1. Alt bölmede **hata listesi** sekmesine tıklayın ve bildirilen sorun türleri için **Oluştur + IntelliSense** ' i seçin.

    Dosya adı ve satır numarası ile birlikte uyarı ve açıklama görürsünüz.

    ![Hata listesini görüntüle](../javascript/media/tutorial-nodejs-error-list.png)

1. Daha önce virgül () ekleyerek kodu düzeltir `,` `"data"` .

    Düzeltildiğinde, kod satırının şöyle görünmesi gerekir: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Uygulamayı Visual Studio hata ayıklayıcısı ekli olarak çalıştırmaya devam edersiniz. Bunu yapmadan önce bir kesme noktası ayarlamanız gerekir.

1. *index.js*, bir kesme noktası ayarlamak için aşağıdaki kod satırından önce sol cilt payı ' na tıklayın:

    `res.render('index', { title: 'Express', "data": getData() });`

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Web sunucusu (Google Chrome)** veya **Web sunucusu (Microsoft Edge)** gibi hata ayıklama araç çubuğundan hata ayıklama hedefini seçin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefini seçin](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefini seçin](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedefi açılır listesinden **Araştır** ' ı seçin ve varsayılan tarayıcı hedefi olarak Chrome ' u seçin ( **Varsayılan olarak ayarla**' yı seçin).

1. Uygulamayı çalıştırmak için **F5** tuşuna **basın (hata ayıklama**  >  **başlatma hata** ayıklaması).

    Hata ayıklayıcı, ayarladığınız kesme noktasında duraklatılır. Şimdi uygulamanızın durumunu inceleyebilirsiniz.

1. `getData`Bir veri ipucunda özelliklerini görmek için üzerine gelin

    ![Değişkenleri inceleme](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Devam etmek için **F5** tuşuna basın (**Hata Ayıkla**  >  **devam et**).

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde başlık olarak "Express" ve ilk paragrafta "Express 'e hoş geldiniz" görüntülenir.

1. Farklı görüntüleri göstermek için düğmelere tıklayın.

    ![Tarayıcıda çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="optional-publish-to-azure-app-service"></a>Seçim Azure App Service yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla**' yı seçin.

   ![Azure App Service’e yayımlama](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure App Service** seçin.

    **App Service** Iletişim kutusunda Azure hesabınızda oturum açabilir ve mevcut Azure aboneliklerine bağlanabilirsiniz.

1. Kalan adımları izleyerek bir abonelik seçin, bir kaynak grubu seçin veya oluşturun, bir App Service düzlemi seçin veya oluşturun ve ardından Azure 'da yayımlama istendiğinde adımları izleyin. Daha ayrıntılı yönergeler için bkz. [Web dağıtımı kullanarak Azure Web sitesinde yayımlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. **Çıkış** penceresinde, Azure 'a dağıtım ilerleme durumu gösterilir.

    Başarılı bir dağıtımda, uygulamanız Azure App Service çalıştıran bir tarayıcıda açılır. Bir görüntüyü göstermek için bir düğmeye tıklayın.

   ![Azure App Service 'de çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Tebrikler, bu öğreticiyi tamamlama!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [AngularJS Language Service uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
