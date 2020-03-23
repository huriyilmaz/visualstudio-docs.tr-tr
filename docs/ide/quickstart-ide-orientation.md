---
title: Görsel Stüdyo IDE Turu
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75596976"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Quickstart: Visual Studio IDE ilk bakış

Visual Studio entegre geliştirme ortamı (IDE) için bu 5-10 dakikalık giriş, bazı pencereler, menüler ve diğer UI özellikleri bir tur alırsınız.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Visual Studio'yu açtıktan sonra göreceğiniz ilk şey büyük olasılıkla **Başlangıç Sayfasıdır.** **Başlangıç Sayfası,** ihtiyacınız olan komutları ve proje dosyalarını daha hızlı bulmanıza yardımcı olmak için bir "hub" olarak tasarlanmıştır. **Son** bölümde, son zamanlarda üzerinde çalıştığınız projeler ve klasörler görüntülenir. **Yeni proje**altında, **Yeni Proje** iletişim kutusunu açmak için bir bağlantıyı tıklatabilir veya **Aç**altında, varolan bir kod projesi veya klasörü açabilirsiniz. Sağtarafta en son geliştirici haberleri bir besleme.

![Visual Studio'da Başlangıç Sayfası](media/start-page.png)

**Başlangıç Sayfasını** kapatıp yeniden görmek isterseniz, **Dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio'da dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Başlangıç penceresi

Visual Studio'yu açtıktan sonra göreceğiniz ilk şey başlangıç penceresidir. Başlangıç penceresi, "koda daha hızlı girmenize" yardımcı olmak için tasarlanmıştır. Kodu klonlama veya kullanıma verme, varolan bir proje yi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

[![Visual Studio 2019'da başlangıç penceresi](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio'yu ilk kez kullanıyorsanız, son proje listeniz boş olacaktır.

MSBuild tabanlı olmayan codebases ile çalışıyorsanız, Visual Studio'da kodunuzu açmak için **yerel klasör** aç seçeneğini kullanırsınız. Daha fazla bilgi için visual [studio'da proje veya çözüm olmadan kod geliştir'e](develop-code-in-visual-studio-without-projects-or-solutions.md)bakın. Aksi takdirde, GitHub veya Azure DevOps gibi bir kaynak sağlayıcıdan yeni bir proje oluşturabilir veya proje klonlayabilirsiniz.

**Kodsuz Devam** seçeneği, Visual Studio geliştirme ortamını belirli bir proje veya kod yüklenmeden açar. [Canlı Paylaşım](/visualstudio/liveshare/) oturumuna katılmak veya hata ayıklama işlemine eklemek için bu seçeneği seçebilirsiniz. Ayrıca başlangıç penceresini kapatmak ve IDE'yi açmak için **Esc** tuşuna basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio'nun özelliklerini keşfetmeye devam etmek için yeni bir proje oluşturalım.

::: moniker range="vs-2017"

1. Başlangıç **Sayfasında,** **Yeni proje**altındaki arama kutusunda, kendi adlarında "konsol" bulunan proje türlerinin listesini filtrelemek için **konsola** yazın.

   ![Visual Studio Başlangıç Sayfasında proje şablonlarını ara](media/start-page-search-templates.png)

   Visual Studio, hızlı bir şekilde kodlamaya başlamanıza yardımcı olan çeşitli proje şablonları sağlar. C# **Console App (.NET Core)** proje şablonu seçin. (Alternatif olarak, Visual Basic, C++, Javascript veya başka bir dil geliştiricisiyseniz, bu dillerden birinde bir proje oluşturmaktan çekinmeyin. Bakacağız UI tüm programlama dilleri için benzer.)

1. Görünen **Yeni Proje** iletişim kutusunda varsayılan proje adını kabul edin ve **Tamam'ı**seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   **Yeni bir proje oluştur**yazan bir iletişim kutusu açılır. Burada, bir proje şablonunu arayabilir, filtreleyebilir ve seçebilirsiniz. Ayrıca, en son kullandığınız proje şablonlarınızın listesini de gösterir.

1. Üstteki arama kutusunda, proje türlerinin listesini adlarında "konsol" bulunanlara filtrelemek için **konsola** yazın. **Dil** seçiciden **C#** (veya seçtiğiniz başka bir dil) seçerek arama sonuçlarını daha da hassaslaştırın.

   ![Visual Studio 2019'da yeni proje iletişim kutusu](media/vs-2019/create-a-new-project.png)

1. Diliniz olarak C#, Visual Basic veya F# seçtiyseniz, **Konsol Uygulaması (.NET Core)** şablonunu seçin ve **ardından İleri'yi**seçin. (Farklı bir dil seçtiyseniz, herhangi bir şablon seçmenniz. Bakacağız UI tüm programlama dilleri için benzer.)

1. Yeni **proje sayfanızı Yapılandır'da** varsayılan proje adını ve konumunu kabul edin ve ardından **Oluştur'u**seçin.

::: moniker-end

   Proje oluşturulur ve *Program.cs* adlı bir dosya **Düzenleyici** penceresinde açılır. **Editör** dosyaların içeriğini gösterir ve Visual Studio'da kodlama çalışmalarınızın çoğunu nerede yapacağınız yerdir.

   ![Visual Studio Editörü](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

Genellikle Visual Studio'nun sağ tarafında bulunan **Solution Explorer,** projenizdeki, çözümünüzdeki veya kod klasörünüzdeki dosya ve klasörhiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve **Çözüm Gezgini'ndeki**bir dosyaya gidebilirsiniz.

![Visual Studio'da Çözüm Gezgini](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio gruplarının üst kısmındaki menü çubuğu kategorilere ayrılır. Örneğin, **Proje** menüsü nde çalıştığınız projeyle ilgili komutlar içerir. **Araçlar** menüsünde, **Seçenekler'i**seçerek Visual Studio'nun nasıl bir şekilde nasıl hissettiğini özelleştirebilir veya Araçları ve **Özellikleri Al'ı**seçerek yüklemenize özellikler ekleyebilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 menü çubuğu](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019'da menü çubuğu](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Hata Listesi

**Görünüm** menüsünü seçerek **Hata Listesi** penceresini ve ardından **Hata Listesi'ni**açın.

**Hata Listesi,** kodunuzu geçerli durumuna ilişkin hataları, uyarıyı ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde herhangi bir hata (örneğin eksik ayraç veya yarı sütun gibi) varsa, bunlar burada listelenir.

![Visual Studio'da Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıktı** penceresi, projenizi oluşturmaktan ve kaynak denetim sağlayıcınızdan gelen çıktı iletilerini gösterir.

Biraz yapı çıktısı görmek için projeyi oluşturalım. **Yapı** menüsünden **Çözüm Oluştur'u**seçin. **Çıktı** penceresi otomatik olarak odak alır ve başarılı bir yapı iletisi görüntüler.

![Visual Studio'da çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu Visual Studio hemen hemen her şeyi gezinmek için hızlı ve kolay bir yoldur. Ne yapmak istediğinizle ilgili bazı metinler girebilirsiniz ve bu metinle ilgili seçeneklerin listesini gösterir. Örneğin, yapının tam olarak ne yaptığıyla ilgili ek ayrıntıları görüntülemek için yapı çıktısının ayrıntılılığını artırmak istediğinizi düşünün. Bunu şu şekilde yapabilirsiniz:

::: moniker range="vs-2017"

1. IDE'nin sağ üst kısmındaki **Hızlı Başlat** arama kutusunu bulun. (Alternatif olarak, erişmek için **Ctrl**+**Q** tuşuna basın.)

2. Arama kutusuna **ayrıntılı lık** yazın. Görüntülenen sonuçlararasından, Seçenekler kategorisi altında **Projeler ve Çözümler > Oluştur ve Çalıştır'ı** seçin. **Options**

   ![Visual Studio 2017'de hızlı başlatma arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu Yap **ve Çalıştır** seçenekleri sayfasına açılır.

::: moniker-end

::: moniker range=">=vs-2019"

1. IDE'nin üst kısmındaki arama kutusunu etkinleştirmek için **Ctrl**+**Q** tuşuna basın.

2. Arama kutusuna **ayrıntılı lık** yazın. Görüntülenen sonuçlardan **MSBuild ayrıntılılığını değiştir'i**seçin.

   ![Visual Studio 2019'da arama kutusu](media/vs-2019/quick-launch-verbosity.png)

   **Seçenekler** iletişim kutusu Yap **ve Çalıştır** seçenekleri sayfasına açılır.

::: moniker-end

3. **MSBuild proje altında çıkış ayrıntılı olarak yapı,** **Normal'i**seçin ve sonra **Tamam'ı**tıklatın.

4. **Solution Explorer'daki** **ConsoleApp1** projesine sağ tıklayarak ve bağlam menüsünden **Yeniden Oluştur'u** seçerek projeyi yeniden oluşturun.

   Bu kez **Çıktı** penceresi, hangi dosyaların nerede kopyalandığı da dahil olmak üzere yapı işleminden daha ayrıntılı günlüğe kaydetmeyi gösterir.

   ![Visual Studio'da verbose çıkış oluşturmak](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri Bildirim Gönder menüsü

Visual Studio'yu kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü nasıl geliştireceğiniz konusunda önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **Geri Bildirim Gönder** menüsünü kullanabilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017'de Geri Bildirim Gönder menüsü](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019'da Geri Bildirim Gönder menüsü](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimini tanımak için Visual Studio'nun özelliklerinden sadece birkaçına baktık. Daha fazla keşfetmek için:

> [!div class="nextstepaction"]
> [Kod düzenleyicisi hakkında bilgi edinin](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio'nun diğer özellikleri](../ide/advanced-feature-overview.md)
- [Tema ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
