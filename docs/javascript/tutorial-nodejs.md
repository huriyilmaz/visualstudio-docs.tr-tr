---
title: Node. js ve Express uygulaması oluşturma
description: Bu öğreticide, Visual Studio için Node. js Araçları ' nı kullanarak bir uygulama oluşturacaksınız
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
ms.openlocfilehash: ecc14e4dc98caa17ac3849e9231ab17491f2acc8
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73428779"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Visual Studio 'da Node. js ve Express uygulaması oluşturma

Node. js ve Express kullanarak Visual Studio geliştirmesi için bu öğreticide, basit bir Node. js web uygulaması oluşturun, bazı kod ekleyin, IDE 'nin bazı özelliklerini araştırıp uygulamayı çalıştırın. 

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod ekleme
> * Kodu düzenlemek için IntelliSense kullanma
> * Uygulamayı çalıştırma
> * Hata ayıklayıcıda bir kesme noktasına isabet edin

## <a name="before-you-begin"></a>Başlamadan önce

İşte size bazı önemli kavramlara yol açmaya yönelik hızlı bir SSS.

### <a name="what-is-nodejs"></a>Node. js nedir?

Node. js, JavaScript sunucu tarafını yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

### <a name="what-is-npm"></a>NPM nedir?

NPM, Node. js için varsayılan paket yöneticisidir. Paket Yöneticisi, programcıların Node. js kitaplıklarının kaynak kodunu yayımlamasını ve paylaşmasını kolaylaştırır ve kitaplıkları yükleme, güncelleştirme ve kaldırma işlemlerini basitleştirmek üzere tasarlanmıştır.

### <a name="what-is-express"></a>Express nedir?

Express, Web uygulamaları oluşturmak için Node. js için sunucu çatısı olarak kullanılan bir Web uygulama çerçevesidir. Express, Pug (eskiden Jade olarak adlandırılır) gibi bir kullanıcı arabirimi oluşturmak için farklı ön uç çerçeveleri seçme işlevini kullanmanıza olanak sağlar. Pug Bu öğreticide kullanılır.

## <a name="prerequisites"></a>Prerequisites

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/)  page gidin ve ücretsiz olarak yüklemek için bu dosyayı açın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/)  page gidin ve ücretsiz olarak yüklemek için bu dosyayı açın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan**Araçlar ve Özellikler al** >  **Araçlar** ' a gidin. **Node. js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde Node. js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Node. js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz. Genel olarak, Visual Studio yüklü Node. js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

    Bu öğretici Node. js 8.10.0 ile test edilmiştir.

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node. js projesi oluşturma

Visual Studio, *projedeki*tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, Node. js ve Express uygulaması için kod içeren basit bir proje ile başlarsınız.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node. js**yazın ve ardından **Yeni bir temel Azure Node. js Express 4 uygulaması** (JavaScript) seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya**  > **Yeni**  > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede, **temel Azure Node. js Express 4 uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Temel Azure Node. js Express 4 uygulama** projesi şablonunu görmüyorsanız **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar. *App. js* proje dosyası düzenleyicide açılır (sol bölme).

    ![Proje yapısı](../javascript/media/tutorial-project-structure.png)

    (1), **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler**' i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz. Proje dosyası Node. js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *Package. JSON* ' daki ayarları kullanarak paketleri yükleyip güncelleyebilir ve NPM düğümündeki Seçenekler ' e sağ tıklayın.

    (4) *Package. JSON* , NPM tarafından yerel olarak yüklenen paketler için paket bağımlılıklarını ve paket sürümlerini yönetmek üzere kullanılan bir dosyadır. Bu dosya hakkında daha fazla bilgi için bkz [. Package. JSON yapılandırması](../javascript/configure-packages-with-package-json.md)

    (5) *app. js* gibi proje dosyaları proje düğümünün altında görünür. *app. js* , proje başlangıç dosyasıdır ve bu nedenle **kalın**olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node. js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

1. **NPM** düğümünü açın ve tüm gerekli NPM paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **eksik NPM paketlerini yüklemeyi**seçebilirsiniz.

## <a name="add-some-code"></a>Kod ekleme

Uygulama ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML 'ye derlenen basit biçimlendirme kodunu kullanır. (Pug, *app. js*içinde Görünüm altyapısı olarak ayarlanır. *App. js* ' de görünüm altyapısını ayarlayan kod `app.set('view engine', 'pug');`.)

1. Çözüm Gezgini (sağ bölme) menüsünde, görünümler klasörünü açın ve *index. Pug*öğesini açın.

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

1. Rotalar klasöründe *index. js*' yi açın.

1. `router.get`çağrısından önce aşağıdaki kodu ekleyin:

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

