---
title: "Hızlı Başlangıç: IDE'Visual Studio turu"
description: Tümleşik geliştirme ortamının (IDE) windows, menüler ve Visual Studio kullanıcı arabirimi özelliklerinden bazıları hakkında bilgi edinmek.
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
ms.openlocfilehash: 36d37966a30efdcf6a3d30eaaa824addbaa108c1
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132880090"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Hızlı Başlangıç: IDE'nin Visual Studio bakış

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte windows, menüler ve diğer kullanıcı arabirimi özelliklerinden bazılarında bir tura çıkarsınız.

::: moniker range="vs-2017"

Henüz yüklemedıysanız, Visual Studio yüklemek için [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2019"

Henüz yüklemedıysanız, Visual Studio yüklemek için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

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

[![Visual Studio 2019'da Başlangıç penceresinin ekran görüntüsü.](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

İlk kez bir uygulama kullanıyorsanız Visual Studio proje listeniz boş olur.

Veri tabanlı olmayan kod MSBuild çalışıyorsanız, kodunuzu yerel klasör  aç seçeneğini kullanarak Visual Studio. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](develop-code-in-visual-studio-without-projects-or-solutions.md) Aksi takdirde, yeni bir proje oluşturabilir veya kaynak sağlayıcısından yeni bir proje kopya GitHub veya Azure DevOps.

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

1. Başlangıç **Sayfasında,** Yeni proje'nin altındaki arama  kutusuna, proje türleri listesini adlarında "konsol" içerenlerle filtrelemek için konsol yazın.

   ![Visual Studio 2017'de Başlangıç Sayfasındaki proje şablonları listesini gösteren ekran görüntüsü.](media/start-page-search-templates.png)

   Visual Studio hızla kodlamaya başlamanıza yardımcı olacak çeşitli türlerde proje şablonları sağlar. Bir C# Konsol **Uygulaması (.NET Core) proje** şablonu seçin. (Alternatif olarak, Visual Basic, C++, JavaScript veya diğer dil geliştiricisiyseniz bu dillerden birini kullanarak proje oluşturabilirsiniz. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Görüntülenen **Yeni Project** iletişim kutusunda varsayılan proje adını kabul et ve Tamam'ı **seçin.**

Proje oluşturulur ve Düzenleyici penceresinde *Program.cs* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

![Visual Studio 2017'de Düzenleyici'nin ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019'da 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada bir proje şablonu arayabilir, filtreleye ve seçebilirsiniz. Ayrıca son kullanılan proje şablonlarının listesini de gösterir.

1. Proje türleri listesini, adlarında **"konsol"** bulunanlara filtrelemek için en üstte bulunan arama kutusuna console yazın. Tüm dil açılan listesinden **C#** (veya tercihen başka bir dil) seçerek arama sonuçlarını **daha** da geliştirin.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Diliniz olarak C#, Visual Basic veya F# seçeneğini kullandıysanız Konsol Uygulaması **şablonunu** ve ardından Sonraki'yi **seçin.** (Farklı bir dil seçtiysanız herhangi bir şablon seçin. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Yeni **projenizi yapılandır penceresinde** varsayılan proje adını ve konumunu kabul et ve ardından Sonraki'yi **seçin.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Visual Studio 2019'daki 'Yeni proje yapılandır' penceresinin ekran görüntüsü. Burada projenin adını girersiniz.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan **menüsünde .NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019'daki 'Ek bilgiler' penceresinin ekran görüntüsü. Burada istediğiniz .NET Core Framework sürümünü seçersiniz.":::

Proje oluşturulur ve Düzenleyici penceresinde *Program.cs* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

![Visual Studio 2019'da Düzenleyici penceresini gösteren ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

    :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022'de 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada bir proje şablonu arayabilir, filtreleye ve seçebilirsiniz. Yeni **proje oluştur penceresi,** son kullanılan proje şablonlarının listesini de gösterir.

1. Proje türleri listesini, adlarında *"konsol"* bulunanlara filtrelemek için en üstte bulunan arama kutusuna console yazın. Tüm dil açılan listesinden **C#** (veya tercihen başka bir dil) seçerek arama **sonuçlarını daha** da geliştirin.

    :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="2022'de istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Diliniz olarak C#, Visual Basic veya F# seçeneğini kullandıysanız Konsol Uygulaması **şablonunu** ve ardından Sonraki'yi **seçin.** Farklı bir dil seçtiysanız herhangi bir şablon seçin.

1. Yeni **projenizi yapılandır penceresinde** varsayılan proje adını ve konumunu kabul et ve ardından Sonraki'yi **seçin.**

    :::image type="content" source="media/vs-2022/quickstart-configure-new-project-console.png" alt-text="2022'de projenin adını Visual Studio 'Yeni proje yapılandır' penceresinin ekran görüntüsü.":::

1. Ek bilgiler penceresinde **Framework** açılan menüsünde **.NET 6.0'ın göründüğünden** emin oldu ve oluştur'a **tıklayın.** 

    :::image type="content" source="media/vs-2022/create-project-additional-info.png" alt-text="2022'de istediğiniz .NET sürümünü Visual Studio 'Ek bilgiler' penceresinin ekran görüntüsü.":::

1. Proje oluşturulmuştur. Çözüm Gezgini penceresinde *program.cs* kod  dosyasını seçin. Bu dosya genellikle Visual Studio.

    :::image type="content" source="media/vs-2022/quickstart-opened-new-project.png" alt-text="Visual Studio 2022'de yeni C# konsol projesinin ekran görüntüsü.":::

*Program.cs dosyası* Düzenleyici **penceresinde** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

:::image type="content" source="media/vs-2022/editor.png" alt-text="Visual Studio 2022'de Düzenleyici'nin ekran görüntüsü.":::

::: moniker-end

## <a name="solution-explorer"></a>Çözüm Gezgini

::: moniker range="<=vs-2019"

**Çözüm Gezgini** genellikle Visual Studio'nin sağ tarafında yer alan Visual Studio proje, çözüm veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve içinde bir dosyaya **Çözüm Gezgini.**

![Uygulamanın içinde Çözüm Gezgini gösteren Visual Studio.](media/quickstart-IDE-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

**Çözüm Gezgini** proje, çözüm veya kod klasörünüzdeki dosya ve klasör hiyerarşisinin grafik gösterimini gösterir. Hiyerarşiye göz atabilir ve dosyayı Seçerek Düzenleyici'de **açabilirsiniz.**

:::image type="content" source="media/vs-2022/quickstart-ide-solution-explorer.png" alt-text="Visual Studio 2022'de Çözüm Gezgini ekran görüntüsü.":::

::: moniker-end

## <a name="menus"></a>Menüler

Komutların üst kısmında yer alan menü Visual Studio kategorilere ayrılır. örneğin **Project** menü, üzerinde çalıştığınız projeyle ilgili komutları içerir. **araçlar** menüsünde **seçenekler**' i seçerek Visual Studio davranışını özelleştirebilir veya **araçlar ve özellikler al**' ı seçerek yüklemenize özellikler ekleyebilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de menü çubuğunu gösteren ekran görüntüsü.](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range="vs-2019"

![Visual Studio 2019 ' de menü çubuğunu gösteren ekran görüntüsü.](media/vs-2019/menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/menu-bar.png" alt-text="Visual Studio 2022 ' deki menü çubuğunun ekran görüntüsü.":::

::: moniker-end

## <a name="error-list"></a>Hata Listesi

**Hata listesi** , kodunuzun geçerli durumu hakkında hataları, uyarıları ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde hatalar varsa (eksik küme ayracı veya noktalı virgül gibi), burada listelenirler.

**Hata listesi** penceresini açmak için **Görünüm** menüsünü ve ardından **hata listesi**' ı seçin.

::: moniker range="<=vs-2019"

:::image type="content" source="media/quickstart-IDE-error-list.png" alt-text="Visual Studio 2019 ' deki Hata Listesi ekran görüntüsü.":::

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-ide-error-list.png" alt-text="Visual Studio 2022 ' deki Hata Listesi ekran görüntüsü.":::

::: moniker-end

## <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresinde, projenizi ve kaynak denetimi sağlayıcınızdan oluşturduğunuz çıkış iletileri görüntülenir.

Ayrıca, bazı derleme çıktısını görmek için projeyi derlim. **Build** menüsünde **Build Solution** öğesini seçin. **Çıkış** penceresi otomatik olarak odağı alır ve başarılı bir derleme iletisi gösterir.

::: moniker range="<=vs-2019"

![Visual Studio'daki Çıkış penceresinin ekran görüntüsü.](media/build-output-minimal.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-build-output-minimal.png" alt-text="Visual Studio 2022 ' deki çıkış penceresinin ekran görüntüsü.":::

::: moniker-end

## <a name="search-box"></a>Arama kutusu

Arama kutusu, Visual Studio tüm şeyleri bulmanın hızlı ve kolay bir yoludur. Yapmak istediğiniz şeydir ilgili bir metin girebilirsiniz ve bu, metinle ilgili seçeneklerin bir listesini gösterir. Örneğin, yapı çıkışının ayrıntı düzeyini arttırmak istediğinizi, bu yapılandırmanın ne yaptığını hakkında daha fazla ayrıntı göstermek istediğinizi düşünün. Şunları yapabilirsiniz:

::: moniker range="vs-2017"

1. IDE 'nin sağ üst köşesindeki **Hızlı başlatma** arama kutusunu bulun. (Alternatif olarak, **CTRL** + tuşuna basın Ona **erişmek için.** )

1. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan projeler ve çözümler ' i seçin. > **Seçenekler** kategorisi altında **derleyin ve çalıştırın** .

   ![Visual Studio 2017 ' deki hızlı başlatma arama kutusunun ekran görüntüsü.](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

1. **MSBuild proje derlemesi çıktı ayrıntı düzeyi** altında **Normal**' i seçin ve ardından **tamam**' a tıklayın.

1. **Çözüm Gezgini** ' de **ConsoleApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   ![Visual Studio 2017 ' deki çıkış penceresi içinde daha ayrıntılı bir derleme günlüğünün ekran görüntüsü.](media/build-output-verbose.png)

::: moniker-end

::: moniker range="vs-2019"

1.  + IDE 'nin üst kısmındaki arama kutusunu etkinleştirmek için CTRL **Q** tuşlarına basın.

1. Arama kutusuna **ayrıntı düzeyi** yazın. görünen sonuçlardan **MSBuild ayrıntı düzeyi değiştir**' i seçin.

   ![Visual Studio 2019 ' deki arama kutusunun ekran görüntüsü.](media/vs-2019/quick-launch-verbosity.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

1. **MSBuild proje derlemesi çıktı ayrıntı düzeyi** altında **Normal**' i seçin ve ardından **tamam**' a tıklayın.

1. **Çözüm Gezgini** ' de **ConsoleApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   ![Visual Studio 2019 ' deki çıkış penceresi içinde daha ayrıntılı bir derleme günlüğünün ekran görüntüsü.](media/build-output-verbose.png)

::: moniker-end

::: moniker range=">=vs-2022"

1.  + IDE 'nin üst kısmındaki arama kutusunu etkinleştirmek için CTRL **Q** tuşlarına basın.

1. Arama kutusuna *ayrıntı düzeyi* yazın. görünen sonuçlardan **MSBuild ayrıntı düzeyi değiştir**' i seçin.

   :::image type="content" source="media/vs-2022/quickstart-search-verbosity.png" alt-text="Visual Studio 2022 ' deki arama kutusunun ekran görüntüsü.":::

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

1. **MSBuild proje derlemesi çıktı ayrıntı düzeyi** altında **Normal**' i seçin ve ardından **tamam**' ı seçin.

1. **Çözüm Gezgini** ' de **ConsoleApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   :::image type="content" source="media/vs-2022/quickstart-build-output-verbose.png" alt-text="Visual Studio 2022 ' deki çıkış penceresi içinde daha ayrıntılı bir derleme günlüğünün ekran görüntüsü.":::

::: moniker-end

## <a name="send-feedback-menu"></a>Geri bildirim Gönder menüsü

::: moniker range="vs-2017"

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir veya ürünün nasıl geliştirileceğine ilişkin önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **geri bildirim gönder** menüsünü kullanabilirsiniz.

![Visual Studio 2017 ' deki geri bildirim gönder menüsünün ekran görüntüsü.](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir veya ürünün nasıl geliştirileceğine ilişkin önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **geri bildirim gönder** menüsünü kullanabilirsiniz.

![Visual Studio 2019 ' deki geri bildirim gönder menüsünün ekran görüntüsü.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio kullanırken herhangi bir sorunla karşılaşmalı ya da ürünün nasıl geliştirileceğine ilişkin önerileriniz varsa, bize bilgi verebilirsiniz. Bunu yapmak için, IDE 'nin sağ üst köşesinin yakınında **geri bildirim gönder** düğmesini seçin ve **geri bildirim gönder** menüsündeki geri bildirim seçeneklerinden birini kullanın.

:::image type="content" source="media/vs-2022/quickstart-ide-send-feedback.png" alt-text="Visual Studio 2022 ' deki geri bildirim gönder düğmesinin ve menüsünün ekran görüntüsü.":::

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

kullanıcı arabirimiyle tanışmanız için Visual Studio özelliklerinden yalnızca birkaçını inceledik. Daha fazla incelemek için:

> [!div class="nextstepaction"]
> [Kod Düzenleyicisi hakkında bilgi edinin](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ıde 'ye genel bakış](../get-started/visual-studio-ide.md)
- [Visual Studio daha fazla özelliği](../ide/advanced-feature-overview.md)
- [Temayı ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
