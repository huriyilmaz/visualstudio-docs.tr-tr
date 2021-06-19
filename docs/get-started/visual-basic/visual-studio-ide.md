---
title: Visual Basic geliştiricilere genel bakış
description: Kodu düzenlemek, hatalarını ayıklamak ve derlemek için Visual Studio 'Yu kullanma hakkında bilgi edinin ve ardından bir uygulamayı Visual Basic geliştirici olarak yayımlayın.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
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
ms.openlocfilehash: 486201d61f6bd2d149c9aea66efee1814ce667e7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386637"
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


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Visual Studio 2019 ' de başlangıç penceresinin, ' kod olmadan devam et ' bağlantısı vurgulanmış ekran görüntüsü.":::

   IDE açılır.

::: moniker-end

2. Menü çubuğunda,   >  **Seçenekler** iletişim kutusunu açmak için Araçlar **Seçenekler** ' i seçin.

3. **Ortam**  >  **genel** seçenekleri sayfasında, **renk teması** seçimini **koyu** olarak değiştirin ve ardından **Tamam**' a tıklayın.

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

1. Menü çubuğunda Araçlar İçeri ve Dışarı **Aktarma**  >  **Ayarları'ı seçin.**

2. Ayarları İçeri **ve Dışarı Aktarma Sihirbazı'nda,** ilk **sayfada Tüm** ayarları sıfırla'yı seçin ve ardından Sonraki'ye **tıklayın.**

3. Geçerli Ayarları **Kaydet sayfasında,** geçerli ayarlarınızı kaydeden veya kaydetmeyen bir seçenek belirleyin ve ardından Sonraki 'ye **tıklayın.** (Herhangi bir ayarı özelleştirmedıysanız Hayır, ayarları sıfırla'yı **seçin ve geçerli ayarlarım üzerine yazmanız gerekir.)**

4. Varsayılan Ayarlar **Koleksiyonu Seçin sayfasında, Visual Basic'ı** **seçin ve** ardından Son'a **tıklayın.**

5. Tamamla **sayfasında Kapat'a** **tıklayın.**

IDE'nizi kişiselleştirmenin diğer yolları hakkında bilgi edinmek için [bkz. Visual Studio.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="create-a-program"></a>Program oluşturma