1. `router.get` işlevi çağrısını aşağıdaki kodla değiştirin:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Yukarıdaki kod, Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfayı, başlık ve veri nesnesini sayfaya geçirerek oluşturur. İndex. *Pug* dosyası, *index. js* çalıştırıldığında yüklenecek sayfa olarak belirtilir. *index. js* , *app. js* kodunda (gösterilmez) varsayılan yol olarak yapılandırılır.

    Visual Studio 'nun çeşitli özelliklerini göstermek için, `res.render`içeren kod satırında bir bilinçli hatası vardır. Uygulamanın çalıştırılabilmesi için sonraki bölümde yaptığınız hatayı çözmeniz gerekir.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense, kod yazarken size yardımcı olan bir Visual Studio aracıdır.

1. *İndex. js*' de `res.render`içeren kod satırına gidin.

1. `data` dizeden sonra imlecinizi koyun, `: get` yazın ve IntelliSense kodda daha önce tanımlanan `getData` işlevini gösterir. `getData`seçin.

    ![IntelliSense kullanma](../javascript/media/tutorial-nodejs-intellisense.png)

1. Bir işlev çağrısı yapmak için ayraçları ekleyin, `getData()`.

1. `"data"` önce virgül (`,`) kaldırın ve ifadede yeşil söz dizimi vurgulamasını görürsünüz. Söz dizimi vurgulamanın üzerine gelin.

    ![Sözdizimi görüntüleme hatası](../javascript/media/tutorial-nodejs-syntax-checking.png)

    Bu iletinin son satırı JavaScript yorumlayıcı 'nın bir virgül (`,`) beklendiğine bildirir.

1. Alt bölmede **hata listesi** sekmesine tıklayın.

    Dosya adı ve satır numarası ile birlikte uyarı ve açıklama görürsünüz.

    ![Hata listesini görüntüle](../javascript/media/tutorial-nodejs-error-list.png)

1. `"data"`önce virgül (`,`) ekleyerek kodu düzeltemedi.

    Düzeltildiğinde kod satırının şöyle görünmesi gerekir: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Uygulamayı Visual Studio hata ayıklayıcısı ekli olarak çalıştırmaya devam edersiniz. Bunu yapmadan önce bir kesme noktası ayarlamanız gerekir.

1. *İndex. js*' de, bir kesme noktası ayarlamak için aşağıdaki kod satırından önce sol cilt payı ' na tıklayın:

    `res.render('index', { title: 'Express', "data": getData() });`

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Hata ayıklama araç çubuğundaki Microsoft Edge veya Chrome gibi hata ayıklama hedefini seçin.

    ::: moniker range=">=vs-2019"
    ![Hata ayıklama hedefini seçin](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefini seçin](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedefi açılır listesinden **Araştır** ' ı seçin ve varsayılan tarayıcı hedefi olarak Chrome ' u seçin ( **Varsayılan olarak ayarla**' yı seçin).

1. Uygulamayı çalıştırmak için **F5** tuşuna**basın (hata ayıklama > ** **başlatın**).

    Hata ayıklayıcı, ayarladığınız kesme noktasında duraklatılır. Şimdi uygulamanızın durumunu inceleyebilirsiniz.

1. Bir veri Ipucunda özelliklerini görmek için `getData` üzerine gelin

    ![Değişkenleri inceleme](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Devam etmek için **F5** tuşuna basın (**Hata Ayıkla** > **devam et**).

    Uygulama bir tarayıcıda açılır.

    Tarayıcı penceresinde başlık olarak "Express" ve ilk paragrafta "Express 'e hoş geldiniz" görüntülenir.

1. Farklı görüntüleri göstermek için düğmelere tıklayın.

    ![Tarayıcıda çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="optional-publish-to-azure-app-service"></a>Seçim Azure App Service yayımlama

1. Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla**' yı seçin.

   ![Azure App Service’e yayımlama](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure App Service**seçin.

    **App Service** Iletişim kutusunda Azure hesabınızda oturum açabilir ve mevcut Azure aboneliklerine bağlanabilirsiniz.

1. Kalan adımları izleyerek bir abonelik seçin, bir kaynak grubu seçin veya oluşturun, bir App Service düzlemi seçin veya oluşturun ve ardından Azure 'da yayımlama istendiğinde adımları izleyin. Daha ayrıntılı yönergeler için bkz. [Web dağıtımı kullanarak Azure Web sitesinde yayımlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy).

1. **Çıkış** penceresinde, Azure 'a dağıtım ilerleme durumu gösterilir.

    Başarılı bir dağıtımda, uygulamanız Azure App Service çalıştıran bir tarayıcıda açılır. Bir görüntüyü göstermek için bir düğmeye tıklayın.

   ![Azure App Service 'de çalışan uygulama](../javascript/media/tutorial-nodejs-running-in-azure.png)

Tebrikler, bu öğreticiyi tamamlama!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)
