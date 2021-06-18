---
ms.date: 05/28/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 128a09500aaa326fad717efcade9040496452963
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112361882"
---
Tümleşik Visual Studio *ortamı,* kod düzenlemek, hata ayıklamak ve derlemek ve ardından uygulama yayımlamak için kullanabileceğiniz yaratıcı bir başlatma panelidir. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılmaktadır. Çoğu IDE'nin sağlediği standart düzenleyici ve hata ayıklayıcının üzerinde Visual Studio geliştirme sürecini kolaylaştıran derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve daha birçok özellik vardır.

::: moniker range="vs-2017"

![The Visual Studio 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Temel özelliklerin ve işlevlerin Visual Studio gösteren çağrılar içeren IDE'nin ekran görüntüsü." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Bu görüntüde, Visual Studio proje ve büyük olasılıkla kullanabileceğiniz birkaç anahtar araç pencereleri olan temel pencereler yer atılır:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini,** dosyaları çözümler ve projeler olarak gruplamanıza yardımcı [olabilir.](../tutorial-projects-solutions.md)

- Büyük [olasılıkla](../../ide/writing-code-in-the-code-and-text-editor.md) zaman harcamanız gereken düzenleyici penceresi (orta), dosya içeriğini görüntüler. Burada kodu düzenleyebilir veya düğmeleri ve metin kutuları olan bir pencere gibi bir kullanıcı arabirimi tasarabilirsiniz.

::: moniker range="vs-2017"

- Çıkış [penceresi](../../ide/reference/output-window.md) (alttaki orta), hata ayıklama Visual Studio hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

- [Git Değişiklikleri](/visualstudio/version-control/) (sağ altta), Git ve GitHub gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenizi ve başka [kullanıcılarla](https://git-scm.com/) kod [paylaşmanıza olanak sağlar.](https://docs.github.com/github)

## <a name="editions"></a>Sürümler

::: moniker range="vs-2017"

Visual Studio Windows ve Mac için kullanılabilir. [Mac için Visual Studio,](/visualstudio/mac/) Visual Studio 2017 ile aynı özelliklere sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makale, Visual Studio 2017'nin Windows sürümüne odaklanır.

Üç sürüm vardır: Community Visual Studio Professional ve Enterprise. Her [sürümde Visual Studio özellikler](https://visualstudio.microsoft.com/vs/compare/) hakkında bilgi edinmek için bkz. Visual Studio sürümleri karşılaştırma.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio Windows ve Mac için kullanılabilir. [Mac için Visual Studio,](/visualstudio/mac/) Visual Studio 2019 ile aynı özelliklere sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makale, Visual Studio 2019'un Windows sürümüne odaklanır.

Visual Studio 2019'un üç sürümü vardır: Community, Professional ve Enterprise. Her [sürümde Visual Studio özellikler](https://visualstudio.microsoft.com/vs/compare/) hakkında bilgi edinmek için bkz. Visual Studio sürümleri karşılaştırma.

::: moniker-end

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Yazılım geliştirirken daha üretken Visual Studio yardımcı olacak özelliklerden bazıları şunlardır:

- Geçişler ve [Hızlı Eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, kod yazma sırasında sizi hatalara veya olası sorunlara karşı uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, derleme sırasında veya programı çalıştırarak hatanın keşfedilmalarını beklemeden sorunları hemen düzeltmeye olanak sağlar. Bir geçişin üzerine gelindiğinde hata hakkında ek bilgiler alırsınız. Hatayı düzeltmek için sol kenar boşluğunda Hızlı Eylemler olarak bilinen eylemlerle birlikte bir ampul de görünebilir.

   ![Visual Studio'da geçişler](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Kod Temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirin ve kod stili ayarlarınız [,](../../ide/reference/options-text-editor-csharp-formatting.md) [.editorconfig](../../ide/create-portable-custom-editor-options.md)kuralları ve Roslyn çözümleyicileri tarafından önerilen kod [düzeltmelerini uygulayabilirsiniz.](../../code-quality/roslyn-analyzers-overview.md) **Kod Temizleme,** kod incelemesine gitmeden önce kodundaki sorunları çözmenize yardımcı olur. (Şu anda yalnızca C# kodu için kullanılabilir.)

   ![Visual Studio'da Kod Temizleme düğmesi](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adı oluşturma, bir veya daha fazla kod satırı ayıklanan yeni bir yöntem, yöntem parametrelerinin sırası değiştirme ve daha fazlası gibi işlemleri içerir.

   ![Visual Studio'da yeniden düzenleme](../media/refactoring-menu.png)

- [ıntellisense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük kod parçaları yazan bir özellik kümesi terimidir. Bu, düzenleyicide satır içinde temel belgelere sahip olmak gibi, başka bir yerde tür bilgilerini aramadan tasarruf etmektir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için bkz. [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) [ve IntelliSense Visual Basic.](../../ide/visual-basic-specific-intellisense.md) Aşağıdaki çizimde IntelliSense'in bir tür için üye listesini nasıl görüntülesi gösterilmiştir:

   ![Visual Studio Listesi](../media/intellisense-list-members.png)

- [Visual Studio arama](../../ide/visual-studio-search.md)

   Visual Studio menüler, seçenekler ve özelliklerle bazen çok fazla zor görünebilir. Visual Studio arama (**Ctrl** Q ), IDE özelliklerini ve kodunu tek bir yerde + hızla bulmanın harika bir yoludur.

   ::: moniker range="vs-2017"

   ![Hızlı Başlat 2017'de Visual Studio kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için [bkz. Hızlı Başlat.](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019'da arama kutusu](../media/vs-2019/quick-launch-nuget.png)

    Daha fazla bilgi ve üretkenlik ipuçları için [bkz. Arama Visual Studio kullanma.](../../ide/visual-studio-search.md)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türünüz veya programlama diliniz ne olursa olsun, diğerleriyle gerçek zamanlı işbirliği yaparak düzenleme ve hata ayıklama. Projenizi anında ve güvenli bir şekilde paylaşabilir ve gerektiğinde hata ayıklama oturumları, terminal örnekleri, localhost web uygulamaları, sesli aramalar ve daha fazlası.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   Çağrı **Hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu, yöntemi değiştirmeyi veya kaldırmayı düşünürken veya bir hatayı bulmaya çalışırken yararlı olabilir.

   ![Çağrı Hiyerarşisi penceresi](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, düzenleyiciden ayrılmadan kodunuz, kodunuzdaki değişiklikler, bağlantılı hatalar, iş öğeleri, kod incelemeleri ve birim testleri ile ilgili başvuruları bulutur.

   ![CodeLens](../media/codelens-overview.png)

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma Git özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma alır.

   ![Tanıma Git](../media/go-to-definition-menu.png)

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Tanıma **Göz At** penceresi, aslında ayrı bir dosya açmadan bir yöntemin veya türün tanımını gösterir.

   ![Tanıma Göz Atma](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>IDE'Visual Studio yükleme

Bu bölümde, yeni bir proje oluşturarak bu projeyle mümkün olan en iyi şekilde Visual Studio. [IntelliSense'i](../../ide/using-intellisense.md) kodlama yardımı olarak kullanır, programın yürütülmesi sırasında değişkenin değerini görmek için uygulamada hata ayıklar ve renk temasını değiştirirsiniz.

::: moniker range="vs-2017"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirin ve sisteminize yükleyin. Modüler yükleyici, tercih ettiği programlama dili veya platform için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için](#create-a-program)yükleme sırasında .NET Core platformlar arası geliştirme iş yükünü **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirin ve sisteminize yükleyin. Modüler yükleyici, tercih ettiği programlama dili veya platform için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için](#create-a-program)yükleme sırasında .NET Core platformlar arası geliştirme iş yükünü **seçin.**

::: moniker-end

![Visual Studio Yükleyicisi'de .NET Core platformlar arası geliştirme Visual Studio Yükleyicisi](../media/dotnet-core-cross-platform-workload.png)

İlk kez Visual Studio kez oturum asanız, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızla oturum açabilirsiniz. [](../../ide/signing-in-to-visual-studio.md)

## <a name="create-a-program"></a>Program oluşturma

Şimdi basit bir program oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni **Proje'yi** >  > **seçin.**

   ![Menü > Yeni Proje dosya dosyası](../media/file-new-project-menu.png)

   Yeni **Proje iletişim** kutusunda birkaç proje şablonu *görüntülenir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Visual C# **altında .NET Core** şablon **kategorisini** seçin ve ardından Konsol Uygulaması **(.NET Core) şablonunu** seçin. Ad **metin** kutusuna **HelloWorld yazın ve** tamam **düğmesini** seçin.

   ![.NET Core uygulama şablonu](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > .NET Core kategorisini **görmüyorsanız.NET Core** platformlar arası geliştirme **iş yükünü yüklemeniz** gerekir. Bunu yapmak için, Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol alt kısmında Yer Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi sonra aşağı kaydırın ve **.NET Core** platformlar arası geliştirme iş yükünü seçin ve ardından Değiştir'i **seçin.**

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısaca, aşağıdakine benzer bir şey görüyoruz:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Uygulamanıza uygun C# kodu düzenleyici penceresinde gösterilir ve bu da yerlerin çoğunu alır. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutular içeren Visual Studio IDE](../media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![' Hello Word! ' çıkışını gösteren cmd.exe konsol penceresinin ekran görüntüsü ve ' devam etmek için herhangi bir tuşa basın '.](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Şu satırı izleyerek aşağıdaki C# kodunu ekleyin `Console.WriteLine("Hello World!");` :

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

   ![Konsol penceresi girişi](../media/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi, bir depoyu kopyalamaya, yeni bir projeyi açmaya veya yepyeni bir proje oluşturmaya yönelik çeşitli seçeneklerle birlikte görüntülenir.

1. **Yeni proje oluştur** öğesini seçin.

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 ' de ' yeni proje oluşturma ' penceresinin ekran görüntüsü.":::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Tüm **Diller** açılan listesinden **C#** ' ı, tüm **platformlar** listesinden **Windows** ' u ve **tüm proje türleri** listesinden **konsol** ' u seçerek şablon sonuçlarını daha da filtreleyebilirsiniz.

    **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' ye tıklayın.

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Visual Studio 2019 ' de, istediğiniz şablonu seçtiğiniz &quot;yeni proje oluştur&quot; penceresinin ekran görüntüsü.":::

1. **Yeni projenizi yapılandırın** penceresinde, **Proje adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınız için dizin konumunu değiştirin (varsayılan yerel ayar `C:\Users\<name>\source\repos` ) ve ardından **İleri**' ye tıklayın.

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 ' de, projenin adını girdiğiniz ' yeni projeyi yapılandırma ' penceresinin ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' in **hedef çerçeve** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' a tıklayın.

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019 ' de istediğiniz .NET Core Framework sürümünü seçtiğiniz ' ek bilgiler ' penceresinin ekran görüntüsü.":::

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu alan düzenleyici penceresinde gösterir. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutular içeren Visual Studio IDE](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![' Hello Word! ' çıkışını gösteren Microsoft Visual Studio hata ayıklama konsolu penceresinin ekran görüntüsü ve ' Bu pencereyi kapatmak için herhangi bir tuşa basın '.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Şu satırı izleyerek aşağıdaki C# kodunu ekleyin `Console.WriteLine("Hello World!");` :

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

   ![Bir ada, girişe ve ' Hello Georgette! ' çıkışına ilişkin istemi gösteren Microsoft Visual Studio hata ayıklama konsolu penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) 'in daha verimli bir şekilde kodlamasına yardımcı olması için birkaç yol göz atalım.

İlk olarak, değişkeni yeniden adlandıralım `name` :

1. `name`Seçmek için değişkene çift tıklayın.

2. Değişken için yeni adı yazın, **Kullanıcı** adı.

   Değişken etrafında gri bir kutu göründüğünü ve kenar boşluğunda ampul göründüğünü unutmayın.

::: moniker range="vs-2017"

3. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ![Visual Studio 'da yeniden adlandırma eylemi](../media/rename-quick-action.png)

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer olur.

   ![Visual Studio 'da yeniden adlandırmayı yeniden düzenlemeyi gösteren animasyonlu GIF](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ![Visual Studio 'da yeniden adlandırma eylemi](../media/vs-2019/rename-quick-action.png)

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer olur.

::: moniker-end

4. Şimdi IntelliSense 'e göz atalım. Belirten satırın altında `Console.WriteLine($"\nHello {username}!");` yazın `DateTime now = DateTime.` .

   Bir kutu, sınıfının üyelerini görüntüler <xref:System.DateTime> . Ayrıca, şu anda seçili olan üyenin açıklaması ayrı bir kutu içinde görüntülenir.

   ![Visual Studio 'da IntelliSense liste üyeleri](../media/intellisense-list-members.png)

5. Sınıfın bir özelliği olan, bu adı çift tıklayarak veya **sekme** tuşuna basarak **Şimdi** adlı üyeyi seçin. Uca noktalı virgül ekleyerek kod satırını doldurun.

6. Bunun yerine, aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırıldıktan sonra satır Sonlandırıcı eklememesi için biraz farklıdır. Diğer bir deyişle, çıktıya gönderilen sonraki metin parçası aynı satıra yazdırılır. Açıklamalarını görmek için kodunuzda bu yöntemlerin her birinin üzerine gelebilmeniz gerekir.

7. Daha sonra, yeniden düzenleme kullanarak kodu biraz daha kısa hale getirebilirsiniz. Satırdaki değişkenine tıklayın `now` `DateTime now = DateTime.Now;` .

   Bu satırdaki kenar boşluğunda küçük bir screwsürücü simgesinin göründüğünü unutmayın.

8. Visual Studio 'Nun hangi önerilerin kullanılabilir olduğunu görmek için screwdriver simgesine tıklayın. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösteriliyor:

   ![Visual Studio 'da satır içi geçici değişken yeniden düzenlemesi](../media/inline-temporary-variable-refactoring.png)

9. Kodu yeniden düzenleme için **satır içi geçici değişken** ' e tıklayın.

::: moniker range="vs-2017"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ! Bir ad, giriş ve çıkış için istemi gösteren cmd.exe konsol penceresinin ekran görüntüsü, ' Hello Georgette! Yılın günü: 151 '.] (.. /Media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ![Bir ada, girişe ve ' Hello Georgette! ' çıkışına ilişkin istemi gösteren Microsoft Visual Studio hata ayıklama konsolu penceresinin ekran görüntüsü Yılın günü: 43 '.](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio 'nun hata ayıklama sistemi, kod tek bir bildirimde bir kez ilerlemenizi ve siz yazarken değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* belirleyebilirsiniz. Bir değişken değerinin kodun çalıştırıldığı şekilde nasıl değiştiğini gözlemleyebilirsiniz ve daha fazlasını yapabilirsiniz.

`username`Programın &quot;uçuş aşamasında&quot; olduğu sırada değişkenin değerini görmek için bir kesme noktası ayarlayalım.

1. Belirten kod satırını bulun `Console.WriteLine($&quot;\nHello {username}!");` . Bu kod satırında bir kesme noktası ayarlamak için, diğer bir deyişle, programın bu satırda yürütmeyi duraklamasını sağlamak için düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırında herhangi bir yere tıklayabilir ve ardından **F9**' e basabilirsiniz.

   Sol taraftaki kenar boşluğunda kırmızı bir daire görünür ve kod kırmızı renkle vurgulanır.

   ![Visual Studio 'da kod satırında kesme noktası](../media/breakpoint.png)

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatma** veya **F5**'e basarak hata ayıklamayı başlatın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde, yazın ve **ENTER** tuşuna basın.

   Odak, Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Bu, programın yürütecektir bir sonraki kod satırı olduğunu belirtir.

1. `username`Değerini görmek için farenizi değişkenin üzerine getirin. Alternatif olarak, ' ı sağ tıklayıp, `username` sonra da değeri de görebileceğiniz **izleme** penceresine eklemek için **Gözcü Ekle** seçeneğini belirleyebilirsiniz.

   ![Visual Studio 'da hata ayıklama sırasında değişken değeri](../media/debugging-variable-value.png)

1. Programın tamamlanmasını çalışmasına izin vermek için **F5** tuşuna basın.

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcı Özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Visual Studio 'Yu özelleştirme

Visual Studio Kullanıcı arabirimini kişiselleştirmek için, varsayılan renk temasını değiştirme de dahil olmak üzere özelleştirebilirsiniz. **Koyu** temaya geçiş yapmak için:

1. Menü çubuğunda,   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

::: moniker range="vs-2017"

2. **Ortam** > **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ![Koyu temalı Visual Studio](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Ortam** > **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ![Koyu temalı Visual Studio](../media/vs-2019/dark-theme.png)

::: moniker-end

IDE 'yi kişiselleştirmek için kullanabileceğiniz diğer yollar hakkında bilgi edinmek için bkz. [Visual Studio 'Yu kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).