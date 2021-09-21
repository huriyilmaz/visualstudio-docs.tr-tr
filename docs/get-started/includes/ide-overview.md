---
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.topic: include
ms.openlocfilehash: d98812bdba2807038d23f43d07ea48f6d3d43bc0
ms.sourcegitcommit: da19ed1e48259b219c61c4cb9e98b006004a5766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128047758"
---
*Tümleşik geliştirme ortamı* (IDE), yazılım geliştirmenin birçok yönlerini destekleyen özellik açısından zengin bir programdır. Visual Studio ıde, kod düzenlemek, hatalarını ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma paneliyle bulunur. standart düzenleyicinin ve üzerinde birçok ıdes 'in sağladığı hata ayıklayıcı, Visual Studio derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve yazılım geliştirme sürecini geliştirmeye yönelik daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio 2017 ıde 'yi gösteren ekran görüntüsü.](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="anahtar özelliklerinin ve işlevselliğinin nerede bulunduğunu belirten belirtme çizgileri içeren Visual Studio 2019 ıde 'nin ekran görüntüsü." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

::: moniker range=">=vs-2022"

[![anahtar özellikleri ve işlevlerinin konumunu belirten belirtme çizgileri ile Visual Studio 2022 ıde 'yi gösteren ekran görüntüsü.](../media/vs-2022/ide-overview.png)](../media/vs-2022/ide-overview.png#lightbox)

::: moniker-end

yukarıdaki görüntüde, önemli pencereleri ve bunların işlevlerini gösteren açık bir proje içeren Visual Studio gösterilmektedir:

- [Çözüm Gezgini](../../ide/use-solution-explorer.md), sağ üst köşedeki kod dosyalarınızı görüntüleyebilir, gidebilir ve yönetebilirsiniz. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](../../ide/solutions-and-projects-in-visual-studio.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.

- Büyük olasılıkla zaman harcamanız gereken Merkezi [Düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md), dosya içeriklerini görüntüler. Düzenleyici penceresinde, kod düzenleyebilir veya düğmeler ve metin kutuları içeren pencere gibi bir kullanıcı arabirimini tasarlayabilirsiniz.

::: moniker range="vs-2017"

- [çıkış penceresi](../../ide/reference/output-window.md) (alt orta), Visual Studio hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimleri gönderir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

- [Git değişikliklerinde](/visualstudio/version-control/) git ve [GitHub](https://docs.github.com/github) [gibi sürüm](https://git-scm.com/) denetimi teknolojilerini kullanarak iş öğelerini izleyebilir ve kodu başkalarıyla paylaşabilirsiniz.

## <a name="editions"></a>Sürümler

Visual Studio Windows ve Mac için kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) , Windows için Visual Studio aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. bu makale Visual Studio Windows sürümüne odaklanır.

Visual Studio üç sürümü vardır: Community, Professional ve Enterprise. her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Compare Visual Studio sürümleri](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

yazılım geliştirme sırasında üretkenliğinizi geliştiren Visual Studio popüler bazı özellikler şunlardır:

- Dalgalı çizgiler ve [hızlı eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, derleme veya çalışma zamanı sırasında hataları bulmayı beklemeden sorunları anında düzeltmenize yardımcı olur. Dalgalı bir çizgi üzerine geldiğinizde, hata hakkında daha fazla bilgi görürsünüz. Ayrıca, hata düzeltmesini gerçekleştirmek için uygulayabileceğiniz *hızlı eylemleri* gösteren bir ampul sol kenar boşluğunda görünebilir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio 'de dalgalı çizgiler gösteren ekran görüntüsü.](../media/squiggles-error.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio 'de dalgalı çizgiler gösteren ekran görüntüsü.](../media/vs-2022/squiggles-error.png)
   ::: moniker-end
  

::: moniker range="vs-2019"
- Kod temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirebilir ve [kod stili ayarlarınız](../../ide/reference/options-text-editor-csharp-formatting.md), [. Editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve [Roslyn çözümleyiciler](../../code-quality/roslyn-analyzers-overview.md)tarafından önerilen tüm kod düzeltmelerini uygulayabilirsiniz. Kod **Temizleme**, şu anda yalnızca C# kodu için kullanılabilir, kod incelemeye geçmeden önce kodunuzda sorunları çözmenize yardımcı olur.

   ![Kod temizleme simgesini ve Visual Studio menüsünü gösteren ekran görüntüsü.](../media/vs-2019/code-cleanup.png)
   ::: moniker-end

::: moniker range=">=vs-2022"
- Kod temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirebilir ve [kod stili ayarlarınız](../../ide/reference/options-text-editor-csharp-formatting.md), [. Editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve [Roslyn çözümleyiciler](../../code-quality/roslyn-analyzers-overview.md)tarafından önerilen tüm kod düzeltmelerini uygulayabilirsiniz. Kod **Temizleme**, şu anda yalnızca C# kodu için kullanılabilir, kod incelemeye geçmeden önce kodunuzda sorunları çözmenize yardımcı olur.

   ![Kod temizleme simgesini ve Visual Studio menüsünü gösteren ekran görüntüsü.](../media/vs-2022/code-cleanup.png)
   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adlandırılması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama ve yöntem parametrelerinin sırasını değiştirme gibi işlemleri içerir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio yeniden düzenlemeyi gösteren ekran görüntüsü.](../media/refactoring-menu.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio yeniden düzenlemeyi gösteren ekran görüntüsü.](../media/vs-2022/refactoring-menu.png)
   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen bir özellikler kümesidir ve bazı durumlarda sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu nedenle tür bilgilerini başka bir yerde aramak zorunda kalmazsınız.

   Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ::: moniker range="<=vs-2019"
   ![Bir IntelliSense üye listesini gösteren ekran görüntüsü.](../media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Bir IntelliSense üye listesini gösteren ekran görüntüsü.](../media/vs-2022/intellisense-list-members.png)
   ::: moniker-end

   IntelliSense özellikleri dile göre farklılık gösterir. daha fazla bilgi için bkz. [C# ıntellisense](../../ide/visual-csharp-intellisense.md), [Visual C++ ıntellisense](../../ide/visual-cpp-intellisense.md), [JavaScript ıntellisense](../../ide/javascript-intellisense.md)ve [Visual Basic ıntellisense](../../ide/visual-basic-specific-intellisense.md).

- [Visual Studio arama](../../ide/visual-studio-search.md)

   Visual Studio menüler, seçenekler ve özellikler zaman içinde çok daha fazla görünebilir. Visual Studio arama veya **Ctrl** + **Q**, ıde özelliklerini ve kodu tek bir yerde hızlı bir şekilde bulmanın harika bir yoludur.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 ' de hızlı başlatma arama kutusunu gösteren ekran görüntüsü.](../media/quick-launch-nuget.png)

   Daha fazla bilgi için bkz. [Hızlı başlatma](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 ' de hızlı başlatma arama kutusunu gösteren ekran görüntüsü.](../media/vs-2019/quick-launch-nuget.png)

    bilgi ve üretkenlik ipuçları için bkz. [Visual Studio aramasını kullanma](../../ide/visual-studio-search.md).

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   ![Visual Studio 'daki hızlı başlatma arama kutusunu gösteren ekran görüntüsü.](../media/vs-2022/quick-launch-nuget.png)

    bilgi ve üretkenlik ipuçları için bkz. [Visual Studio aramasını kullanma](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türü veya programlama diliniz ne olursa olsun, başkalarıyla birlikte düzenleme ve hata ayıklama işlemlerini gerçek zamanlı olarak yapın. Projenizi anında ve güvenli bir şekilde paylaşabilirsiniz. Ayrıca hata ayıklama oturumları, Terminal örnekleri, localhost Web uygulamaları, sesli çağrılar ve daha fazlasını paylaşabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu bilgiler, yöntemi değiştirme veya kaldırma hakkında düşüntiğinizde veya bir hatayı izlemeye çalışırken yararlı olabilir.

   ::: moniker range="<=vs-2019"
   ![Çağrı hiyerarşisi penceresini gösteren ekran görüntüsü.](../../ide/reference/media/call-hierarchy-csharp-expanded.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Çağrı hiyerarşisi penceresini gösteren ekran görüntüsü.](../media/vs-2022/call-hierarchy-csharp-expanded.png)
   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, Düzenleyiciden çıkmadan kod başvurularını, kod değişikliklerini, bağlantılı hataları, iş öğelerini, kod incelemelerini ve birim testlerini bulmanıza yardımcı olur.

   ::: moniker range="<=vs-2019"
   ![CodeLens 'i gösteren ekran görüntüsü.](../media/codelens-overview.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![CodeLens 'i gösteren ekran görüntüsü.](../media/vs-2022/codelens-overview.png)
   ::: moniker-end

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   **Tanıma Git** özelliği sizi doğrudan bir işlevin veya tür tanımının konumuna götürür.

   ::: moniker range="<=vs-2019"
   ![Tanıma Git menü öğesini gösteren ekran görüntüsü.](../media/go-to-definition-menu.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Tanıma Git menü öğesini gösteren ekran görüntüsü.](../media/vs-2022/go-to-definition-menu.png)
   ::: moniker-end

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Özet **tanım** penceresi, ayrı bir dosya açmadan bir yöntemi veya tür tanımını gösterir.

   ::: moniker range="<=vs-2019"
   ![Bir Özet Tanım penceresini gösteren ekran görüntüsü.](../media/peek-definition.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Bir Özet Tanım penceresini gösteren ekran görüntüsü.](../media/vs-2022/peek-definition.png)
   ::: moniker-end

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturursunuz. [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanır, uygulama yürütmesi sırasında değişken değerini görmek için bir uygulamada hata ayıklayın ve renk temasını değiştirin.

::: moniker range="vs-2017"

başlamak için [Visual Studio indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range="vs-2019"

başlamak için [Visual Studio indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, istediğiniz programlama dilleri veya platformları için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünün ekran görüntüsü.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range=">=vs-2022"

başlamak için [Visual Studio indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyicide, istediğiniz programlama dilleri veya platformları için ihtiyaç duyduğunuz Özellik grupları olan *iş yüklerini* seçer ve yüklersiniz. [Bir program oluşturmak](#create-a-program)için aşağıdaki adımları kullanmak üzere yükleme sırasında **.net masaüstü geliştirme** iş yükünü seçtiğinizden emin olun.

![Visual Studio Yükleyicisi seçili .net masaüstü geliştirme iş yükünün ekran görüntüsü.](../media/vs-2022/dot-net-development-workload.png)

::: moniker-end

Visual Studio ilk kez açtığınızda, Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="create-a-program"></a>Program oluşturma

' İ inceleyin ve basit bir program oluşturun.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   ![dosya > menü çubuğunda yeni Project gösteren ekran görüntüsü.](../media/file-new-project-menu.png)

   **yeni Project** iletişim kutusunda çeşitli proje *şablonları* gösterilmektedir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. **Visual C#** altında **.NET Core** şablon kategorisini seçin ve **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna **HelloWorld** yazın ve **Tamam** düğmesini seçin.

   ![.NET Core uygulama şablonunu gösteren ekran görüntüsü.](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. bunu yapmak için **yeni Project** iletişim kutusunun sol alt kısmındaki **aç Visual Studio Yükleyicisi** bağlantısını seçin. Visual Studio Yükleyicisi açıldıktan sonra, aşağı kaydırarak **.net Core platformlar arası geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdaki ekrana benzer bir şey görmeniz gerekir:

   ![Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu alan düzenleyici penceresinde gösterir. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![kırmızı kutulara Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama > hata ayıklama menüsü olmadan Başlat ' a gösteren ekran görüntüsü.](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![' Merhaba Dünya! ' çıkışını gösteren cmd.exe konsol penceresinin ekran görüntüsü ve ' devam etmek için herhangi bir tuşa basın '.](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya daha fazla kod ekleyelim. Şu satırı izleyerek aşağıdaki C# kodunu ekleyin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. Aşağıdaki koda gelen satırı değiştirin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata **ayıklama** > **olmadan Başlat** öğesini seçerek veya **CTRL** + **F5** tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Konsol penceresi girişini gösteren ekran görüntüsü.](../media/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi, bir depoyu kopyalama, son bir projeyi açma veya yeni bir proje oluşturma seçenekleriyle birlikte görüntülenir.

1. **Yeni proje oluştur** öğesini seçin.

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 ' de ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. tüm **diller** açılan listesinden **C#** ' ı seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz, tüm **platformlar** listesinden ve **tüm proje türleri** listesinden **konsolundan** **Windows** .

    **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' ye tıklayın.

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Visual Studio 2019 ' de, istediğiniz şablonu seçtiğinizde ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınız için dizin konumunu değiştirin (varsayılan yerel ayar `C:\Users\<name>\source\repos` ) ve ardından **ileri**' ye tıklayın.

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 ' de projenin adını girdiğiniz ' yeni projeyi yapılandırma ' penceresinin ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' in **hedef çerçeve** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' a tıklayın.

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019 ' de, istediğiniz .net Core Framework sürümünü seçtiğiniz ' ek bilgiler ' penceresinin ekran görüntüsü.":::

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdaki ekrana benzer bir şey görmeniz gerekir:

   ![Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/vs-2019/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu alan düzenleyici penceresinde gösterir. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![kırmızı kutulara Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama > hata ayıklama menü öğesi olmadan başlangıcını gösteren ekran görüntüsü.](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![' Merhaba Dünya! ' çıkışını gösteren Microsoft Visual Studio hata ayıklama konsolu penceresinin ekran görüntüsü ve ' Bu pencereyi kapatmak için herhangi bir tuşa basın '.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya daha fazla kod ekleyelim. Şu satırı izleyerek aşağıdaki C# kodunu ekleyin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. Aşağıdaki koda gelen satırı değiştirin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata **ayıklama** > **olmadan Başlat** öğesini seçerek veya **CTRL** + **F5** tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![bir ada, girişe ve ' Hello georgette! ' çıkışına ilişkin istemi gösteren Microsoft Visual Studio hata ayıklama konsolu penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end
::: moniker range=">=vs-2022"

1. Visual Studio’yu çalıştırın. Başlangıç penceresi, bir depoyu kopyalama, son bir projeyi açma veya yeni bir proje oluşturma seçenekleriyle birlikte görüntülenir.

1. **Yeni proje oluştur** öğesini seçin.

   ![yeni proje oluştur seçiliyken Visual Studio başlat menüsünün ekran görüntüsü.](../media/vs-2022/create-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. Bir şablonu bulmak için arama kutusuna anahtar sözcükleri yazabilir veya girebilirsiniz. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre filtreler. tüm **diller** açılan listesinden **C#** ' ı seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz, tüm **platformlar** listesinden ve **tüm proje türleri** listesinden **konsolundan** **Windows** .

    **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Konsol uygulaması seçiliyken yeni proje oluştur penceresinin ekran görüntüsü.](../media/vs-2022/start-window-create-new-project.png)

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** kutusuna **HelloWorld** yazın. İsteğe bağlı olarak, proje dizini konumunu *C: \\ Users \\ \<name> \\ kaynak \\ deposunun* varsayılan konumundan değiştirip **İleri**' yi seçin.

   ![Yeni projenizi, HelloWorld adlı proje adı ile yapılandırın penceresinin ekran görüntüsü.](../media/vs-2022/configure-new-project.png)

1. **Ek bilgi** penceresinde, **.net 6,0** ' in **hedef Framework** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' u seçin.

   ![.NET 6,0 seçiliyken ek bilgi penceresinin ekran görüntüsü.](../media/vs-2022/create-project-additional-info.png)

   Visual Studio projeyi oluşturur. Program <xref:System.Console.WriteLine?displayProperty=nameWithType> **, Hello, World!** dizesini görüntüleyen yöntemi çağıran basit bir "Merhaba Dünya" uygulamasıdır. bir konsol penceresinde.

   proje dosyaları, **Çözüm Gezgini** adlı bir pencerede Visual Studio ıde 'nin sağ tarafında görünür. **Çözüm Gezgini** penceresinde **program. cs** dosyasını seçin. Uygulamanızın C# kodu, alanın çoğunu alan merkezi düzenleyici penceresinde açılır.

   ![düzenleyicide Program. cs kodu ile Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/vs-2022/overview-ide-console-app.png)

   Kod, anahtar sözcükler ve türler gibi farklı parçaları göstermek için otomatik olarak renklendirilir. Satır numaraları kodu bulmanıza yardımcı olur.

   Koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi veya artı işaretlerini de seçebilirsiniz. Bu kod ana hattı özelliği, ekran dağınıklığını en aza indirmeye yardımcı olmak için, görmeniz gerekmeyen kodu gizlemenizi sağlar.

   ![kırmızı kutulara Visual Studio ıde 'yi gösteren ekran görüntüsü.](../media/vs-2022/overview-ide-console-app-red-boxes.png)

   Diğer birçok menü ve araç penceresi mevcuttur.

1. Visual Studio üst menüden **hata ayıklama**  >  **olmadan başlat** öğesini seçerek uygulamayı başlatın. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama > hata ayıklama menü öğesi olmadan başlangıcını gösteren ekran görüntüsü.](../media/vs-2022/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Hello, World!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Hello, World! çıktısını gösteren hata ayıklama konsolu penceresinin ekran görüntüsü ve bu pencereyi kapatmak için herhangi bir tuşa basın.](../media/vs-2022/overview-console-window.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

1. Uygulamaya daha fazla kod ekleyelim. Şu satırı izleyerek aşağıdaki C# kodunu ekleyin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından Kullanıcı bazı metinleri girene kadar bekler.

1. Aşağıdaki satıra yazan çizgiyi değiştirin `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata **ayıklama** > **olmadan Başlat** öğesini seçerek veya **CTRL** + **F5** tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı yazın ve **ENTER** tuşuna basın.

   ![Bir ad, giriş ve Hello Georgette! çıkışı için istem gösteren hata ayıklama konsolu penceresinin ekran görüntüsü.](../media/vs-2022/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) 'in daha verimli bir şekilde kodlamasına yardımcı olması için birkaç yol göz atalım.

İlk olarak, değişkeni yeniden adlandırın `name` :

1. Değişkene çift tıklayın `name` ve değişken için yeni ad, *Kullanıcı* adı yazın.

   Değişken etrafında bir kutu belirir ve kenar boşluğunda ampul görünür.

1. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ::: moniker range="vs-2017"
   ![Visual Studio yeniden adlandırma eylemini gösteren ekran görüntüsü.](../media/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range="vs-2019"
   ![Visual Studio yeniden adlandırma eylemini gösteren ekran görüntüsü.](../media/vs-2019/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio yeniden adlandırma eylemini gösteren ekran görüntüsü.](../media/vs-2022/rename-quick-action.png)
   ::: moniker-end

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer olur.

   ::: moniker range="vs-2017"
   ![Visual Studio yeniden düzenlemeyi yeniden adlandırma gösteren animasyonlu GIF.](../media/rename-refactoring.gif)
   ::: moniker-end

1. Şimdi IntelliSense 'e göz atın. Belirten satırın altında `Console.WriteLine($"\nHello {username}!");` yazın `DateTime now = DateTime.` .

   Bir kutu, sınıfının üyelerini görüntüler <xref:System.DateTime> . Şu anda seçili olan üyenin açıklaması ayrı bir kutu içinde de görüntülenir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio 'teki IntelliSense Liste üyelerini gösteren ekran görüntüsü.](../media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio 'teki IntelliSense Liste üyelerini gösteren ekran görüntüsü.](../media/vs-2022/intellisense-list-members.png)
   ::: moniker-end

1. Sınıfın bir özelliği olan, ' a çift tıklayarak veya **sekme** tuşuna basarak **Şimdi** adlı üyeyi seçin. Satır sonuna noktalı virgül ekleyerek kod satırını doldurun: `DateTime now = DateTime.Now;` .

1. Bu satırın altına aşağıdaki kod satırlarını girin:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırıldıktan sonra bir satır Sonlandırıcı eklemediğinden farklıdır. Diğer bir deyişle, çıktıya gönderilen sonraki metin parçası aynı satıra yazdırılır. Açıklamalarını görmek için kodunuzda bu yöntemlerin her birinin üzerine gelebilmeniz gerekir.

1. Daha sonra, yeniden düzenleme kullanarak kodu biraz daha kısa hale getirin. Satırdaki değişkeni seçin `now` `DateTime now = DateTime.Now;` . Bu satırdaki kenar boşluğunda bir screwdriver simgesi görüntülenir.

1. Visual Studio sunulan önerileri görmek için screwdriver simgesini seçin. Bu durumda, genel kod davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösterilmektedir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio 'da satır Içi geçici değişken önerisini gösteren ekran görüntüsü.](../media/inline-temporary-variable-refactoring.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio 'da satır Içi geçici değişken önerisini gösteren ekran görüntüsü.](../media/vs-2022/inline-temporary-variable-refactoring.png)
   ::: moniker-end

1. Kodu yeniden düzenleme için **satır içi geçici değişken** ' i seçin.

1. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

   ::: moniker range="<=vs-2019"
   ![Bir ada, girişe ve ' Hello Georgette! ' çıkışına ilişkin istemi gösteren hata ayıklama konsolu penceresinin ekran görüntüsü Yılın günü: 43 '.](../media/vs-2019/overview-console-final.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Bir ada, girişe ve ' Hello Georgette! ' çıkışına ilişkin istemi gösteren hata ayıklama konsolu penceresinin ekran görüntüsü Yılın günü: 244 '.](../media/vs-2022/overview-console-final.png)
   ::: moniker-end

## <a name="debug-code&quot;></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio hata ayıklama sistemi, bir seferde kod tek bir bildirimde ilerlemenizi ve gittiğiniz değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* ayarlayabilir ve kodun çalıştığı şekilde değişken değerinin nasıl değiştiğini gözlemleyebilirsiniz.

Program çalışırken değişkenin değerini görmek için bir kesme noktası ayarlayın `username` .

1. `Console.WriteLine($&quot;\nHello {username}!");`Satırın yanındaki sol kenar boşluğuna veya cilt payına tıklayarak belirten kod satırında bir kesme noktası ayarlayın. Ayrıca kod satırını seçip **F9** tuşuna basabilirsiniz.

   Cilt alanında kırmızı bir daire görünür ve çizgi vurgulanır.

   ::: moniker range="<=vs-2019"
   ![Visual Studio bir kod satırı üzerinde bir kesme noktası gösteren ekran görüntüsü.](../media/breakpoint.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio bir kod satırı üzerinde bir kesme noktası gösteren ekran görüntüsü.](../media/vs-2022/breakpoint.png)
   ::: moniker-end

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatın** veya **F5**'e basın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde adınızı girin.

   odak Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Sarı vurgu, bu kod satırının sonraki yürütüleceği anlamına gelir. Kesme noktası, uygulamanın bu satırda yürütmeyi duraklatmasını sağlar.

1. `username`Değerini görmek için farenizi değişkenin üzerine getirin. Ayrıca, ' ı sağ tıklayıp `username` **izleme Ekle** ' yi seçerek değişkeni **izleme** penceresine ekleyebilirsiniz; burada da bu değeri görebilirsiniz.

   ::: moniker range="<=vs-2019"
   ![Visual Studio hata ayıklama sırasında bir değişken değeri gösteren ekran görüntüsü.](../media/debugging-variable-value.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio hata ayıklama sırasında bir değişken değeri gösteren ekran görüntüsü.](../media/vs-2022/debugging-variable-value.png)
   ::: moniker-end

1. Uygulamayı çalıştırmaya son vermek için **F5** tuşuna basın.

Visual Studio hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcı özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Visual Studio özelleştirme

varsayılan renk temasını değiştirme da dahil olmak üzere Visual Studio kullanıcı arabirimini kişiselleştirebilirsiniz. Renk temasını değiştirmek için:

::: moniker range="vs-2017"

1. Menü çubuğunda,  > **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

1. **Ortam** > **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ![koyu temada Visual Studio gösteren ekran görüntüsü.](../media/dark-theme.png)
::: moniker-end

::: moniker range="vs-2019"

1. Menü çubuğunda,  > **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

1. **Ortam** > **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ![koyu temada Visual Studio gösteren ekran görüntüsü.](../media/vs-2019/dark-theme.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Menü çubuğunda, Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** sayfasında Renk Teması seçimini Mavi veya Açık olarak değiştirerek >  Tamam'ı **seçin.**   

   IDE'nin tamamı için renk teması buna göre değişir. Aşağıdaki ekran görüntüsü mavi temayı gösterir:

   ![Mavi temada Visual Studio gösteren ekran görüntüsü.](../media/vs-2022/blue-theme.png)
::: moniker-end

IDE'nizi kişiselleştirmenin diğer yolları hakkında bilgi edinmek için [bkz. Visual Studio.](../../ide/personalizing-the-visual-studio-ide.md)