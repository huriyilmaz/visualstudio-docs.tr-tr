---
title: Node.js ve Express uygulaması oluşturma
description: Bu öğreticide, Visual Studio Hızlı Web uygulaması çerçevesini kullanarak basit bir Node.js uygulaması oluşturmayı öğrenin.
ms.date: 09/14/2021
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
ms.openlocfilehash: 0dbd5b8cd41e3839c7b3c34521bc537b12b5143b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430464"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Öğretici: Visual Studio Node.js ve Express uygulaması oluşturma

Visual Studio geliştirmeye yönelik bu öğretici Node.js ve Express kullanır. Bu öğreticide, basit bir Node.js Web uygulaması oluşturur, bazı kodlar ekler, IDE 'nin bazı özelliklerini keşfedebilir ve uygulamayı çalıştırırsınız. 

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod ekleme
> * Kodu düzenlemek için IntelliSense kullanma
> * Uygulamayı çalıştırma
> * Hata ayıklayıcıda bir kesme noktasına isabet edin

Başlamadan önce, size bazı önemli kavramları tanıtmak için hızlı bir SSS aşağıda verilmiştir:

- **Node.js nedir?**
  
  Node.js, JavaScript kodunu yürüten sunucu tarafı bir JavaScript çalışma zamanı ortamıdır.

- **NPM nedir?**
  
  Paket Yöneticisi Node.js kaynak kodu kitaplıklarını yayımlamayı ve paylaşmayı kolaylaştırır. Node.js için varsayılan paket yöneticisi NPM 'dir. NPM Paket Yöneticisi kitaplık yükleme, güncelleştirme ve kaldırma işlemlerini basitleştirir.

- **Express nedir?**
  
  Express, Node.js Web uygulamaları oluşturmak için kullanılan bir sunucu Web uygulaması çerçevesidir. Express ile, bir kullanıcı arabirimi oluşturmak için farklı ön uç çerçeveleri kullanabilirsiniz. Bu öğretici, ön uç çerçevesi için daha önce Jade adlı Pug 'yi kullanır.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici aşağıdaki önkoşulları gerektirir:

- Node.js geliştirme iş yükü yüklü Visual Studio.
  
  Henüz Visual Studio yüklemediyseniz:
  
  1. Visual Studio ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.
     
  1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve ardından **yükler**' i seçin.
     
     ![Visual Studio Yükleyicisi seçili düğüm j iş yükünü gösteren ekran görüntüsü.](media/quickstart-nodejs-workload.png)
  
  zaten yüklüyse Visual Studio:
  
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
Bu öğretici Node.js 8.10.0 ile test edilmiştir.
::: moniker-end

## <a name="create-a-new-nodejs-project"></a>Yeni bir Node.js projesi oluştur

Visual Studio *projedeki* tek bir uygulama için dosyaları yönetir. Proje kaynak kodu, kaynakları ve yapılandırma dosyalarını içerir.

Bu öğreticide, Node.js ve Express uygulaması için kod içeren basit bir proje ile başlarsınız.

::: moniker range=">=vs-2022"
1. Visual Studio açın ve başlangıç penceresini kapatmak için **Esc** tuşuna basın.
   
