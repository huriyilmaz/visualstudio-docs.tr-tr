---
title: Visual Basic geliştiricilere genel bakış
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5cf5f8d3660abcf941eb5cc429b8f190459d9c56
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596053"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Visual Studio IDE 'ye hoş geldiniz | Visual Basic

Visual Studio *tümleşik geliştirme ortamı* bir yaratıcı launching düzenleme, hata ayıklama ve kod oluşturmak için kullanın ve ardından bir uygulama yayımlama takımdır. Bir tümleşik geliştirme ortamı (IDE) birçok yönüyle yazılım geliştirme için kullanılabilen zengin bir programdır. Standart Düzenleyici ve hata ayıklayıcı sağladığımız çoğu IDE'ler sağlamanızı, Visual Studio yazılım geliştirme işlemini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Visual Studio 2019 IDE ![](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Bu görüntü, büyük olasılıkla kullanacağınız birkaç anahtar araç pencereleri ve bir Proje Aç ile Visual Studio gösterir:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** dosyalarına gruplandırarak kodunuzu düzenleme şeklinizdir yardımcı olabilecek [çözümler ve projeler](tutorial-projects-solutions.md).

- [Düzenleyicisi penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (Merkezi), büyük olasılıkla, zamanınızın çoğunu geçireceksiniz burada dosya içeriğini görüntüler. Burada kodunu düzenleyin veya düğme ve metin kutusu içeren bir pencere gibi bir kullanıcı arabirimi tasarım budur.

- [Çıkış penceresine](../../ide/reference/output-window.md) (alt Merkezi), burada Visual Studio hata ayıklama ve hata iletileri, derleyici uyarılarını, yayımlama durum iletilerini ve diğer bildirimleri gönderir. Her ileti kaynağı kendi sekmesi vardır.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ alt) sağlar, iş öğelerini izlemek ve kod başkalarıyla paylaşmak gibi sürüm denetimi teknolojileri kullanarak [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Sürümler

Windows ve Mac için Visual Studio kullanılabilir [Mac için Visual Studio](/visualstudio/mac/) birçok Visual Studio 2017 aynı özelliklere sahiptir ve platformlar arası ve mobil uygulamalarını geliştirmek için optimize edilmiştir. Bu makalede Visual Studio 2017'in Windows sürümünde odaklanır.

Visual Studio 2017'in üç sürüm bulunur: Community, Professional ve Enterprise. Bkz: [Visual Studio 2017 IDE'lerini karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) her iki sürümünde desteklenen hangi özellikler hakkında bilgi edinmek için.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio yazılım geliştirme sırasında daha üretken olmanıza yardımcı olan popüler özelliklerinden bazıları şunlardır:

