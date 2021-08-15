---
title: JavaScript veya TypeScript uygulamasında hata ayıklama
description: Visual Studio javaScript ve TypeScript uygulamalarının hata ayıklaması için destek Visual Studio
ms.date: 11/01/2019
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 6287ccebaca054bc639f7317d1a6e3e2d9f6f8457c025682a25cddb0a043c2b7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370950"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Visual Studio'de JavaScript veya TypeScript uygulamasında hata Visual Studio

JavaScript ve TypeScript kodunda hata ayıklamak için Visual Studio. Kesme noktaları ayarp isabet, hata ayıklayıcıyı iliştirme, değişkenleri inceleme, çağrı yığınını görüntüleme ve diğer hata ayıklama özelliklerini kullanma.

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak yükleyin. Uygulama geliştirmenin türüne bağlı olarak, uygulama geliştirme iş yükünüNode.js **yüklemeniz** Visual Studio.

## <a name="debug-server-side-script"></a>Sunucu tarafı betiği hata ayıklama

1. Projeniz Visual Studio açıkken bir sunucu tarafı JavaScript dosyası açın *(server.js* gibi), kesme noktası ayarlamak için sol kenarda yer alan oluklara tıklayın:

    ![JavaScript kodunu Visual Studio kod penceresinin ekran görüntüsü. Sol oluk içinde kırmızı bir nokta, bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio değerlerine, bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz.

1. Uygulamanızı çalıştırmak için **F5** tuşuna basın (**Hata**  >  **AyıklamaYı Başlat hata ayıklama).**

    Hata ayıklayıcı, ayar istediğiniz kesme noktası sırasında duraklatılır (geçerli deyim sarı olarak işaretlenir). Artık Yerel Ayarlar ve İzleme pencereleri gibi hata ayıklayıcı pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerine gelerek **uygulama** durumunu **inceleyebilirsiniz.**

1. Uygulamaya **devam etmek için F5** tuşuna basın.

1. Chrome veya F12 Araçları'Geliştirici Araçları F12 **tuşuna basın.** DoM'ları incelemek ve JavaScript Konsolu'nu kullanarak uygulamayla etkileşim kurmak için bu araçları kullanabilirsiniz.

## <a name="debug-client-side-script"></a>İstemci tarafı betiği hata ayıklama

::: moniker range=">=vs-2019"
Visual Studio Chrome ve Microsoft Edge (Chromium) için istemci tarafı hata ayıklama desteği sağlar. Bazı senaryolarda hata ayıklayıcı, JavaScript ve TypeScript kodundaki kesme noktalarına ve HTML dosyalarındaki ekli betiklere otomatik olarak isabet eder. ASP.NET uygulamalarına istemci tarafı betiğinde hata ayıklamak için Microsoft Edge'de [JavaScript'te](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) Hata Ayıklama blog gönderisi ve Google Chrome için [bu gönderiye bakın.](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome) ASP.NET Core'da TypeScript'te hata ayıklamak için [bkz. TypeScript ile ASP.NET Core uygulama oluşturma.](tutorial-aspnet-with-typescript.md)
::: moniker-end
::: moniker range="vs-2017"
Visual Studio Chrome ve yalnızca chrome için istemci tarafı hata ayıklama Internet Explorer sağlar. Bazı senaryolarda hata ayıklayıcı, JavaScript ve TypeScript kodundaki kesme noktalarına ve HTML dosyalarındaki ekli betiklere otomatik olarak isabet eder. ASP.NET uygulamalarına istemci tarafı betiğinde hata ayıklamak için Google Chrome'da ASP.NET hata ayıklama blog [gönderisi'ne bakın.](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)
::: moniker-end

Uygulama dışında ASP.NET burada açıklanan adımları izleyin.

### <a name="prepare-your-app-for-debugging"></a>Uygulamalarınızı hata ayıklama için hazırlama

