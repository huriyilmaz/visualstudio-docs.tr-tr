---
title: JavaScript veya TypeScript uygulamasını hata ayıklama
description: Visual Studio, Visual Studio'da JavaScript ve TypeScript uygulamalarının hata ayıklanması için destek sağlar
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
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678980"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Visual Studio'da bir JavaScript veya TypeScript uygulamasını hata ayıklama

Visual Studio'yu kullanarak JavaScript ve TypeScript kodunu hata ayıklayabilirsiniz. Kesme noktalarını ayarlayabilir ve vurabilirsiniz, hata ayıklama ekleyebilir, değişkenleri inceleyebilir, arama yığınını görüntüleyebilir ve diğer hata ayıklama özelliklerini kullanabilirsiniz.

> [!TIP]
> Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin. Yaptığınız uygulama geliştirme türüne bağlı olarak, Visual Studio ile **Düğüm.js geliştirme iş yükünü** yüklemeniz gerekebilir.

## <a name="debug-server-side-script"></a>Hata ayıklama sunucu tarafı komut dosyası

1. Projeniz Visual Studio'da açıkken, sunucu tarafındaki javascript dosyasını açın *(server.js*gibi), bir kırılma noktası ayarlamak için sol oluktaki olukta tıklayın:

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    Kesme noktaları, güvenilir hata ayıklamanın en temel ve temel özelliğidir. Kesme noktası, Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösterir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz.

1. Uygulamanızı çalıştırmak için **F5** **(Hata** > **Ayıklama Hata Ayıklama)** tuşuna basın.

    Hata ayıklama ayarladığınız kesme noktasında duraklar (geçerli deyim sarı yla işaretlenir). Artık, **Yerel Halk** ve **İzle** pencereleri gibi hata ayıklama pencerelerini kullanarak, şu anda kapsamda olan değişkenlerin üzerinde gezinerek uygulama durumunuzu inceleyebilirsiniz.

1. Uygulamaya devam etmek için **F5** tuşuna basın.

1. Chrome Geliştirici Araçlarını veya F12 Araçlarını kullanmak istiyorsanız **F12**tuşuna basın. Bu araçları, JAVAScript Konsolu'nu kullanarak DOM'u incelemek ve uygulamayla etkileşimde kalmak için kullanabilirsiniz.

## <a name="debug-client-side-script"></a>Hata ayıklama istemci tarafı komut dosyası

::: moniker range=">=vs-2019"
Visual Studio yalnızca Chrome ve Microsoft Edge (Krom) için istemci tarafı hata ayıklama desteği sağlar. Bazı senaryolarda hata ayıklayıcı, JavaScript ve TypeScript kodunda ve HTML dosyalarındaki gömülü komut dosyalarında kesme noktalarına otomatik olarak vurur. ASP.NET uygulamalarında istemci tarafı komut dosyası hata ayıklama için, [Microsoft Edge'deki Hata Ayıklama JavaScript](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) blog yazısına ve Google Chrome için bu [gönderiye](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome)bakın. TypeScript'i ASP.NET Core'da hata ayıklama için [typescript ile ASP.NET Core uygulaması oluşturma bölümüne](tutorial-aspnet-with-typescript.md)bakın.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio yalnızca Chrome ve Internet Explorer için istemci tarafı hata ayıklama desteği sağlar. Bazı senaryolarda hata ayıklayıcı, JavaScript ve TypeScript kodunda ve HTML dosyalarındaki gömülü komut dosyalarında kesme noktalarına otomatik olarak vurur. ASP.NET uygulamalarında istemci tarafı komut dosyası hata ayıklama için, [Google Chrome'daki ASP.NET projelerinin](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)istemci tarafı hata ayıklama blog yazısına bakın.
::: moniker-end

ASP.NET dışındaki uygulamalar için burada açıklanan adımları izleyin.

### <a name="prepare-your-app-for-debugging"></a>Uygulamanızı hata ayıklama için hazırlayın

