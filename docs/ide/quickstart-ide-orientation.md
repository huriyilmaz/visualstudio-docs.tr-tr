---
title: 'Hızlı başlangıç: Visual Studio IDE turu'
description: Visual Studio tümleşik geliştirme ortamının (IDE) bazı Windows, menü ve diğer kullanıcı arabirimi özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4511658a454c1431967905e88428842c3ba00c64
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870902"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Hızlı başlangıç: Visual Studio IDE 'ye Ilk bakış

Bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (IDE) giriş bölümünde bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri için bir tura çıkacağız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Visual Studio 'Yu açtıktan sonra ilk olarak **Başlangıç sayfası büyük olasılıkla başlangıç sayfasıdır**. **Başlangıç sayfası** , ihtiyacınız olan komutları ve proje dosyalarını hızlı bir şekilde bulmanıza yardımcı olmak için "Hub" olarak tasarlanmıştır. **Son** bölümde, son zamanlarda çalıştığınız projeler ve klasörler görüntülenir. **Yeni proje**' nin altında, **Yeni proje** iletişim kutusunu açmak için bir bağlantıya tıklayabilir veya **Aç**' ın altında varolan bir kod projesini veya klasörünü açabilirsiniz. Sağ tarafta en son geliştirici haberlerinin bir akışı bulunur.

