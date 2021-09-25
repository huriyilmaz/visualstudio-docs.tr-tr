---
title: "Hızlı Başlangıç: IDE'Visual Studio turu"
description: Tümleşik geliştirme ortamının (IDE) windows, menüler ve Visual Studio kullanıcı arabirimi özellikleri hakkında bilgi edinmek.
ms.custom: vs-acquisition
titleSuffix: ''
ms.date: 09/14/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2ff4270fb819c010a31e4dce9e3e3376d41cf205
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428427"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Hızlı Başlangıç: Visual Studio IDE'ye bakın

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte bazı pencereler, menüler ve diğer kullanıcı arabirimi özelliklerine göz atacak.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Büyük olasılıkla Başlangıç Sayfası'Visual Studio açtıktan sonra **göreceğiz ilk şey.** Başlangıç **Sayfası,** ihtiyacınız olan komutları ve proje dosyalarını daha hızlı bulmanıza yardımcı olmak için bir "hub" olarak tasarlanmıştır. Son **bölüm,** son zamanlarda üzerinde çalıştığın projeleri ve klasörleri görüntüler. Yeni **proje altında** bir bağlantıya tıklayarak Yeni  Project iletişim kutusunu açabilir veya Aç'ın altında mevcut bir kod projesini veya klasörünü açabilirsiniz. Sağda, en son geliştirici haberlerinin akışı yer alan bir akış yer alan.

