---
title: Bir Düğüm.js ve Express uygulaması oluşturma
description: Bu eğitimde, Visual Studio için Node.js araçlarını kullanarak bir uygulama oluşturmak
ms.date: 09/24/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 416926742da427ba7ff18c6fa07de6477361cfa3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235086"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Visual Studio'da Bir Düğüm.js ve Express uygulaması oluşturun

Node.js ve Express kullanarak Visual Studio geliştirme için bu eğitimde, basit bir Node.js web uygulaması oluşturmak, bazı kod eklemek, IDE bazı özelliklerini keşfetmek ve uygulamayı çalıştırın. 

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Bazı kod ekleme
> * Kodu yeniden kullanmak için IntelliSense'i kullanma
> * Uygulamayı çalıştırma
> * Hata ayıklamada bir kesme noktasına çarptı

## <a name="before-you-begin"></a>Başlamadan önce

Burada bazı anahtar kavramları tanıtmak için hızlı bir SSS's.

### <a name="what-is-nodejs"></a>Node.js nedir?

Node.js, JavaScript sunucu tarafını çalıştıran sunucu tarafındaki javascript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPm nedir?

npm, Node.js için varsayılan paket yöneticisidir. Paket yöneticisi, programcıların Node.js kitaplıklarının kaynak kodunu yayımlamalarını ve paylaşmalarını kolaylaştırır ve kitaplıkların yüklenmesini, güncellenmesini ve yüklenmesini kolaylaştırmak için tasarlanmıştır.

### <a name="what-is-express"></a>Ekspres nedir?

