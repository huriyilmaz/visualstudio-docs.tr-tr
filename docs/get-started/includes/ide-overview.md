---
ms.date: 09/22/2020
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: fbbd2278a59197601afe02e777e89245fc6bb421
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2020
ms.locfileid: "97844769"
---
Visual Studio *Tümleşik geliştirme ortamı* , kod düzenlemek, hatalarını ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma paneliyle bulunur. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen özellik açısından zengin bir programdır. En çok kullanılan standart düzenleyici ve hata ayıklayıcı üzerinde ve üzerinde, Visual Studio, yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve çok daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![Visual Studio 2019 IDE](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Bu resimde, büyük olasılıkla kullanabileceğiniz bir açık proje ve birkaç anahtar araç penceresi içeren Visual Studio gösterilmektedir:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](../tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Bu, kodu düzenleyebileceğiniz veya düğmeler ve metin kutuları içeren pencere gibi bir kullanıcı arabirimi tasarlayabileceğiniz yerdir.

::: moniker range="vs-2017"

- [Çıkış penceresi](../../ide/reference/output-window.md) (alt orta), Visual Studio 'nun hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

::: moniker range="vs-2017"

Visual Studio, Windows ve Mac için kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2017 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede, Visual Studio 2017 ' nin Windows sürümü ele alınmaktadır.

Visual Studio 'nun üç sürümü vardır: Community, Professional ve Enterprise. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

::: moniker range="vs-2019"

Visual Studio, Windows ve Mac için kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2019 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede, Visual Studio 2019 ' nin Windows sürümü ele alınmaktadır.

Visual Studio 2019: Community, Professional ve Enterprise 'ın üç sürümü vardır. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio sürümlerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio 'da, yazılım geliştirirken daha üretken olmanıza yardımcı olan popüler özelliklerden bazıları şunlardır:

- Dalgalı çizgiler ve [hızlı eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, hata oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları anında çözmenizi sağlar. Dalgalı bir çizgi üzerine geldiğinizde, hatayla ilgili ek bilgileri görürsünüz. Ayrıca, bir ampulü, hızlı eylemler olarak bilinen eylemlerle birlikte, hatayı düzelrebilir.

   ![Visual Studio 'da dalgalı çizgiler](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Kod temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirin ve [kod stili ayarlarınız](../../ide/reference/options-text-editor-csharp-formatting.md), [. Editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve [Roslyn çözümleyiciler](../../code-quality/roslyn-analyzers-overview.md)tarafından önerilen tüm kod düzeltmelerini uygulayın. Kod **Temizleme** , kod incelemeye geçmeden önce kodunuzda sorunları çözmenize yardımcı olur. (Şu anda yalnızca C# kodu için kullanılabilir.)

   ![Visual Studio 'da kod temizleme düğmesi](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adlandırılması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemleri içerir.

   ![Visual Studio'da yeniden düzenleme](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen özellikler kümesi için bir terimdir ve bazı durumlarda, sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu da tür bilgilerini başka bir yerde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir. Daha fazla bilgi için bkz. [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)ve [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ![Visual Studio üye listesi](../media/intellisense-list-members.png)

- [Visual Studio arama](../../ide/visual-studio-search.md)

   Visual Studio çok sayıda menü, seçenek ve özellik ile zaman içinde yoğun görünebilir. Visual Studio arama (**CTRL** + **Q**), IDE özelliklerini ve kodu tek bir yerde hızlı bir şekilde bulmanın harika bir yoludur.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 'de Hızlı Başlat arama kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için bkz. [Hızlı başlatma](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 'de arama kutusu](../media/vs-2019/quick-launch-nuget.png)

    Bilgi ve üretkenlik ipuçları için bkz. [Visual Studio aramasını kullanma](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türü veya programlama diliniz ne olursa olsun, başkalarıyla birlikte düzenleme ve hata ayıklama işlemlerini gerçek zamanlı olarak yapın. Projenizi anında ve güvenli bir şekilde paylaşabilir, gerekirse hata ayıklama oturumları, Terminal örnekleri, localhost Web Apps, sesli çağrılar ve daha fazlasını yapabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu, yöntemi değiştirme veya kaldırma hakkında düşündüğünde veya bir hatayı izlemeye çalışırken yararlı bilgiler olabilir.

   ![Çağrı hiyerarşisi penceresi](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuzun başvurularını, kodunuzda yaptığınız değişiklikleri, bağlantılı hataları, iş öğelerini, kod incelemelerinizi ve birim testlerini, Düzenleyiciden çıkmadan bulmanıza yardımcı olur.

   ![CodeLens](../media/codelens-overview.png)

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma Git özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür.

   ![Tanıma Git](../media/go-to-definition-menu.png)

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Özet **tanım** penceresi, aslında ayrı bir dosya açmadan bir yöntemin veya türün tanımını gösterir.

   ![Tanıma göz at](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE 'yi yükler

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanacaksınız, programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamanın hatalarını ayıkladığınızda ve renk temasını değiştireceksiniz.

::: moniker range="vs-2017"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

![Visual Studio Yükleyicisi 'de .NET Core platformlar arası geliştirme iş yükü](../media/dotnet-core-cross-platform-workload.png)

Visual Studio 'Yu ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="create-a-program"></a>Program oluşturma

Şimdi bir basit program oluşturalım.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda **Dosya** > **Yeni** > **Proje**' yi seçin.

   ![Dosya > menü çubuğunda yeni proje](../media/file-new-project-menu.png)

   **Yeni proje** iletişim kutusunda çeşitli proje *şablonları* gösterilmektedir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. **Visual C#** altında **.NET Core** şablon kategorisini seçin ve **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna **HelloWorld** yazın ve **Tamam** düğmesini seçin.

   ![.NET Core uygulama şablonu](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. Bunu yapmak için, **Yeni proje** iletişim kutusunun sol alt kısmındaki **Aç Visual Studio yükleyicisi** bağlantısını seçin. Visual Studio Yükleyicisi açıldıktan sonra, aşağı kaydırarak **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Uygulamanızın C# kodu, alanın çoğunu alan düzenleyici penceresinde gösterir. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

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

   ![Visual Studio başlangıç penceresi yeni bir proje oluştur](../media/vs-2019/start-window-create-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. **Dil** açılan listesinden **C#** ' u seçerek şablon sonuçlarını daha da filtreleyebilirsiniz. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

    ![Visual Studio 'da yeni proje oluşturma](../media/vs-2019/create-new-project.png)

1. **Yeni projenizi yapılandırın** penceresinde, **Proje adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınızın dizin konumunu değiştirin ve ardından **Oluştur**' u seçin.

   ![Visual Studio 'da yeni proje yapılandırma](../media/vs-2019/configure-new-project.png)

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

## <a name="debug-code"></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio 'nun hata ayıklama sistemi, kod tek bir bildirimde bir kez ilerlemenizi ve siz yazarken değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* belirleyebilirsiniz. Bir değişken değerinin kodun çalıştırıldığı şekilde nasıl değiştiğini gözlemleyebilirsiniz ve daha fazlasını yapabilirsiniz.

`username`Programın "uçuş aşamasında" olduğu sırada değişkenin değerini görmek için bir kesme noktası ayarlayalım.

1. Belirten kod satırını bulun `Console.WriteLine($"\nHello {username}!");` . Bu kod satırında bir kesme noktası ayarlamak için, diğer bir deyişle, programın bu satırda yürütmeyi duraklamasını sağlamak için düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırında herhangi bir yere tıklayabilir ve ardından **F9**' e basabilirsiniz.

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