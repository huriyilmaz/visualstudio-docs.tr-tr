---
title: JavaScript veya TypeScript uygulamasında hata ayıklama
description: Visual Studio, Visual Studio 'da JavaScript ve TypeScript uygulamalarında hata ayıklama desteği sağlar
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 386a489faf859038cd0f529da74a0fbac07b7250
ms.sourcegitcommit: f9f389e72787de30eb869a55ef7725a10a4011f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73636551"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Visual Studio 'da JavaScript veya TypeScript uygulamasında hata ayıklama

Visual Studio kullanarak JavaScript ve TypeScript kodunda hata ayıklaması yapabilirsiniz. Kesme noktaları ayarlayabilir ve isabet edebilir, hata ayıklayıcıyı ekleyebilir, değişkenleri inceleyebilir, çağrı yığınını görüntüleyebilir ve diğer hata ayıklama özelliklerini kullanabilirsiniz.

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleme yapın. Yaptığınız uygulama geliştirme türüne bağlı olarak, Visual Studio ile **Node. js geliştirme iş yükünü** yüklemeniz gerekebilir.

## <a name="debug-server-side-script"></a>Sunucu tarafında hata ayıklama betiği

1. Projenizi Visual Studio 'da açtığınızda, sunucu tarafı bir JavaScript dosyası (örneğin, *Server. js*) açın, bir kesme noktası ayarlamak için sol Cilt payının cilt payını tıklatın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Bir kesme noktası, Visual Studio 'Nun çalışan kodunuzu askıya alması gerektiğini gösterir; böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz.

1. Uygulamanızı çalıştırmak için **F5** tuşuna basın (**hata** ayıklama  >  hata**ayıklamayı Başlat**).

    Hata ayıklayıcı ayarladığınız kesme noktasında duraklatılır (geçerli ifade sarı olarak işaretlenir). Artık, şu anda kapsamda olan değişkenlerin üzerine giderek, **Yereller** ve **izleme** pencereleri gibi hata ayıklayıcı pencereleri kullanarak uygulamanızın durumunu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Chrome Geliştirici Araçları veya F12 araçlarını kullanmak istiyorsanız **F12**tuşuna basın. Bu araçları, DOM 'ı incelemek ve JavaScript konsolunu kullanarak uygulamayla etkileşim kurmak için kullanabilirsiniz.

## <a name="debug-client-side-script"></a>İstemci tarafı komut dosyasında hata ayıkla

::: moniker range=">=vs-2019"
Visual Studio yalnızca Chrome ve Microsoft Edge (Kmıum) için istemci tarafı hata ayıklama desteği sağlar. Bazı senaryolarda, hata ayıklayıcı JavaScript ve TypeScript kodunda ve HTML dosyalarındaki katıştırılmış betiklerdeki kesme noktalarını otomatik olarak ziyaret ediyor. ASP.NET uygulamalarında istemci tarafı komut dosyasında hata ayıklamak için, [Microsoft Edge 'de blog gönderisi hata ayıklama JavaScript](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) ve [Google Chrome için bu gönderi](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome)bölümüne bakın.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio yalnızca Chrome ve Internet Explorer için istemci tarafı hata ayıklama desteği sağlar. Bazı senaryolarda, hata ayıklayıcı JavaScript ve TypeScript kodunda ve HTML dosyalarındaki katıştırılmış betiklerdeki kesme noktalarını otomatik olarak ziyaret ediyor. ASP.NET uygulamalarında istemci tarafı komut dosyasında hata ayıklamak için [Google Chrome 'daki ASP.net projelerinin istemci tarafında hata ayıklama](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)bölümüne bakın.
::: moniker-end

ASP.NET dışındaki uygulamalar için, burada açıklanan adımları izleyin.

### <a name="prepare-your-app-for-debugging"></a>Uygulamanızı hata ayıklama için hazırlama