1. **CTRL** + **Q** tuşlarına basın, arama kutusuna *node.js* yazın ve ardından açılan listeden **temel Azure Node.js Express 4 uygulaması-JavaScript** ' i seçin.
   
   **Temel Azure Node.js Express 4 uygulama** seçeneğini görmüyorsanız, Node.js geliştirme iş yükünü yüklemeniz gerekir. Yönergeler için bkz. [Önkoşullar](#prerequisites).
   
1. **Yeni projenizi yapılandırın** Iletişim kutusunda **Oluştur**' u seçin.
   
   Visual Studio yeni çözüm ve projeyi oluşturur ve sağ bölmede projeyi açar. *app.js* proje dosyası sol bölmedeki düzenleyicide açılır.
   
1. Sağ bölmedeki **Çözüm Gezgini** içindeki proje yapısına bakın.
   
   ![Çözüm Gezgini içinde proje yapısını gösteren ekran görüntüsü.](media/vs-2022/tutorial-project-structure.png)
   
   - En üst düzey, varsayılan olarak projenizle aynı ada sahip olan *çözümdür* (**1**). Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.
   
   - Projeniz (**2**) **yeni projenizi Yapılandır** iletişim kutusunda verdiğiniz adı kullanarak kalın renkle vurgulanır. Dosya sisteminde proje, proje klasörünüzdeki bir *. njsproj* dosyasıdır.
     
     Projeye sağ tıklayıp bağlam menüsünden **Özellikler** ' i seçerek proje özelliklerini ve ortam değişkenlerini görüntüleyebilir ve ayarlayabilirsiniz. Diğer geliştirme araçlarıyla çalışabilirsiniz çünkü proje dosyası Node.js proje kaynağında özel değişiklikler yapmaz.
   
   - **NPM** düğümü (**3**) yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilirsiniz.
     
     Paketleri *Package. JSON* ' daki ayarları ve **NPM** düğümündeki sağ tıklama seçeneklerini kullanarak yükleyebilir ve güncelleştirebilirsiniz.
   
   - Project dosyaları (**4**) proje düğümünün altında görünür. Proje başlangıç dosyası **app.js**, kalın olarak gösterilir.
     
     Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

   - NPM, yerel olarak yüklenmiş paketlerin bağımlılıklarını ve sürümlerini yönetmek için **Package. JSON** dosyasını (**5**) kullanır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](npm-package-management.md).
   
1. Tüm gerekli NPM paketlerinin mevcut olduğundan emin olmak için **NPM** düğümünü açın.
   
   Herhangi bir paket **(eksik)** olarak görünür, **NPM** düğümüne sağ tıklayın, **NPM paketlerini yüklensin**' i seçin ve eksik paketleri yükler.