- Dalgalı çizgiler ve [hızlı Eylemler](../../ide/quick-actions.md)

   Siz yazarken, hatalar veya kodunuzdaki olası sorunlar için uyarı dalgalı alt çizgiler dalgalı çizgiler var. Bu görsel ipuçları hata derleme sırasında veya programı çalıştırdığınızda bulunmak beklenmeden hemen sorunları düzeltmek etkinleştirin. Bir dalgalı çizgi gelin, hatayla ilgili ek bilgileri görürsünüz. Hatayı düzeltmek için hızlı Eylemler bilinen eylemlerle sol kenar boşluğunda bir ampul de görünebilir.

   ::: moniker range="vs-2017"

   ![Visual Studio'da dalgalı çizgiler](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio'da dalgalı çizgiler](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, bir veya daha fazla kod satırlarını yöntem parametreleri ve daha fazlasını sırasını değiştirerek yeni bir yönteme ayıklama değişkenlerin akıllı yeniden adlandırma gibi işlemleri içerir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da yeniden düzenleme menüsü](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da yeniden düzenleme menüsü](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, doğrudan düzenleyicide kod hakkında bilgi görüntüler ve bazı durumlarda, küçük kod parçalarını sizin için yazma özellikleri kümesi için kullanılan bir terimdir. Bu temel belgeleri satır içi başka bir yerde türü bilgi aramak zorunda kalmaktan kurtarır düzenleyicisinde gibidir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md), ve [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense üye listesi bir türü için nasıl görüntülediğini gösterir:

   ::: moniker range="vs-2017"

   ![Visual Studio üye listesi](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio üye listesi](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Arama kutusu

   Visual Studio zamanlarda sürü menüleri, seçenekleri ve özellikleri ile zor görünebilir. Arama kutusu, Visual Studio 'da gerekenleri hızlı bir şekilde bulmanın harika bir yoludur. Aradığınız bir şey adını yazmaya başladığınızda, Visual Studio tam olarak gitmek gerek duyduğunuz aldığınız sonuçları listeler. Visual Studio 'ya işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek istiyorsanız, arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   > [!TIP]
   > Arama kutusunun bir kısayolu olarak **Ctrl**+**Q** tuşuna basın.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 'de Hızlı Başlat arama kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için bkz. [Hızlı başlatma](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 'de arama kutusu](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türü veya programlama diliniz ne olursa olsun, başkalarıyla birlikte düzenleme ve hata ayıklama işlemlerini gerçek zamanlı olarak yapın. Projenizi anında ve güvenli bir şekilde paylaşabilir, gerekirse hata ayıklama oturumları, Terminal örnekleri, localhost Web Apps, sesli çağrılar ve daha fazlasını yapabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi seçili bir yöntemi çağıran yöntemleri gösterir. Bu, değiştirme veya kaldırma yöntemi düşündüğünüzü yararlı bilgiler olması veya bir hatayı izlemek çalışırken oluşturabilirsiniz.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da çağrı hiyerarşisi penceresi](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da çağrı hiyerarşisi penceresi](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuz için başvurular bulmanıza yardımcı olur, düzenleyiciden çıkmadan, kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testleri değiştirir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da CodeLens](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da CodeLens](media/vs-2019/codelens.png)

   ::: moniker-end

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma özelliği, doğrudan bir işlev veya tür tanımlandığı konumuna götürür.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 ' de tanıma git](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de tanıma git](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Tanıma göz at](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   **Özet tanım** penceresi, ayrı bir dosyayı açmaya gerek kalmadan bir yöntem veya tür tanımı gösterir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da açıklama Özeti](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da açıklama Özeti](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE yükleyin

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. Renk temasını değiştirecek, [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanacaksınız ve programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamanın hatalarını ayıklayacaksınız.

::: moniker range="vs-2017"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici seçin ve yüklemek sağlayan *iş yükleri*, programlama dili veya tercih ettiğiniz platform için gerekli özellikler grupları olduğu. İçin adımları [bir program oluşturma](#create-a-program), seçtiğinizden emin olun **.NET Core çoklu platform geliştirme** yüklemesi sırasında iş yükü.

::: moniker-end

::: moniker range=">=vs-2019"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici seçin ve yüklemek sağlayan *iş yükleri*, programlama dili veya tercih ettiğiniz platform için gerekli özellikler grupları olduğu. İçin adımları [bir program oluşturma](#create-a-program), seçtiğinizden emin olun **.NET Core çoklu platform geliştirme** yüklemesi sırasında iş yükü.

::: moniker-end

![.NET core çoklu platform geliştirme iş yükünü Visual Studio yükleyicisi](../media/dotnet-core-cross-platform-workload.png)

Visual Studio 'Yu ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="customize-visual-studio"></a>Visual Studio'yu özelleştirme

Varsayılan renk temasını değiştirme dahil olmak üzere Visual Studio kullanıcı arabirimi kişiselleştirebilirsiniz.

### <a name="change-the-color-theme"></a>Renk temasını değiştirme

Değiştirilecek **koyu** teması:

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.

   ![Visual Studio 2019 ' de başlangıç penceresi](media/vs-2019/continue-without-code.png)

   IDE açılır.

::: moniker-end

2. Menü çubuğunda, **Araçları** > **seçenekleri** açmak için **seçenekleri** iletişim.

3. Üzerinde **ortam** > **genel** seçenekler sayfası, değişiklik **renk teması** seçimi **koyu**seçin **Tamam**.

   ![Visual Studio 'da renk temasını koyu olarak değiştirme](media/change-color-theme.png)

   IDE renk temasını tamamı için değişir **koyu**.

   ::: moniker range="vs-2017"

   ![Visual Studio'da koyu tema](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio'da koyu tema](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Ortam ayarlarını seçin

Ardından, Visual Studio 'Yu Visual Basic geliştiricilere uyarlanmış ortam ayarlarını kullanacak şekilde yapılandıracağız.

1. Menü çubuğunda, **Araçları** > **içeri ve dışarı aktarma ayarları**.

2. **Ayarları içeri ve dışarı aktarma sihirbazında**, ilk sayfadaki **tüm ayarları Sıfırla** ' yı seçin ve ardından **İleri**' yi seçin.

3. **Geçerli ayarları Kaydet** sayfasında, geçerli ayarlarınızı kaydetmek için bir seçenek belirleyin ve ardından **İleri**' yi seçin. (Herhangi bir ayarı özelleştirilmediyseniz, **Hayır, geçerli ayarlarım üzerine yazarak ayarları Sıfırla**' yı seçin.)

4. **Varsayılan ayarlar koleksiyonunu seçin** sayfasında, **Visual Basic**' yi seçin ve ardından **son**' u seçin.

5. **Sıfırlama Tamam** sayfasında **Kapat**' ı seçin.

IDE'yi kişiselleştirme diğer yollar hakkında bilgi edinmek için [kişiselleştirme Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Bir program oluşturma

Şimdi kolları sıvayın ve basit bir program oluşturun.

::: moniker range="vs-2017"

1. Visual Studio menü çubuğunda **dosya** > **Yeni proje**' yi seçin.

   ![Dosya > Yeni Proje menü çubuğunda](media/file-new-project-menu.png)

   **Yeni proje** iletişim kutusu gösterir birkaç proje *şablonları*. Şablon, belirtilen proje türü için gereken ayarları ve temel dosyaları içerir.

1. **Visual Basic**altında **.NET Core** kategorisini seçin ve **konsol uygulaması (.NET Core)** şablonunu seçin. İçinde **adı** metin kutusunda, **HelloWorld**ve ardından **Tamam** düğmesi.

   ![.NET core uygulaması şablonu](media/overview-npd.png)

   > [!NOTE]
   > Görmüyorsanız **.NET Core** kategorisi, yüklemeniz gereken **.NET Core çoklu platform geliştirme** iş yükü. Bunu yapmak için **açık Visual Studio yükleyicisi** alt sol tarafındaki bağlantıyı **yeni proje** iletişim. Visual Studio yükleyicisi açıldığında, aşağıya kaydırın ve **.NET Core çoklu platform geliştirme** iş yükü ve ardından **Değiştir**.

   Visual Studio projesi oluşturur. Çağıran basit bir "Hello World" uygulaması olan <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" sabit dizesini görüntülemek için yöntemi (program çıktısı) konsol penceresinde.

   Kısa bir süre sonra aşağıdaki gibi görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Farklı anahtar sözcükleri ve türleri gibi bir kod bölümlerini göstermek için metni otomatik olarak renklendirilmiş dikkat edin. Ayrıca, hangi küme ayraçları başka bir eşleşen küçük, dikey kesikli satır kodda belirtmek ve satır numaralarını Yardım kodu daha sonra bulun. Daraltma veya genişletme kod blokları için küçük, kutulanmış eksi işaretleri seçebilirsiniz. Anahat oluşturma özelliği bu kod, ekranda dağınıklığı aza indirilmesine yardımcı ihtiyacınız olmayan kodu Gizle olanak tanır. Proje dosyalarını adlı bir pencerede sağ tarafta listelenen **Çözüm Gezgini**.

   ![Kırmızı kutuları ile Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   Kullanılabilir diğer menüleri ve araç pencerelerini, ancak geçelim şimdilik.

1. Şimdi uygulamayı başlatın. Bunu seçerek yapabilirsiniz **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü çubuğundaki menü. Ayrıca basabilirsiniz **Ctrl**+**F5**.

   ![Hata ayıklama > menü hata ayıklama olmadan Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve bir konsol penceresi iletiyle açılır **Merhaba Dünya!** . Artık çalışan bir uygulamanın var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulama için bazı ek kod ekleyelim. Aşağıdaki Visual Basic kodu `Console.WriteLine("Hello World!")`satırı önüne ekleyin:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod görüntüler **adınız ne?** konsol penceresi, ve ardından kullanıcı tarafından izlenen metin girene kadar bekler **Enter** anahtarı.

1. Yazan satırı değiştirin `Console.WriteLine("Hello World!")` aşağıdaki koda:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **Ctrl**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulaması oluşturur ve bir konsol penceresi açar ve sizden adınız için ister.

1. Konsol penceresi ve ENTER tuşuna adınızı girin **Enter**.

   ![Konsol penceresi girdisi](../media/overview-console-input.png)

1. Konsol penceresini kapatın ve çalışan programa durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio menü çubuğunda **dosya** > **Yeni proje**' yi seçin.

   ![Dosya > Yeni Proje menü çubuğunda](media/vs-2019/file-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu*gösterir. Şablon, belirtilen proje türü için gereken ayarları ve temel dosyaları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Ayrıca, **dil** açılır listesinden **Visual Basic** seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz.

1. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da yeni proje oluşturma](media/vs-2019/create-new-project.png)

1. **Yeni projenizi yapılandırın** penceresinde, **Proje adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınızın dizin konumunu değiştirin ve ardından **Oluştur**' u seçin.

   ![Visual Studio 'da yeni proje yapılandırma](media/vs-2019/configure-new-project.png)

   Visual Studio projesi oluşturur. Çağıran basit bir "Hello World" uygulaması olan <xref:System.Console.WriteLine?displayProperty=nameWithType> "Hello World!" sabit dizesini görüntülemek için yöntemi (program çıktısı) konsol penceresinde.

   Kısa bir süre sonra aşağıdaki gibi görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Farklı anahtar sözcükleri ve türleri gibi bir kod bölümlerini göstermek için metni otomatik olarak renklendirilmiş dikkat edin. Ayrıca, hangi küme ayraçları başka bir eşleşen küçük, dikey kesikli satır kodda belirtmek ve satır numaralarını Yardım kodu daha sonra bulun. Daraltma veya genişletme kod blokları için küçük, kutulanmış eksi işaretleri seçebilirsiniz. Anahat oluşturma özelliği bu kod, ekranda dağınıklığı aza indirilmesine yardımcı ihtiyacınız olmayan kodu Gizle olanak tanır. Proje dosyalarını adlı bir pencerede sağ tarafta listelenen **Çözüm Gezgini**.

   ![Kırmızı kutuları ile Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   Kullanılabilir diğer menüleri ve araç pencerelerini, ancak geçelim şimdilik.

1. Şimdi uygulamayı başlatın. Bunu seçerek yapabilirsiniz **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü çubuğundaki menü. Ayrıca basabilirsiniz **Ctrl**+**F5**.

   ![Hata ayıklama > menü hata ayıklama olmadan Başlat](media/vs-2019/start-without-debugging.png)

   Visual Studio uygulamayı derler ve bir konsol penceresi iletiyle açılır **Merhaba Dünya!** . Artık çalışan bir uygulamanın var!

   ![Konsol penceresi](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulama için bazı ek kod ekleyelim. Aşağıdaki Visual Basic kodu `Console.WriteLine("Hello World!")`satırı önüne ekleyin:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod görüntüler **adınız ne?** konsol penceresi, ve ardından kullanıcı tarafından izlenen metin girene kadar bekler **Enter** anahtarı.

1. Yazan satırı değiştirin `Console.WriteLine("Hello World!")` aşağıdaki koda:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **Ctrl**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulaması oluşturur ve bir konsol penceresi açar ve sizden adınız için ister.

1. Konsol penceresi ve ENTER tuşuna adınızı girin **Enter**.

   ![Konsol penceresi](../media/vs-2019/overview-console-input.png)

1. Konsol penceresini kapatın ve çalışan programa durdurmak için herhangi bir tuşa basın.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Birkaç farklı şekilde bakalım, [yeniden düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) yardımcı olabilecek daha verimli bir şekilde kod.

İlk olarak, Şimdi Yeniden Adlandır `name` değişkeni:

1. Çift `name` değişkeni seçin.

2. Değişken için yeni adı yazın **username**.

   Değişkeni ve bir ampul gri kutu göründüğüne dikkat edin, kenar boşluğunda görünür.

3. Kullanılabilir göstermek için ampul simgesini [hızlı Eylemler](../../ide/quick-actions.md). Seçin **Yeniden Adlandır 'name 'username' için'** .

   ![Visual Studio'da eylemini yeniden adlandır](media/rename-quick-action.png)

   Değişkeni, bu örnekte yalnızca iki basamağı olan proje boyunca yeniden adlandırılır.

4. Artık IntelliSense bir göz atalım. `Console.WriteLine("Hello " + username + "!")`belirten satırın altına aşağıdaki kod parçasını yazın:

    ```vb
   Dim now = Date.
   ```

   Bir kutu üyelerini görüntüler <xref:System.DateTime> sınıfı. Ayrıca, ayrı bir kutuda şu anda seçilen üyenin açıklamasını görüntüler.

   ![Visual Studio IntelliSense üyeleri Listele](media/intellisense-list-members.png)

5. Sınıfın bir özelliği olan **Şimdi**adlı üyeyi seçin. Bu özellik, çift tıklayarak ya da yukarı veya aşağı ok tuşlarını kullanarak ve ardından **sekme**tuşuna basarak seçerek.

6. Bunun yerine, aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> biraz farklı <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> içeren Yazar sonra bir satır Sonlandırıcı eklemez. Bu sonraki çıkışa gönderilir metin parçası aynı satırda yazdırılır anlamına gelir. Bu yöntemlerin her biri kendi açıklamasını görmek için kodunuzda gelebilirsiniz.

7. Ardından, yeniden yeniden düzenleme kod biraz daha kısa olmak için kullanacağız. Değişkenin üzerine tıklayın `now` satırında `Dim now = Date.Now`.

   Kenar boşluğunda bu satırdaki bir tornavida ikonu görüntülendiğine dikkat edin.

8. Önerileri görmek için tornavida simgesine tıklayarak Visual Studio kullanılabilir sahiptir. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösteriliyor:

   ![Satır içi geçici değişken Visual Studio'da yeniden düzenleme](media/inline-temporary-variable-refactoring.png)

9. Tıklayın **satır içi geçici değişken** kodun yeniden.

::: moniker range="vs-2017"

10. Tuşlarına basarak programı yeniden çalıştırın **Ctrl**+**F5**. Çıktı aşağıdakine benzer olacaktır:

    ![Konsol penceresi ile program çıktısı](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Tuşlarına basarak programı yeniden çalıştırın **Ctrl**+**F5**. Çıktı aşağıdakine benzer olacaktır:

    ![Konsol penceresi ile program çıktısı](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Kodda hata ayıklama

Kod yazmak, çalıştırmak ve hatalar için test gerekir. Visual Studio'nun hata ayıklama sistem aynı anda bir deyim kod adım adım ve kullandıkça, değişkenleri inceleyebilir olanak sağlar. Ayarlayabileceğiniz *kesme noktaları* belirli bir satır kod yürütmeyi durdurun. Bir değişken değişiklikleri değeri olarak kodu nasıl çalıştığını ve daha fazlasını gözlemleyebilirsiniz.

Değerini görmek için bir kesme noktası ayarlayalım `username` program "uçuşta" iken değişkeni.

1. İfadesini içeren kod satırını bulun `Console.WriteLine("Hello " + username + "!")`. Bu kod satırı, programın bu satırı yürütmeyi Duraklat yapmak için diğer bir deyişle, bir kesme noktası ayarlamak için düzenleyicisinin en sol kenar boşluğunda tıklayın. Ayrıca kod satırında herhangi bir yere tıklayın ve sonra basın **F9**.

   Kırmızı bir daire en sol kenar boşluğunda görünür ve kodu vurgulanır.

   ![Visual Studio'da kod satırında kesme noktası](media/breakpoint.png)

1. Seçerek hata ayıklamayı Başlat **hata ayıklama** > **hata ayıklamayı Başlat** veya basarak **F5**.

1. Konsol penceresinde görünür ve adınız için ister, yazın ve basın **Enter**.

   Odak, Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Bu program yürütülen kodun sonraki satıra olduğunu gösterir.

1. Fareyi üzerine `username` değerini görmek için değişkeni. Alternatif olarak, üzerinde sağ tıklayabilirsiniz `username` seçip **Gözcü Ekle** değişkeni eklemek için **Watch** penceresinde de görebileceğiniz değeri.

   ![Visual Studio'da hata ayıklama sırasında değişken değeri](media/debugging-variable-value.png)

1. Programın tamamlanmaya kadar çalışmasına izin vermek için basın **F5** yeniden.

Visual Studio'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcısı özellik Turu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu tanıtıcı makaleler biriyle boyunca izleyerek daha fazla Visual Studio'ı keşfedin:

> [!div class="nextstepaction"]
> [Kod düzenleyicisini kullanmayı öğrenin](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- Bulma [daha fazla Visual Studio özellikleri](../../ide/advanced-feature-overview.md)
- Ziyaret [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Okuma [Visual Studio blogu](https://devblogs.microsoft.com/visualstudio/)