Kaynağınız TypeScript veya Babel gibi bir transpiler tarafından küçültülmüş veya oluşturulmuşsa, en iyi hata ayıklama deneyimi için [kaynak haritaları](#generate_source_maps) kullanılması gerekir. Kaynak eşlemeleri olmadan, hata ayıklayıcıyı çalışan bir istemci tarafı komut dosyasına ekleyebilirsiniz. Ancak, özgün kaynak dosyasında değil, yalnızca Mini olarak belirtilen veya transpiled dosyasında kesme noktaları ayarlayabilir ve bunları ziyaret edebilirsiniz. Örneğin, bir Vue. js uygulamasında, mini kullanılan betik bir `eval` bildirimine bir dize olarak geçirilir ve kaynak haritaları kullanmadığınız sürece bu kodda Visual Studio hata ayıklayıcısını kullanarak etkin bir şekilde ileretmenin bir yolu yoktur. Karmaşık hata ayıklama senaryolarında, bunun yerine Microsoft Edge için Chrome Geliştirici Araçları veya F12 araçları da kullanabilirsiniz.

Kaynak haritaları oluşturmaya yönelik yardım için bkz. [hata ayıklama için kaynak haritaları oluşturma](#generate_source_maps).

### <a name="prepare_the_browser_for_debugging"></a>Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için, IDE veya Chrome 'da **Microsoft Edge Beta** adlı Microsoft Edge (Kmıum) kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome ' ı kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri tarayıcının hata ayıklama etkinken açılmasını önleyebilir. (Tarayıcı uzantıları çalışıyor olabilir ve tam hata ayıklama modunu engelleyebilir, bu nedenle beklenmedik Chrome örneklerini bulmak için Görev Yöneticisi 'Ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için tüm Chrome örneklerini de kapatın. Her iki tarayıcı de kmıum Code tabanını kullandığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' den başlayarak, tarayıcı > başlatma sırasında `--remote-debugging-port=9222` bayrağını **hata ayıklama** araç çubuğundan ve sonra **Ekle** **' yi seçip** , sonra da **bağımsız değişkenler** alanında bayrağını ayarlayarak ayarlayabilirsiniz. Hata **ayıklamayla**hata ayıklama veya Chrome **ile kenar** gibi farklı bir kolay ad kullanın. Ayrıntılar için bkz. [sürüm notları](/visualstudio/releases/2019/release-notes-v16.2).

    ![Tarayıcınızı hata ayıklama etkinken açılacak şekilde ayarlama](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmıyor, bu nedenle boş bir tarayıcı sayfası alırsınız.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğe iliştirme

Hata ayıklayıcıyı Visual Studio 'dan iliştirmek ve istemci tarafı kodda isabet kesme noktaları eklemek için, hata ayıklayıcının doğru süreci belirlemesine yardımcı olması gerekir. Bunu etkinleştirmenin bir yolu aşağıda verilmiştir.

1. Visual Studio 'ya geçin ve kaynak kodunuzda bir JavaScript dosyası, TypeScript dosyası, *. Vue* dosyası veya JSX dosyası olabilecek bir kesme noktası ayarlayın. (Dönüş bildirimi veya var bildirimi gibi kesme noktalarına izin veren bir kod satırında kesme noktası ayarlayın.)

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Belirli kodu bir transpiled dosyasında bulmak için **Ctrl**+**F** (**düzenle** > **Bul ve Değiştir** > **hızlı bul**) kullanın.

    İstemci tarafı kod için, bir TypeScript dosyasında bir kesme noktasına isabet etmek üzere *. Vue*veya JSX dosyası genellikle [kaynak eşlemelerinin](#generate_source_maps)kullanılmasını gerektirir. Visual Studio 'da hata ayıklamayı desteklemek için bir kaynak eşlemesinin doğru şekilde yapılandırılması gerekir.

2. Visual Studio 'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl**+**F5** tuşuna**basın (hata ayıklama > ** **başlatın**).

    ::: moniker range=">=vs-2019"
    Kolay ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefi olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

3. **Işleme eklemek** >  **Hata Ayıkla** ' yı seçin.

    > [!TIP]
    > Visual Studio 2017 ' den başlayarak, bu adımları izleyerek işleme ilk kez iliştirdikten sonra, **işlem için yeniden iliştir** > **Hata Ayıkla** ' yı seçerek aynı işleme hızlıca tekrar iliştirebilirsiniz.

4. **Işleme İliştir** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, **Ekle** alanına hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge-ucmıum)** için doğru hata ayıklayıcıyı seçin, filtre kutusuna **grafik** Arama sonuçları.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de, **Ekle** alanına **WebKit Code** ' u seçin, arama sonuçlarını filtrelemek için filtre kutusuna **Chrome** yazın.
    ::: moniker-end

5. Doğru ana bilgisayar bağlantı noktasıyla (Bu örnekte localhost) tarayıcı işlemini seçin ve **Ekle**' yi seçin.

    Bağlantı noktası (örneğin, 1337) doğru tarayıcı örneğini seçmenize yardımcı olması için **başlık** alanında da görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnekte bunun Microsoft Edge (Kmıum) tarayıcısı için nasıl göründüğü gösterilmektedir.

    ![İşleme İliştir](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme İliştir](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Visual Studio 'da DOM Gezgini ve JavaScript konsolu açıldığında hata ayıklayıcının doğru şekilde eklenmiş olduğunu bilirsiniz. Bu hata ayıklama araçları, Microsoft Edge için Chrome Geliştirici Araçları ve F12 araçlarına benzerdir.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcı iliştirilemez ve "hata ayıklama bağdaştırıcısı başlatılamadı" veya "işleme iliştirilemiyor" iletisini görüyorsanız. İşlem geçerli durumda geçerli değil. ", tarayıcı hata ayıklama modunda başlatılmadan önce hedef tarayıcının tüm örneklerini kapatmak için Windows Görev Yöneticisi 'Ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modu engelleniyor olabilir.

6. Kesme noktasına sahip kod zaten yürütülmüş olabileceğinden, tarayıcı sayfanızı yenileyin. Gerekirse, kesme noktasıyla birlikte kodun yürütülmesine neden olacak şekilde işlem yapın.

    Hata ayıklayıcıda duraklalarken, değişkenlerin üzerine giderek ve hata ayıklayıcı pencerelerini kullanarak uygulamanızın durumunu inceleyebilirsiniz. Kod aracılığıyla (**F5**, **F10**ve **F11**) hata ayıklayıcıyı ilerleyebilirsiniz. Temel hata ayıklama özellikleri hakkında daha fazla bilgi için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

    Daha önce izlediğiniz adımlara, ortamınız ve tarayıcı durumunuza bağlı olarak, transpiled *. js* dosyasında ya da kaynak dosyada kesme noktasına ulaşırsınız. Her iki durumda da kodun içinde ilerleyebileceğiniz değişkenleri inceleyebilirsiniz.

   * TypeScript, JSX veya *. Vue* kaynak dosyasındaki kodu kesmeniz gerekiyorsa ve bunu yapamadığından, [sorun giderme](#troubleshooting_source_maps) bölümünde açıklandığı gibi ortamınızın doğru şekilde ayarlandığından emin olun.

   * Bir transpiled JavaScript dosyasındaki (örneğin, *App-Bundle. js*) kodu kesmeniz gerekiyorsa ve bunu yapamadığından, *dosya adı. js. map*kaynak eşleme dosyasını kaldırın.

### <a name="troubleshooting_source_maps"></a>Kesme noktaları ve kaynak haritaları sorunlarını giderme

TypeScript, JSX veya *. Vue* kaynak dosyasındaki kodu kesmeniz gerekirse ve bunu yapamaması gerekiyorsa, hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi **işlemek için İliştir** ' i kullanın. Ortamınızın doğru ayarlandığından emin olun:

* Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları da dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi kullanılarak).
      
* [Tarayıcıyı hata ayıklama modunda başlattığınızdan](#prepare_the_browser_for_debugging)emin olun.

* Kaynak eşleme dosyanızın kaynak dosyanıza doğru başvuruyu içerdiğinden ve Visual Studio hata ayıklayıcının kaynak dosyayı bulmasını önleyen *WebPack:///* gibi desteklenmeyen ön ekler içermediğinden emin olun. Örneğin, *WebPack:///.app.TSX* gibi bir başvuru, *./app5tsx*olarak düzeltilemeyebilir. Bunu kaynak eşleme dosyasında el ile veya özel bir yapı yapılandırması aracılığıyla yapabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklama için kaynak haritaları oluşturma](#generate_source_maps).

Alternatif olarak, bir kaynak dosyada (örneğin, *app. TSX*) kodu kesmeniz gerekiyorsa ve bunu yapamazsanız, kaynak dosyadaki `debugger;` ifadesini kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları (veya Microsoft Edge Için F12 araçları) kesme noktaları ayarlayın.

## <a name="generate_source_maps"></a>Hata ayıklama için kaynak haritaları oluştur

Visual Studio, JavaScript kaynak dosyalarında kaynak haritaları kullanma ve oluşturma özelliğine sahiptir. Bu genellikle, kaynağınız TypeScript veya Babel gibi bir transpiler tarafından küçültülmüş veya oluşturulduysa gereklidir. Kullanılabilir seçenekler proje türüne bağlıdır.

* Visual Studio 'da bir TypeScript projesi, varsayılan olarak sizin için kaynak eşlemeleri oluşturur. Daha fazla bilgi için bkz. [tsconfig. JSON dosyası kullanarak kaynak eşlemelerini yapılandırma](#configure_source_maps).

* Bir JavaScript projesinde, Web paketi gibi bir paketcisi ve projenize ekleyebileceğiniz TypeScript derleyicisi (veya Babel) gibi bir derleyici kullanarak kaynak haritaları oluşturabilirsiniz. TypeScript derleyicisi için Ayrıca, bir *tsconfig. JSON* dosyası eklemeniz ve `sourceMap` derleyici seçeneğini ayarlamanız gerekir. Bunun, temel bir WebPack yapılandırması kullanılarak nasıl yapılacağını gösteren bir örnek için, bkz. [tepki Ile Node. js uygulaması oluşturma](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Kaynak eşlemeleriyle karşılaşırsanız lütfen devam etmeden önce [JavaScript kaynak haritalarına giriş](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) konusunu okuyun. 

Kaynak eşlemelerinin gelişmiş ayarlarını yapılandırmak için, bir TypeScript projesinde *tsconfig. JSON* veya proje ayarlarını kullanın, ancak her ikisini birden kullanmayın.

Visual Studio kullanarak hata ayıklamayı etkinleştirmek için, oluşturulan kaynak haritadaki kaynak dosyanıza yönelik başvurunun doğru olduğundan emin olmanız gerekir (Bu işlem test gerektirebilir). Örneğin, WebPack kullanıyorsanız, kaynak eşleme dosyasındaki başvurular, Visual Studio 'Nun bir TypeScript veya JSX kaynak dosyası bulmasını önleyen *WebPack:///* önekini içerir. Özellikle, hata ayıklama amacıyla bunu Düzeltmediğiniz zaman, kaynak dosyasına ( *app. TSX*gibi) yapılan başvuru, *WebPack:///./app.TSX* gibi bir şekilde değiştirilmelidir ve hata ayıklamayı sağlayan *./app.exe.* yol, kaynak dosyanıza göredir). Aşağıdaki örnek, Visual Studio ile çalışmak için en yaygın paketleyiciler olan WebPack 'te kaynak eşlemelerini nasıl yapılandırabildiğini gösterir.

(Yalnızca WebPack) Kesme noktasını JSX dosyasında (bir transpiled JavaScript dosyası yerine) bir TypeScript olarak ayarlıyorsanız, WebPack yapılandırmanızı güncelleştirmeniz gerekir. Örneğin, *WebPack-config. js*' de, aşağıdaki kodu değiştirmeniz gerekebilir:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

Şu kodla:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Bu, Visual Studio 'da istemci tarafı kodda hata ayıklamayı etkinleştirmek için yalnızca geliştirme bir ayardır.

Karmaşık senaryolar için tarayıcı araçları (**F12**) bazen hata ayıklama için en iyi şekilde çalışır, çünkü özel öneklere değişiklik gerektirmez.

### <a name="configure_source_maps"></a>Tsconfig. JSON dosyası kullanarak kaynak eşlemelerini yapılandırma

Projenize bir *tsconfig. JSON* dosyası eklerseniz, Visual Studio Dizin kökünü bir TypeScript projesi olarak değerlendirir. Dosyayı eklemek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından **> yeni öğe > TYPESCRIPT JSON yapılandırma dosyası Ekle**' yi seçin. Aşağıdaki gibi bir *tsconfig. JSON* dosyası projenize eklenir.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Tsconfig. JSON için derleyici seçenekleri

* **ınlinesourcemap**: her kaynak dosya için ayrı bir kaynak eşlemesi oluşturmak yerine kaynak eşlemeleriyle tek bir dosya yayma.
* **ınlineso,** kaynağı tek bir dosya içindeki kaynak eşlemeleriyle birlikte yayma; *ınlinesourcemap* veya *sourcemap* 'in ayarlanmasını gerektirir.
* **MAPROOT**: hata ayıklayıcının varsayılan konum yerine kaynak eşleme ( *. map*) dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *. Map* dosyalarının *. js* dosyalarından farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı *. Map* dosyalarının konumuna yönlendirmek için kaynak eşlemesinde katıştırılır.
* **sourcemap**: karşılık gelen bir *. map* dosyası oluşturur.
* **SourceRoot**: hata ayıklayıcının kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynaklarının, tasarım zamanında konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı kaynak dosyaların bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.

Derleyici seçenekleri hakkında daha fazla bilgi için TypeScript el kitabı sayfasındaki [derleyici seçeneklerini](https://www.typescriptlang.org/docs/handbook/compiler-options.html) kontrol edin.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Proje ayarlarını kullanarak kaynak eşlemelerini yapılandırma (TypeScript Projesi)

Proje özelliklerini kullanarak kaynak eşleme ayarlarını da yapılandırabilir ve ardından Proje **> özellikler > TypeScript Build > hata ayıklaması**' ni seçebilirsiniz.

Bu proje ayarları kullanılabilir.

* **Kaynak eşlemeleri oluştur** ( *tsconfig. JSON*içinde **sourcemap** ile eşdeğer): karşılık gelen *. Map* dosyasını oluşturur.
* **Kaynak eşlemelerinin kök dizinini belirtin** ( *tsconfig. JSON*içinde **MAPROOT** ile eşdeğer): hata ayıklayıcının oluşturulan konumlar yerine eşleme dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *. Map* dosyalarının. js dosyalarından farklı bir konumda bulunması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı eşleme dosyalarının bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.
* **TypeScript dosyalarının kök dizinini belirtin** ( *tsconfig. JSON*içinde **SourceRoot** ile eşdeğerdir): hata ayıklayıcının kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynak dosyalarının tasarım zamanında konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı kaynak dosyaların bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor kullanarak dinamik dosyalardaki JavaScript hatalarını ayıklama (ASP.NET)

::: moniker range=">=vs-2019"
Visual Studio 2019 ' den itibaren, Visual Studio yalnızca Chrome ve Microsoft Edge (Kmıum) için hata ayıklama desteği sağlar.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio yalnızca Chrome ve Internet Explorer için hata ayıklama desteği sağlar.
::: moniker-end

Ancak, Razor söz dizimi (cshtml, vbhtml) ile oluşturulan dosyalarda otomatik olarak kesme noktalarına vuramaz. Bu tür dosyaların hatalarını ayıklamak için kullanabileceğiniz iki yaklaşım vardır:

* **Kesmek istediğiniz `debugger;` Ifadesini yerleştirin**: Bu, dinamik betiğin yürütmeyi durdurmasına ve Oluşturulma sırasında anında hata ayıklamayı başlatmasına neden olur.
* **Visual Studio 'da sayfayı yükleyin ve dinamik belgeyi açın**: hata ayıklama sırasında dinamik dosyayı açmanız, kesme noktasını ayarlamanız ve bu yöntemin çalışması için sayfayı yenilemeniz gerekir. Chrome veya Internet Explorer kullanıyor olmanıza bağlı olarak, aşağıdaki stratejilerden birini kullanarak dosyayı bulacaksınız:

   Chrome için, **YourPageName > Çözüm Gezgini > betik belgelerini**ziyaret edin.

    > [!NOTE]
    > Chrome kullanırken, **\<script > etiketleri arasında kullanılabilir kaynak bulunmadığını**bir ileti alabilirsiniz. Bu Tamam, hata ayıklamaya devam et.

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Kmıum) için Chrome ile aynı yordamı kullanın.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Internet Explorer için, **Windows Internet explorer > YourPageName > Çözüm Gezgini > betik belgelerine**gidin.
   ::: moniker-end

Daha fazla bilgi için bkz. [Google Chrome 'da ASP.net projelerinde istemci tarafı hata ayıklama](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