Kaynağınız Minified veya TypeScript veya Babel gibi bir transpiler tarafından oluşturulan ise, [kaynak haritalarının](#generate_source_maps) kullanımı en iyi hata ayıklama deneyimi için gereklidir. Kaynak eşlemler olmadan, hata ayıklamayı çalışan istemci tarafındaki bir komut dosyasına eklemeye devam edebilirsiniz. Ancak, yalnızca orijinal kaynak dosyasında değil, mayınlı veya transpilleştirilmiş dosyada kesme noktalarını ayarlayabilir ve vurabilirsiniz. Örneğin, bir Vue.js uygulamasında, minified script bir `eval` deyim için bir dize olarak geçirilir ve kaynak haritalar kullanmadığınız sürece Visual Studio hata ayıklayıcıkullanarak bu kodu etkili bir şekilde geçmek için bir yol yoktur. Karmaşık hata ayıklama senaryolarında, Bunun yerine Microsoft Edge için Chrome Geliştirici Araçları veya F12 Araçları da kullanabilirsiniz.

Kaynak eşlemleri oluşturmak için yardım için [bkz.](#generate_source_maps)

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Tarayıcıyı hata ayıklama için hazırlayın

::: moniker range=">=vs-2019"
Bu senaryo için, şu anda IDE'de **Microsoft Edge Beta** veya Chrome olarak adlandırılan Microsoft Edge (Krom) kullanın.
::: moniker-end
::: moniker range="vs-2017"
Bu senaryo için Chrome'u kullanın.
::: moniker-end

1. Hedef tarayıcının tüm pencerelerini kapatın.

   Diğer tarayıcı örnekleri, hata ayıklama etkinken tarayıcının açılmasını engelleyebilir. (Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engelliyor olabilir, bu nedenle Chrome'un beklenmeyen örneklerini bulmak için Görev Yöneticisi'ni açmanız gerekebilir.)

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Chromium) için, Chrome'un tüm örneklerini de kapatın. Her iki tarayıcı da krom kodu tabanını kullandığından, bu en iyi sonuçları verir.
   ::: moniker-end

2. Hata ayıklama etkinken tarayıcınızı başlatın.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'dan başlayarak, `--remote-debugging-port=9222` Hata **Ayıklama** araç çubuğundan > **Gözat'ı** seçerek tarayıcı lansmanında bayrağı ayarlayabilir, ardından **Ekle'yi**seçerek ve **ardından Bağımsızlar** alanında bayrağı ayarlayabilirsiniz. **Hata Ayıklama ile Edge** veya Hata **Ayıklama ile Chrome**gibi tarayıcı için farklı bir dostu ad kullanın. Ayrıntılar [için, Yayın Notları'na](/visualstudio/releases/2019/release-notes-v16.2)bakın.

    ![Hata ayıklama etkinken tarayıcınızı açacak şekilde ayarlayın](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    Alternatif olarak, Windows **Başlat** düğmesinden **Çalıştır** komutunu açın (sağ tıklayın ve **Çalıştır'ı**seçin ) ve aşağıdaki komutu girin:

    `msedge --remote-debugging-port=9222`

    Veya

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Windows **Start** düğmesinden **Çalıştır** komutunu açın (sağ tıklayın ve **Çalıştır'ı**seçin ) ve aşağıdaki komutu girin:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Bu, tarayıcınızı hata ayıklama etkinken başlatır.

    Uygulama henüz çalışmıyor, bu nedenle boş bir tarayıcı sayfası elde elabilirsiniz.

### <a name="attach-the-debugger-to-client-side-script"></a>Hata ayıklamayı istemci tarafındaki komut dosyasına ekleme

Görsel Studio'dan hata ayıklayıcıyı eklemek ve istemci tarafındaki koda kesme noktaları vurmak için hata ayıklayıcının doğru işlemi belirlemek için yardıma ihtiyacı vardır. Bunu etkinleştirmenin bir yolu da budur.

1. Visual Studio'ya geçin ve ardından kaynak kodunuzda JavaScript dosyası, TypeScript dosyası veya JSX dosyası olabilecek bir kesme noktası ayarlayın. (Kesme noktasını, iade bildirimi veya var bildirimi gibi kesme noktalarına izin veren bir kod satırında ayarlayın.)

    ![Kesme noktası ayarlama](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Aktarılan bir dosyadaki belirli kodu bulmak için **Ctrl**+**F** **(Hızlı** > **Bul'u Bul ve Değiştir** > **Quick Find**) kullanın.

    İstemci tarafı kodu için, TypeScript dosyasında bir kesme noktasına çarpmak için, *.vue*veya JSX dosyası genellikle [kaynak haritaların](#generate_source_maps)kullanılmasını gerektirir. Bir kaynak eşlemi Visual Studio'da hata ayıklamayı destekleyecek şekilde doğru şekilde yapılandırılmalıdır.

2. Visual Studio'da hata ayıklama hedefi olarak hedef tarayıcınızı seçin ve uygulamayı tarayıcıda çalıştırmak için **Ctrl**+**F5** 'e **(Hata Ayıklama** > Olmadan**Hata Ayıklama)** basın.

    ::: moniker range=">=vs-2019"
    Uygun bir ada sahip bir tarayıcı yapılandırması oluşturduysanız, hata ayıklama hedefiniz olarak bunu seçin.
    ::: moniker-end

    Uygulama yeni bir tarayıcı sekmesinde açılır.

3. İşleme **Hata Ayıklama** > **Ekle'yi**seçin.

    > [!TIP]
    > Visual Studio 2017'den başlayarak, bu adımları izleyerek işleme ilk kez bağlandığınızda, İşleme Hata**Ayıklama'yı** **Debug** > seçerek aynı işleme hızlı bir şekilde yeniden bağlanabilirsiniz.

4. **İşleme Ekle** iletişim kutusunda, ekleyebileceğiniz tarayıcı örneklerinin filtrelenmiş bir listesini alın.
    ::: moniker range=">=vs-2019"
    Visual Studio 2019'da, arama sonuçlarını filtrelemek için filtre kutusuna **ekle** alanında hedef tarayıcınız **JavaScript (Chrome)** **chrome** veya **edge** **JavaScript (Microsoft Edge - Chromium)** için doğru hata ayıklayıcıyı seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de, Alana **Ekle'de** **Webkit kodunu** seçin, arama sonuçlarına filtre lemek için filtre kutusuna **krom** yazın.
    ::: moniker-end

5. Doğru ana bilgisayar bağlantı noktası (bu örnekte localhost) ile tarayıcı işlemini seçin ve **Ekle'yi**seçin.

    Bağlantı noktası (örneğin, 1337) doğru tarayıcı örneğini seçmenize yardımcı olmak için **Başlık** alanında da görünebilir.

    ::: moniker range=">=vs-2019"
    Aşağıdaki örnek, bunun Microsoft Edge (Krom) tarayıcısını nasıl kullandığını gösterir.

    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![İşleme ekle](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Hata ayıklamanın, VISUAL Studio'da DOM Explorer ve JavaScript Konsolu açıldığında doğru şekilde iliştirdiğini biliyorsunuz. Bu hata ayıklama araçları, Microsoft Edge için Chrome Geliştirici Araçları ve F12 Araçları'na benzer.
    ::: moniker-end

    > [!TIP]
    > Hata ayıklayıcı eklemiyorsa ve "Hata ayıklayıcı başlatılamadı" veya "İşleme ekleneme" iletisini görürseniz. Geçerli durumda bir işlem yasal değildir.", hata ayıklama modunda tarayıcıyı başlatmadan önce hedef tarayıcının tüm örneklerini kapatmak için Windows Görev Yöneticisi'ni kullanın. Tarayıcı uzantıları çalışıyor ve tam hata ayıklama modunu engelliyor olabilir.

6. Kesme noktası olan kod zaten yürütülmüş olabileceğinden, tarayıcı sayfanızı yenileyin. Gerekirse, yürütmeiçin kesme noktası ile kod neden eyleme geçin.

    Hata ayıklamada duraklatılırken, değişkenlerin üzerinde gezinerek ve hata ayıklama pencerelerini kullanarak uygulama durumunuzu inceleyebilirsiniz. Hata ayıklayıcıyı koda **(F5**, **F10**ve **F11)** basarak ilerletebilirsiniz. Temel hata ayıklama özellikleri hakkında daha fazla bilgi için [hata ayıklama](../debugger/debugger-feature-tour.md)ilk bakışta bakın.

    Uygulama türünüze, daha önce hangi adımları izlediğinize ve tarayıcı durumunuz gibi diğer etkenlere bağlı olarak, transpiled *.js* dosyasında veya kaynak dosyasında kesme noktasına ulaşabilirsiniz. Her iki şekilde de, kod üzerinden adım ve değişkenleri inceleyebilirsiniz.

   * Bir TypeScript, JSX veya *.vue* kaynak dosyasında kod kırmanız gerekiyorsa ve bunu yapamıyorsanız, [Sorun Giderme](#troubleshooting_source_maps) bölümünde açıklandığı gibi ortamınızın doğru ayarlandığınızdan emin olun.

   * Bir transpiled JavaScript dosyasında kod kırmak gerekir (örneğin, *app-bundle.js)* ve bunu yapamıyorsanız, kaynak harita dosyası, *filename.js.map*kaldırın.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Sorun giderme kesme noktaları ve kaynak haritalar

Bir TypeScript veya JSX kaynak dosyasında kod kırmanız gerekiyorsa ve bunu yapamıyorsanız, hata ayıklayıcıyı eklemek için önceki adımlarda açıklandığı gibi **İşleme Ekle'yi** kullanın. Ortamınızın doğru ayarlandığınızdan emin olun:

* Tarayıcıyı hata ayıklama modunda çalıştırabilmeniz için Chrome uzantıları (Görev Yöneticisi'ni kullanarak) dahil olmak üzere tüm tarayıcı örneklerini kapattınız.
      
* [Tarayıcıyı hata ayıklama modunda başlattığınızdan](#prepare_the_browser_for_debugging)emin olun.

* Kaynak harita dosyanızın kaynak dosyanıza doğru göreli yolu içerdiğinden ve Visual Studio hata ayıkıcısının kaynak dosyayı bulmasını engelleyen *webpack:///* gibi desteklenmeyen önekleri içermediğinden emin olun. Örneğin, *webpack:///.app.tsx* gibi bir başvuru *./app.tsx'e*düzeltilebilir. Bunu kaynak harita dosyasında (sınama için yararlı olan) veya özel bir yapı yapılandırması aracılığıyla el ile yapabilirsiniz. Daha fazla bilgi için hata [ayıklama için kaynak eşlemleri oluştur'a](#generate_source_maps)bakın.

Alternatif olarak, bir kaynak dosyada kod kırmanız gerekiyorsa (örneğin, *app.tsx)* ve bunu `debugger;` yapamıyorsanız, kaynak dosyadaki deyimi kullanmayı deneyin veya bunun yerine Chrome Geliştirici Araçları'nda (veya Microsoft Edge için F12 Araçları) kesme noktaları ayarlayın.

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a>Hata ayıklama için kaynak haritalar oluşturma

Visual Studio, JavaScript kaynak dosyalarında kaynak haritaları kullanma ve oluşturma özelliğine sahiptir. Kaynağınız Minified veya TypeScript veya Babel gibi bir transpiler tarafından oluşturulan genellikle bu gereklidir. Kullanılabilir seçenekler proje türüne bağlıdır.

* Visual Studio'daki bir TypeScript projesi varsayılan olarak sizin için kaynak eşlemler oluşturur. Daha fazla bilgi için [bkz.](#configure_source_maps)

* Bir JavaScript projesinde, webpack gibi bir paketleyici ve projenize ekleyebileceğiniz TypeScript derleyicisi (veya Babel) gibi bir derleyici kullanarak kaynak haritalar oluşturabilirsiniz. TypeScript derleyicisi için bir *tsconfig.json* dosyası eklemeniz ve derleyici seçeneğini ayarlamanız `sourceMap` gerekir. Temel bir web paketi yapılandırmasını kullanarak bunun nasıl yapılacağını gösteren [bir](../javascript/tutorial-nodejs-with-react-and-jsx.md)örnek için bkz.

> [!NOTE]
> Kaynak haritalarda yeniyseniz, devam etmeden önce lütfen [JavaScript Kaynak Haritalar'a Giriş'i](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) okuyun. 

Kaynak haritalar için gelişmiş ayarları yapılandırmak için, bir TypeScript projesinde *tsconfig.json* veya proje ayarlarını kullanın, ancak her ikisini de kullanmayın.

Visual Studio'yu kullanarak hata ayıklamayı etkinleştirmek için, oluşturulan kaynak haritadaki kaynak dosyanıza yapılan başvurunun doğru olduğundan emin olmanız gerekir (bu test gerektirebilir). Örneğin, web paketi kullanıyorsanız, kaynak harita dosyasındaki başvurular, Visual Studio'nun Bir TypeScript veya JSX kaynak dosyası bulmasını engelleyen *webpack:///* önekini içerir. Özellikle, hata ayıklama amacıyla bunu düzeltdiğinizde, kaynak dosyaya yapılan başvuru *(app.tsx*gibi), *webpack:///./app.tsx* gibi bir şeyden *./app.tsx*gibi bir şeye değiştirilmelidir , bu da hata ayıklamayı sağlar (yol kaynak dosyanıza göredir). Aşağıdaki örnek, visual studio ile çalışmak için en yaygın paketleyicilerden biri olan webpack'teki kaynak haritalarını nasıl yapılandırabileceğinizi gösterir.

(Yalnızca Web paketi) Bir TypeScript jsx dosyasında (transpiled JavaScript dosyası yerine) kesme noktası ayarlıyorsanız, webpack yapılandırmanızı güncelleştirmeniz gerekir. Örneğin, *webpack-config.js'de*aşağıdaki kodu değiştirmeniz gerekebilir:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

bu kod ile:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Bu, Visual Studio'da istemci tarafı kodunun hata ayıklanmasını etkinleştirmek için yalnızca geliştirme ayarıdır.

Karmaşık senaryolar için tarayıcı araçları **(F12)** bazen hata ayıklama için en iyi şekilde çalışır, çünkü özel öneklerde değişiklik gerektirmezler.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Tsconfig.json dosyakullanarak kaynak eşlemleri yapılandırma

Projenize bir *tsconfig.json* dosyası eklerseniz, Visual Studio dizin kökünü TypeScript projesi olarak ele alar. Dosyayı eklemek için, Çözüm Gezgini'nde projenizi sağ tıklatın ve ardından **Yeni Öğe > > TypeScript JSON Yapılandırma Dosyası'nı**seçin. Aşağıdaki gibi *bir tsconfig.json* dosyası projenize eklenir.

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

#### <a name="compiler-options-for-tsconfigjson"></a>tsconfig.json için derleyici seçenekleri

* **inlineSourceMap**: Her kaynak dosya için ayrı bir kaynak eşlem oluşturmak yerine kaynak haritaları içeren tek bir dosya yontun.
* **inlineSources**: Tek bir dosya içinde kaynak haritaları yanında kaynak yayan; *inlineSourceMap* veya *sourceMap'in* ayarlanmasını gerektirir.
* **mapRoot**: Hata ayıklamanın varsayılan konum yerine kaynak eşlemi (*.map*) dosyalarını bulması gereken konumu belirtir. Çalışma zamanı *.map* dosyalarının *.js* dosyalarından farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklamayı *.map* dosyalarının konumuna yönlendirmek için kaynak haritaya katıştırılır.
* **sourceMap**: Karşılık gelen bir *.map* dosyası oluşturur.
* **sourceRoot**: Hata ayıklamanın kaynak konumlar yerine TypeScript dosyalarını bulması gereken konumu belirtir. Çalışma zamanı kaynaklarının tasarım zamanındaki konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklamayı kaynak dosyaların bulunduğu yere yönlendirmek için kaynak eşleme dekzilere katıştırılır.

Derleyici seçenekleri hakkında daha fazla bilgi için TypeScript El Kitabındaki [Derleyici Seçenekleri](https://www.typescriptlang.org/docs/handbook/compiler-options.html) sayfasını kontrol edin.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Proje ayarlarını kullanarak kaynak eşlemleri yapılandırma (TypeScript project)

Ayrıca projeyi sağ tıklatarak ve ardından **Project > Properties > TypeScript Build > Hata Ayıklama'yı**seçerek proje özelliklerini kullanarak kaynak eşleme ayarlarını yapılandırabilirsiniz.

Bu proje ayarları kullanılabilir.

* **Kaynak haritaları oluşturun** *(tsconfig.json'daki* **sourceMap'e** eşdeğer): Karşılık gelen *.map* dosyası oluşturur.
* **Kaynak haritaların kök dizini belirtin** *(tsconfig.json'daki* **mapRoot'a** eşdeğer): Hata ayıklamanın oluşturulan konumlar yerine harita dosyalarını bulması gereken yeri belirtir. Çalışma zamanı *.map* dosyalarının .js dosyalarından farklı bir konumda bulunması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklama yığmayı harita dosyalarının bulunduğu yere yönlendirmek için kaynak eşleme de katıştırılır.
* **TypeScript dosyalarının kök dizinini belirtin** *(tsconfig.json'daki* **sourceRoot'a** eşdeğer): Hata ayıklamanın kaynak konumlar yerine TypeScript dosyalarını bulması gereken yeri belirtir. Çalışma zamanı kaynak dosyalarının tasarım zamanındaki konumdan farklı bir konumda olması gerekiyorsa bu bayrağı kullanın. Belirtilen konum, hata ayıklamayı kaynak dosyaların bulunduğu yere yönlendirmek için kaynak eşleme dekzilere katıştırılır.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Razor kullanarak dinamik dosyalarda JavaScript debug (ASP.NET)

::: moniker range=">=vs-2019"
Visual Studio 2019'dan itibaren Visual Studio, yalnızca Chrome ve Microsoft Edge (Chromium) için hata ayıklama desteği sağlar.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio yalnızca Chrome ve Internet Explorer için hata ayıklama desteği sağlar.
::: moniker-end

Ancak, Razor sözdizimi (cshtml, vbhtml) ile oluşturulan dosyalarda kesme noktalarına otomatik olarak vuramazsınız. Bu tür bir dosyayı hata ayıklamak için kullanabileceğiniz iki yaklaşım vardır:

* **İfadeyi `debugger;` kırmak istediğiniz yere yerleştirin**: Bu, dinamik komut dosyasının yürütmeyi durdurmasına ve oluşturulurken hemen hata ayıklamaya başlamasına neden olur.
* **Sayfayı yükleyin ve Visual Studio'da dinamik belgeyi açın**: Hata ayıklama sırasında dinamik dosyayı açmanız, kesme noktanızı ayarlamanız ve bu yöntemin çalışması için sayfayı yenilemeniz gerekir. Chrome veya Internet Explorer kullanıyor sanız, aşağıdaki stratejilerden birini kullanarak dosyayı bulacaksınız:

   Chrome için **Solution Explorer > YourPageName > Komut Dosyası Belgeleri'ne**gidin.

    > [!NOTE]
    > Chrome'u kullanırken, **komut dosyası> \<etiketleri arasında kaynak bulunmayan**bir ileti alabilirsiniz. Sorun değil, hata ayıklama devam et.

   ::: moniker range=">=vs-2019"
   Microsoft Edge (Chromium) için Chrome ile aynı yordamı kullanın.
   ::: moniker-end

   ::: moniker range="vs-2017"
   Internet Explorer **için, Windows Internet > Explorer > YourPageName > Solution Explorer > Komut Dosyası Belgeleri'ne**gidin.
   ::: moniker-end

Daha fazla bilgi için, [Google Chrome'daki ASP.NET projelerin istemci tarafından hata ayıklanmasına](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)bakın.
