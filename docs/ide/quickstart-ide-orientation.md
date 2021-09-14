---
title: 'hızlı başlangıç: Visual Studio ıde turu'
description: Visual Studio tümleşik geliştirme ortamının (ıde) bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri hakkında bilgi edinin.
ms.custom: vs-acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: eb31e62a74b9309d86a02005047fd0c96bb2e1e4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635969"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>hızlı başlangıç: Visual Studio ıde 'ye ilk bakış

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş bölümünde bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri için bir tura çıkacağız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Visual Studio açtıktan sonra göreceğiniz ilk şey, büyük olasılıkla **başlangıç sayfasıdır**. **Başlangıç sayfası** , ihtiyacınız olan komutları ve proje dosyalarını hızlı bir şekilde bulmanıza yardımcı olmak için "Hub" olarak tasarlanmıştır. **Son** bölümde, son zamanlarda çalıştığınız projeler ve klasörler görüntülenir. **yeni proje** altında, **yeni Project** iletişim kutusunu açmak için bir bağlantıya tıklayabilir veya **aç**' ın altında var olan bir kod projesini veya klasörünü açabilirsiniz. Sağ tarafta en son geliştirici haberlerinin bir akışı bulunur.

![Visual Studio başlangıç sayfası](media/start-page.png)

**Başlangıç sayfasını** kapatır ve yeniden görmek Isterseniz **dosyayı dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Visual Studio açtıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kopyalama veya kullanıma alma, mevcut bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarını içeren bir klasörü açma seçeneklerine sahiptir.