![Visual Studio 'da başlangıç sayfası](media/start-page.png)

**Başlangıç sayfasını** kapatır ve yeniden görmek Isterseniz **dosyayı dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio 'da Dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Visual Studio 'Yu açtıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kopyalama veya kullanıma alma, mevcut bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarını içeren bir klasörü açma seçeneklerine sahiptir.

[![Visual Studio 2019 ' de başlangıç penceresi](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio 'Yu ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild tabanlı olmayan kod tabanlarında çalışıyorsanız, Visual Studio 'da kodunuzu açmak için **yerel klasör aç** seçeneğini kullanacaksınız. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](develop-code-in-visual-studio-without-projects-or-solutions.md). Aksi takdirde, yeni bir proje oluşturabilir veya GitHub ya da Azure DevOps gibi bir kaynak sağlayıcıdan proje kopyalayabilirsiniz.

**Kod olmadan devam et** seçeneği, Visual Studio geliştirme ortamını belirli bir proje veya kod yüklenmeden yalnızca açar. Bir [live share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio 'nun özelliklerini araştırmaya devam etmek için yeni bir proje oluşturalım.

::: moniker range="vs-2017"

1. **Başlangıç sayfasında**, **Yeni proje** altındaki arama kutusuna, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın.

   ![Visual Studio başlangıç sayfasında proje şablonları ara](media/start-page-search-templates.png)

   Visual Studio, hızla kodlamaya başlamanıza yardımcı olan çeşitli türlerde proje şablonları sağlar. Bir C# **konsol uygulaması (.NET Core)** proje şablonu seçin. (Alternatif olarak, bir Visual Basic, C++, JavaScript veya diğer dil geliştirici iseniz, bu dillerden birinde bir proje oluşturmayı ücretsiz olarak kullanabilirsiniz. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. Görüntülenen **Yeni proje** iletişim kutusunda, varsayılan proje adını kabul edin ve **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni bir proje oluşturur** yazılı bir iletişim kutusu açılır. Burada, bir proje şablonunu arayabilir, filtreleyebilir ve seçebilirsiniz. Ayrıca, son kullanılan proje şablonlarının bir listesini gösterir.

1. Üstteki arama kutusunda, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın. **Dil** seçicisinden **C#** (veya tercih ettiğiniz başka bir dil) seçerek arama sonuçlarını daha da belirginleştirin.

   ![Visual Studio 2019 'de yeni proje iletişim kutusu](media/vs-2019/create-a-new-project.png)

1. Diliniz olarak C#, Visual Basic veya F # ' ı seçtiyseniz **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin. (Farklı bir dil seçtiyseniz, herhangi bir şablonu seçmeniz yeterlidir. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. **Yeni projenizi yapılandırın** sayfasında varsayılan proje adını ve konumunu kabul edin ve **Oluştur**' u seçin.

::: moniker-end

   Proje oluşturulur ve **Düzenleyici** penceresinde *program.cs* adlı bir dosya açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve kodlarınızın çoğunun Visual Studio 'da çalışmasını istediğiniz yerdir.

   ![Visual Studio 'da düzenleyici](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

Genellikle Visual Studio 'nun sağ tarafındaki **Çözüm Gezgini**, projenizde, çözümünüzde veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafik bir gösterimini gösterir. Hiyerarşiye gözatabilir ve **Çözüm Gezgini** bir dosyaya gidebilirsiniz.

![Visual Studio 'da Çözüm Gezgini](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio gruplarının üst kısmında bulunan menü çubuğu, kategoriler halinde komutları. Örneğin, **Proje** menüsü, çalışmakta olduğunuz projeyle ilgili komutları içerir. **Araçlar** menüsünde, **Seçenekler**' i seçerek Visual Studio 'Nun davranışını özelleştirebilir veya **Araçlar ve Özellikler al**' ı seçerek yüklemenize özellikler ekleyebilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de menü çubuğu](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de menü çubuğu](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Hata Listesi

**Görünüm** menüsünü seçip **hata listesi** **hata listesi** penceresini açın.

**Hata listesi** , kodunuzun geçerli durumuyla ilgili hataları, uyarıları ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde bir hata (eksik küme ayracı veya noktalı virgül) varsa, burada listelenir.

![Visual Studio 'da Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresinde, projenizi ve kaynak denetimi sağlayıcınızdan oluşturduğunuz çıkış iletileri görüntülenir.

Ayrıca, bazı derleme çıktısını görmek için projeyi derlim. **Build** menüsünde **Build Solution** öğesini seçin. **Çıkış** penceresi, odağı otomatik olarak edinir ve başarılı bir derleme iletisi görüntüler.

![Visual Studio 'da çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, Visual Studio 'da çok daha fazla şeye gitmeniz için hızlı ve kolay bir yoldur. Yapmak istediğiniz konuyla ilgili bir metin girebilirsiniz ve bu, metne ait seçeneklerin bir listesini gösterir. Örneğin, yapı çıkışının ayrıntı düzeyini arttırmak istediğinizi, tam olarak oluşturma işlemi hakkında ek ayrıntılar görüntüleyecek şekilde düşünün. Şunları yapabilirsiniz:

::: moniker range="vs-2017"

1. IDE 'nin sağ üst köşesindeki **Hızlı başlatma** arama kutusunu bulun. (Alternatif olarak, **CTRL** + tuşuna basın Ona **erişmek için.** )

2. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan projeler ve çözümler ' i seçin. > **Seçenekler** kategorisi altında **derleyin ve çalıştırın** .

   ![Visual Studio 2017 'de Hızlı Başlat arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Ctrl** + IDE 'nin üst kısmındaki arama kutusunu etkinleştirmek için CTRL **Q** tuşlarına basın.

2. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan **MSBuild ayrıntı düzeyini Değiştir**' i seçin.

   ![Visual Studio 2019 'de arama kutusu](media/vs-2019/quick-launch-verbosity.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

::: moniker-end

3. **MSBuild proje derlemesi çıkış ayrıntı düzeyi** altında **normal**' i seçin ve ardından **Tamam**' a tıklayın.

4. **Çözüm Gezgini** ' de **ConsoleApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   ![Visual Studio 'da ayrıntılı derleme çıkışı](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri bildirim Gönder menüsü

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir ya da ürünü geliştirme hakkında önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **geri bildirim gönder** menüsünü kullanabilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de geri bildirim menüsü gönder](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de geri bildirim menüsü gönder](media/vs-2019/send-feedback-menu.png)

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