:::moniker-end
:::moniker range="vs-2019"
1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve ardından **Yeni temel Azure Node.js Express 4 uygulaması oluştur** (JavaScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    
    **Temel Azure Node.js Express 4 uygulama** projesi şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni çözümü oluşturur ve projenizi sağ bölmede açar. *app.js* proje dosyası düzenleyicide açılır (sol bölme).

    ![Çözüm Gezgini içinde proje yapısını gösteren ekran görüntüsü.](../javascript/media/tutorial-project-structure.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde **kalın** olarak vurgulanır. Dosya sisteminde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir. Projeye sağ tıklayıp **Özellikler**' i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini ayarlayabilirsiniz. Proje dosyası Node.js proje kaynağında özel değişiklikler yapmadığından, diğer geliştirme araçlarıyla gidiş dönüşü yapabilirsiniz.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilir veya *Package. JSON* ' daki ayarları kullanarak paketleri yükleyip güncelleyebilir ve NPM düğümündeki Seçenekler ' e sağ tıklayın.

    (4) *Package. JSON* , NPM tarafından, yerel olarak yüklenen paketlere yönelik paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için bkz. [NPM paketlerini yönetme](../javascript/npm-package-management.md).

    (5) *app.js* gibi Project dosyalar proje düğümünün altında görünür. *app.js* , proje başlangıç dosyasıdır ve bu nedenle **kalın** olarak görünür. Başlangıç dosyasını projedeki bir dosyaya sağ tıklayıp **Node.js başlangıç dosyası olarak ayarla**' yı seçerek ayarlayabilirsiniz.

1. **NPM** düğümünü açın ve tüm gerekli NPM paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **NPM paketlerini yükleyebilirsiniz**' i seçebilirsiniz.
:::moniker-end
:::moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni uygulama iletişim kutusunun sol **bölmesinde JavaScript Project** genişletin ve ardından Yeni'yi **Node.js.**  Orta bölmede Temel Azure Node.js **Express 4 uygulaması'Node.js tamam'ı** **seçin.**
    
    Temel Azure Node.js **Express 4 uygulama projesi** şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **gerekir.** Yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio çözümü oluşturur ve projenizi sağ bölmede açar. app.js proje dosyası düzenleyicide (sol bölme) açılır.

    ![Çözüm Gezgini'da proje yapısını gösteren ekran görüntüsü.](../javascript/media/tutorial-project-structure.png)

    (1) New  Project iletişim kutusunda verdiği ad kullanılarak projeniz **kalın Project** vurgulanır. Dosya sisteminde, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi. Projeye sağ tıklar ve Özellikler'i seçerek projeyle ilişkili özellikleri ve ortam değişkenlerini **ayarlayın.** Proje dosyası proje kaynağında özel değişiklikler yapmay olduğundan, diğer geliştirme araçlarıyla Node.js yapabilirsiniz.

    (2) En üst düzeyde varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

    (3) npm düğümü yüklü npm paketlerini gösterir. npm paketlerini bir iletişim kutusu kullanarak aramak ve yüklemek için npm düğümüne sağ tıklar veya *package.json'daki* ayarları kullanarak paketleri yükleyebilir ve güncelleştirin ve npm düğümünde sağ tıklayın.

    (4) *package.json,* npm tarafından yerel olarak yüklenmiş paketlerin paket bağımlılıklarını ve paket sürümlerini yönetmek için kullanılan bir dosyadır. Daha fazla bilgi için [bkz. Npm paketlerini yönetme.](../javascript/npm-package-management.md)

    (5) Project *gibi* app.jsproje düğümü altında gösterir. *app.js* proje başlangıç dosyasıdır ve bu nedenle kalın olarak **gösterilir.** Proje içinde bir dosyaya sağ tıklar ve Başlangıç dosyası olarak ayarla'Node.js **başlangıç dosyasını ayarlayın.**

1. **npm düğümünü** açın ve tüm gerekli npm paketlerinin mevcut olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklar ve Npm Paketlerini **Yükle'yi seçebilirsiniz.**
    ::: moniker-end

## <a name="add-some-code"></a>Kod ekleme

Uygulama, ön uç JavaScript çerçevesi için Pug kullanır. Pug, HTML'ye derlenmiş basit işaretleme kodunu kullanır.

Pug, koduyla birlikteapp.js *görünümü* altyapısı olarak `app.set('view engine', 'pug');` ayarlanır.

1. Dosya **Çözüm Gezgini** görünümler **klasörünü** açın ve **index.pug'yi seçerek** dosyayı açın.

1. Dosya içeriğini aşağıdaki işaretlemeyle değiştirin.

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
      a: img(id='myImage' height='300' width='300' src='')
    ```

    Yukarıdaki kod dinamik olarak bir başlık ve karşılama iletisine sahip bir HTML sayfası oluşturur. Sayfa, bir düğmeye her bastığınızda değişir bir görüntü görüntülemek için kod da içerir.

1. **routes klasöründe** **index.js.**

1. İşlev çağrısının önceye aşağıdaki `router.get` kodu ekleyin:

    ```js
    var getData = function () {
        var data = {
            'item1': 'https://images.unsplash.com/photo-1563422156298-c778a278f9a5',
            'item2': 'https://images.unsplash.com/photo-1620173834206-c029bf322dba',
            'item3': 'https://images.unsplash.com/photo-1602491673980-73aa38de027a'
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

    Yukarıdaki kod, Express yönlendirici nesnesini kullanarak geçerli sayfayı ayarlar ve sayfayı işler ve başlığı ve veri nesnesini sayfaya iletir. Kod, *dizin.pug dosyasını,* bir dosya çalıştırılana kadar yük *index.js* belirtir. Burada *app.js* kod, varsayılan yolindex.js *olarak* yapılandırılan koddur.

    Birçok farklı Visual Studio göstermek için, içeren kod satırda kasıtlı bir hata `res.render` vardır. Sonraki bölümde IntelliSense, uygulamanın çalışması için hatayı düzeltmeye yardımcı olur.

## <a name="use-intellisense"></a>IntelliSense kullanma

IntelliSense, Visual Studio yardımcı olan bir araçtır.

1. index.js düzenleyicisinde Visual Studio içinde yer alan kod satırına `res.render` gidin.

1. İmlecinizi dizenin `"data"` altına yerleştirerek `: get` yazın. IntelliSense, `getData` daha önce kodda tanımlandığı işlevi görüntüler. `getData` öğesini seçin.

    ::: moniker range=">=vs-2022"
    ![IntelliSense kullanmayı gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-intellisense.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![IntelliSense kullanmayı gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-intellisense.png)
    ::: moniker-end

1. Kodu bir işlev çağrısı yapmak için parantez ekleyin: `getData()` .

1. öncesinde virgülleri `"data"` kaldırın. İfadede yeşil söz dizimi vurgulaması görüntülenir. Söz dizimi vurgulamanın üzerine gelin.

    ::: moniker range=">=vs-2022"
    ![IntelliSense'te söz dizimi hatasını gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-syntax-checking.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![IntelliSense'te söz dizimi hatasını gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-syntax-checking.png)
    ::: moniker-end

    İletinin son satırı, JavaScript yorumlayıcının bir virgül beklendiğini size söyler.

1. Alt bölmede Hata Listesi **sekmesini** seçin ve bildirilen sorunların türü için açılan listeden Derleme **+ IntelliSense'i** seçin.

    Bölmede dosya adı ve satır numarasıyla birlikte uyarı ve açıklama görüntülenir.

    ::: moniker range=">=vs-2022"
    ![Hatanın listelenmiş olduğu Hata Listesi bölmesini gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-error-list.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Hatanın listelenmiş olduğu Hata Listesi bölmesini gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-error-list.png)
    ::: moniker-end

1. öncesini virgülle değiştirerek kodu `"data"` düzeltin.

    Düzeltilmiş kod satırı şu şekilde olmalı: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="run-the-app"></a>Uygulamayı çalıştırma

Ardından, uygulamanın hata ayıklayıcısı eklenmiş Visual Studio çalıştırın. Bunu yapmadan önce bir kesme noktası ayarlay gerekir.

### <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, çalışan Visual Studio askıya alınması gereken yeri gösterir. Ardından değişken değerlerini, bellek davranışını veya bir kod dallarının çalıştırıp çalışmamalarını gözlemlersiniz.

- Kesme noktası ayarlamak için, *index.js* içinde, aşağıdaki kod satırı öncesinde sol olukluna tıklayın:

  `res.render('index', { title: 'Express', "data": getData() });`

  ::: moniker range=">=vs-2022"
  ![Kesme noktası ayarlamayı gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-set-breakpoint.png)
  ::: moniker-end
  ::: moniker range="<=vs-2019"
  ![Kesme noktası ayarlamayı gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-set-breakpoint.png)
  ::: moniker-end

### <a name="run-the-app-in-debug-mode"></a>Uygulamayı Hata Ayıklama modunda çalıştırma

1. Hata ayıklama araç çubuğunda  Web Sunucusu **(Google Chrome)** veya Web Sunucusu (Microsoft Edge) **gibi hata ayıklama hedefini seçin.**

    ::: moniker range=">=vs-2022"
    ![Hata ayıklama hedefini seçmeyi gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2019"
    ![Hata ayıklama hedefini seçmeyi gösteren ekran görüntüsü.](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Hata ayıklama hedefini seçmeyi gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Tercih ettiğiniz hata ayıklama hedefinin makinede kullanılabilir olduğunu biliyorsanız ancak bir  seçenek olarak görünmüyorsa, hata ayıklama hedefi açılan listesinden Birlikte Gözat'ı seçin. Listeden varsayılan tarayıcı hedefini seçin ve Varsayılan olarak **Ayarla'ya tıklayın.**

1. Uygulamayı **çalıştırmak için F5** **tuşuna basın veya** Hata  >  **AyıklamaYı Başlat'ı** seçin.

    Hata ayıklayıcı, ayar istediğiniz kesme noktası üzerinden duraklatılır, böylece uygulama durumunu incelersiniz.

1. `getData`DataTip'te özelliklerini görmek için üzerine gelin:

    ::: moniker range=">=vs-2022"
    [![Hata ayıklama sırasında değişkenleri incelemeyi gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-inspect-variables.png)](media/vs-2022/tutorial-nodejs-inspect-variables.png#lightbox)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Hata ayıklama sırasında değişkenleri incelemeyi gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-inspect-variables.png)
    ::: moniker-end

1. Uygulamayı **çalıştırmaya devam etmek** için F5 **tuşuna** basın veya  >  **Devam'da** Hata Ayıkla'ya basın.

    Uygulama bir tarayıcıda açılır. Tarayıcı penceresinde başlık olarak **Express** ve ilk paragraf olarak **Express'e Hoş Geldiniz'i** görüyor olun.

1. One! , **Two!** ve **Three!** düğmeleriyle görüntüleniyor.

    ![Tarayıcıda çalışan uygulamayı gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Web tarayıcısını kapatın.

## <a name="publish-to-azure-app-service-optional"></a>Yayımlama Azure App Service (isteğe bağlı)

::: moniker range=">=vs-2022"
1. **Çözüm Gezgini**'nde projeye sağ tıklayın ve **Yayımla**'yı seçin. 
   
   - İstendiğinde Yayımlama profili **ekle'yi seçin.**
   - Azure Webjob Tools'ı yüklemeniz istenirse Yükle'yi **seçin.**
   
1. İlk Yayımla **ekranında** **Azure'ı ve** ardından Sonraki'yi **seçin.**
   
   ![Azure'ın seçili olduğu Yayımla iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-publish-azure.png)
   
   
1. İkinci Yayımla **ekranında** Azure App Service **(Windows) seçeneğini ve** ardından Sonraki'yi **seçin.**
   
   ![Azure App Service seçeneğinin seçili olduğu Yayımla iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-publish-azure-app.png)
   
1. Sonraki ekranda gerekirse Azure'da oturum açma. Yayımlamak istediğiniz Azure aboneliğini, App Service grubunu ve ardından Son'a **tıklayın.**

   - Azure aboneliğiniz, kaynak grubunuz veya App Service, bu ekranda yer alan istemleri takip edin.
   
   ![Azure web uygulamasının seçili olduğu Yayımla iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-publish-web-app.png)
   
   Daha ayrıntılı yönergeler için bkz. [Web dağıtımı kullanarak Azure web sitesinde yayımlama.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)
   
1. Yayımlama yapılandırmasına göz atarak Yayımla'yı **seçin.**

   ![Visual Studio'da Yapılandırmayı yayımla düğmesini gösteren ekran görüntüsü.](media/vs-2022/tutorial-nodejs-publish-ready.png)
   
   İlk Visual Studio **penceresinde** Azure dağıtımının ilerleme durumu gösterilir.
   
1. Başarılı bir dağıtımda, uygulamanız tarayıcıda Azure App Service açılır. Görüntü görüntülemek için bir düğme seçin.
   
   ![Tarayıcıda çalışan web uygulamasını Azure App Service ekran görüntüsü.](media/vs-2022/tutorial-nodejs-running-in-azure.png)

::: moniker-end
::: moniker range="<=vs-2019"
1. Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin.**

   ![Azure App Service'da yayımla'yı gösteren ekran görüntüsü.](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. **Microsoft Azure App Service.**

    App Service **iletişim** kutusunda Azure hesabınızla oturum açabilirsiniz ve mevcut Azure aboneliklerine bağlanabilirsiniz.

1. Abonelik seçmek, kaynak grubu seçmek veya oluşturmak, app service planı seçmek veya oluşturmak için kalan adımları izleyin ve ardından Azure'da yayımlamanız istendiğinde adımları izleyin. Daha ayrıntılı yönergeler için bkz. [Web dağıtımı kullanarak Azure web sitesinde yayımlama.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. Çıktı **penceresi,** Azure'a dağıtım ilerlemesini gösterir.

    Başarılı bir dağıtımda, uygulamanız Azure App Service. Bir görüntüyü görüntülemek için bir düğmeye tıklayın.

   ![Tarayıcıda çalışan web uygulamasını Azure App Service ekran görüntüsü.](../javascript/media/tutorial-nodejs-running-in-azure.png)
::: moniker-end
Tebrikler, bu öğreticiyi tamamladıktan sonra!

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [AngularJS dil hizmeti uzantısı](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