Kaynağınız TypeScript veya Babel gibi bir transpiler tarafından simge [](#generate_source_maps) durumuna geliyorsa veya oluşturulduktan sonra en iyi hata ayıklama deneyimi için kaynak eşlemelerinin kullanımı gerekir. Kaynak eşlemeleri olmadan, hata ayıklayıcıyı çalışan bir istemci tarafı betiğine iliştirebilirsiniz. Ancak, özgün kaynak dosyada değil, yalnızca küçük veya yarı yarıya inen dosyada kesme noktaları ayarp isabet ediyor olabilirsiniz. Örneğin bir Vue.js uygulamasında, en küçük betik bir deyimine dize olarak geçirilecek ve kaynak eşlemeleri kullanmadıkça bu kodda Visual Studio hata ayıklayıcısını kullanarak etkili bir şekilde adım adım `eval` atabilirsiniz. Karmaşık hata ayıklama senaryolarında, bunun yerine Chrome Geliştirici Araçları veya F12 Araçları'Microsoft Edge kullanabilirsiniz.

Kaynak eşlemeleri oluşturma yardımı için [bkz. Hata ayıklama için kaynak eşlemeleri oluşturma.](#generate_source_maps)

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a> Tarayıcıyı hata ayıklama için hazırlama

::: moniker range=">=vs-2019"
Bu senaryo için şu anda IDE Microsoft Edge de Chromium adlı **Microsoft Edge Beta** veya Chrome'u kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome kullanın.
::: moniker-end

1. Hedef tarayıcı için tüm pencereleri kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinleştirildiğinde tarayıcının açılmasını önleyebilirsiniz. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu önliyor olabilir, bu nedenle Beklenmeyen Chrome örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekir.)

   ::: moniker range=">=vs-2019"
   Daha Microsoft Edge (Chromium) için tüm Chrome örneklerini de kapatın. her iki tarayıcı da chromium kod tabanını kullanır, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinleştirildiğinde tarayıcınızı başlatabilirsiniz.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, Hata Ayıklama araç çubuğundan `--remote-debugging-port=9222` **Gözat...**  >'yi ve ardından Ekle'yi seçerek ve ardından Bağımsız  Değişkenler alanında bayrağını ayarlayarak tarayıcı başlatma sırasında bayrağını ayarlayın. Tarayıcı için Hata Ayıklama ile **Edge** veya Hata Ayıklama ile Chrome gibi **farklı bir kolay ad kullanın.** Ayrıntılar için bkz. [Sürüm Notları.](/visualstudio/releases/2019/release-notes-v16.2)

    ![Tarayıcınızı hata ayıklama etkin olarak açılacak şekilde ayarlayın](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Başlat **düğmesinden** Çalıştır Windows  açın (sağ tıklayın ve **Çalıştır'ı seçin)** ve aşağıdaki komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Başlat **düğmesinden** Çalıştır Windows **(sağ** tıklayın ve Çalıştır'ı **seçin)** ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkin olarak başlatır.

    Uygulama henüz çalışmamıştır, bu nedenle boş bir tarayıcı sayfası açılır.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklayıcıyı istemci tarafı betiğine ekleme

Hata ayıklayıcıyı istemci Visual Studio kodda kesme noktalarına isabet etmek için hata ayıklayıcının doğru işlemi tanımlamaya yardımcı olması gerekir. Bunu etkinleştirmenin bir yolu şu şekildedir.

1. Yeni Visual Studio ve kaynak kodunda bir kesme noktası ayarlayın. Bu bir JavaScript dosyası, TypeScript dosyası veya JSX dosyası olabilir. (Kesme noktası, dönüş deyimi veya var bildirimi gibi kesme noktalarına izin veren bir kod satırı olarak ayarlayın.)

    ![Visual Studio penceresinin ekran görüntüsü. Dönüş deyimi seçilir ve sol oluk içinde kırmızı bir nokta, bir kesme noktası ayar olduğunu gösterir.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Belirli bir kodu, değiştirilmiş bir dosyada bulmak için **Ctrl** F ( Bul'ı Düzenle ve +    >  **Hızlı Bul'ı**  >  **Değiştir) tuşlarını kullanın.**

    İstemci tarafı kodunda TypeScript dosyasındaki bir kesme noktası, *.vue* veya JSX dosyasına isabet etmek için genellikle kaynak [eşlemelerinin kullanımı gerekir.](#generate_source_maps) Kaynak eşlemesi, kaynak eşlemede hata ayıklamayı destekleyecek şekilde doğru Visual Studio.

2. Visual Studio'de hata ayıklama hedefi olarak hedef tarayıcınızı seçin, ardından uygulamayı tarayıcıda çalıştırmak için **Ctrl** F5 ( Hata Ayıklama Olmadan Başlat +    >  ) tuşlarına basın.

    ::: moniker range=">=vs-2019"
    Kolay bir adla bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

3. İşleme **Eklemede Hata**  >  **Ayıkla'ya seçin.**

    > [!TIP]
    > 2017'Visual Studio başlayarak, bu adımları kullanarak işleme ilk kez iliştirilme işlemini tamamlayarak, İşleme Yeniden Ekle'ye Hata Ayıkla'ya seçerek aynı işleme hızla  >  **yeniden iliştirebilirsiniz.**

4. İşleme **Ekle iletişim** kutusunda, ekleyebilirsiniz tarayıcı örneklerinin filtrelenmiş bir listesini elde edin.
    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, Hedef tarayıcınız, **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium)** için doğru hata  ayıklayıcıyı seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome veya **kenar** yazın. 
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de, Ekle alanında **Webkit** kodu'u  seçin, arama sonuçlarını filtrelemek için filtre kutusuna chrome yazın. 
    ::: moniker-end

5. Doğru konak bağlantı noktasıyla tarayıcı işlemini seçin (bu örnekte localhost) ve **Ekle'yi seçin.**

    Doğru tarayıcı örneğini seçmenize yardımcı olmak için bağlantı  noktası (örneğin, 1337) Başlık alanında da görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnek, bunun Microsoft Edge (Chromium) tarayıcısını nasıl göründüğünü gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    DOM Gezgini ve JavaScript Konsolu açık olduğunda hata ayıklayıcının doğru şekilde ekli olduğunu Visual Studio. Bu hata ayıklama araçları, chrome için Geliştirici Araçları F12 Araçları'Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcı eklenemedi ve "Hata ayıklama bağdaştırıcısı başlatılamadı" veya "İşleme eklanamadı. Bir işlem geçerli durumda yasal değildir." hata ayıklama modunda Windows tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Windows Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engel ediyor olabilir.

6. Kesme noktası olan kod zaten yürütülür durumda olduğundan tarayıcı sayfanızı yenileyin. Gerekirse, kesme noktası olan kodun yürütülse neden olacak bir eylem gerçekleştirin.

    Hata ayıklayıcıda duraklatılmış durumdayken değişkenlerin üzerine gelerek ve hata ayıklayıcı pencerelerini kullanarak uygulama durumunu inceleyebilirsiniz. Kod (**F5**, F10 ve **F11)** adım adım ilerleyerek hata ayıklayıcıyı **ilerletebilirsiniz.** Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

    Uygulama türünüz, daha önce hangi  adımları takip ettiğine ve tarayıcı durumunuz gibi diğer faktörlere bağlı olarak, kesme noktasıyla.jsdosyada veya kaynak dosyada kesme noktasıyla sonuçlayabilirsiniz. Her iki şekilde de kod adımlarını atabilir ve değişkenleri inceleyebilirsiniz.

   * Bir TypeScript, JSX veya *.vue* kaynak dosyasında koda ihtiyacınız varsa ve bunu yapamazsanız, Sorun Giderme bölümünde açıklandığı gibi ortamınız doğru şekilde ayarlanmış [olduğundan emin](#troubleshooting_source_maps) olun.

   * Koda transpiled JavaScript dosyasında (örneğin, *app-bundle.js)* kesmeniz gerekirse ve bunu yapamazsanız, *filename.js.map kaynak harita dosyasını kaldırın.*

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a> Kesme noktaları ve kaynak eşleme sorunlarını giderme

Bir TypeScript veya JSX kaynak dosyasındaki kodu kesmeniz gerekirse ve  bunu yapamazsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi İşleme Ekle'yi kullanın. Ortamınız doğru şekilde ayarlanmış olduğundan emin olun:

* Tarayıcıyı hata ayıklama modunda çalıştırmak için Chrome uzantıları dahil olmak üzere tüm tarayıcı örneklerini kapattınız (Görev Yöneticisi'ni kullanarak).
      
* Tarayıcıyı [hata ayıklama modunda başlatın.](#prepare_the_browser_for_debugging)

* Kaynak eşleme dosyanız, kaynak dosyanız için doğru göreli yolu içerir ve webpack:/// gibi desteklenmeyen ön ekler içermez ve bu da *Visual Studio* hata ayıklayıcısının bir kaynak dosyayı bulmasını önizler içerir. Örneğin, *./app.tsx* *webpack:///.app.tsx* gibi bir başvuru düzeltilmiş olabilir. Bunu kaynak eşleme dosyasında (test etmek için yararlıdır) veya özel bir derleme yapılandırması aracılığıyla el ile yapabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklama için kaynak eşlemeleri oluşturma.](#generate_source_maps)

Alternatif olarak, bir kaynak dosyada *(örneğin, app.tsx)* koda izin vermek zorundaysanız ve bunu yapamazsanız, kaynak dosyada deyimini kullanmayı deneyin veya `debugger;` Chrome Geliştirici Araçları'de (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlamayı deneyin.

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Hata ayıklama için kaynak haritaları oluştur

Visual Studio, JavaScript kaynak dosyalarında kaynak haritaları kullanma ve oluşturma özelliğine sahiptir. Bu genellikle, kaynağınız TypeScript veya Babel gibi bir transpiler tarafından küçültülmüş veya oluşturulduysa gereklidir. Kullanılabilir seçenekler proje türüne bağlıdır.

* Visual Studio bir TypeScript projesi, varsayılan olarak sizin için kaynak eşlemeleri oluşturur. Daha fazla bilgi için bkz. [dosya üzerinde tsconfig.jskullanarak kaynak eşlemelerini yapılandırma](#configure_source_maps).

* Bir JavaScript projesinde, Web paketi gibi bir paketcisi ve projenize ekleyebileceğiniz TypeScript derleyicisi (veya Babel) gibi bir derleyici kullanarak kaynak haritaları oluşturabilirsiniz. TypeScript derleyicisi için Ayrıca, dosyaya bir *tsconfig.js* eklemeniz ve `sourceMap` derleyici seçeneğini ayarlamanız gerekir. Bunun temel bir WebPack yapılandırması kullanılarak nasıl yapılacağını gösteren bir örnek için, bkz. [React Node.js uygulama oluşturma](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> kaynak eşlemeleriyle karşılaşırsanız lütfen devam etmeden önce [JavaScript kaynak Haritalar giriş](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) bölümünü okuyun. 

Kaynak eşlemelerinin gelişmiş ayarlarını yapılandırmak için bir TypeScript projesinde *tsconfig.js* veya proje ayarlarını kullanın, ancak her ikisini birden kullanmayın.

Visual Studio kullanarak hata ayıklamayı etkinleştirmek için, oluşturulan kaynak eşlemesindeki kaynak dosyanıza yönelik başvurunun doğru olduğundan emin olmanız gerekir (bu işlem test gerektirebilir). örneğin, webpack kullanıyorsanız, kaynak eşleme dosyasındaki başvurular, Visual Studio bir TypeScript veya jsx kaynak dosyası bulmasını önleyen *webpack:///* önekini içerir. Özellikle, hata ayıklama amacıyla bunu Düzeltmediğiniz zaman, kaynak dosyasına ( *app. TSX* gibi) yapılan başvuru, *WebPack:///./app.TSX* gibi bir şekilde değiştirilmelidir *.* bu, hata ayıklamayı (yol, kaynak dosyanıza görelidir) sağlar. Aşağıdaki örnek, Visual Studio ile çalışmak için en yaygın paketleyiciler olan WebPack 'te kaynak haritaları nasıl yapılandırabildiğini gösterir.

(Yalnızca WebPack) Kesme noktasını JSX dosyasında (bir transpiled JavaScript dosyası yerine) bir TypeScript olarak ayarlıyorsanız, WebPack yapılandırmanızı güncelleştirmeniz gerekir. Örneğin, *webpack-config.js*, aşağıdaki kodu değiştirmeniz gerekebilir:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

yerine şu kodu yazın:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Bu, Visual Studio istemci tarafı kodda hata ayıklamayı etkinleştirmek için yalnızca geliştirme bir ayardır.

Karmaşık senaryolar için tarayıcı araçları (**F12**) bazen hata ayıklama için en iyi şekilde çalışır, çünkü özel öneklere değişiklik gerektirmez.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a> Dosya tsconfig.jskullanarak kaynak haritaları yapılandırma

projenize bir *tsconfig.js* eklerseniz, Visual Studio dizin kökünü TypeScript projesi olarak değerlendirir. Dosyayı eklemek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından **> yeni öğe > TYPESCRIPT JSON yapılandırma dosyası Ekle**' yi seçin. Aşağıdaki gibi bir dosyadaki *tsconfig.js* projenize eklenir.

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

#### <a name="compiler-options-for-tsconfigjson"></a>tsconfig.jsiçin derleyici seçenekleri

* **ınlinesourcemap**: her kaynak dosya için ayrı bir kaynak eşlemesi oluşturmak yerine kaynak eşlemeleriyle tek bir dosya yayma.
* **ınlineso,** kaynağı tek bir dosya içindeki kaynak eşlemeleriyle birlikte yayma; *ınlinesourcemap* veya *sourcemap* 'in ayarlanmasını gerektirir.
* **MAPROOT**: hata ayıklayıcının varsayılan konum yerine kaynak eşleme (*. map*) dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *. Map* dosyalarının *.js* dosyalarından farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı *. Map* dosyalarının konumuna yönlendirmek için kaynak eşlemesinde katıştırılır.
* **sourcemap**: karşılık gelen bir *. map* dosyası oluşturur.
* **SourceRoot**: hata ayıklayıcının kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynaklarının, tasarım zamanında konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı kaynak dosyaların bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.

Derleyici seçenekleri hakkında daha fazla bilgi için TypeScript el kitabı sayfasındaki [derleyici seçeneklerini](https://www.typescriptlang.org/docs/handbook/compiler-options.html) kontrol edin.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Proje ayarlarını kullanarak kaynak eşlemelerini yapılandırma (TypeScript Projesi)

ayrıca, proje özelliklerini kullanarak kaynak eşleme ayarlarını projeye sağ tıklayıp **Project > özellikler > TypeScript Build > hata ayıklama**' ı seçerek yapılandırabilirsiniz.

Bu proje ayarları kullanılabilir.

* **Kaynak haritaları oluştur** ( *tsconfig.jsüzerinde* **sourcemap** ile eşdeğer): karşılık gelen *. Map* dosyasını oluşturur.
* **Kaynak eşlemelerinin kök dizinini belirtin** ( *tsconfig.json* **MAPROOT** ile eşdeğerdir): hata ayıklayıcının oluşturulan konumlar yerine eşleme dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *. Map* dosyalarının .js dosyalarından farklı bir konumda bulunması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı eşleme dosyalarının bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.
* **TypeScript dosyalarının kök dizinini belirtin** ( *tsconfig.jsüzerinde* **SourceRoot** ile eşdeğerdir): hata ayıklayıcının kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynak dosyalarının tasarım zamanında konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı kaynak dosyaların bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor kullanarak dinamik dosyalardaki JavaScript 'te hata ayıklama (ASP.NET)

::: moniker range=">=vs-2019"
Visual Studio 2019 ' den başlayarak Visual Studio, yalnızca Chrome ve Microsoft Edge (Chromium) için hata ayıklama desteği sağlar.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio, yalnızca Chrome ve ınternet Explorer için hata ayıklama desteği sağlar.
::: moniker-end

Ancak, Razor söz dizimi (cshtml, vbhtml) ile oluşturulan dosyalarda otomatik olarak kesme noktalarına vuramaz. Bu tür dosyaların hatalarını ayıklamak için kullanabileceğiniz iki yaklaşım vardır:

* **Kesmek istediğiniz `debugger;` ifadeyi yerleştirin**: Bu, dinamik betiğin yürütmeyi durdurmasına ve Oluşturulma sırasında anında hata ayıklamayı başlatmasına neden olur.
* **sayfayı yükleyin ve Visual Studio dinamik belgeyi açın**: hata ayıklama sırasında dinamik dosyayı açmanız, kesme noktasını ayarlamanız ve bu yöntemin çalışması için sayfayı yenilemeniz gerekir. Chrome veya Internet Explorer kullanıyor olmanıza bağlı olarak, aşağıdaki stratejilerden birini kullanarak dosyayı bulacaksınız:

   Chrome için, **YourPageName > Çözüm Gezgini > betik belgelerini** ziyaret edin.

    > [!NOTE]
    > Chrome kullanırken, **\<script> Etiketler arasında kullanılabilir kaynak olmadığını** bir ileti alabilirsiniz. Bu Tamam, hata ayıklamaya devam et.

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Chromium) için, Chrome ile aynı yordamı kullanın.
   ::: moniker-end

   ::: moniker range="vs-2017"
   ınternet explorer için **Çözüm Gezgini > betik belgelerine gidin > Windows ınternet explorer > yourpagename**.
   ::: moniker-end

daha fazla bilgi için bkz. [Google Chrome 'daki ASP.NET projelerinin istemci tarafı hata ayıklaması](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