![Visual Studio 2017'de Başlangıç Sayfasının ekran görüntüsü.](media/start-page.png)

Başlangıç Sayfasını kapatıp **yeniden** görmek için Dosya menüsünden yeniden **açabilirsiniz.**

![Visual Studio 2017'de Dosya menüsünün ekran görüntüsü.](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range="vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Bu pencereyi açtıktan sonra ilk olarak Visual Studio penceresi gösterilir. Başlangıç penceresi, "koda daha hızlı" başlamanıza yardımcı olmak için tasarlanmıştır. Kodu kopyalama veya denetleme, mevcut bir proje veya çözümü açma, yeni proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

[![Visual Studio 2019'daki Başlangıç penceresinin ekran görüntüsü.](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

İlk kez bir uygulama kullanıyorsanız Visual Studio proje listeniz boş olur.

Veri tabanlı olmayan kod MSBuild çalışıyorsanız, kodunuzu yerel klasör  aç seçeneğini kullanarak kodlarınızı Visual Studio. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](develop-code-in-visual-studio-without-projects-or-solutions.md) Aksi takdirde, yeni bir proje oluşturabilir veya kaynak sağlayıcısından yeni bir proje kopya GitHub veya Azure DevOps.

Kod **olmadan devam seçeneği,** herhangi bir Visual Studio veya kod yüklenmeden uygulama geliştirme ortamını açar. Bir oturuma katılmak veya hata ayıklama [Live Share](/visualstudio/liveshare/) eklemek için bu seçeneği kullanabilirsiniz. Başlangıç penceresini  kapatıp IDE'ye açmak için Esc tuşuna da basabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="start-window"></a> Başlangıç penceresi

Bu pencereyi açtıktan sonra ilk olarak Visual Studio penceresi gösterilir. Başlangıç penceresi, "koda daha hızlı" başlamanıza yardımcı olmak için tasarlanmıştır. Kodu kopyalama veya denetleme, mevcut bir proje veya çözümü açma, yeni proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

:::image type="content" source="media/vs-2022/quickstart-start-window-labeled.png" border="true" alt-text="2022'de başlangıç penceresini gösteren açıklamalı Visual Studio görüntüsü." lightbox="media/vs-2022/quickstart-start-window-labeled.png":::

İlk kez bir uygulama kullanıyorsanız Visual Studio proje listeniz boş olur.

Yerel klasör kullanmayan kod MSBuild, kodunuzu yerel klasör aç seçeneğini  kullanarak Visual Studio. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](develop-code-in-visual-studio-without-projects-or-solutions.md) Aksi takdirde, yeni bir proje oluşturabilir veya kaynak sağlayıcısından yeni bir proje kopya GitHub veya Azure DevOps.

Kod **olmadan devam seçeneği,** Visual Studio veya kod yüklenmeden geliştirme ortamını açar. Bir oturuma katılmak veya hata ayıklama [Live Share](/visualstudio/liveshare/) eklemek için bu seçeneği kullanabilirsiniz. Başlangıç penceresini  kapatıp IDE'ye açmak için Esc tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Yeni Visual Studio keşfetmeye devam etmek için yeni bir proje oluştur o zaman.

::: moniker range="vs-2017"

1. Başlangıç **Sayfasında,** Yeni proje altındaki arama kutusuna,  proje türleri listesini adlarında "konsol" bulunanlara filtrelemek için konsol yazın.

   ![Visual Studio 2017'de Başlangıç Sayfasında proje şablonlarının listesini gösteren ekran görüntüsü.](media/start-page-search-templates.png)

   Visual Studio hızlı bir şekilde kodlamaya başlamanıza yardımcı olacak çeşitli türlerde proje şablonları sağlar. Bir C# Konsol **Uygulaması (.NET Core) proje** şablonu seçin. (Alternatif olarak, Visual Basic, C++, JavaScript veya diğer dil geliştiricisiyseniz bu dillerden birini kullanarak proje oluşturabilirsiniz. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Görüntülenen **Yeni Project** iletişim kutusunda varsayılan proje adını kabul et ve Tamam'ı **seçin.**

Proje oluşturulur ve Düzenleyici penceresinde *Program.cs* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

![Visual Studio 2017'de Düzenleyici'nin ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019'da 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada bir proje şablonu arayabilir, filtreleye ve seçebilirsiniz. Ayrıca son kullanılan proje şablonlarının listesini de gösterir.

1. Proje türleri listesini, adlarında **"konsol"** bulunanlara filtrelemek için en üstte bulunan arama kutusuna console yazın. Tüm dil açılan listesinden **C#** (veya tercihen başka bir dil) seçerek arama **sonuçlarını** daha da geliştirin.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Diliniz olarak C#, Visual Basic veya F# seçeneğini kullandıysanız Konsol Uygulaması **şablonunu** ve ardından Sonraki'yi **seçin.** (Farklı bir dil seçtiysanız herhangi bir şablon seçin. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Yeni **projenizi yapılandır penceresinde** varsayılan proje adını ve konumunu kabul et ve ardından Sonraki'yi **seçin.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Visual Studio 2019'daki 'Yeni proje yapılandır' penceresinin ekran görüntüsü. Burada projenin adını girersiniz.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan menüsünde **.NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019'daki 'Ek bilgiler' penceresinin ekran görüntüsü. Burada istediğiniz .NET Core Framework sürümünü seçersiniz.":::

Proje oluşturulur ve Düzenleyici penceresinde *Program.cs* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

![Visual Studio 2019'daki Düzenleyici penceresini gösteren ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022'de 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada bir proje şablonu arayabilir, filtreleye ve seçebilirsiniz. Yeni **proje oluştur penceresi,** son kullanılan proje şablonlarının listesini de gösterir.

1. Proje türleri listesini, adlarında *"konsol"* bulunanlara filtrelemek için en üstte bulunan arama kutusuna console yazın. Tüm dil açılan listesinden **C#** (veya tercihen başka bir dil) seçerek arama **sonuçlarını daha da** geliştirin.

    :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="2022'de istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Diliniz olarak C#, Visual Basic veya F# seçeneğini kullandıysanız Konsol Uygulaması **şablonunu** ve ardından Sonraki'yi **seçin.** Farklı bir dil seçtiysanız herhangi bir şablon seçin.

1. Yeni **projenizi yapılandır penceresinde** varsayılan proje adını ve konumunu kabul et ve ardından Sonraki'yi **seçin.**

    :::image type="content" source="media/vs-2022/quickstart-configure-new-project-console.png" alt-text="2022'de projenin adını Visual Studio 'Yeni proje yapılandır' penceresinin ekran görüntüsü.":::

1. Ek bilgiler penceresinde **Çerçeve** açılan menüsünde  **.NET 6.0 (Önizleme)** seçeneğinin göründüğünden emin oldu ve oluştur'a **tıklayın.**

    :::image type="content" source="media/vs-2022/create-project-additional-info.png" alt-text="2022'de istediğiniz .NET sürümünü Visual Studio 'Ek bilgiler' penceresinin ekran görüntüsü.":::

1. Proje oluşturulmuştur. Çözüm Gezgini penceresinde *program.cs* kod dosyasını **seçin.** Bu dosya genellikle Visual Studio.

    :::image type="content" source="media/vs-2022/quickstart-opened-new-project.png" alt-text="Visual Studio 2022'de yeni C# konsol projesinin ekran görüntüsü.":::

*Program.cs dosyası* Düzenleyici **penceresinde** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

:::image type="content" source="media/vs-2022/editor.png" alt-text="Visual Studio 2022'de Düzenleyici'nin ekran görüntüsü.":::

::: moniker-end

## <a name="solution-explorer"></a>Çözüm Gezgini

::: moniker range="<=vs-2019"

**Çözüm Gezgini** genellikle Visual Studio'nin sağ tarafında bulunan Visual Studio, proje, çözüm veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve içinde bir dosyaya **Çözüm Gezgini.**

![Dosyanın içinde Çözüm Gezgini gösteren Visual Studio.](media/quickstart-IDE-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

**Çözüm Gezgini** proje, çözüm veya kod klasörünüzdeki dosya ve klasör hiyerarşisinin grafik gösterimini gösterir. Hiyerarşiye göz atabilir ve dosyayı Seçerek Düzenleyici'de **açabilirsiniz.**

:::image type="content" source="media/vs-2022/quickstart-ide-solution-explorer.png" alt-text="Visual Studio 2022'de Çözüm Gezgini ekran görüntüsü.":::

::: moniker-end

## <a name="menus"></a>Menüler

Üst kısmında yer alan menü çubuğu, Visual Studio gruplara ayrılır. Örneğin, **Project** menüsünde çalışmakta olan projeyle ilgili komutlar vardır. Araçlar **menüsünde Seçenekler'i** seçerek Visual Studio özelliklerini özelleştirebilirsiniz veya Araçları ve Özellikleri Al'ı seçerek **yüklemenize özellikler ekleyebilirsiniz.**

::: moniker range="vs-2017"

![Visual Studio 2017'de Menü çubuğunu gösteren ekran görüntüsü.](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range="vs-2019"

![Visual Studio 2019'daki Menü çubuğunu gösteren ekran görüntüsü.](media/vs-2019/menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/menu-bar.png" alt-text="Visual Studio 2022'de Menü çubuğunun ekran görüntüsü.":::

::: moniker-end

## <a name="error-list"></a>Hata Listesi

Hata **Listesi,** kodunuzun geçerli durumuyla ilgili hataları, uyarıyı ve iletileri gösterir. Dosyanız veya projenizin herhangi bir yerinde hatalar (eksik ayraç veya noktalı virgül gibi) varsa bunlar burada listelenir.

Hata Listesi **penceresini açmak için** Görünüm menüsünü **ve** ardından Hata Listesi'ne **tıklayın.**

::: moniker range="<=vs-2019"

:::image type="content" source="media/quickstart-IDE-error-list.png" alt-text="Visual Studio 2019'daki Hata Listesi'nin ekran görüntüsü.":::

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-ide-error-list.png" alt-text="Visual Studio 2022'de Hata Listesi'nin ekran görüntüsü.":::

::: moniker-end

## <a name="output-window"></a>Çıktı penceresi

Çıkış **penceresi,** projenizi ve kaynak denetim sağlayıcınızdan gelen çıkış iletilerini gösterir.

Bazı derleme çıkışlarını görmek için projeyi derlemeye bakalım. Derleme **menüsünden** Çözümü **Derleme'yi seçin.** Çıkış **penceresi** odağı otomatik olarak alır ve başarılı bir derleme iletisi gösterir.

::: moniker range="<=vs-2019"

![Visual Studio'daki Çıkış penceresinin ekran görüntüsü.](media/build-output-minimal.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-build-output-minimal.png" alt-text="Visual Studio 2022'de Çıkış penceresinin ekran görüntüsü.":::

::: moniker-end

## <a name="search-box"></a>Arama kutusu

Arama kutusu, her şeyi bulmanın hızlı ve kolay bir yolu Visual Studio. Yapmak istediğinizle ilgili bazı metinler girebilirsiniz ve metinle ilgili seçeneklerin listesi görüntülenir. Örneğin, derlemenin ne yaptığı hakkında daha fazla ayrıntı görüntülemek için derleme çıkışının ayrıntısını artırmak istediğinizi düşünün. Bunu şu şekilde yapabiliriz:

::: moniker range="vs-2017"

1. **IDE'Hızlı Başlat** sağ üst köşesindeki arama kutusunu bulun. (Alternatif olarak **Ctrl tuşuna basın** + **Q** ile erişin.)

1. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan, Seçenekler kategorisi **altında Projeler ve Çözümler --> Ve Çalıştır'ı** seçin. 

   ![Visual Studio 2017'de Hızlı başlatma arama kutusunun ekran görüntüsü.](media/quickstart-IDE-quick-launch.png)

   Seçenekler **iletişim** kutusu Derleme ve **Çalıştırma seçenekleri** sayfası açılır.

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal 'i seçin** ve ardından Tamam'a **tıklayın.** 

1. Projenizi yeniden derlemek için konsolda **ConsoleApp1** projesine sağ **Çözüm Gezgini** ve bağlam **menüsünden Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   ![Visual Studio 2017'de Çıkış penceresindeki daha ayrıntılı derleme günlüğünün ekran görüntüsü.](media/build-output-verbose.png)

::: moniker-end

::: moniker range="vs-2019"

1. **IDE'nin** üst kısmında bulunan arama kutusunu etkinleştirmek için Ctrl + **Q** tuşlarına basın.

1. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan, Değişiklik **ve MSBuild seçin.**

   ![Visual Studio 2019'daki Arama kutusunun ekran görüntüsü.](media/vs-2019/quick-launch-verbosity.png)

   Seçenekler **iletişim** kutusu Derleme ve **Çalıştırma seçenekleri** sayfası açılır.

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal 'i seçin** ve ardından Tamam'a **tıklayın.** 

1. Projenizi yeniden derlemek için konsolda **ConsoleApp1** projesine sağ **Çözüm Gezgini** ve bağlam **menüsünden Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   ![Visual Studio 2019'daki Çıkış penceresindeki daha ayrıntılı derleme günlüğünün ekran görüntüsü.](media/build-output-verbose.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. **IDE'nin** üst kısmında bulunan arama kutusunu etkinleştirmek için Ctrl + **Q** tuşlarına basın.

1. Arama *kutusuna ayrıntılı* yazın. Görüntülenen sonuçlardan, Değişiklik **ve MSBuild seçin.**

   :::image type="content" source="media/vs-2022/quickstart-search-verbosity.png" alt-text="Visual Studio 2022'de Arama kutusunun ekran görüntüsü.":::

   Seçenekler **iletişim** kutusu Derleme ve **Çalıştırma seçenekleri** sayfası açılır.

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal'i** ve **ardından** Tamam'ı **seçin.**

1. Projenizi yeniden derlemek için konsolda **ConsoleApp1** projesine sağ **Çözüm Gezgini** ve bağlam **menüsünden Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   :::image type="content" source="media/vs-2022/quickstart-build-output-verbose.png" alt-text="Visual Studio 2022'de Çıkış penceresindeki daha ayrıntılı derleme günlüğünün ekran görüntüsü.":::

::: moniker-end

## <a name="send-feedback-menu"></a>Geri Bildirim Gönder menüsü

::: moniker range="vs-2017"

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, geri bildirim  penceresinin üst kısmında bulunan Geri Bildirim Gönder menüsünü Visual Studio kullanabilirsiniz.

![Visual Studio 2017'de Geri Bildirim Gönder menüsünün ekran görüntüsü.](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, geri bildirim  penceresinin üst kısmında bulunan Geri Bildirim Gönder menüsünü Visual Studio kullanabilirsiniz.

![Visual Studio 2019'da Geri Bildirim Gönder menüsünün ekran görüntüsü.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

::: moniker range=">=vs-2022"

Ürünü kullanırken herhangi bir sorun Visual Studio veya ürünü nasıl iyileştirdiğinize ilişkin önerileriniz varsa bize haber veabilirsiniz. Bunu yapmak için **IDE'nin** sağ üst köşesindeki Geri Bildirim Gönder düğmesini seçin ve Geri Bildirim Gönder menüsündeki geri bildirim **seçenekleriden birini** kullanın.

:::image type="content" source="media/vs-2022/quickstart-ide-send-feedback.png" alt-text="Visual Studio 2022'de Geri Bildirim Gönder düğmesinin ve menüsünün ekran görüntüsü.":::

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimi hakkında bilgi almak için Visual Studio özelliklerine göz atalım. Daha fazla bilgi için:

> [!div class="nextstepaction"]
> [Kod düzenleyicisi hakkında bilgi](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
- [Daha fazla Visual Studio](../ide/advanced-feature-overview.md)
- [Tema ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