Şimdi basit bir program oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Yeni Visual Studio çubuğunda Dosya Yeni **Proje'yi** > **seçin.**

   ![Menü > Yeni Proje dosya dosyası](media/file-new-project-menu.png)

   Yeni **Proje iletişim** kutusunda birkaç proje şablonu *görüntülenir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Visual Basic **altında .NET Core** **kategorisini** seçin ve ardından Konsol Uygulaması **(.NET Core) şablonunu** seçin. Ad **metin** kutusuna **HelloWorld yazın ve** tamam **düğmesini** seçin.

   ![.NET Core uygulama şablonu](media/overview-npd.png)

   > [!NOTE]
   > .NET Core kategorisini **görmüyorsanız.NET Core** platformlar arası geliştirme **iş yükünü yüklemeniz** gerekir. Bunu yapmak için Yeni Proje **iletişim Visual Studio Yükleyicisi** alttaki Dosya Aç **bağlantısını** seçin. Uygulama Visual Studio Yükleyicisi sonra ekranı aşağı kaydırın ve **.NET Core** platformlar arası geliştirme iş yükünü seçin ve ardından Değiştir'i **seçin.**

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısaca, aşağıdakine benzer bir şey görüyoruz:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu düzenleyici penceresinde görünür ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretlerini seçebilirsiniz. Bu kod açıklama özelliği, ihtiyacınız olan kodu gizleyerek ekrandaki dağınıklığı en aza indirmenizi sağlar. Proje dosyaları, Çözüm Gezgini adlı bir pencerede **sağ tarafta listelenir.**

   ![Visual Studio kutuları olan IDE'leri kullanma](media/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de vardır, ancak şimdilik devam edin.

1. Şimdi uygulamayı başlatabilirsiniz. Bunu yapmak için menü çubuğundaki **Hata Ayıklama menüsünden** Hata **Ayıklama** Olmadan Başlat'ı seçebilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata ayıklama > hata ayıklama olmadan başlat menüsü](../media/overview-start-without-debugging.png)

   Visual Studio, uygulamayı derler ve şu iletiyle bir konsol penceresi **Merhaba Dünya!**. Artık çalışan bir uygulama var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Şimdi uygulamaya bazı ek kodlar ekleriz. Aşağıdaki kodu Visual Basic satırın önünde `Console.WriteLine("Hello World!")` ekleyin:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve ardından kullanıcı bir metin girene kadar enter tuşuna **basın.**

1. aşağıdaki kodla `Console.WriteLine("Hello World!")` ifade eden satırı değiştirme:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **Ctrl** F5 tuşlarına basarak + **uygulamayı yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız girin ve Enter tuşuna **basın.**

   ![Konsol penceresi girişi](../media/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yeni Visual Studio Çubuğunda Dosya Yeni **Proje'yi**  >    >  **seçin.** (Alternatif olarak **Ctrl tuşuna basın** + **Shift ile kaydırma** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="> Visual Studio 2019 menü çubuğundan Yeni > Proje Visual Studio seçiminin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Bizim istediğiniz şablonu bulmak için arama kutusuna **.net Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Şablon sonuçlarını filtrelemek için Tüm  **Visual Basic** açılan  listesinden Windows, Tüm platformlar  **listesinden Windows** ve Tüm proje türleri listesinden Konsol'u **seçebilirsiniz.**

   Konsol Uygulaması **şablonunu seçin** ve ardından Sonraki'ye **tıklayın.**

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Yeni **projenizi yapılandır** penceresinde Proje adı  kutusuna **HelloWorld** yazın, isteğe bağlı olarak proje dosyalarınızın dizin konumunu (varsayılan yerel ayardır) ve ardından `C:\Users\<name>\source\repos` Sonraki'ye **tıklayın.**

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Visual Studio 2019'daki 'Yeni projenizi yapılandır' penceresinin ekran görüntüsü. Burada projenin adını girersiniz.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan menüsünde **.NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019'daki 'Ek bilgiler' penceresinin ekran görüntüsü. Burada istediğiniz .NET Core Framework sürümünü seçersiniz.":::

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısaca, aşağıdakine benzer bir şey görüyoruz:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu düzenleyici penceresinde görünür ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretlerini seçebilirsiniz. Bu kod açıklama özelliği, ihtiyacınız olan kodu gizleyerek ekrandaki dağınıklığı en aza indirmenizi sağlar. Proje dosyaları, Çözüm Gezgini adlı bir pencerede **sağ tarafta listelenir.**

   ![Visual Studio kutuları olan IDE'leri kullanma](media/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de vardır, ancak şimdilik devam edin.

1. Şimdi uygulamayı başlatabilirsiniz. Bunu yapmak için menü çubuğundaki **Hata Ayıklama menüsünden** Hata **Ayıklama** Olmadan Başlat'ı seçebilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata ayıklama > hata ayıklama olmadan başlat menüsü](media/vs-2019/start-without-debugging.png)

   Visual Studio, uygulamayı derler ve şu iletiyle bir konsol penceresi **Merhaba Dünya!**. Artık çalışan bir uygulama var!

   ![Aşağıdaki iletiyi gösteren konsol penceresinin Merhaba Dünya görüntüsü.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Şimdi uygulamaya bazı ek kodlar ekleriz. Aşağıdaki kodu Visual Basic satırın önünde `Console.WriteLine("Hello World!")` ekleyin:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve ardından kullanıcı bir metin girene kadar enter tuşuna **basın.**

1. aşağıdaki kodla `Console.WriteLine("Hello World!")` ifade eden satırı değiştirme:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **Ctrl** F5 tuşlarına basarak + **uygulamayı yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız girin ve Enter tuşuna **basın.**

   ![What is your name sorusunu ve uygulamanın yanıtını gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden düzenlemenin ve [IntelliSense'in](../../ide/using-intellisense.md) daha [verimli](../../ide/refactoring-in-visual-studio.md) bir şekilde kodlamanıza yardımcı olmak için birkaç yolu göz atabilirsiniz.

İlk olarak değişkeni yeniden adlandır `name` o zaman:

1. Seçmek için `name` değişkenine çift tıklayın.

2. değişkeninin yeni adını (kullanıcı adı) **yazın.**

   Değişkenin etrafında gri bir kutu ve kenar boşluğunda bir ampul göründüğüne dikkat et.

3. Kullanılabilir Hızlı Eylemler'i göstermek için ampul [simgesini seçin.](../../ide/quick-actions.md) **'name' adını 'username' olarak yeniden adlandır'ı seçin.**

   ![Yeniden adlandırma eylemi Visual Studio](media/rename-quick-action.png)

   değişkeni proje genelinde yeniden adlandırıldı ve bu bizim durumumuz için yalnızca iki yer.

4. Şimdi IntelliSense'e göz at bakalım. iletisinin yer aldığı `Console.WriteLine("Hello &quot; + username + &quot;!")` satırın altına aşağıdaki kod parçasını yazın:

    ```vb
   Dim now = Date.
   ```

   Sınıfın üyelerini bir kutu <xref:System.DateTime> görüntüler. Ayrıca, o anda seçili olan üyenin açıklaması ayrı bir kutuda görüntülenir.

   ![Visual Studio'daki IntelliSense liste üyeleri](media/intellisense-list-members.png)

5. Sınıfa çift tıklayarak veya yukarı veya aşağı ok tuşlarını kullanarak ve ardından Sekme tuşuna basarak sınıfının bir özelliği olan **Now** adlı üyeyi **seçin.**

6. Bunun altına aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırılırken satır sonlandırıcı eklemeyilmesiyle biraz farklıdır. Bu, çıkışa gönderilen sonraki metnin aynı satırda yazdırılacak olduğu anlamına gelir. Açıklamalarını görmek için kodunda bu yöntemlerin her biri üzerine gelin.

7. Daha sonra kodu biraz daha kısa hale gelecek şekilde yeniden düzenlemeyi kullanacağız. satırda `now` değişkenine `Dim now = Date.Now` tıklayın.

   Bu çizginin kenar boşluğunda küçük bir tornavida simgesi göründüğüne dikkatin.

8. Hangi önerilerin sağ olduğunu görmek için tornavida simgesine Visual Studio tıklayın. Bu durumda, kodun genel [](../../ide/reference/inline-temporary-variable.md) davranışını değiştirmeden bir kod satırı kaldırmak için satır içi geçici değişkeni yeniden düzenlemesi gösteriliyor:

   ![Verilerde satır içi geçici değişken yeniden Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Kodu **yeniden düzenlemesi için Satır içi** geçici değişken'e tıklayın.

::: moniker range="vs-2017"

10. **Ctrl** F5 tuşlarına basarak + **programı yeniden çalıştırın.** Çıkış aşağıdakine benzer:

    ![Program çıktısı ile konsol penceresi](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **Ctrl** F5 tuşlarına basarak + **programı yeniden çalıştırın.** Çıkış aşağıdakine benzer:

    ![Program çıktısı ile konsol penceresi](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Kod hatalarını ayıklama

Kod yazarak çalıştırmanız ve hatalara karşı test etmek gerekir. Visual Studio hata ayıklama sistemi, tek tek bir deyimde adım adım incelemenizi ve değişkenleri ilerlerken incelemenizi sağlar. Kodun *belirli bir satırda* yürütülmesini durduran kesme noktaları ayarlayın. Kod çalıştırıken değişkenin değerinin nasıl değiştiklerini ve daha fazlasını gözlemlersiniz.

Program &quot;uçuşta&quot; olduğu sırada değişkenin `username` değerini görmek için bir kesme noktası ayarla verelim.

1. şöyle bir kod satırı `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` bulun: . Bu kod satırına bir kesme noktası ayarlamak, yani programın yürütmeyi bu satırda duraklatmak için düzenleyicinin en sol kenar boşluğuna tıklayın. Ayrıca kod satırı üzerinde herhangi bir yere tıklar ve ardından **F9 tuşuna basabilirsiniz.**

   En sol kenar boşluğunda kırmızı bir daire görünür ve kod kırmızıyla vurgulanır.

   ![Kod satırı üzerinde kesme noktası Visual Studio](media/breakpoint.png)

1. Hata AyıklamaYı Başlat Hata Ayıklamayı **Başlat'ı**  >  **seçerek veya** F5 tuşuna basarak **hata ayıklamayı başlat.**

1. Konsol penceresi görüntülendiğinde ve adınız sorulup yazarak Enter tuşuna **basın.**

   Odak kod düzenleyicisine Visual Studio ve kesme noktası olan kod satırı sarıyla vurgulanır. Bu, programın yürütecek olduğu bir sonraki kod satırı olduğunu işaret ediyor.

1. Değerini görmek için farenizi `username` değişkenin üzerine gelin. Alternatif olarak, sağ tıklayarak İzleme Ekle'yi seçerek değişkeni İzleme penceresine ekleyebilir ve burada değerini `username` de görebilirsiniz.  

   ![Visual Studio'de hata ayıklama sırasında değişken değeri](media/debugging-variable-value.png)

1. Programın tamamlanmasını çalıştırmak için **F5 tuşuna tekrar** basın.

Hata ayıklama hakkında daha fazla bilgi için Visual Studio hata [ayıklayıcısı özellik turuna bakın.](../../debugger/debugger-feature-tour.md)

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki Visual Studio makalelerle birlikte aşağıdaki adımları daha ayrıntılı bir şekilde keşfedin:

> [!div class="nextstepaction"]
> [Kod düzenleyicisini kullanmayı öğrenin](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- Daha [fazla Visual Studio keşfedin](../../ide/advanced-feature-overview.md)
- Visualstudio.microsoft.com [](https://visualstudio.microsoft.com/vs/)
- Visual Studio [blog'larını okuyun](https://devblogs.microsoft.com/visualstudio/)