[![Visual Studio 2019 ' de başlangıç penceresi](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild tabanlı olmayan kod tabanlarında çalışıyorsanız, kodunuzu Visual Studio açmak için **yerel klasör aç** seçeneğini kullanacaksınız. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](develop-code-in-visual-studio-without-projects-or-solutions.md). aksi takdirde, yeni bir proje oluşturabilir veya GitHub veya Azure DevOps gibi bir kaynak sağlayıcıdan bir proje kopyalayabilirsiniz.

**kod olmadan devam et** seçeneği, yalnızca belirli bir proje veya kod yüklenmeden Visual Studio geliştirme ortamını açar. bir [Live Share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio özelliklerini araştırmaya devam etmek için yeni bir proje oluşturalım.

::: moniker range="vs-2017"

1. **Başlangıç sayfasında**, **Yeni proje** altındaki arama kutusuna, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın.

   ![Visual Studio başlangıç sayfasında proje şablonları ara](media/start-page-search-templates.png)

   Visual Studio hızla kodlamaya başlamanıza yardımcı olan çeşitli türlerde proje şablonları sağlar. Bir C# **konsol uygulaması (.NET Core)** proje şablonu seçin. (alternatif olarak, bir Visual Basic, C++, Javascript veya diğer dil geliştirici iseniz, bu dillerden birinde bir proje oluşturmayı ücretsiz olarak kullanabilirsiniz. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. görüntülenen **yeni Project** iletişim kutusunda, varsayılan proje adını kabul edin ve **tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 ' de ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada, bir proje şablonunu arayabilir, filtreleyebilir ve seçebilirsiniz. Ayrıca, son kullanılan proje şablonlarının bir listesini gösterir.

1. Üstteki arama kutusunda, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın. **Tüm dil** açılır listesinden **C#** (veya tercih ettiğiniz başka bir dil) seçerek arama sonuçlarını daha da belirginleştirin.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Visual Studio 2019 ' de, istediğiniz şablonu seçtiğinizde ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

1. diliniz olarak C#, Visual Basic veya F # ' ı seçtiyseniz **konsol uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin. (Farklı bir dil seçtiyseniz, herhangi bir şablonu seçmeniz yeterlidir. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. **Yeni projeyi yapılandırın** penceresinde, varsayılan proje adını ve konumunu kabul edin ve ardından **İleri**' yi seçin.

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Visual Studio 2019 ' de projenin adını girdiğiniz ' yeni proje yapılandırma ' penceresinin ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' in **hedef çerçeve** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' a tıklayın.

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019 ' de, istediğiniz .net Core Framework sürümünü seçtiğiniz ' ek bilgiler ' penceresinin ekran görüntüsü.":::

::: moniker-end

   Proje oluşturulur ve **Düzenleyici** penceresinde *program. cs* adlı bir dosya açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve Visual Studio kodlarınızın büyük bir kısmını.

   ![Visual Studio Düzenleyicisi](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

genellikle Visual Studio sağ tarafında bulunan **Çözüm Gezgini**, projenizde, çözümünüzde veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafik gösterimini gösterir. Hiyerarşiye gözatabilir ve **Çözüm Gezgini** bir dosyaya gidebilirsiniz.

![Visual Studio Çözüm Gezgini](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio gruplar komutlarının üst kısmında bulunan menü çubuğu kategoriler halinde. örneğin **Project** menü, üzerinde çalıştığınız projeyle ilgili komutları içerir. **araçlar** menüsünde **seçenekler**' i seçerek Visual Studio davranışını özelleştirebilir veya **araçlar ve özellikler al**' ı seçerek yüklemenize özellikler ekleyebilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de menü çubuğu](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de menü çubuğu](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Hata Listesi

**Görünüm** menüsünü seçip **hata listesi** **hata listesi** penceresini açın.

**Hata listesi** , kodunuzun geçerli durumuyla ilgili hataları, uyarıları ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde bir hata (eksik küme ayracı veya noktalı virgül) varsa, burada listelenir.

![Visual Studio Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresinde, projenizi ve kaynak denetimi sağlayıcınızdan oluşturduğunuz çıkış iletileri görüntülenir.

Ayrıca, bazı derleme çıktısını görmek için projeyi derlim. **Build** menüsünde **Build Solution** öğesini seçin. **Çıkış** penceresi, odağı otomatik olarak edinir ve başarılı bir derleme iletisi görüntüler.

![Visual Studio çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, Visual Studio çok fazla şeye gitmek için hızlı ve kolay bir yoldur. Yapmak istediğiniz konuyla ilgili bir metin girebilirsiniz ve bu, metne ait seçeneklerin bir listesini gösterir. Örneğin, yapı çıkışının ayrıntı düzeyini arttırmak istediğinizi, tam olarak oluşturma işlemi hakkında ek ayrıntılar görüntüleyecek şekilde düşünün. Şunları yapabilirsiniz:

::: moniker range="vs-2017"

1. IDE 'nin sağ üst köşesindeki **Hızlı başlatma** arama kutusunu bulun. (Alternatif olarak, **CTRL** + tuşuna basın Ona **erişmek için.** )

2. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan projeler ve çözümler ' i seçin. > **Seçenekler** kategorisi altında **derleyin ve çalıştırın** .

   ![Visual Studio 2017 ' de hızlı başlat arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

::: moniker-end

::: moniker range=">=vs-2019"

1.  + IDE 'nin üst kısmındaki arama kutusunu etkinleştirmek için CTRL **Q** tuşlarına basın.

2. Arama kutusuna **ayrıntı düzeyi** yazın. görünen sonuçlardan **MSBuild ayrıntı düzeyi değiştir**' i seçin.

   ![Visual Studio 2019 ' de arama kutusu](media/vs-2019/quick-launch-verbosity.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

::: moniker-end

3. **MSBuild proje derlemesi çıktı ayrıntı düzeyi** altında **Normal**' i seçin ve ardından **tamam**' a tıklayın.

4. **Çözüm Gezgini** ' de **ConsoleApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   ![Visual Studio ayrıntılı derleme çıkışı](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri bildirim Gönder menüsü

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir veya ürünün nasıl geliştirileceğine ilişkin önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **geri bildirim gönder** menüsünü kullanabilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de geri bildirim gönder menüsü](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de geri bildirim gönder menüsü](media/vs-2019/send-feedback-menu.png)

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
