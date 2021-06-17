---
title: "Hızlı Başlangıç: IDE'Visual Studio turu"
description: Tümleşik geliştirme ortamının (IDE) windows, menüler ve Visual Studio kullanıcı arabirimi özelliklerinden bazıları hakkında bilgi edinmek.
ms.custom: acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f10c3fcca5d87f8371d1373314406cf4aa47ec3
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113233"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Hızlı Başlangıç: Visual Studio IDE'ye bakın

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri turuna çıkarsınız.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Büyük olasılıkla Başlangıç Sayfası'Visual Studio açtıktan sonra **göreceğiz ilk şey.** Başlangıç **Sayfası,** ihtiyacınız olan komutları ve proje dosyalarını daha hızlı bulmanıza yardımcı olmak için bir "hub" olarak tasarlanmıştır. Son **bölüm,** son zamanlarda üzerinde çalıştığın projeleri ve klasörleri görüntüler. Yeni **proje altında** bir bağlantıya tıklayarak Yeni  Proje iletişim kutusunu açabilirsiniz veya Aç'ın altında mevcut bir kod projesini veya klasörünü açabilirsiniz. Sağda, en son geliştirici haberlerinin akışı yer alan bir akış yer alan.

![Visual Studio'de Başlangıç Sayfası](media/start-page.png)

Başlangıç Sayfasını kapatıp **yeniden** görmek için Dosya menüsünden yeniden **açabilirsiniz.**

![Dosya menüsündeki Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Bu pencereyi açtıktan sonra ilk olarak Visual Studio penceresi gösterilir. Başlangıç penceresi, "koda daha hızlı" başlamanıza yardımcı olmak için tasarlanmıştır. Kodu kopyalama veya denetleme, mevcut bir proje veya çözümü açma, yeni proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

[![Visual Studio 2019'da başlangıç penceresi](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

İlk kez bir uygulama kullanıyorsanız Visual Studio proje listeniz boş olur.

MSBuild tabanlı olmayan kod temelleriyle çalışıyorsanız, kodunuzu  yerel klasör aç seçeneğini kullanarak Visual Studio. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](develop-code-in-visual-studio-without-projects-or-solutions.md) Aksi takdirde, yeni bir proje oluşturabilir veya GitHub ya da Azure DevOps gibi bir kaynak sağlayıcısından proje Azure DevOps.

Kod **olmadan devam seçeneği,** herhangi bir Visual Studio veya kod yüklenmeden uygulama geliştirme ortamını açar. Bir oturuma katılmak veya hata ayıklama [Live Share](/visualstudio/liveshare/) eklemek için bu seçeneği kullanabilirsiniz. Başlangıç penceresini  kapatıp IDE'ye açmak için Esc tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Bu özelliklerin Visual Studio devam etmek için yeni bir proje oluştur o zaman.

::: moniker range="vs-2017"

1. Başlangıç **Sayfasında,** Yeni proje'nin altındaki arama  kutusuna, proje türleri listesini adlarında "konsol" içerenlerle filtrelemek için konsol yazın.

   ![Başlangıç Sayfasında proje Visual Studio arama](media/start-page-search-templates.png)

   Visual Studio hızla kodlamaya başlamanıza yardımcı olacak çeşitli türlerde proje şablonları sağlar. Bir C# Konsol **Uygulaması (.NET Core) proje** şablonu seçin. (Alternatif olarak, Visual Basic, C++, Javascript veya diğer dil geliştiricisiyseniz bu dillerden birini kullanarak proje oluşturabilirsiniz. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Görüntülenen **Yeni Proje iletişim** kutusunda varsayılan proje adını kabul et ve Tamam'ı **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019'da 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada bir proje şablonu arayabilir, filtreleye ve seçebilirsiniz. Ayrıca son kullanılan proje şablonlarının listesini de gösterir.

1. Proje türleri listesini, adlarında **"konsol"** bulunanlara filtrelemek için en üstte bulunan arama kutusuna console yazın. Tüm dil açılan listesinden **C#** (veya tercihen başka bir dil) seçerek arama sonuçlarını **daha** da geliştirin.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Diliniz olarak C#, Visual Basic veya F# seçeneğini kullandıysanız Konsol Uygulaması şablonunu **ve** ardından Sonraki'yi **seçin.** (Farklı bir dil seçtiysanız herhangi bir şablon seçin. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Yeni **projenizi yapılandır penceresinde** varsayılan proje adını ve konumunu kabul et ve ardından Sonraki'yi **seçin.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Visual Studio 2019'da projenin adını girmenizi istediğiniz 'Yeni bir proje yapılandır' penceresinin ekran görüntüsü.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan menüsünde **.NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019'daki 'Ek bilgiler' penceresinin ekran görüntüsü. Burada istediğiniz .NET Core Framework sürümünü seçersiniz.":::

::: moniker-end

   Proje oluşturulur ve Düzenleyici penceresinde *Program.cs* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

   ![Visual Studio'de düzenleyici](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

**Çözüm Gezgini** genellikle Visual Studio'nin sağ tarafında yer alan Visual Studio projeniz, çözümünüz veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve içinde bir dosyaya **Çözüm Gezgini.**

![Çözüm Gezgini Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Komutların üst kısmında yer alan menü Visual Studio kategorilere ayrılır. Örneğin, **Proje menüsünde** çalışmakta olan projeyle ilgili komutlar vardır. Araçlar **menüsünde Seçenekler'i** seçerek Visual Studio özelliklerini özelleştirebilirsiniz veya Araçları ve Özellikleri Al'ı seçerek özellikleri **yüklemenize ekleyebilirsiniz.**

::: moniker range="vs-2017"

![Visual Studio 2017'de menü çubuğu](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019'da menü çubuğu](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Hata Listesi

Görünüm menüsünü **ve ardından** Hata Listesi'ne **seçerek** Hata Listesi **penceresini açın.**

Hata **Listesi,** kodunuzun geçerli durumuyla ilgili hataları, uyarıyı ve iletileri gösterir. Dosyanız veya projenizin herhangi bir yerinde hatalar (eksik ayraç veya noktalı virgül gibi) varsa bunlar burada listelenir.

![Visual Studio'de Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

Çıkış **penceresi,** projenizi ve kaynak denetim sağlayıcınızdan gelen çıkış iletilerini gösterir.

Bazı derleme çıkışlarını görmek için projeyi derlemeye bakalım. Derleme **menüsünden** Çözümü **Derleme'yi seçin.** Çıkış **penceresi** otomatik olarak odağı alır ve başarılı bir derleme iletisi görüntüler.

![Visual Studio'de çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, web'de neredeyse her şeye gitmek için hızlı ve kolay bir Visual Studio. Yapmak istediğinizle ilgili bazı metinler girebilirsiniz ve metinle ilgili seçeneklerin listesini gösterir. Örneğin, tam olarak derlemenin ne yaptığı hakkında ek ayrıntılar görüntülemek için derleme çıkışının ayrıntısını artırmak istediğinizi düşünün. Bunu şu şekilde yapabiliriz:

::: moniker range="vs-2017"

1. **IDE'Hızlı Başlat** sağ üst köşesindeki arama kutusunu bulun. (Alternatif olarak **Ctrl tuşuna basın** + **Q** ile erişin.)

2. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan, Seçenekler kategorisi **altında Projeler ve Çözümler --> Ve Çalıştır'ı** seçin. 

   ![Visual Studio 2017'de hızlı başlatma arama kutusu](media/quickstart-IDE-quick-launch.png)

   Seçenekler **iletişim** kutusu, Oluşturma ve **Çalıştırma seçenekleri** sayfası açılır.

::: moniker-end

::: moniker range=">=vs-2019"

1. **IDE'nin** üst kısmında bulunan arama kutusunu etkinleştirmek için Ctrl + **Q** tuşlarına basın.

2. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan **MSBuild ayrıntılılığı değiştir'i seçin.**

   ![Visual Studio 2019'da arama kutusu](media/vs-2019/quick-launch-verbosity.png)

   Seçenekler **iletişim** kutusu, Oluşturma ve **Çalıştırma seçenekleri** sayfası açılır.

::: moniker-end

3. **MSBuild proje derleme çıkışı ayrıntılılığı altında** Normal 'i **seçin** ve ardından Tamam'a **tıklayın.**

4. Projenizi yeniden derlemek için konsolda **ConsoleApp1** projesine sağ **tıklayın Çözüm Gezgini** menüden **Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   ![Derlemede ayrıntılı derleme çıkışı Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri Bildirim Gönder menüsü

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, geri bildirim  penceresinin üst kısmında bulunan Geri Bildirim Gönder Visual Studio kullanabilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017'de Geri Bildirim Gönder menüsü](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019'da Geri Bildirim Gönder menüsü](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimiyle tanışmanız için Visual Studio 'nun yalnızca birkaç özelliğine baktık. Daha fazla incelemek için:

> [!div class="nextstepaction"]
> [Kod Düzenleyicisi hakkında bilgi edinin](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 'nun daha fazla özelliği](../ide/advanced-feature-overview.md)
- [Temayı ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
