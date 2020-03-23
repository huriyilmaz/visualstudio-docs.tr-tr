---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: c6e715602d0157f52109d7d0bedf25fbd25a23a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79082068"
---
Visual Studio *tümleşik geliştirme ortamı,* kodu düzenlemek, hata ayıklamak ve oluşturmak ve ardından bir uygulamayı yayımlamak için kullanabileceğiniz yaratıcı bir başlatma rampasıdır. Entegre geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen zengin özelliklere sahip bir programdır. Çoğu IDA'nın sağladığı standart düzenleyici ve hata ayıklayıcının üzerinde ve üzerinde, Visual Studio yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve daha birçok özellik içerir.

::: moniker range="vs-2017"

![Görsel Stüdyo 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![Görsel Stüdyo 2019 IDE](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Bu resim, Visual Studio'da açık bir proje ve büyük olasılıkla kullanacağınız birkaç anahtar araç penceresi ile gösterilmektedir:

- [Solution Explorer](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üstte), kod dosyalarınızı görüntülemenizi, gezinmenizi ve yönetmenize olanak tanır. **Solution Explorer,** dosyaları [çözüm ve projelere](../tutorial-projects-solutions.md)gruplandırma yaparak kodunuzu düzenlemenize yardımcı olabilir.

- Zamanınızın büyük kısmını harcayacağınız [düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (merkez), dosya içeriğini görüntüler. Burada kod düzenleme veya düğmeleri ve metin kutuları ile bir pencere gibi bir kullanıcı arabirimi tasarımı.

::: moniker range="vs-2017"

- [Çıktı penceresi](../../ide/reference/output-window.md) (alt orta) Visual Studio'nun hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durum iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ altta), [Git](https://git-scm.com/) ve [Team Foundation Sürüm Denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts)gibi sürüm denetim teknolojilerini kullanarak iş öğelerini izlemenizi ve kodu başkalarıyla paylaşmanızı sağlar.

## <a name="editions"></a>Sürümler

::: moniker range="vs-2017"

Visual Studio, Windows ve Mac için kullanılabilir. [Visual Studio for Mac,](/visualstudio/mac/) Visual Studio 2017 ile aynı özelliklere sahiptir ve çapraz platform ve mobil uygulamalar geliştirmek için optimize edilmiştir. Bu makale, Visual Studio 2017'nin Windows sürümüne odaklanılır.

Visual Studio'nun üç sürümü vardır: Topluluk, Profesyonel ve Kurumsal. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için [Visual Studio sürümlerini karşılaştırın'](https://visualstudio.microsoft.com/vs/compare/) a bakın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio, Windows ve Mac için kullanılabilir. [Visual Studio for Mac,](/visualstudio/mac/) Visual Studio 2019 ile aynı özelliklere sahiptir ve çapraz platform ve mobil uygulamalar geliştirmek için optimize edilmiştir. Bu makale, Visual Studio 2019'un Windows sürümüne odaklanılır.

Visual Studio 2019'un üç sürümü vardır: Topluluk, Profesyonel ve Kurumsal. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için [Visual Studio sürümlerini karşılaştırın'](https://visualstudio.microsoft.com/vs/compare/) a bakın.

::: moniker-end

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio'da yazılım geliştirdikçe daha üretken olmanıza yardımcı olan popüler özelliklerden bazıları şunlardır:

- Squiggles ve [Hızlı Eylemler](../../ide/quick-actions.md)

   Dalgalı dalgalı, yazarken kodunuzda ki hatalara veya olası sorunlara karşı sizi uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları hemen çözmenizi sağlar. Bir dalgalı üzerinde gezinirseniz, hata hakkında ek bilgiler görürsünüz. Bir ampul de hataları düzeltmek için, Hızlı Eylemler olarak bilinen eylemleri ile sol kenar boşluğunda görünebilir.

   ![Görsel Stüdyo'da Squiggles](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Kod Temizleme

   Bir düğmeyi tıklatarak, kodunuzu biçimlendirin ve [kod stili ayarlarınız](../../ide/reference/options-text-editor-csharp-formatting.md), [.editorconfig kurallarınız](../../ide/create-portable-custom-editor-options.md)ve [Roslyn çözümleyicileriniz](../../code-quality/roslyn-analyzers-overview.md)tarafından önerilen kod düzeltmelerini uygulayın. **Kod Temizleme,** kod incelemesine gitmeden önce kodunızdaki sorunları çözmenize yardımcı olur. (Şu anda yalnızca C# kodu için kullanılabilir.)

   ![Visual Studio'da Kod Temizleme düğmesi](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adlandırma, bir veya daha fazla kod satırının yeni bir yönteme ayıklanması, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemleri içerir.

   ![Visual Studio'da yeniden düzenleme](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, kodunuz hakkındaki bilgileri doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük kod bitleri yazan bir dizi özellik için bir terimdir. Bu, editörde temel belgelerin sıralı olması gibi bir şey, bu da sizi yazı bilgilerini başka bir yerde aramaktan kurtarır. IntelliSense özellikleri dile göre değişir. Daha fazla bilgi [için, C # IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md), ve [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md)bakın. Aşağıdaki resimde, IntelliSense'in bir tür için üye listesini nasıl görüntülenebilmektedir:

   ![Visual Studio Üye Listesi](../media/intellisense-list-members.png)

- Arama kutusu

   Visual Studio bu kadar çok menü, seçenek ve özellikleri ile zaman zaman ezici görünebilir. Arama kutusu hızla Visual Studio ne ihtiyacınız bulmak için harika bir yoldur. Aradığınız bir şeyin adını yazmaya başladığınızda, Visual Studio sizi tam olarak gitmeniz gereken yere götürecek sonuçları listeler. Visual Studio'ya işlevsellik eklemeniz gerekirse, örneğin ek bir programlama dili için destek eklemek için arama kutusu, visual studio yük leyicisini iş yükü veya tek tek bir bileşen yüklemek için açan sonuçlar sağlar.

   > [!TIP]
   > Arama kutusuna kısayol olarak **Ctrl**+**Q** tuşuna basın.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017'de Hızlı Başlat arama kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için [Hızlı Başlatma'ya](../../ide/reference/quick-launch-environment-options-dialog-box.md)bakın.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019'da arama kutusu](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türünüz veya programlama diliniz ne olursa olsun, gerçek zamanlı olarak başkalarıyla işbirliği içinde edin ve hata ayıklanın. Projenizi anında ve güvenli bir şekilde paylaşabilir ve gerektiğinde hata ayıklama oturumlarını, terminal örneklerini, localhost web uygulamalarını, sesli aramaları ve daha fazlasını yapabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı Hiyerarşisi** penceresi, seçili yöntemi çağıran yöntemleri gösterir. Bu, yöntemi değiştirmeyi veya kaldırmayı düşündüğünüzde veya bir hatayı izlemeye çalışırken yararlı bilgiler olabilir.

   ![Çağrı Hiyerarşisi penceresi](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuzda yapılan başvuruları, kodunuzdaki değişiklikleri, bağlantılı hataları, iş öğelerini, kod incelemelerini ve birim testlerini editörden ayrılmadan bulmanıza yardımcı olur.

   ![CodeLens](../media/codelens-overview.png)

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma Git özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür.

   ![Tanıma Git](../media/go-to-definition-menu.png)

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Peek Tanımı** penceresi, ayrı bir dosyayı açmadan bir yöntemin veya türün tanımını gösterir.

   ![Tanımına Göz at](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE'yi yükleyin

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. [IntelliSense'i](../../ide/using-intellisense.md) kodlama yardımı olarak kullanır, programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamayı hata ayıklama ve renk temasını değiştirin.

::: moniker range="vs-2017"

Başlamak için [Visual Studio'ya indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini*seçmenize ve yüklemenize olanak tanır. [Program oluşturma](#create-a-program)adımlarını izlemek için yükleme sırasında **.NET Core çapraz platform geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Başlamak için [Visual Studio'ya indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini*seçmenize ve yüklemenize olanak tanır. [Program oluşturma](#create-a-program)adımlarını izlemek için yükleme sırasında **.NET Core çapraz platform geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

![.NET Core çapraz platform geliştirme iş yükü Visual Studio Installer](../media/dotnet-core-cross-platform-workload.png)

Visual Studio'yu ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabınızı veya iş veya okul hesabınızı kullanarak [oturum açabilirsiniz.](../../ide/signing-in-to-visual-studio.md)

## <a name="create-a-program"></a>Program oluşturma

Hadi dalıp basit bir program oluşturalım.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda **Yeni** > **Proje** **yi seçin.** >

   ![Menü çubuğunda Dosya > Yeni Proje](../media/file-new-project-menu.png)

   **Yeni Proje** iletişim kutusu birkaç proje *şablonu*gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. **Visual C#** altında **.NET Core** şablonu kategorisini seçin ve ardından **Konsol Uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusunda **HelloWorld**yazın ve ardından **Tamam** düğmesini seçin.

   ![.NET Core uygulama şablonu](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız, **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. Bunu yapmak için, **Yeni Proje** iletişim kutusunun sol alt kısmındaki Open Visual **Studio Installer** bağlantısını seçin. Visual Studio Installer açıldıktan sonra aşağı kaydırın ve **.NET Core çapraz platform geliştirme iş** yükünü seçin ve sonra **Değiştir'i**seçin.

   Visual Studio projeyi oluşturur. Bu gerçek dize görüntülemek için <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntem çağıran basit bir "Merhaba Dünya" uygulaması "Merhaba Dünya!" konsol (program çıktısı) penceresinde.

   Kısa bir süre içinde, aşağıdaki gibi bir şey görmeniz gerekir:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu kaplayan düzenleyici penceresinde gösterir. Metnin, anahtar kelimeler ve türler gibi kodun farklı bölümlerini belirtmek için otomatik olarak renklendirilmiş olduğuna dikkat edin. Ayrıca, koddaki küçük, dikey kesik çizgiler hangi ayraçların birbiriyle eşleşip kodu bulmanıza yardımcı olduğunu gösterir. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretleri seçebilirsiniz. Bu kod anahat özelliği, ihtiyacınız olmayan kodları gizlemenize olanak tanır ve ekrandaki dağınıklığı en aza indirmenize yardımcı olur. Proje dosyaları **Çözüm Gezgini**adlı bir pencerede sağ tarafta listelenir.

   ![Kırmızı kutulu Visual Studio IDE](../media/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de mevcuttur, ancak şimdilik devam edelim.

1. Şimdi, uygulamayı başlatın. Bunu, menü çubuğundaki **Hata Ayıklama** **menüsünden Hata Ayıklama olmadan Başlat'ı** seçerek yapabilirsiniz. **Ctrl**+**F5**tuşuna da basabilirsiniz.

   ![Hata ayıklama > Hata ayıklama menüsü olmadan başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve merhaba dünya mesajı ile bir konsol penceresi **açılır!**. Artık çalışan bir uygulamanız var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizdeki herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Aşağıdaki C# kodunu aşağıdaki satırdan `Console.WriteLine("Hello World!");`önce ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, **adınız nedir?** konsol penceresinde görüntülenir ve kullanıcı nın bazı metni girmesini ve ardından **Enter** tuşu'nu girmesini bekler.

1. Aşağıdaki koda `Console.WriteLine("Hello World!");` yazan satırı değiştirin:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **Hata Ayıklama** > olmadan Hata **Ayıklama Başlat'ı** seçerek veya **Ctrl**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden yeniden inşa eder ve bir konsol penceresi açılır ve adınız için sizi ister.

1. Konsol penceresine adınızı girin ve **Enter**tuşuna basın.

   ![Konsol penceresi girişi](../media/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

   Başlangıç penceresi, repo klonlamak, yeni bir proje açmak veya yepyeni bir proje oluşturmak için çeşitli seçeneklerle görüntülenir.

1. **Yeni bir proje oluştur'u**seçin.

   ![Visual Studio başlangıç penceresi yeni bir proje oluşturmak](../media/vs-2019/start-window-create-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birkaç proje *şablonu*gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.net çekirdek konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar kelimelere göre otomatik olarak filtrelenir. **Dil** açılır listesinden **C#** seçerek şablon sonuçlarını daha da filtreleyebilirsiniz. Konsol **Uygulaması (.NET Core)** şablonunu seçin ve sonra **İleri'yi**seçin.

    ![Visual Studio'da yeni bir proje oluşturun](../media/vs-2019/create-new-project.png)

1. Yeni **proje pencerenizi Yapılandır'** da, **Proje ad** kutusuna **HelloWorld** girin, proje dosyalarınızın dizin konumunu isteğe bağlı olarak değiştirin ve ardından **Oluştur'u**seçin.

   ![Visual Studio'da yeni projeyi yapılandır](../media/vs-2019/configure-new-project.png)

   Visual Studio projeyi oluşturur. Bu gerçek dize görüntülemek için <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntem çağıran basit bir "Merhaba Dünya" uygulaması "Merhaba Dünya!" konsol (program çıktısı) penceresinde.

   Kısa bir süre içinde, aşağıdaki gibi bir şey görmeniz gerekir:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu kaplayan düzenleyici penceresinde gösterir. Metnin, anahtar kelimeler ve türler gibi kodun farklı bölümlerini belirtmek için otomatik olarak renklendirilmiş olduğuna dikkat edin. Ayrıca, koddaki küçük, dikey kesik çizgiler hangi ayraçların birbiriyle eşleşip kodu bulmanıza yardımcı olduğunu gösterir. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretleri seçebilirsiniz. Bu kod anahat özelliği, ihtiyacınız olmayan kodları gizlemenize olanak tanır ve ekrandaki dağınıklığı en aza indirmenize yardımcı olur. Proje dosyaları **Çözüm Gezgini**adlı bir pencerede sağ tarafta listelenir.

   ![Kırmızı kutulu Visual Studio IDE](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de mevcuttur, ancak şimdilik devam edelim.

1. Şimdi, uygulamayı başlatın. Bunu, menü çubuğundaki **Hata Ayıklama** **menüsünden Hata Ayıklama olmadan Başlat'ı** seçerek yapabilirsiniz. **Ctrl**+**F5**tuşuna da basabilirsiniz.

   ![Hata ayıklama > Hata ayıklama menüsü olmadan başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve merhaba dünya mesajı ile bir konsol penceresi **açılır!**. Artık çalışan bir uygulamanız var!

   ![Konsol penceresi](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizdeki herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Aşağıdaki C# kodunu aşağıdaki satırdan `Console.WriteLine("Hello World!");`önce ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, **adınız nedir?** konsol penceresinde görüntülenir ve kullanıcı nın bazı metni girmesini ve ardından **Enter** tuşu'nu girmesini bekler.

1. Aşağıdaki koda `Console.WriteLine("Hello World!");` yazan satırı değiştirin:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **Hata Ayıklama** > olmadan Hata **Ayıklama Başlat'ı** seçerek veya **Ctrl**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden yeniden inşa eder ve bir konsol penceresi açılır ve adınız için sizi ister.

1. Konsol penceresine adınızı girin ve **Enter**tuşuna basın.

   ![Konsol penceresi](../media/vs-2019/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Refactoring ve IntelliSense'i kullanın

[Refactoring](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense'in](../../ide/using-intellisense.md) daha verimli bir şekilde kod lamanıza yardımcı olabileceği birkaç yönteme bakalım.

İlk olarak, değişkeni `name` yeniden adlandıralım:

1. Seçmek için `name` değişkeni çift tıklatın.

2. Değişkenin yeni adını yazın, **kullanıcı adı.**

   Değişkenin çevresinde gri bir kutunun ve kenar boşluğunda bir ampulün göründüğüne dikkat edin.

::: moniker range="vs-2017"

3. Kullanılabilir [Hızlı Eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. **'Kullanıcı adı' olarak 'ad' olarak yeniden adlandır'ı**seçin.

   ![Visual Studio'da aksiyonu yeniden adlandırın](../media/rename-quick-action.png)

   Değişken proje genelinde yeniden adlandırılmıştır, bizim durumumuzda sadece iki yer dir.

   ![Visual Studio'da yeniden adlandırmayı gösteren animasyonlu gif](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Kullanılabilir [Hızlı Eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. **'Kullanıcı adı' olarak 'ad' olarak yeniden adlandır'ı**seçin.

   ![Visual Studio'da aksiyonu yeniden adlandırın](../media/vs-2019/rename-quick-action.png)

   Değişken proje genelinde yeniden adlandırılmıştır, bizim durumumuzda sadece iki yer dir.

::: moniker-end

4. Şimdi IntelliSense bir göz atalım. " yazın `DateTime now = DateTime.`yazan `Console.WriteLine($"\nHello {username}!");`satırın altında.

   Bir kutu <xref:System.DateTime> sınıfın üyelerini görüntüler. Buna ek olarak, şu anda seçili üyenin açıklaması ayrı bir kutuda görüntülenir.

   ![Visual Studio'daki IntelliSense liste üyeleri](../media/intellisense-list-members.png)

5. Sınıfın bir özelliği olan **Şimdi**adlı üyeyi, üzerine çift tıklayarak veya **Sekme**tuşuna basarak seçin. Sonuna bir yarı-iki nokta nokta ekleyerek kod satırını tamamlayın.

6. Bunun altında, aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType>yazdırdıktan sonra <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> bir satır sonlandırıcı eklememesi açısından biraz farklıdır. Bu, çıktıya gönderilen bir sonraki metin parçasının aynı satırda yazdırılacAcağı anlamına gelir. Açıklamalarını görmek için bu yöntemlerin her birinin üzerinde gezinebilirsiniz.

7. Daha sonra, kodu biraz daha kısa yapmak için yeniden yeniden düzenleme yi kullanacağız. Satırdaki `now` `DateTime now = DateTime.Now;`değişkene tıklayın.

   Bu satırın kenar boşluğunda küçük bir tornavida simgesinin göründüğüne dikkat edin.

8. Visual Studio'nun hangi önerileri olduğunu görmek için tornavida simgesini tıklatın. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [Satır Altı geçici değişken](../../ide/reference/inline-temporary-variable.md) refactoring'i gösterir:

   ![Visual Studio'da satır satırlı geçici değişken refactoring](../media/inline-temporary-variable-refactoring.png)

9. Kodu yeniden düzenlemek için **Satır Satırlı geçici değişkeni** tıklatın.

::: moniker range="vs-2017"

10. **Ctrl**+**F5**tuşuna basarak programı yeniden çalıştırın. Çıktı şuna benzer:

    ![Program çıktılı konsol penceresi](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **Ctrl**+**F5**tuşuna basarak programı yeniden çalıştırın. Çıktı şuna benzer:

    ![Program çıktılı konsol penceresi](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Hata ayıklama kodu

Kod yazarken, çalıştırmak ve hataları için test etmek gerekir. Visual Studio'nun hata ayıklama sistemi, her seferinde bir ekibe kod geçmenizi ve değişkenleri incelerken incelemenizi sağlar. Belirli bir satırda kodun yürütülmesini durduran *kesme noktaları* ayarlayabilirsiniz. Kod çalışırken bir değişkenin değerinin nasıl değiştiğini ve daha fazlasını gözlemleyebilirsiniz.

Program "uçuşta" iken `username` değişkenin değerini görmek için bir kesme noktası ayarlayalım.

1. Yazan `Console.WriteLine($"\nHello {username}!");`kod satırını bulun. Bu kod satırında bir kesme noktası ayarlamak için, diğer bir deyişle, programın bu satırda yürütmeyi duraklatmasını sağlamak için, düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırında herhangi bir yere tıklayıp **F9**tuşuna basabilirsiniz.

   En sol kenar boşluğunda kırmızı bir daire görüntülenir ve kod kırmızı yla vurgulanır.

   ![Visual Studio'da kod satırında kırılma noktası](../media/breakpoint.png)

1. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** seçerek veya **F5**tuşuna basarak hata ayıklamaya başlayın.

1. Konsol penceresi görüntülendiğinde ve adınızı sorduğunda, yazın ve **Enter**tuşuna basın.

   Odak Visual Studio kod düzenleyicisine döner ve kesme noktası ile kod satırı sarı ile vurgulanır. Bu, programın yürüteceği bir sonraki kod satırı olduğunu belirtir.

1. Değerini görmek için `username` farenizi değişkenin üzerine doğru kullanın. Alternatif olarak, değişkeni `username` **Saat** penceresine eklemek için Saat **Ekle'ye** sağ tıklayıp saat değerini de görebilirsiniz seçeneğini belirleyebilirsiniz.

   ![Visual Studio'da hata ayıklama sırasında değişken değer](../media/debugging-variable-value.png)

1. Programın tamamlanması için çalışmasını sağlamak için **f5** tuşuna yeniden basın.

Visual Studio'da hata ayıklama hakkında daha fazla bilgi almak için [Debugger özellik turuna](../../debugger/debugger-feature-tour.md)bakın.

## <a name="customize-visual-studio"></a>Görsel Stüdyo'u Özelleştir

Varsayılan renk tesini değiştirmek de dahil olmak üzere Visual Studio kullanıcı arabirimini kişiselleştirebilirsiniz. **Karanlık** temaya değiştirmek için:

1. Menü çubuğunda, **Seçenekler** iletişim kutusunu açmak için **Araçlar** > **Seçenekleri'ni** seçin.

::: moniker range="vs-2017"

2. **Çevre** > **Genel** seçenekleri sayfasında, **Renk teması** seçimini **Koyu**olarak değiştirin ve ardından **Tamam'ı**seçin.

   Tüm IDE'nin renk teması **Koyu'ya**dönüşür.

   ![Karanlık temagörsel stüdyo](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Çevre** > **Genel** seçenekleri sayfasında, **Renk teması** seçimini **Koyu**olarak değiştirin ve ardından **Tamam'ı**seçin.

   Tüm IDE'nin renk teması **Koyu'ya**dönüşür.

   ![Karanlık temagörsel stüdyo](../media/vs-2019/dark-theme.png)

::: moniker-end

IDE'yi kişiselleştirebileceğiniz diğer yollar hakkında bilgi edinmek için [Visual Studio'yu Kişiselleştir'e](../../ide/personalizing-the-visual-studio-ide.md)bakın.