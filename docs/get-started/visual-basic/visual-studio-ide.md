---
title: Visual Basic geliştiricilere genel bakış
description: Kodu düzenlemek, hatalarını ayıklamak ve derlemek için Visual Studio 'Yu kullanma hakkında bilgi edinin ve ardından bir uygulamayı Visual Basic geliştirici olarak yayımlayın.
ms.date: 11/15/2018
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3d771fac2cf494e92cbc27fdbdca0b78af97b67e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944400"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Visual Studio IDE 'ye hoş geldiniz | Visual Basic

Visual Studio *Tümleşik geliştirme ortamı* , kod düzenlemek, hatalarını ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma paneliyle bulunur. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen özellik açısından zengin bir programdır. En çok kullanılan standart düzenleyici ve hata ayıklayıcı üzerinde ve üzerinde, Visual Studio, yazılım geliştirme sürecini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve çok daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![Visual Studio 2019 IDE](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Bu resimde, büyük olasılıkla kullanabileceğiniz bir açık proje ve birkaç anahtar araç penceresi içeren Visual Studio gösterilmektedir:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Bu, kodu düzenleyebileceğiniz veya düğmeler ve metin kutuları içeren pencere gibi bir kullanıcı arabirimi tasarlayabileceğiniz yerdir.

- [Çıkış penceresi](../../ide/reference/output-window.md) (alt orta), Visual Studio 'nun hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

Visual Studio, Windows ve Mac için kullanılabilir. [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2017 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede, Visual Studio 2017 ' nin Windows sürümü ele alınmaktadır.

Visual Studio 2017: Community, Professional ve Enterprise 'ın üç sürümü vardır. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio 2017 IDEs 'ı karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio 'da, yazılım geliştirirken daha üretken olmanıza yardımcı olan popüler özelliklerden bazıları şunlardır:

- Dalgalı çizgiler ve [hızlı eylemler](../../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, hata oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları anında çözmenizi sağlar. Dalgalı bir çizgi üzerine geldiğinizde, hatayla ilgili ek bilgileri görürsünüz. Ayrıca, bir ampulü, hızlı eylemler olarak bilinen eylemlerle birlikte, hatayı düzelrebilir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da dalgalı çizgiler](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da dalgalı çizgiler](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adlandırılması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemleri içerir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da yeniden düzenleme menüsü](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da yeniden düzenleme menüsü](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen özellikler kümesi için bir terimdir ve bazı durumlarda, sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu da tür bilgilerini başka bir yerde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir. Daha fazla bilgi için bkz. [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)ve [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ::: moniker range="vs-2017"

   ![Visual Studio üye listesi](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio üye listesi](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Arama kutusu

   Visual Studio çok sayıda menü, seçenek ve özellik ile zaman içinde yoğun görünebilir. Arama kutusu, Visual Studio 'da gerekenleri hızlı bir şekilde bulmanın harika bir yoludur. Aradığınız bir şeyin adını yazmaya başladığınızda, Visual Studio size tam olarak gitmeniz gereken yere sahip olan sonuçları listeler. Visual Studio 'ya işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek istiyorsanız, arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   > [!TIP]
   >  + Arama kutusunun kısayol olarak Ctrl **Q** tuşuna basın.

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

   **Çağrı hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu, yöntemi değiştirme veya kaldırma hakkında düşündüğünde veya bir hatayı izlemeye çalışırken yararlı bilgiler olabilir.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da çağrı hiyerarşisi penceresi](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da çağrı hiyerarşisi penceresi](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuzun başvurularını, kodunuzda yaptığınız değişiklikleri, bağlantılı hataları, iş öğelerini, kod incelemelerinizi ve birim testlerini, Düzenleyiciden çıkmadan bulmanıza yardımcı olur.

   ::: moniker range="vs-2017"

   ![Visual Studio 'da CodeLens](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da CodeLens](media/vs-2019/codelens.png)

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

   ![Visual Studio 'da açıklama Özeti](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio 'da açıklama Özeti](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE 'yi yükler

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. Renk temasını değiştirecek, [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanacaksınız ve programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamanın hatalarını ayıklayacaksınız.

::: moniker range="vs-2017"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini* seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

![Visual Studio Yükleyicisi 'de .NET Core platformlar arası geliştirme iş yükü](../media/dotnet-core-cross-platform-workload.png)

Visual Studio 'Yu ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="customize-visual-studio"></a>Visual Studio 'Yu özelleştirme

Visual Studio Kullanıcı arabirimini kişiselleştirmek için, varsayılan renk temasını değiştirme de dahil olmak üzere özelleştirebilirsiniz.

### <a name="change-the-color-theme"></a>Renk temasını değiştirme

**Koyu** temaya geçiş yapmak için:

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde, **kod olmadan devam et**' i seçin.

   ![Visual Studio 2019 ' de başlangıç penceresi](media/vs-2019/continue-without-code.png)

   IDE açılır.

::: moniker-end

2. Menü çubuğunda,   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

3. **Ortam**  >  **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' ı seçin.

   ![Visual Studio 'da renk temasını koyu olarak değiştirme](media/change-color-theme.png)

   IDE 'nin tamamına yönelik renk teması **koyu** olarak değişir.

   ::: moniker range="vs-2017"

   ![Koyu temalı Visual Studio](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Koyu temalı Visual Studio](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Ortam ayarlarını seçin

Ardından, Visual Studio 'Yu Visual Basic geliştiricilere uyarlanmış ortam ayarlarını kullanacak şekilde yapılandıracağız.

1. Menü çubuğunda **Araçlar**  >  **içeri aktar ve dışarı aktar ayarları**' nı seçin.

2. **Ayarları içeri ve dışarı aktarma sihirbazında**, ilk sayfadaki **tüm ayarları Sıfırla** ' yı seçin ve ardından **İleri**' yi seçin.

3. **Geçerli ayarları Kaydet** sayfasında, geçerli ayarlarınızı kaydetmek için bir seçenek belirleyin ve ardından **İleri**' yi seçin. (Herhangi bir ayarı özelleştirilmediyseniz, **Hayır, geçerli ayarlarım üzerine yazarak ayarları Sıfırla**' yı seçin.)

4. **Varsayılan ayarlar koleksiyonunu seçin** sayfasında, **Visual Basic**' yi seçin ve ardından **son**' u seçin.

5. **Sıfırlama Tamam** sayfasında **Kapat**' ı seçin.

IDE 'yi kişiselleştirmek için kullanabileceğiniz diğer yollar hakkında bilgi edinmek için bkz. [Visual Studio 'Yu kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Program oluşturma

Şimdi bir basit program oluşturalım.

::: moniker range="vs-2017"

1. Visual Studio menü çubuğunda **Dosya** > **Yeni proje**' yi seçin.

   ![Dosya > menü çubuğunda yeni proje](media/file-new-project-menu.png)

   **Yeni proje** iletişim kutusunda çeşitli proje *şablonları* gösterilmektedir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. **Visual Basic** altında **.NET Core** kategorisini seçin ve **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna **HelloWorld** yazın ve **Tamam** düğmesini seçin.

   ![.NET Core uygulama şablonu](media/overview-npd.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. Bunu yapmak için, **Yeni proje** iletişim kutusunun sol alt kısmındaki **Aç Visual Studio yükleyicisi** bağlantısını seçin. Visual Studio Yükleyicisi açıldıktan sonra, aşağı kaydırarak **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutular içeren Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine("Hello World!")` :

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

1. Visual Studio menü çubuğunda **Dosya** > **Yeni proje**' yi seçin.

   ![Dosya > menü çubuğunda yeni proje](media/vs-2019/file-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Ayrıca, **dil** açılır listesinden **Visual Basic** seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz.

1. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da yeni proje oluşturma](media/vs-2019/create-new-project.png)

1. **Yeni projenizi yapılandırın** penceresinde, **Proje adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınızın dizin konumunu değiştirin ve ardından **Oluştur**' u seçin.

   ![Visual Studio 'da yeni proje yapılandırma](media/vs-2019/configure-new-project.png)

   Visual Studio projeyi oluşturur. <xref:System.Console.WriteLine?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağıran basit bir "Merhaba Dünya" uygulaması Konsol (program çıktısı) penceresinde.

   Kısa süre içinde aşağıdakine benzer bir şey görmeniz gerekir:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu, alanın çoğunu alan düzenleyici penceresinde görünür. Metnin anahtar sözcükler ve türler gibi farklı parçalarını göstermek için otomatik olarak renklendirildiğine dikkat edin. Ayrıca, koddaki küçük, dikey kesikli çizgiler, hangi küme ayracın birbiriyle eşleştiğini gösterir ve satır numaraları kodu daha sonra bulmanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutular içeren Visual Studio IDE](media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama menüsü olmadan > Başlat](media/vs-2019/start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Merhaba Dünya iletisini gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. Aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine("Hello World!")` :

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

   ![Visual Studio 'da yeniden adlandırma eylemi](media/rename-quick-action.png)

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer olur.

4. Şimdi IntelliSense 'e göz atalım. Yazılı satırın altına `Console.WriteLine("Hello " + username + "!")` Aşağıdaki kod parçasını yazın:

    ```vb
   Dim now = Date.
   ```

   Bir kutu, sınıfının üyelerini görüntüler <xref:System.DateTime> . Ayrıca, şu anda seçili olan üyenin açıklaması ayrı bir kutu içinde görüntülenir.

   ![Visual Studio 'da IntelliSense liste üyeleri](media/intellisense-list-members.png)

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

8. Visual Studio 'Nun hangi önerilerin kullanılabilir olduğunu görmek için screwdriver simgesine tıklayın. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösteriliyor:

   ![Visual Studio 'da satır içi geçici değişken yeniden düzenlemesi](media/inline-temporary-variable-refactoring.png)

9. Kodu yeniden düzenleme için **satır içi geçici değişken** ' e tıklayın.

::: moniker range="vs-2017"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ![Program çıktısı olan konsol penceresi](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

    ![Program çıktısı olan konsol penceresi](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio 'nun hata ayıklama sistemi, kod tek bir bildirimde bir kez ilerlemenizi ve siz yazarken değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* belirleyebilirsiniz. Bir değişken değerinin kodun çalıştırıldığı şekilde nasıl değiştiğini gözlemleyebilirsiniz ve daha fazlasını yapabilirsiniz.

`username`Programın "uçuş aşamasında" olduğu sırada değişkenin değerini görmek için bir kesme noktası ayarlayalım.

1. Belirten kod satırını bulun `Console.WriteLine("Hello " + username + "!")` . Bu kod satırında bir kesme noktası ayarlamak için, diğer bir deyişle, programın bu satırda yürütmeyi duraklamasını sağlamak için düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırında herhangi bir yere tıklayabilir ve ardından **F9**' e basabilirsiniz.

   Sol taraftaki kenar boşluğunda kırmızı bir daire görünür ve kod kırmızı renkle vurgulanır.

   ![Visual Studio 'da kod satırında kesme noktası](media/breakpoint.png)

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatma** veya **F5**'e basarak hata ayıklamayı başlatın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde, yazın ve **ENTER** tuşuna basın.

   Odak, Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Bu, programın yürütecektir bir sonraki kod satırı olduğunu belirtir.

1. `username`Değerini görmek için farenizi değişkenin üzerine getirin. Alternatif olarak, ' ı sağ tıklayıp, `username` sonra da değeri de görebileceğiniz **izleme** penceresine eklemek için **Gözcü Ekle** seçeneğini belirleyebilirsiniz.

   ![Visual Studio 'da hata ayıklama sırasında değişken değeri](media/debugging-variable-value.png)

1. Programın tamamlanmasını çalışmasına izin vermek için **F5** tuşuna basın.

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcı Özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki tanıtım makaleleriyle birlikte Visual Studio 'Yu daha ayrıntılı bir şekilde bulun:

> [!div class="nextstepaction"]
> [Kod düzenleyicisini kullanmayı öğrenin](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Daha fazla Visual Studio özelliği](../../ide/advanced-feature-overview.md) bulun
- [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/) ziyaret edin
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/) okuyun
