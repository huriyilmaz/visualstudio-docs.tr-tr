---
title: JavaScript veya TypeScript uygulamasında hata ayıklama
description: Visual Studio, Visual Studio 'da JavaScript ve TypeScript uygulamalarında hata ayıklama desteği sağlar
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 47f709ae086a32c0680fca060744898251a76afd
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589141"
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

Visual Studio yalnızca Chrome ve Internet Explorer için hata ayıklama desteği sağlar. Bazı senaryolarda, hata ayıklayıcı JavaScript ve TypeScript kodunda ve HTML dosyalarındaki katıştırılmış betiklerdeki kesme noktalarını otomatik olarak ziyaret ediyor.

Kaynağınız TypeScript veya Babel gibi bir transpiler tarafından küçültülmüş veya oluşturulmuşsa, en iyi hata ayıklama deneyimi için [kaynak haritaları](#generate_sourcemaps) kullanılması gerekir. Kaynak eşlemeleri olmadan, hata ayıklayıcıyı çalışan bir istemci tarafı komut dosyasına ekleyebilirsiniz. Ancak, özgün kaynak dosyasında değil, yalnızca Mini olarak belirtilen veya transpiled dosyasında kesme noktaları ayarlayabilir ve bunları ziyaret edebilirsiniz. Örneğin, bir Vue. js uygulamasında, mini kullanılan betik bir `eval` bildirimine bir dize olarak geçirilir ve kaynak haritaları kullanmadığınız sürece bu kodda Visual Studio hata ayıklayıcısını kullanarak etkin bir şekilde ileretmenin bir yolu yoktur. Bazı karmaşık hata ayıklama senaryolarında, Microsoft Edge için Chrome Geliştirici Araçları veya F12 araçları da kullanabilirsiniz.

Hata ayıklayıcıyı Visual Studio 'dan ve istemci tarafı kodundaki kesme noktalarına eklemek için, hata ayıklayıcının genellikle doğru işlemi belirlemesine yardımcı olması gerekir. Bu, Chrome kullanarak bunu etkinleştirmenin bir yoludur.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Chrome kullanarak hata ayıklayıcıyı istemci tarafı betiğe iliştirme

1. Tüm Chrome pencerelerini kapatın.

    Bu eylem, hata ayıklama modunda Chrome 'ı çalıştırabilmeniz için gereklidir.

2. Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayıp **Çalıştır**' ı seçin) ve şu komutu girin:

    `chrome.exe --remote-debugging-port=9222`

    Bu komut, hata ayıklama etkinken Chrome 'u başlatır.

    ::: moniker range=">=vs-2019"

    > [!NOTE]
    > Tarayıcı başlatma sırasında `--remote-debugging-port` bayrağını, **hata ayıklama** araç çubuğundan **.** .. > ve ardından **Ekle**' yi seçip, sonra da **bağımsız değişkenler** alanında bayrağını ayarlayarak da ayarlayabilirsiniz. Tarayıcı için **hata ayıklamayla birlikte**farklı bir kolay ad kullanın. Ayrıntılar için bkz. [sürüm notları](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-preview).

    ::: moniker-end

3. Visual Studio 'ya geçin ve kaynak kodunuzda bir kesme noktası ayarlayın. (Bir `return` bildirimi veya `var` bildirimi gibi kesme noktalarına izin veren kod satırında kesme noktasını ayarlayın).

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Büyük ve üretilen bir dosyada belirli bir kodu bulmanız gerekiyorsa, **Ctrl** +**F** (**düzenle**  > **Bul ve Değiştir**  > **hızlı bul**) kullanın.

4. Visual Studio 'da hata ayıklama hedefi olarak Chrome seçiliyken, uygulamayı tarayıcıda çalıştırmak için **Ctrl** +**F5** tuşuna**basın (hata ayıklama  > ** **başlatın**).

    Uygulama yeni bir tarayıcı sekmesinde açılır.

    Makinenizde Chrome varsa, ancak bir seçenek olarak görünmüyorsa, hata ayıklama hedefi açılır listesinden **Araştır** ' ı seçin ve varsayılan tarayıcı hedefi olarak Chrome ' u seçin ( **Varsayılan olarak ayarla**' yı seçin).

5. **Işleme eklemek** >  **Hata Ayıkla** ' yı seçin.

6. **Işleme İliştir** iletişim kutusunda, arama sonuçlarını filtrelemek Için, **Ekle** alanına **WebKit Code** ' u seçin, filtre kutusuna **Chrome** yazın.

    **WebKit kodu** , bir Webkit tabanlı tarayıcı olan Chrome için gereken değerdir.

7. Doğru ana bilgisayar bağlantı noktası (Bu çizimde 1337) ile Chrome işlemini seçin ve **Ekle**' yi seçin.

    ![İşleme İliştir](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    ::: moniker range="vs-2017"
    Visual Studio 'da DOM Gezgini ve JavaScript konsolu açıldığında hata ayıklayıcının doğru şekilde eklenmiş olduğunu bilirsiniz. Bu hata ayıklama araçları, Microsoft Edge için Chrome Geliştirici Araçları ve F12 araçlarına benzerdir.
    ::: moniker-end

    > [!NOTE]
    > Hata ayıklayıcı iliştirilemez ve "işleme iliştirilemiyor" iletisini görürsünüz. Bir işlem geçerli durumda geçerli değildir "hata ayıklama modunda Chrome 'u başlatmadan önce tüm Chrome örneklerini kapatmak için Görev Yöneticisi 'ni kullanın. Chrome uzantıları çalışıyor ve tam hata ayıklama modu engelleniyor olabilir.

8. Kesme noktası olan kod zaten yürütüldüğünden, kesme noktasına isabet etmek için tarayıcı sayfanızı yenileyin.

    Hata ayıklayıcıda duraklalarken, değişkenlerin üzerine giderek ve hata ayıklayıcı pencerelerini kullanarak uygulamanızın durumunu inceleyebilirsiniz. Kod aracılığıyla (**F5**, **F10**ve **F11**) hata ayıklayıcıyı ilerleyebilirsiniz.

    Mini veya transpiled JavaScript için, ortamınıza ve tarayıcı durumunuza bağlı olarak, transpiled JavaScript ya da TypeScript dosyanızdaki (kaynak haritaları kullanarak), bir JavaScript veya eşleştirilmiş konumunda kesme noktasına ulaşırsınız. Her iki durumda da kodun içinde ilerleyebileceğiniz değişkenleri inceleyebilirsiniz.

    * Bir TypeScript dosyasındaki kodu kesmeniz ve bunu yapamaması gerekiyorsa, hata ayıklayıcıyı iliştirmek için önceki adımlarda açıklandığı gibi **işlemek Için İliştir** ' i kullanın. Ardından,**dosya adı. TSX** >  **betik belgelerini** açıp bir kesme noktası ayarlayın ve tarayıcınızda sayfayı yenileyin (kesme noktasına izin veren bir kod satırında kesme noktasını ayarlayın) Çözüm Gezgini Içinden dinamik olarak oluşturulan TypeScript dosyasını açın. `return` bildirimi veya `var` bildirimi).

        Alternatif olarak, bir TypeScript dosyasındaki kodu kesmeniz ve bunu yapamazsanız, TypeScript dosyasında `debugger;` ifadesini kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları kesme noktaları ayarlayın.

    * Bir transpiled JavaScript dosyasındaki (örneğin, *App-Bundle. js*) kodu kesmeniz gerekiyorsa ve bunu yapamadığından, *dosya adı. js. map*kaynak eşleme dosyasını kaldırın.

     > [!TIP]
     > Bu adımları izleyerek işleme ilk kez iliştirdikten sonra, **hata ayıkla**  > **işleme yeniden iliştir**' i seçerek aynı işleme hızlıca tekrar iliştirebilirsiniz.

## <a name="generate_sourcemaps"></a>Hata ayıklama için kaynak haritaları oluştur

Visual Studio, JavaScript kaynak dosyalarında kaynak haritaları kullanma ve oluşturma özelliğine sahiptir. Bu genellikle, kaynağınız TypeScript veya Babel gibi bir transpiler tarafından küçültülmüş veya oluşturulduysa gereklidir. Kullanılabilir seçenekler proje türüne bağlıdır.

* Visual Studio 'da bir TypeScript projesi, varsayılan olarak sizin için kaynak eşlemeleri oluşturur.

* Bir JavaScript projesinde, Web paketi gibi bir paketcisi ve projenize ekleyebileceğiniz TypeScript derleyicisi (veya Babel) gibi bir derleyici kullanarak kaynak haritaları oluşturmanız gerekir. TypeScript derleyicisi için bir *tsconfig. JSON* dosyası da eklemeniz gerekir. Bunun, temel bir WebPack yapılandırması kullanılarak nasıl yapılacağını gösteren bir örnek için, bkz. [tepki Ile Node. js uygulaması oluşturma](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Kaynak eşlemeleriyle karşılaşırsanız lütfen devam etmeden önce [JavaScript kaynak haritalarına giriş](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) konusunu okuyun.

Kaynak eşlemelerinin gelişmiş ayarlarını yapılandırmak için, bir TypeScript projesinde *tsconfig. JSON* veya proje ayarlarını kullanın, ancak her ikisini birden kullanmayın.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Tsconfig. JSON dosyası kullanarak kaynak eşlemelerini yapılandırma

Projenize bir *tsconfig. JSON* dosyası eklerseniz, Visual Studio Dizin kökünü bir TypeScript projesi olarak değerlendirir. Dosyayı eklemek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından **> yeni öğe ekle > Web > betikleri > TYPESCRIPT JSON yapılandırma dosyası**' nı seçin. Aşağıdaki gibi bir *tsconfig. JSON* dosyası projenize eklenir.

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

### <a name="configure-source-maps-using-project-settings"></a>Proje ayarlarını kullanarak kaynak haritaları yapılandırma

Proje özelliklerini kullanarak kaynak eşleme ayarlarını da yapılandırabilir ve ardından Proje **> özellikler > TypeScript Build > hata ayıklaması**' ni seçebilirsiniz.

Bu proje ayarları kullanılabilir.

* **Kaynak eşlemeleri oluştur** ( *tsconfig. JSON*içinde **sourcemap** ile eşdeğer): karşılık gelen *. Map* dosyasını oluşturur.
* **Kaynak eşlemelerinin kök dizinini belirtin** ( *tsconfig. JSON*içinde **MAPROOT** ile eşdeğer): hata ayıklayıcının oluşturulan konumlar yerine eşleme dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *. Map* dosyalarının. js dosyalarından farklı bir konumda bulunması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı eşleme dosyalarının bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.
* **TypeScript dosyalarının kök dizinini belirtin** ( *tsconfig. JSON*içinde **SourceRoot** ile eşdeğerdir): hata ayıklayıcının kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynak dosyalarının tasarım zamanında konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklayıcıyı kaynak dosyaların bulunduğu yere yönlendirecek şekilde kaynak eşlemeye katıştırılır.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor kullanarak dinamik dosyalardaki JavaScript hatalarını ayıklama (ASP.NET)

Visual Studio yalnızca Chrome ve Internet Explorer için hata ayıklama desteği sağlar. Otomatik olarak, HTML dosyaları üzerinde JavaScript/TypeScript ve katıştırılmış betiklerine kesme noktaları ekler.

Dinamik olarak oluşturulan dosyaların hatalarını ayıklama işlemi otomatik değildir. Razor söz dizimi (cshtml, vbhtml) ile oluşturulan dosyalardaki kesme noktalarına otomatik olarak isabet edemez. Bu tür dosyaların hatalarını ayıklamak için kullanabileceğiniz iki yaklaşım vardır:

* **Kesmek istediğiniz `debugger;` Ifadesini yerleştirin**: Bu, dinamik betiğin yürütmeyi durdurmasına ve Oluşturulma sırasında anında hata ayıklamayı başlatmasına neden olur.
* **Visual Studio 'da sayfayı yükleyin ve dinamik belgeyi açın**: hata ayıklama sırasında dinamik dosyayı açmanız, kesme noktasını ayarlamanız ve bu yöntemin çalışması için sayfayı yenilemeniz gerekir. Chrome veya Internet Explorer kullanıyor olmanıza bağlı olarak, aşağıdaki stratejilerden birini kullanarak dosyayı bulacaksınız:

   Chrome için, **YourPageName > Çözüm Gezgini > betik belgelerini**ziyaret edin.

    > [!NOTE]
    > Chrome kullanırken, **\<script > etiketleri arasında kullanılabilir kaynak bulunmadığını**bir ileti alabilirsiniz. Bu Tamam, hata ayıklamaya devam et.

   Internet Explorer için, **Windows Internet explorer > YourPageName > Çözüm Gezgini > betik belgelerine**gidin.

Daha fazla bilgi için bkz. [Google Chrome 'da ASP.net projelerinde istemci tarafı hata ayıklama](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).