Express, Node.js için web uygulamaları oluşturmak için sunucu çerçevesi olarak kullanılan bir web uygulama çerçevesidir. Express, Pug (eski adıyla Jade) gibi bir kullanıcı arabirimi oluşturmak için farklı ön uç çerçevelerini seçmenizi sağlar. Pug bu öğretici de kullanılır.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yükünü yüklü olmalıdır.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'yi henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. **Düğüm.js geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

    ![VS Yükleyici'de Düğüm.js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Düğüm.js çalışma saatini yüklemelisiniz.

    Yüklü değilse, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için LTS sürümünü [Node.js](https://nodejs.org/en/download/) web sitesinden yüklemenizi öneririz. Node.js 32-bit ve 64-bit mimariler için inşa edilmiştir. Visual Studio'daki Düğüm.js iş yüküne dahil olan Düğüm.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca bir tanenin yüklenmesini destekler.
    
    Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındayüklü çalışma süresine başvuru yapacak şekilde yapılandırabilirsiniz (proje oluşturduktan sonra, proje düğümüne sağ tıklayın, **Özellikler'i**seçin ve **Düğüm.exe yolunu**ayarlayın). Node.js'nin genel yüklemesini kullanabilir veya Node.js projelerinizin her birinde yerel bir yorumlayıcıya giden yolu belirtebilirsiniz. 

    Bu öğretici Node.js 8.10.0 ile test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Düğüm.js projesi oluşturma

Visual Studio, *projedeki*tek bir uygulamaiçin dosyaları yönetir. Proje kaynak kodu, kaynaklar ve yapılandırma dosyalarını içerir.

Bu öğreticide, Bir Düğüm.js ve ekspres uygulama için kod içeren basit bir proje ile başlar.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Düğüm.js**yazın, ardından yeni bir Temel Azure Düğümü Express 4 uygulaması (JavaScript) **oluşturun'u** seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **JavaScript**genişletmek, sonra **Node.js**seçin. Orta bölmede, **Temel Azure Düğümü.js Express 4 uygulamasını**seçin, ardından **Tamam'ı**seçin.
    ::: moniker-end
    **Temel Azure Düğümü.js Express 4 uygulama** projesi şablonunu görmüyorsanız, Düğüm **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

    Visual Studio yeni çözümü oluşturur ve projenizi doğru bölmede açar. *App.js* proje dosyası düzenleyicide (sol bölmede) açılır.

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1) **Yeni Proje** iletişim kutusunda vermiş olduğunuz adı kullanarak projeniz **kalın** olarak vurgulanır. Dosya sisteminde, bu proje proje klasörünüzde bir *.njsproj* dosyası yla temsil edilir. Projeyle ilişkili özellikleri ve ortam değişkenlerini, projeyi sağ tıklatarak ve **Özellikler'i**seçerek ayarlayabilirsiniz. Proje dosyası Düğüm.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla yuvarlama yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projeile aynı ada sahip bir çözüm vardır. Diskteki *bir .sln* dosyasıyla temsil edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. NPM düğümlerini aramak ve bir iletişim kutusu kullanarak npm paketlerini yüklemek veya *paketleri package.json'daki* ayarları ve npm düğümündeki sağ tıklatma seçeneklerini kullanarak yüklemek ve güncellemek için npm düğümüne sağ tıklayabilirsiniz.

    (4) *package.json* yerel olarak yüklenmiş paketler için paket bağımlılıkları ve paket sürümleri yönetmek için npm tarafından kullanılan bir dosyadır. Bu dosya hakkında daha fazla bilgi için [package.json yapılandırması](../javascript/configure-packages-with-package-json.md)

    (5) *app.js* gibi proje dosyaları proje düğümü altında gösterir. *app.js* proje başlangıç dosyası dır ve bu yüzden **kalın**gösterir . Projedeki bir dosyayı sağ tıklayarak ve **Node.js başlangıç dosyası olarak**Ayarla'yı seçerek başlangıç dosyasını ayarlayabilirsiniz.

1. **npm** düğümini açın ve gerekli tüm npm paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklayıp **Eksik npm Paketlerini Yükle'yi**seçebilirsiniz.

## <a name="add-some-code"></a>Bazı kod ekleme

Uygulama ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML'ye derlenen basit biçimlendirme kodu kullanır. (Pug *app.js*görünüm motoru olarak ayarlanır. *app.js'de* görünüm altyapısını ayarlayan kod `app.set('view engine', 'pug');`.)

1. Çözüm Gezgini'nde (sağ bölme), görünümler klasörünü açın, ardından *index.pug'ı*açın.

1. İçeriği aşağıdaki biçimlendirmeyle değiştirin.

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

    Önceki kod, başlık ve karşılama iletisi içeren bir HTML sayfasını dinamik olarak oluşturmak için kullanılır. Sayfa, bir düğmeye bastığınızda değişen bir görüntüyü görüntülemek için kod da içerir.

1. Rotalar klasöründe, *açık index.js*.

1. Aramadan önce aşağıdaki kodu `router.get`ekleyin:

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

    Bu kod, dinamik olarak oluşturulan HTML sayfasına geçtiğiniz bir veri nesnesi oluşturur.

1. İşlev `router.get` çağrısını aşağıdaki kodla değiştirin:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Önceki kod, Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve başlığı ve veri nesnesini sayfaya geçirerek sayfayı işler. *Index.pug* dosyası burada *index.js* çalıştığında yüklenir sayfa olarak belirtilir. *index.js* *app.js* kodunda varsayılan rota olarak yapılandırılır (gösterilmez).

    Visual Studio'nun çeşitli özelliklerini göstermek için, kod satırında `res.render`kasıtlı bir hata vardır. Uygulamanın çalıştırılaması için hatayı düzeltmeniz gerekir ve bunu bir sonraki bölümde yaparsınız.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense kod yazarken size yardımcı olan bir Visual Studio aracıdır.

1. *Index.js'de*, içeren `res.render`kod satırına gidin.

1. `data` Dize, yazın `: get` ve IntelliSense sonra imleç koyun kodda daha önce tanımlanan `getData` işlevi gösterecektir. `getData` öğesini seçin.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Bir işlev çağrısı yapmak için parantez `getData()`ekleyin.

1. Virgülden önce`,` `"data"` ( ) kaldırın ve ifadeüzerinde yeşil sözdizimi vurgulanır bakın. Sözdizimi vurgulama üzerinde gezinmek.

    ![Sözdizimi hatasini görüntüleme](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu iletinin son satırı, JavaScript yorumlayıcısının virgül beklediğini söyler (`,`).

1. Alt bölmede **Hata Listesi** sekmesini tıklatın.

    Dosya adı ve satır numarasıyla birlikte uyarı yı ve açıklamayı görürsünüz.

    ![Hata listesini görüntüleme](../javascript/media/tutorial-nodejs-error-list.png)

1. Önce virgül (`,`) ekleyerek `"data"`kodu düzeltin.

    Düzeltildiğinde, kod satırı şu şekilde görünmelidir:`res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Bir sonraki uygulama, Visual Studio hata ayıklama ekli çalıştıracak. Bunu yapmadan önce, bir kırılma noktası ayarlamanız gerekir.

1. *Index.js'de,* bir kesme noktası ayarlamak için aşağıdaki kod satırından önce sol olukta tıklayın:

    `res.render('index', { title: 'Express', "data": getData() });`

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösterir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Microsoft Edge veya Chrome gibi Hata Ayıklama araç çubuğundaki hata ayıklama hedefini seçin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefini seçin](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefini seçin](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Chrome makinenizde mevcutsa, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedef açılır listesinden **Gözat** La'yı seçin ve varsayılan tarayıcı hedefi olarak Chrome'u seçin **(Varsayılan Olarak Ayarla'yı**seçin).

1. Uygulamayı çalıştırmak için **F5** **(Hata** > **Ayıklama Hata Ayıklama)** tuşuna basın.

    Hata ayıklama ayarladığınız kesme noktasında duraklar. Artık uygulama durumunuzu inceleyebilirsiniz.

1. Özelliklerini Bir `getData` DataTip'te görmek için üzerine gezin

    ![Değişkenleri inceleme](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Devam etmek için **F5** **(Hata Ayıklama** > **Devam**) tuşuna basın.

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde, "Express"i başlık olarak ve "Express'e Hoş Geldiniz" başlığını ilk paragrafta göreceksiniz.

1. Farklı görüntüler görüntülemek için düğmeleri tıklatın.

    ![Tarayıcıda çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="optional-publish-to-azure-app-service"></a>(İsteğe bağlı) Azure Uygulama Hizmetinde Yayımla

1. Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı**seçin.

   ![Azure App Service’e yayımlama](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure Uygulama Hizmeti'ni**seçin.

    Uygulama **Hizmeti** iletişim kutusunda, Azure hesabınızda oturum açabilir ve mevcut Azure aboneliklerine bağlanabilirsiniz.

1. Bir abonelik seçmek, bir kaynak grubu seçmek veya oluşturmak, bir uygulama hizmeti düzlemi seçmek veya oluşturmak için kalan adımları izleyin ve ardından Azure'da yayımlanması istendiğinde adımları izleyin. Daha ayrıntılı talimatlar için [bkz.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. **Çıktı** penceresi, Azure'a dağıtım konusunda kaydedilen ilerlemeyi gösterir.

    Başarılı dağıtımda uygulamanız Azure Uygulama Hizmeti'nde çalışan bir tarayıcıda açılır. Görüntüyü görüntülemek için bir düğmeyi tıklatın.

   ![Azure Uygulama Hizmeti'nde çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Bu öğretici tamamladıktan sonra tebrikler!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux Uygulama Hizmetine dağıtın](../javascript/publish-nodejs-app-azure.md)
