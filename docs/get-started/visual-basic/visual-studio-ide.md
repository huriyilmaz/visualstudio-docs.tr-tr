---
title: Visual Basic geliştiricilere genel bakış
description: kodu düzenlemek, hatalarını ayıklamak ve derlemek için Visual Studio kullanma hakkında bilgi edinin ve ardından bir uygulamayı Visual Basic geliştiricisi olarak yayımlayın.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2b7649af4136c13688a6f2311d715b7c4bb113bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152217"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Visual Studio ıde 'ye hoş geldiniz | Visual Basic

Visual Studio *tümleşik geliştirme ortamı* , kodu düzenlemek, hatalarını ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma paneliyle bulunur. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen özellik açısından zengin bir programdır. standart düzenleyicinin ve üzerinde birçok ıdes 'in sağladığı hata ayıklayıcı, Visual Studio derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve yazılım geliştirme sürecini kolaylaştırmak için çok daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio ıde](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Visual Studio 2019 ıde](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

bu görüntüde, büyük olasılıkla kullanabileceğiniz bir açık proje ve birkaç anahtar araç penceresi içeren Visual Studio gösterilmektedir:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Bu, kodu düzenleyebileceğiniz veya düğmeler ve metin kutuları içeren pencere gibi bir kullanıcı arabirimi tasarlayabileceğiniz yerdir.

- [çıkış penceresi](../../ide/reference/output-window.md) (alt orta), Visual Studio hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimleri gönderir. Her ileti kaynağının kendi sekmesi vardır.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation Sürüm Denetimi (tfvc)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

Visual Studio Windows ve Mac için kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2017 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. bu makale, Visual Studio 2017 Windows sürümüne odaklanır.

Visual Studio 2017 ' nin üç sürümü vardır: Community, Professional ve Enterprise. her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Compare Visual Studio 2017 ıdes](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

yazılım geliştirirken daha üretken olmanıza yardımcı olan Visual Studio popüler özelliklerden bazıları şunlardır:

- Dalgalı çizgiler ve [hızlı eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, hata oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları anında çözmenizi sağlar. Dalgalı bir çizgi üzerine geldiğinizde, hatayla ilgili ek bilgileri görürsünüz. Ayrıca, bir ampulü, hızlı eylemler olarak bilinen eylemlerle birlikte, hatayı düzelrebilir.

   ::: moniker range="vs-2017"

   ![Visual Studio dalgalı çizgiler](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio dalgalı çizgiler](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adlandırılması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemleri içerir.

   ::: moniker range="vs-2017"

   ![Visual Studio yeniden düzenleme menüsü](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio yeniden düzenleme menüsü](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen özellikler kümesi için bir terimdir ve bazı durumlarda, sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu da tür bilgilerini başka bir yerde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir. daha fazla bilgi için bkz. [C# ıntellisense](../../ide/visual-csharp-intellisense.md), [Visual C++ ıntellisense](../../ide/visual-cpp-intellisense.md), [JavaScript ıntellisense](../../ide/javascript-intellisense.md)ve [Visual Basic ıntellisense](../../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ::: moniker range="vs-2017"

   ![Visual Studio Üye listesi](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio Üye listesi](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Arama kutusu

   Visual Studio birçok menü, seçenek ve özellik ile zaman içinde çok daha fazla görünebilir. Arama kutusu, Visual Studio ihtiyacınız olanları hızlı bir şekilde bulmanın harika bir yoludur. aradığınız bir şeyin adını yazmaya başladığınızda Visual Studio, sizi tam olarak gitmeniz gereken yere götürür sonuçları listeler. Visual Studio işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek üzere arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   > [!TIP]
   >  + Arama kutusunun kısayol olarak Ctrl **Q** tuşuna basın.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 ' de hızlı başlat arama kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için bkz. [Hızlı başlatma](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de arama kutusu](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türü veya programlama diliniz ne olursa olsun, başkalarıyla birlikte düzenleme ve hata ayıklama işlemlerini gerçek zamanlı olarak yapın. Projenizi anında ve güvenli bir şekilde paylaşabilir, gerekirse hata ayıklama oturumları, Terminal örnekleri, localhost Web Apps, sesli çağrılar ve daha fazlasını yapabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu, yöntemi değiştirme veya kaldırma hakkında düşündüğünde veya bir hatayı izlemeye çalışırken yararlı bilgiler olabilir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'de çağrı hiyerarşisi penceresi](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'de çağrı hiyerarşisi penceresi](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuzun başvurularını, kodunuzda yaptığınız değişiklikleri, bağlantılı hataları, iş öğelerini, kod incelemelerinizi ve birim testlerini, Düzenleyiciden çıkmadan bulmanıza yardımcı olur.

   ::: moniker range="vs-2017"

   ![CodeLens Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma Git özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 ' de tanıma git](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de tanıma git](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Özet **tanım** penceresi, aslında ayrı bir dosya açmadan bir yöntemin veya türün tanımını gösterir.

   ::: moniker range="vs-2017"

   ![Visual Studio tanım Özeti](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio tanım Özeti](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Visual Studio ıde 'yi yükler

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. Renk temasını değiştirecek, [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanacaksınız ve programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamanın hatalarını ayıklayacaksınız.

::: moniker range="vs-2017"

başlamak için [Visual Studio indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

başlamak için [Visual Studio indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

![Visual Studio Yükleyicisi 'de .net Core platformlar arası geliştirme iş yükü](../media/dotnet-core-cross-platform-workload.png)

Visual Studio ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="customize-visual-studio"></a>Visual Studio özelleştirme

Visual Studio kullanıcı arabirimini kişiselleştirebilirsiniz, bu da varsayılan renk temasını değiştirebilirsiniz.

### <a name="change-the-color-theme"></a>Renk temasını değiştirme

**Koyu** temaya geçiş yapmak için:

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Visual Studio 2019 ' deki başlangıç penceresinin ekran görüntüsü, ' kod olmadan devam et ' bağlantısı vurgulanmış.":::

   IDE açılır.

::: moniker-end

2. Menü çubuğunda,   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

3. **Ortam**  >  **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' a tıklayın.

   ![Visual Studio renk temasını koyu olarak değiştirme](media/change-color-theme.png)

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ::: moniker range="vs-2017"

   ![koyu temada Visual Studio](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![koyu temada Visual Studio](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Ortam ayarlarını seçin

daha sonra, Visual Basic geliştiricilere uyarlanmış ortam ayarlarını kullanmak için Visual Studio yapılandıracağız.

1. menü çubuğunda **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin.

2. **içeri ve dışarı aktarma Ayarlar sihirbazında**, ilk sayfadaki **tüm ayarları sıfırla** ' yı seçin ve ardından **ileri**' ye tıklayın.

3. **geçerli Ayarlar kaydet** sayfasında, geçerli ayarlarınızı kaydetmek için bir seçenek belirleyin ve ardından **ileri**' ye tıklayın. (Herhangi bir ayarı özelleştirilmediyseniz, **Hayır, geçerli ayarlarım üzerine yazarak ayarları Sıfırla**' yı seçin.)

4. **Ayarlar varsayılan koleksiyonunu seçin** sayfasında **Visual Basic**' i seçin ve ardından **son**' a tıklayın.

5. **Sıfırlama Tamam** sayfasında **Kapat**' a tıklayın.

IDE 'yi kişiselleştirmek için kullanabileceğiniz diğer yollar hakkında bilgi edinmek için bkz. [kişiselleştirme Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Program oluşturma

Şimdi bir basit program oluşturalım.

::: moniker range="vs-2017"

1. Visual Studio menü çubuğunda **dosya** > **yeni Project**' ni seçin.

   ![dosya > menü çubuğunda yeni Project](media/file-new-project-menu.png)

   **yeni Project** iletişim kutusunda çeşitli proje *şablonları* gösterilmektedir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. **Visual Basic** altında **.net core** kategorisini seçin ve **konsol uygulaması (.net Core)** şablonunu seçin. **Ad** metin kutusuna **HelloWorld** yazın ve **Tamam** düğmesini seçin.

   ![.NET Core uygulama şablonu](media/overview-npd.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. bunu yapmak için **yeni Project** iletişim kutusunun sol alt kısmındaki **aç Visual Studio Yükleyicisi** bağlantısını seçin. Visual Studio Yükleyicisi açıldıktan sonra, aşağı kaydırarak **.net Core platformlar arası geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Visual Studio Kırmızı kutular ile IDE](media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. Aşağıdaki koda gelen satırı değiştirin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **CTRL** F5 tuşuna basarak uygulamayı yeniden çalıştırın + .

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Konsol penceresi girişi](../media/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin. (Alternatif olarak, **CTRL** + tuşuna basın **SHIFT** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Visual Studio 2019 menü çubuğundan yeni > Project seçimi > dosyanın ekran görüntüsü.":::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. tüm **diller** açılan listesinden **Visual Basic** seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz, tüm **platformlar** listesinden ve **tüm proje türleri** listesinden **konsolundan** **Windows** .

   **Konsol uygulaması** şablonunu seçin ve ardından **İleri**' ye tıklayın.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Visual Studio 2019 ' de, istediğiniz şablonu seçtiğinizde ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınız için dizin konumunu değiştirin (varsayılan yerel ayar `C:\Users\<name>\source\repos` ) ve ardından **ileri**' ye tıklayın.

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019 ' de projenin adını girdiğiniz ' yeni projeyi yapılandırma ' penceresinin ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' in **hedef çerçeve** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' a tıklayın.

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019 ' de, istediğiniz .net Core Framework sürümünü seçtiğiniz ' ek bilgiler ' penceresinin ekran görüntüsü.":::

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Visual Studio Kırmızı kutular ile IDE](media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](media/vs-2019/start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Merhaba Dünya iletisini gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. Aşağıdaki koda gelen satırı değiştirin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **CTRL** F5 tuşuna basarak uygulamayı yeniden çalıştırın + .

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Ad Sorunuzun ne olduğunu ve uygulamanın yanıtını gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) 'in daha verimli bir şekilde kodlamasına yardımcı olması için birkaç yol göz atalım.

İlk olarak, değişkeni yeniden adlandıralım `name` :

1. `name`Seçmek için değişkene çift tıklayın.

2. Değişken için yeni adı yazın, **Kullanıcı** adı.

   Değişken etrafında gri bir kutu göründüğünü ve kenar boşluğunda ampul göründüğünü unutmayın.

3. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ![Visual Studio eylemi yeniden adlandır](media/rename-quick-action.png)

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer olur.

4. Şimdi IntelliSense 'e göz atalım. Yazılı satırın altına `Console.WriteLine("Hello " + username + "!")` Aşağıdaki kod parçasını yazın:

    ```vb
   Dim now = Date.
   ```

   Bir kutu, sınıfının üyelerini görüntüler <xref:System.DateTime> . Ayrıca, şu anda seçili olan üyenin açıklaması ayrı bir kutu içinde görüntülenir.

   ![Visual Studio içindeki IntelliSense listesi üyeleri](media/intellisense-list-members.png)

5. Sınıfın bir özelliği olan **Şimdi** adlı üyeyi seçin. Bu özellik, çift tıklayarak ya da yukarı veya aşağı ok tuşlarını kullanarak ve ardından **sekme** tuşuna basarak seçerek.

6. Bunun yerine, aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırıldıktan sonra satır Sonlandırıcı eklememesi için biraz farklıdır. Diğer bir deyişle, çıktıya gönderilen sonraki metin parçası aynı satıra yazdırılır. Açıklamalarını görmek için kodunuzda bu yöntemlerin her birinin üzerine gelebilmeniz gerekir.

7. Daha sonra, yeniden düzenleme kullanarak kodu biraz daha kısa hale getirebilirsiniz. Satırdaki değişkenine tıklayın `now` `Dim now = Date.Now` .

   Bu satırdaki kenar boşluğunda küçük bir screwsürücü simgesinin göründüğünü unutmayın.

8. Visual Studio hangi önerilerin kullanılabilir olduğunu görmek için screwdriver simgesine tıklayın. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösteriliyor:

   ![Visual Studio iç satır içi geçici değişken yeniden düzenlemesi](media/inline-temporary-variable-refactoring.png)

9. Kodu yeniden düzenleme için **satır içi geçici değişken** ' e tıklayın.

::: moniker range="vs-2017"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ![Program çıktısı olan konsol penceresi](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ![Program çıktısı olan konsol penceresi](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio hata ayıklama sistemi, bir seferde kod tek bir bildirimde ilerlemenizi ve gittiğiniz değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* belirleyebilirsiniz. Bir değişken değerinin kodun çalıştırıldığı şekilde nasıl değiştiğini gözlemleyebilirsiniz ve daha fazlasını yapabilirsiniz.

`username`Programın &quot;uçuş aşamasında&quot; olduğu sırada değişkenin değerini görmek için bir kesme noktası ayarlayalım.

1. Belirten kod satırını bulun `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` . Bu kod satırında bir kesme noktası ayarlamak için, diğer bir deyişle, programın bu satırda yürütmeyi duraklamasını sağlamak için düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırında herhangi bir yere tıklayabilir ve ardından **F9**' e basabilirsiniz.

   Sol taraftaki kenar boşluğunda kırmızı bir daire görünür ve kod kırmızı renkle vurgulanır.

   ![Visual Studio kod satırında kesme noktası](media/breakpoint.png)

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatma** veya **F5**'e basarak hata ayıklamayı başlatın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde, yazın ve **ENTER** tuşuna basın.

   odak Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Bu, programın yürütecektir bir sonraki kod satırı olduğunu belirtir.

1. `username`Değerini görmek için farenizi değişkenin üzerine getirin. Alternatif olarak, ' ı sağ tıklayıp, `username` sonra da değeri de görebileceğiniz **izleme** penceresine eklemek için **Gözcü Ekle** seçeneğini belirleyebilirsiniz.

   ![Visual Studio hata ayıklama sırasında değişken değeri](media/debugging-variable-value.png)

1. Programın tamamlanmasını çalışmasına izin vermek için **F5** tuşuna basın.

Visual Studio hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcı özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki tanıtım makaleleriyle birlikte Visual Studio daha fazlasını yapın:

> [!div class="nextstepaction"]
> [Kod düzenleyicisini kullanmayı öğrenin](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [daha fazla Visual Studio özellik](../../ide/advanced-feature-overview.md) bul
- [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/) ziyaret edin
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/) okuyun
