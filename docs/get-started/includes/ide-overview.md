---
ms.date: 11/04/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.topic: include
ms.openlocfilehash: 54effd262078cb9758d9464eb7438075b865e348
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131663704"
---
Tümleşik *geliştirme ortamı* (IDE), yazılım geliştirmenin birçok özelliğini destekleyen zengin bir programdır. Bu Visual Studio IDE, kod düzenlemek, hata ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz yaratıcı bir başlatma panelidir. Çoğu IDE'nin sağlediği standart düzenleyici ve hata ayıklayıcının üzerinde ve üzerinde, Visual Studio, kod tamamlama araçları, grafik tasarımcıları ve yazılım geliştirme sürecini geliştirmek için daha birçok özellik vardır.

::: moniker range="vs-2017"

![2017 IDE'Visual Studio gösteren ekran görüntüsü.](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Visual Studio 2019 IDE'nin, önemli özelliklerin ve işlevlerin bulunduğu yeri belirten çağrılar içeren ekran görüntüsü." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

::: moniker range=">=vs-2022"

[![2022 IDE'Visual Studio gösteren ekran görüntüsü, önemli özelliklerin ve işlevlerin konumunu belirten eklemeler.](../media/vs-2022/ide-overview.png)](../media/vs-2022/ide-overview.png#lightbox)

::: moniker-end

Yukarıdaki görüntüde, Visual Studio pencerelerini ve işlevlerini gösteren açık bir projeyle birlikte aşağıdaki özellikler yer aleni şekilde görüntüdedir:

- Bu [Çözüm Gezgini](../../ide/use-solution-explorer.md)sağ üst köşedeki kod dosyalarınızı abilir, gezinebilirsiniz ve yönetebilirsiniz. **Çözüm Gezgini,** dosyaları çözümler ve projeler olarak gruplamanıza yardımcı [olabilir.](../../ide/solutions-and-projects-in-visual-studio.md)

- Büyük [olasılıkla zaman](../../ide/writing-code-in-the-code-and-text-editor.md)harcamanız gereken merkezi düzenleyici penceresi, dosya içeriğini görüntüler. Düzenleyici penceresinde, kodu düzenleyebilir veya düğmeleri ve metin kutuları olan bir pencere gibi bir kullanıcı arabirimi tasarabilirsiniz.

::: moniker range="vs-2017"

- Çıkış [penceresi](../../ide/reference/output-window.md) (alttaki orta), hata ayıklama Visual Studio hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

- Sağ [altta](/visualstudio/version-control/) yer alan Git Değişiklikleri'nde, Git ve GitHub gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini [izleyebilir](https://git-scm.com/) ve başka [GitHub.](https://docs.github.com/github)

## <a name="editions"></a>Sürümler

Visual Studio mac ve Windows kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) platformlar arası ve mobil uygulamalar Visual Studio Windows için en iyi duruma getirilmiş özelliklere sahiptir. Bu makale, Windows sürümüne Visual Studio.

Üç sürüm vardır: Visual Studio, Community, Professional ve Enterprise. Her [sürümde Visual Studio özellikler hakkında](https://visualstudio.microsoft.com/vs/compare/) bilgi edinmek için bkz. Visual Studio sürümleri karşılaştırma.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Yazılım geliştirme Visual Studio üretkenliğinizi geliştiren bazı popüler özellikler şunlardır:

- Geçişler ve [Hızlı Eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarak kodundaki hatalara veya olası sorunlara karşı sizi uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, derleme veya çalışma zamanı sırasında hataları keşfetmeyi beklemeden sorunları hemen düzeltmeye yardımcı olur. Bir geçişin üzerine gelindiğinde hata hakkında daha fazla bilgi alırsınız. Hatayı düzeltmek için gerçekleştirebilir hızlı eylemleri gösteren *sol* kenar boşluğunda bir ampul de görünebilir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio'daki geçişleri gösteren ekran görüntüsü.](../media/squiggles-error.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio'daki geçişleri gösteren ekran görüntüsü.](../media/vs-2022/squiggles-error.png)
   ::: moniker-end

::: moniker range="vs-2019"
- Kod Temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirebilirsiniz ve kod stili ayarlarınız [,](../../ide/reference/options-text-editor-csharp-formatting.md) [.editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve Roslyn çözümleyicileri tarafından önerilen kod [düzeltmelerini uygulayabilirsiniz.](../../code-quality/roslyn-analyzers-overview.md) **Şu anda** yalnızca C# kodu için kullanılabilen Kod Temizleme, kod incelemesine gitmeden önce kodundaki sorunları çözmenize yardımcı olur.

   ![Kod Temizleme simgesini ve uygulama menüsündeki menüyü gösteren Visual Studio.](../media/vs-2019/code-cleanup.png)
   ::: moniker-end

::: moniker range=">=vs-2022"
- Kod Temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirebilirsiniz ve kod stili ayarlarınız [,](../../ide/reference/options-text-editor-csharp-formatting.md) [.editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve Roslyn çözümleyicileri tarafından önerilen kod [düzeltmelerini uygulayabilirsiniz.](../../code-quality/roslyn-analyzers-overview.md) **Şu anda** yalnızca C# kodu için kullanılabilen Kod Temizleme, kod incelemesine gitmeden önce kodundaki sorunları çözmenize yardımcı olur.

   ![Kod Temizleme simgesini ve uygulama menüsündeki menüyü gösteren Visual Studio.](../media/vs-2022/code-cleanup.png)
   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adı oluşturma, bir veya daha fazla kod satırı ayıklanan yeni bir yöntem ve yöntem parametrelerinin sırası değiştirme gibi işlemleri içerir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio'da Yeniden Düzenleme'Visual Studio.](../media/refactoring-menu.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Visual Studio'da Yeniden Düzenleme'Visual Studio.](../media/vs-2022/refactoring-menu.png)
   ::: moniker-end

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntülemenizi ve bazı durumlarda sizin için küçük kod bitlerini yazmanızı sağlar. Bu, düzenleyicide satır içinde temel belgelere sahip olmak gibi bir şey, bu nedenle başka bir yerde tür bilgilerini aramana gerek kalmadan.

   Aşağıdaki çizimde, IntelliSense'in bir tür için üye listesini nasıl görüntülesi gösterilmiştir:

   ::: moniker range="<=vs-2019"
   ![IntelliSense üye listesini gösteren ekran görüntüsü.](../media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![IntelliSense üye listesini gösteren ekran görüntüsü.](../media/vs-2022/intellisense-list-members.png)
   ::: moniker-end

   IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için bkz. [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) [ve IntelliSense Visual Basic.](../../ide/visual-basic-specific-intellisense.md)

- [Visual Studio arama](../../ide/visual-studio-search.md)

   Visual Studio menüler, seçenekler ve özellikler bazen aşırı zor görünebilir. Visual Studio veya **Ctrl** Q, IDE özelliklerini ve kodunu tek bir yerde hızla + bulmanın harika bir yoludur.

   ::: moniker range="vs-2017"

   ![Hızlı Başlat 2017'de Visual Studio gösteren ekran görüntüsü.](../media/quick-launch-nuget.png)

   Daha fazla bilgi için [bkz. Hızlı Başlat.](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019'daki Hızlı Başlat kutusunu gösteren ekran görüntüsü.](../media/vs-2019/quick-launch-nuget.png)

    Daha fazla bilgi ve üretkenlik ipuçları için [bkz. Arama Visual Studio kullanma.](../../ide/visual-studio-search.md)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   ![Visual Studio'Hızlı Başlat arama kutusunu gösteren ekran görüntüsü.](../media/vs-2022/quick-launch-nuget.png)

    Daha fazla bilgi ve üretkenlik ipuçları için [bkz. Arama Visual Studio kullanma.](../../ide/visual-studio-search.md)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türünüz veya programlama diliniz ne olursa olsun, diğerleriyle gerçek zamanlı işbirliği yaparak düzenleme ve hata ayıklama. Projenizi anında ve güvenli bir şekilde paylaşabilirsiniz. Hata ayıklama oturumlarını, terminal örneklerini, localhost web uygulamalarını, sesli çağrıları ve daha fazlasını da paylaşabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   Çağrı **Hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu bilgiler, yöntemi değiştirmeyi veya kaldırmayı düşünürken veya bir hatayı bulmaya çalışırken yararlı olabilir.

   ::: moniker range="<=vs-2019"
   ![Çağrı Hiyerarşisi penceresini gösteren ekran görüntüsü.](../../ide/reference/media/call-hierarchy-csharp-expanded.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Çağrı Hiyerarşisi penceresini gösteren ekran görüntüsü.](../media/vs-2022/call-hierarchy-csharp-expanded.png)
   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, düzenleyiciden ayrılmadan kod başvurularını, kod değişikliklerini, bağlantılı hataları, iş öğelerini, kod incelemelerini ve birim testlerini bulumanıza yardımcı olur.

   ::: moniker range="<=vs-2019"
   ![CodeLens'i gösteren ekran görüntüsü.](../media/codelens-overview.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![CodeLens'i gösteren ekran görüntüsü.](../media/vs-2022/codelens-overview.png)
   ::: moniker-end

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma **Git özelliği** sizi doğrudan bir işlevin veya tür tanımının bulunduğu konuma alır.

   ::: moniker range="<=vs-2019"
   ![Tanıma Git menü öğesini gösteren ekran görüntüsü.](../media/go-to-definition-menu.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Tanıma Git menü öğesini gösteren ekran görüntüsü.](../media/vs-2022/go-to-definition-menu.png)
   ::: moniker-end

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Tanıma **Göz At** penceresinde ayrı bir dosya açılmadan bir yöntem veya tür tanımı gösterilir.

   ::: moniker range="<=vs-2019"
   ![Tanıma Göz At penceresini gösteren ekran görüntüsü.](../media/peek-definition.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Tanıma Göz At penceresini gösteren ekran görüntüsü.](../media/vs-2022/peek-definition.png)
   ::: moniker-end

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Bu bölümde, yeni bir uygulamayla bazı şeyleri denemek için basit bir proje Visual Studio. [IntelliSense'i](../../ide/using-intellisense.md) kodlama yardımı olarak kullanır, uygulama yürütme sırasında değişken bir değer görmek için uygulamada hata ayıklar ve renk temasını değiştirirsiniz.

::: moniker range="vs-2017"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirin ve sisteminize yükleyin. Modüler yükleyici, tercih ettiği programlama dili veya platform için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için](#create-a-program)yükleme sırasında .NET Core platformlar arası geliştirme iş yükünü **seçin.**

::: moniker-end

::: moniker range="vs-2019"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirin ve sisteminize yükleyin. Modüler yükleyici, istediğiniz programlama dilleri veya *platformlar* için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için,](#create-a-program)yükleme sırasında **.NET Core platformlar arası geliştirme iş yükünü seçmeye** emin olun.

![Uygulamanın .NET Core platformlar arası geliştirme iş yükünün ekran Visual Studio Yükleyicisi.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range=">=vs-2022"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirin ve sisteminize yükleyin. Modüler yükleyicide, istediğiniz programlama dilleri *veya platformlar* için ihtiyacınız olan özellik grupları olan iş yüklerini seçer ve yükleyebilirsiniz. Bir program oluşturmak üzere aşağıdaki [adımları kullanmak için,](#create-a-program)yükleme sırasında .NET masaüstü geliştirme **iş yükünü seçmeyi** emin olun.

:::image type="content" source="../../ide/media/vs-2022/dot-net-development-workload.png" alt-text="Uygulamanın içinde seçilen .NET masaüstü geliştirme iş yükünün Visual Studio Yükleyicisi.":::

::: moniker-end

Visual Studio kez Microsoft hesabı oturum açmak için Microsoft hesabı [](../../ide/signing-in-to-visual-studio.md) veya okul hesabınızla oturum açabilirsiniz.

## <a name="create-a-program"></a>Program oluşturma

Basit bir program oluşturma ve bu programa dalın.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni **Dosya'Project.** >  > 

   ![Menü çubuğundaKimlik > Yeni Project'i gösteren ekran görüntüsü.](../media/file-new-project-menu.png)

   Yeni **Project** iletişim kutusunda birkaç proje *şablonu görüntülenir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Visual C# **altında .NET Core** şablon **kategorisini** seçin ve ardından Konsol Uygulaması **(.NET Core) şablonunu** seçin. Ad **metin** kutusuna **HelloWorld yazın ve** tamam **düğmesini** seçin.

   ![.NET Core uygulama şablonunu gösteren ekran görüntüsü.](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > .NET Core kategorisini **görmüyorsanız.NET Core** platformlar arası geliştirme **iş yükünü yüklemeniz** gerekir. Bunu yapmak için, Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol alt kısmında bulunan Dosya aç **Project** seçin. Uygulama Visual Studio Yükleyicisi sonra ekranı aşağı kaydırın ve **.NET Core** platformlar arası geliştirme iş yükünü seçin ve ardından Değiştir'i **seçin.**

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısa bir süre sonra aşağıdaki ekrana benzer bir şey görürsünüz:

   ![IDE'nin Visual Studio ekran görüntüsü.](../media/overview-ide-console-app.png)

   Uygulamanıza göre C# kodu düzenleyici penceresinde gösterilir ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretlerini seçebilirsiniz. Bu kod açıklama özelliği, ihtiyacınız olan kodu gizleyerek ekrandaki dağınıklığı en aza indirmenizi sağlar. Proje dosyaları, Çözüm Gezgini adlı bir pencerede **sağ tarafta listelenir.**

   ![IDE'nin kırmızı Visual Studio gösteren ekran görüntüsü.](../media/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de vardır, ancak şimdilik devam edin.

1. Şimdi uygulamayı başlatabilirsiniz. Bunu yapmak için menü çubuğundaki **Hata Ayıklama menüsünden** Hata **Ayıklama** Olmadan Başlat'ı seçebilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata ayıklama ve hata ayıklama > başlat menüsünü gösteren ekran görüntüsü.](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve şu iletiyle bir konsol penceresi **Merhaba Dünya!**. Artık çalışan bir uygulama var!

   !['cmd.exe!' çıkışını gösteren Merhaba Dünya görüntüsü ve 'Devam etmek için herhangi bir tuşa basın'.](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Şimdi uygulamaya biraz daha kod ekleriz. aşağıdaki C# kodunu şu satırdan önce `Console.WriteLine("Hello World!");` ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve ardından kullanıcının bir metin girmesini ve enter tuşuna kadar **beklemesini** sağlar.

1. aşağıdaki kodla `Console.WriteLine("Hello World!");` ifade eden satırı değiştirme:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata Ayıklama Olmadan Başlat'ı **seçerek veya** >  **Ctrl** F5 tuşlarına basarak uygulamayı + **yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız girin ve Enter tuşuna **basın.**

   ![Konsol penceresi girişini gösteren ekran görüntüsü.](../media/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi, bir repo kopyalama, yakın zamanda bir proje açma veya yeni proje oluşturma seçenekleriyle birlikte görüntülenir.

1. Yeni **proje oluştur'a seçin.**

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019'da 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Bizim istediğiniz şablonu bulmak için arama kutusuna **.net Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Tüm dil açılan **listesinden C#** dilini  seçerek, Tüm  platformlar listesinden Windows ve  Tüm proje türleri listesinden Konsol'a bakarak şablon sonuçlarını daha **fazla filtreleyebilirsiniz.** 

    Konsol Uygulaması **şablonunu seçin** ve ardından Sonraki'ye **tıklayın.**

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Yeni **projenizi yapılandır** penceresinde, **Project** adı kutusuna **HelloWorld** yazın, isteğe bağlı olarak proje dosyalarınızın dizin konumunu (varsayılan yerel ayardır) ve ardından `C:\Users\<name>\source\repos` Sonraki 'ye **tıklayın.**

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019'da projenin adını girdiğiniz 'Yeni projenizi yapılandır' penceresinin ekran görüntüsü.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan menüsünde **.NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019'da istediğiniz .NET Core Framework sürümünü seçerek 'Ek bilgiler' penceresinin ekran görüntüsü.":::

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısa bir süre sonra aşağıdaki ekrana benzer bir şey görürsünüz:

   ![IDE'nin Visual Studio ekran görüntüsü.](../media/vs-2019/overview-ide-console-app.png)

   Uygulamanıza göre C# kodu düzenleyici penceresinde gösterilir ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretlerini seçebilirsiniz. Bu kod açıklama özelliği, ihtiyacınız olan kodu gizleyerek ekrandaki dağınıklığı en aza indirmenizi sağlar. Proje dosyaları, Çözüm Gezgini adlı bir pencerede **sağ tarafta listelenir.**

   ![IDE'nin kırmızı Visual Studio gösteren ekran görüntüsü.](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de vardır, ancak şimdilik devam edin.

1. Şimdi uygulamayı başlatabilirsiniz. Bunu yapmak için menü çubuğundaki **Hata Ayıklama menüsünden** Hata **Ayıklama** Olmadan Başlat'ı seçebilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata Ayıklama ve Hata Ayıklama > Başlat menü öğesini gösteren ekran görüntüsü.](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve şu iletiyle bir konsol penceresi **Merhaba Dünya!**. Artık çalışan bir uygulama var!

   !['Merhaba Dünya!' çıkışını gösteren Hata Ayıklama Konsolu penceresinin Microsoft Visual Studio görüntüsü ve 'Bu pencereyi kapatmak için herhangi bir tuşa basın'.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Şimdi uygulamaya biraz daha kod ekleriz. aşağıdaki C# kodunu şu satırdan önce `Console.WriteLine("Hello World!");` ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve ardından kullanıcının bir metin girmesini ve enter tuşuna kadar **beklemesini** sağlar.

1. aşağıdaki kodla `Console.WriteLine("Hello World!");` ifade eden satırı değiştirme:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata Ayıklama Olmadan Başlat'ı **seçerek veya** >  **Ctrl** F5 tuşlarına basarak uygulamayı + **yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız girin ve Enter tuşuna **basın.**

   ![Ad, giriş Microsoft Visual Studio çıkışını gösteren Hata Ayıklama Konsolu penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end
::: moniker range=">=vs-2022"

1. Visual Studio’yu çalıştırın. Başlangıç penceresi, bir repo kopyalama, yakın zamanda bir proje açma veya yeni proje oluşturma seçenekleriyle birlikte görüntülenir.

1. Yeni **proje oluştur'a seçin.**

   ![Yeni proje oluştur Visual Studio başlat menüsünün ekran görüntüsü.](../media/vs-2022/create-new-project.png)

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Şablon bulmak için arama kutusuna anahtar sözcükler yazabilirsiniz veya girebilirsiniz. Kullanılabilir şablonların listesi, girersiniz anahtar sözcüklere göre filtreler. Tüm diller açılan **listesinden C#** dilini, Tüm platformlar  listesinden ve Konsol'Windows tüm  proje türleri listesinden C# seçerek şablon sonuçlarını daha fazla   **filtreleyebilirsiniz.**

    Konsol Uygulaması **şablonunu ve** ardından Sonraki'yi **seçin.**

   ![Konsol Uygulaması'nın seçili olduğu Yeni proje oluştur penceresinin ekran görüntüsü.](../media/vs-2022/start-window-create-new-project.png)

1. Yeni **projenizi yapılandır penceresinde,** Yeni **projenizin** adı **kutusuna HelloWorld Project** girin. İsteğe bağlı olarak, proje dizini konumunu varsayılan C: Kullanıcılar *\\ kaynak \\ \<name> \\ \\ repos'larından değiştirerek* Sonraki'yi **seçin.**

   ![Yeni projenizi yapılandır penceresinin, Proje adı HelloWorld girildi olarak ekran görüntüsü.](../media/vs-2022/configure-new-project.png)

1. Ek **bilgiler penceresinde** Hedef Çerçeve açılan menüsünde **.NET 6.0'ın** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

   ![.NET 6.0'ın seçili olduğu Ek bilgiler penceresinin ekran görüntüsü.](../media/vs-2022/create-project-additional-info.png)

   Visual Studio projeyi oluşturur. Program, Hello, World! Merhaba Dünya için yöntemini çağıran <xref:System.Console.WriteLine?displayProperty=nameWithType> basit bir "Merhaba Dünya" **uygulamasıdır.** bir konsol penceresinde.

   Proje dosyaları, Visual Studio IDE'nin sağ tarafında, **Çözüm Gezgini.** Yeni **Çözüm Gezgini** **Program.cs dosyasını** seçin. Uygulamanıza uygun C# kodu, merkezi düzenleyici penceresinde açılır ve bu da yerlerin çoğunu alır.

   ![Düzenleyicide Program.cs Visual Studio IDE'yi gösteren ekran görüntüsü.](../media/vs-2022/overview-ide-console-app.png)

   Kod, anahtar sözcükler ve türler gibi farklı bölümleri göstermek için otomatik olarak renklenir. Satır numaraları kodu bulumanıza yardımcı olur.

   Kodda küçük, dikey kesikli satırlar, hangi ayraçların bir diğer küme ayracıyla eş olduğunu gösteriyor. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi veya artı işaretleri de seçebilirsiniz. Bu kod açıklama özelliği, görmenizi gerektir etmeyen kodu gizleyerek ekrandaki dağınıklığı en aza indirmeye yardımcı olur.

   ![IDE'nin kırmızı Visual Studio gösteren ekran görüntüsü.](../media/vs-2022/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri kullanılabilir.

1. Üst menüden Hata **Ayıklama**  >  **Olmadan Başlat'ı** seçerek Visual Studio başlatabilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata Ayıklama ve Hata Ayıklama > Başlat menü öğesini gösteren ekran görüntüsü.](../media/vs-2022/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve **Hello, World!** iletisiyle bir konsol penceresi açılır. Artık çalışan bir uygulama var!

   ![Çıktıyı gösteren Hata Ayıklama Konsolu penceresinin ekran görüntüsü Merhaba Dünya! ve Bu pencereyi kapatmak için herhangi bir tuşa basın.](../media/vs-2022/overview-console-window.png)

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

1. Şimdi uygulamaya biraz daha kod ekleriz. aşağıdaki C# kodunu şu satırdan önce `Console.WriteLine("Hello World!");` ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve kullanıcı metin girene kadar bekler.

1. şu satıra `Console.WriteLine("Hello World!");` kadar olan satırı değiştirme:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Hata Ayıklama Olmadan Başlat'ı **seçerek veya** >  **Ctrl** F5 tuşlarına basarak + **uygulamayı yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız yazın ve Enter tuşuna **basın.**

   ![Bir ad, giriş ve Çıkış Hello Lynctte! istemini gösteren Hata Ayıklama Konsolu penceresinin ekran görüntüsü.](../media/vs-2022/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden düzenlemenin ve [IntelliSense'in](../../ide/using-intellisense.md) daha [verimli](../../ide/refactoring-in-visual-studio.md) bir şekilde kodlamanıza yardımcı olmak için birkaç yolu göz atabilirsiniz.

İlk olarak değişkeni yeniden `name` adlandırin:

1. değişkenine çift `name` tıklayın ve değişkeninin yeni adını (username) *yazın.*

   Değişkenin etrafında bir kutu ve kenar boşluğunda bir ampul görünür.

1. Kullanılabilir Hızlı Eylemler'i göstermek için ampul [simgesini seçin.](../../ide/quick-actions.md) **'name' adını 'username' olarak yeniden adlandır'ı seçin.**

   ::: moniker range="vs-2017"
   ![Uygulamanın yeniden adlandırma eylemlerini gösteren Visual Studio.](../media/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range="vs-2019"
   ![Uygulamanın yeniden adlandırma eylemlerini gösteren Visual Studio.](../media/vs-2019/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Uygulamanın yeniden adlandırma eylemlerini gösteren Visual Studio.](../media/vs-2022/rename-quick-action.png)
   ::: moniker-end

   Değişkeni proje genelinde yeniden adlandırıldı ve bu bizim durumumuz için yalnızca iki yer.

   ::: moniker range="vs-2017"
   ![Yeniden adlandırma yeniden düzenlemeyi grafikte gösteren animasyonlu gif Visual Studio.](../media/rename-refactoring.gif)
   ::: moniker-end

1. Şimdi IntelliSense'e göz at. olan satırın altına `Console.WriteLine($"\nHello {username}!");` `DateTime now = DateTime.` yazın.

   Sınıfın üyelerini bir kutu <xref:System.DateTime> görüntüler. Seçili olan üyenin açıklaması da ayrı bir kutuda görüntülenir.

   ::: moniker range="<=vs-2019"
   ![Raporlarda IntelliSense liste üyelerini gösteren Visual Studio.](../media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Raporlarda IntelliSense liste üyelerini gösteren Visual Studio.](../media/vs-2022/intellisense-list-members.png)
   ::: moniker-end

1. Çift tıklayarak **veya Tab** tuşuna basarak sınıfının bir özelliği olan Now adlı üyeyi **seçin.** Satırın sonuna noktalı virgül ekleyerek kod satırı tamamlanır: `DateTime now = DateTime.Now;` .

1. Bu satırın altına aşağıdaki kod satırlarını girin:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırılırken satır sonlandırıcı eklemeyilmesinden farklıdır. Bu, çıkışa gönderilen sonraki metnin aynı satırda yazdırılacak olduğu anlamına gelir. Açıklamalarını görmek için kodunda bu yöntemlerin her biri üzerine gelin.

1. Ardından kodu biraz daha kısa hale gelecek şekilde yeniden düzenlemeyi kullanın. satırda `now` değişkenlerini `DateTime now = DateTime.Now;` seçin. Bu çizginin kenar boşluğunda bir tornavida simgesi görünür.

1. Aşağıdaki seçeneklerden uygun önerileri görmek için tornavida simgesini Visual Studio. Bu durumda, [genel kod davranışını değiştirmeden](../../ide/reference/inline-temporary-variable.md) bir kod satırı kaldırmak için satır içi geçici değişken yeniden düzenlemesi gösterir.

   ::: moniker range="<=vs-2019"
   ![Uygulamanın satır içi geçici değişken önerisini gösteren Visual Studio.](../media/inline-temporary-variable-refactoring.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Uygulamanın satır içi geçici değişken önerisini gösteren Visual Studio.](../media/vs-2022/inline-temporary-variable-refactoring.png)
   ::: moniker-end

1. Kodu **yeniden düzenlemek için Satır içi** geçici değişken'i seçin.

1. **Ctrl** F5 tuşlarına basarak + **programı yeniden çalıştırın.** Çıkış aşağıdakine benzer:

   ::: moniker range="<=vs-2019"
   ![Ad, giriş ve çıkış istemini gösteren Hata Ayıklama Konsolu penceresinin ekran görüntüsü Yılın günü: 43'.](../media/vs-2019/overview-console-final.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Ad, giriş ve çıkış istemini gösteren Hata Ayıklama Konsolu penceresinin ekran görüntüsü Yılın günü: 244'.](../media/vs-2022/overview-console-final.png)
   ::: moniker-end

## <a name="debug-code"></a>Kod hatalarını ayıklama

Kod yazarak çalıştırarak hataları test etmek gerekir. Visual Studio hata ayıklama sistemi, kodda tek tek bir deyimde adım adım ilerler ve değişkenleri ilerlerken incelemenizi sağlar. Belirli bir *satırda kodun* yürütülmesini durduran kesme noktaları ayarlayın ve kod çalıştırıken değişken değerinin nasıl değiştiklerini gözlemlersiniz.

Program çalışırken değişkenin değerini görmek `username` için bir kesme noktası ayarlayın.

1. Satırın yanındaki en sol kenar boşluğuna veya boşluka tıklayarak kod satırına bir `Console.WriteLine($"\nHello {username}!");` kesme noktası ayarlayın. Ayrıca kod satırı seçerek F9 tuşuna **da basabilirsiniz.**

   Oluk içinde kırmızı bir daire görünür ve çizgi vurgulanır.

   ::: moniker range="<=vs-2019"
   ![Bir kod satırı üzerinde kesme noktası gösteren ekran görüntüsü Visual Studio.](../media/breakpoint.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Bir kod satırı üzerinde kesme noktası gösteren ekran görüntüsü Visual Studio.](../media/vs-2022/breakpoint.png)
   ::: moniker-end

1. Hata AyıklamaYı Başlat Hata Ayıklamayı **Başlat'ı**  >  **seçerek veya** F5 tuşuna basarak **hata ayıklamayı başlat.**

1. Konsol penceresi görüntülendiğinde ve sizden bir ad sorduğunda, adınız girin.

   Odak, Visual Studio düzenleyicisine geri döner ve kesme noktası olan kod satırı sarıyla vurgulanır. Sarı vurgu, bu kod satırın daha sonra yürütülecek olduğu anlamına gelir. Kesme noktası, uygulamanın bu satırda yürütmeyi duraklatmalarını sağlar.

1. Değerini görmek için farenizi `username` değişkenin üzerine gelin. Ayrıca sağ tıklar ve İzleme Ekle'yi seçerek değişkeni İzleme penceresine ekleyebilir ve burada `username` değerini de görebilirsiniz.  

   ::: moniker range="<=vs-2019"
   ![Hata ayıklama sırasında bir değişken değerini gösteren ekran görüntüsü Visual Studio.](../media/debugging-variable-value.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   ![Hata ayıklama sırasında bir değişken değerini gösteren ekran görüntüsü Visual Studio.](../media/vs-2022/debugging-variable-value.png)
   ::: moniker-end

1. Uygulamayı **çalıştırmayı tamamlamak** için F5 tuşuna tekrar basın.

Hata ayıklamada hata ayıklama hakkında daha fazla Visual Studio bkz. [Hata Ayıklayıcı özellik turu.](../../debugger/debugger-feature-tour.md)

## <a name="customize-visual-studio"></a>Özelleştirme Visual Studio

Varsayılan renk temasını Visual Studio kullanıcı arabirimini kişiselleştirebilirsiniz. Renk temasını değiştirmek için:

::: moniker range="vs-2017"

1. Menü çubuğunda, Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** > **sayfasında** Renk teması seçimini  **Koyu olarak** ve ardından Tamam'ı **seçin.**

   IDE'nin tamamı için renk teması Koyu olarak **değişir.**

   ![Koyu temada Visual Studio gösteren ekran görüntüsü.](../media/dark-theme.png)
::: moniker-end

::: moniker range="vs-2019"

1. Menü çubuğunda, Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** > **sayfasında** Renk teması seçimini  **Koyu olarak** ve ardından Tamam'ı **seçin.**

   IDE'nin tamamı için renk teması Koyu olarak **değişir.**

   ![Koyu temada Visual Studio gösteren ekran görüntüsü.](../media/vs-2019/dark-theme.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Menü çubuğunda,  > **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

1. **Ortam** > **genel** Seçenekler sayfasında, **renk teması** seçimini **mavi** veya **hafif** olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması buna göre değişir. Aşağıdaki ekran görüntüsünde mavi tema gösterilmektedir:

   ![mavi temada Visual Studio gösteren ekran görüntüsü.](../media/vs-2022/blue-theme.png)
::: moniker-end

IDE 'yi kişiselleştirmek için kullanabileceğiniz diğer yollar hakkında bilgi edinmek için bkz. [kişiselleştirme Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).