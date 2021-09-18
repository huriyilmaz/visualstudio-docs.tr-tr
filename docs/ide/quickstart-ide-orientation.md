---
title: 'hızlı başlangıç: Visual Studio ıde turu'
description: Visual Studio tümleşik geliştirme ortamının (ıde) bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri hakkında bilgi edinin.
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
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920458"
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

![Visual Studio 2017 ' deki başlangıç sayfasının ekran görüntüsü.](media/start-page.png)

**Başlangıç sayfasını** kapatır ve yeniden görmek Isterseniz **dosyayı dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio 2017 ' deki dosya menüsünün ekran görüntüsü.](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range="vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Visual Studio açtıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kopyalama veya kullanıma alma, mevcut bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarını içeren bir klasörü açma seçeneklerine sahiptir.

[![Visual Studio 2019 ' deki başlangıç penceresinin ekran görüntüsü.](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild tabanlı olmayan kod tabanlarında çalışıyorsanız, kodunuzu Visual Studio açmak için **yerel klasör aç** seçeneğini kullanacaksınız. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](develop-code-in-visual-studio-without-projects-or-solutions.md). aksi takdirde, yeni bir proje oluşturabilir veya GitHub veya Azure DevOps gibi bir kaynak sağlayıcıdan bir proje kopyalayabilirsiniz.

**kod olmadan devam et** seçeneği, yalnızca belirli bir proje veya kod yüklenmeden Visual Studio geliştirme ortamını açar. bir [Live Share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="start-window"></a> Başlangıç penceresi

Visual Studio açtıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kopyalama veya kullanıma alma, mevcut bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarına sahip bir klasörü açma seçeneklerine sahiptir.

:::image type="content" source="media/vs-2022/quickstart-start-window-labeled.png" border="true" alt-text="Visual Studio 2022 ' deki başlangıç penceresini gösteren açıklamalı ekran görüntüsü." lightbox="media/vs-2022/quickstart-start-window-labeled.png":::

Visual Studio ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild kullanmayan codetabanlarla çalışıyorsanız, kodunuzu Visual Studio açmak için **yerel klasör aç** seçeneğini kullanırsınız. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](develop-code-in-visual-studio-without-projects-or-solutions.md). aksi takdirde, yeni bir proje oluşturabilir veya GitHub veya Azure DevOps gibi bir kaynak sağlayıcıdan bir proje kopyalayabilirsiniz.

**kod olmadan devam et** seçeneği, hiçbir belirli proje veya kod yüklenmeden Visual Studio geliştirme ortamını açar. bir [Live Share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio özelliklerini araştırmaya devam etmek için yeni bir proje oluşturalım.

::: moniker range="vs-2017"

1. **Başlangıç sayfasında**, **Yeni proje** altındaki arama kutusuna, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın.

   ![Visual Studio 2017 ' de başlangıç sayfasında proje şablonlarının listesini gösteren ekran görüntüsü.](media/start-page-search-templates.png)

   Visual Studio hızla kodlamaya başlamanıza yardımcı olan çeşitli türlerde proje şablonları sağlar. Bir C# **konsol uygulaması (.NET Core)** proje şablonu seçin. (alternatif olarak, bir Visual Basic, C++, JavaScript veya diğer dil geliştirici iseniz, bu dillerden birinde bir proje oluşturmayı ücretsiz olarak kullanabilirsiniz. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. görüntülenen **yeni Project** iletişim kutusunda, varsayılan proje adını kabul edin ve **tamam**' ı seçin.

Proje oluşturulur ve **Düzenleyici** penceresinde *program. cs* adlı bir dosya açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve Visual Studio kodlarınızın büyük bir kısmını.

![Visual Studio 2017 ' deki düzenleyiciyi gösteren ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range="vs-2019"

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

Proje oluşturulur ve **Düzenleyici** penceresinde *program. cs* adlı bir dosya açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve Visual Studio kodlarınızın büyük bir kısmını.

![Visual Studio 2019 ' de düzenleyici penceresini gösteren ekran görüntüsü.](media/editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

    :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022 ' de ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türü için gereken temel dosyaları ve ayarları içerir.

   Burada, bir proje şablonunu arayabilir, filtreleyebilir ve seçebilirsiniz. **Yeni proje oluştur** penceresi, son kullanılan proje şablonlarının bir listesini de gösterir.

1. Üstteki arama kutusunda, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için *konsol* yazın. **Tüm dil** açılan listesinden **C#** (veya tercih ettiğiniz başka bir dil) seçerek arama sonuçlarını daha da belirginleştirin.

    :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Visual Studio 2022 ' de, istediğiniz şablonu seçtiğinizde ' yeni proje oluştur ' penceresinin ekran görüntüsü.":::

1. diliniz olarak C#, Visual Basic veya F # ' ı seçtiyseniz **konsol uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin. Farklı bir dil seçtiyseniz, herhangi bir şablonu seçmeniz yeterlidir.

1. **Yeni projeyi yapılandırın** penceresinde, varsayılan proje adını ve konumunu kabul edin ve ardından **İleri**' yi seçin.

    :::image type="content" source="media/vs-2022/quickstart-configure-new-project-console.png" alt-text="Visual Studio 2022 ' de projenin adını girdiğiniz ' yeni proje yapılandırma ' penceresinin ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.net 6,0 (Önizleme)** ' nin **çerçeve** açılan menüsünde göründüğünden emin olun ve ardından **Oluştur**' u seçin.

    :::image type="content" source="media/vs-2022/create-project-additional-info.png" alt-text="Visual Studio 2022 ' deki ' ek bilgi ' penceresinin, istediğiniz .net sürümünü seçtiğiniz ekran görüntüsü.":::

1. Proje oluşturulmuştur. **Çözüm Gezgini** penceresinde, genellikle Visual Studio sağ tarafında olan kod dosyası *program. cs* ' yi seçin.

    :::image type="content" source="media/vs-2022/quickstart-opened-new-project.png" alt-text="Visual Studio 2022 ' deki yeni C# konsol projesinin ekran görüntüsü.":::

Dosya *programı. cs* , **Düzenleyici** penceresinde açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve Visual Studio kodlarınızın büyük bir kısmını.

:::image type="content" source="media/vs-2022/editor.png" alt-text="Visual Studio 2022 ' deki düzenleyicinin ekran görüntüsü.":::

::: moniker-end

## <a name="solution-explorer"></a>Çözüm Gezgini

::: moniker range="<=vs-2019"

genellikle Visual Studio sağ tarafında bulunan **Çözüm Gezgini**, projenizde, çözümünüzde veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafik gösterimini gösterir. Hiyerarşiye gözatabilir ve **Çözüm Gezgini** bir dosyaya gidebilirsiniz.

![Visual Studio Çözüm Gezgini gösteren ekran görüntüsü.](media/quickstart-IDE-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

**Çözüm Gezgini** , projenizde, çözümünüzde veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafik gösterimini gösterir. Hiyerarşiye gözatıp **düzenleyicide** açılacak bir dosya seçebilirsiniz.

:::image type="content" source="media/vs-2022/quickstart-ide-solution-explorer.png" alt-text="Visual Studio 2022 Çözüm Gezgini ekran görüntüsü.":::

::: moniker-end

## <a name="menus"></a>Menüler

Visual Studio gruplar komutlarının üst kısmında bulunan menü çubuğu kategoriler halinde. Örneğin, **Project** menüsünde çalışmakta olan projeyle ilgili komutlar vardır. Araçlar **menüsünde Seçenekler'i** seçerek Visual Studio özelliklerini özelleştirebilirsiniz veya Araçları ve Özellikleri Al'ı seçerek **yüklemenize özellik ekleyebilirsiniz.**

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

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal**'i seçin ve ardından Tamam'a **tıklayın.** 

1. Projenizi yeniden derlemek için konsolda **ConsoleApp1** projesine sağ **Çözüm Gezgini** ve bağlam **menüsünden Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   ![Visual Studio 2017'de Çıkış penceresindeki daha ayrıntılı derleme günlüğünün ekran görüntüsü.](media/build-output-verbose.png)

::: moniker-end

::: moniker range="vs-2019"

1. **IDE'nin** üst kısmında bulunan arama kutusunu etkinleştirmek için Ctrl + **Q** tuşlarına basın.

1. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan, Değişiklik **ve MSBuild seçin.**

   ![Visual Studio 2019'daki Arama kutusunun ekran görüntüsü.](media/vs-2019/quick-launch-verbosity.png)

   Seçenekler **iletişim** kutusu Derleme ve **Çalıştırma seçenekleri** sayfası açılır.

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal**'i seçin ve ardından Tamam'a **tıklayın.** 

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

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, geri bildirim  penceresinin üst kısmında bulunan Geri Bildirim Gönder Visual Studio kullanabilirsiniz.

![Visual Studio 2017'de Geri Bildirim Gönder menüsünün ekran görüntüsü.](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, geri bildirim  penceresinin üst kısmında bulunan Geri Bildirim Gönder Visual Studio kullanabilirsiniz.

![Visual Studio 2019'da Geri Bildirim Gönder menüsünün ekran görüntüsü.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

::: moniker range=">=vs-2022"

Ürünü kullanırken herhangi bir sorun Visual Studio veya ürünü iyileştirmeye yönelik önerileriniz varsa bize haber veabilirsiniz. Bunu yapmak için **IDE'nin** sağ üst köşesindeki Geri Bildirim Gönder düğmesini seçin ve Geri Bildirim Gönder menüsündeki geri bildirim **seçenekleriden birini** kullanın.

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
