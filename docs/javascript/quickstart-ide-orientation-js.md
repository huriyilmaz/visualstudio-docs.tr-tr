---
title: Görsel Stüdyo IDE Turu
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 713e7319618b42e2cdc4b8c0951bd79c225ac1b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73636580"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Visual Studio IDE’ye ilk bakış

Visual Studio entegre geliştirme ortamı (IDE) için bu 5-10 dakikalık giriş, bazı pencereler, menüler ve diğer UI özellikleri bir tur alırsınız.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Başlangıç penceresi

Visual Studio'yu başlattıktan sonra göreceğiniz ilk şey başlangıç penceresidir. Başlangıç penceresi, "koda daha hızlı girmenize" yardımcı olmak için tasarlanmıştır. Kodu kapatma veya kullanıma verme, varolan bir proje yi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

[![Visual Studio 2019'un başlangıç penceresi](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Visual Studio'yu ilk kez kullanıyorsanız, son proje listeniz boş olacaktır.

MSBuild tabanlı olmayan codebases ile çalışıyorsanız, Visual Studio'da kodunuzu açmak için **yerel klasör** aç seçeneğini kullanırsınız. Daha fazla bilgi için visual [studio'da proje veya çözüm olmadan kod geliştir'e](develop-javascript-code-without-solutions-projects.md)bakın. Aksi takdirde, GitHub veya Azure DevOps gibi bir kaynak sağlayıcıdan yeni bir proje oluşturabilir veya proje klonlayabilirsiniz.

**Kodsuz Devam** seçeneği, Visual Studio geliştirme ortamını belirli bir proje veya kod yüklenmeden açar. [Canlı Paylaşım](/visualstudio/liveshare/) oturumuna katılmak veya hata ayıklama işlemine eklemek için bu seçeneği seçebilirsiniz. Ayrıca başlangıç penceresini kapatmak ve IDE'yi açmak için **Esc** tuşuna basabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Visual Studio'yu başlattıktan sonra göreceğiniz ilk şey büyük olasılıkla **Başlangıç Sayfasıdır.** **Başlangıç Sayfası,** ihtiyacınız olan komutları ve proje dosyalarını daha hızlı bulmanıza yardımcı olmak için bir "hub" olarak tasarlanmıştır. **Son** bölümde, son zamanlarda üzerinde çalıştığınız projeler ve klasörler görüntülenir. **Yeni proje**altında, **Yeni Proje** iletişim kutusunu açmak için bir bağlantıyı tıklatabilir veya **Aç**altında, varolan bir kod projesi veya klasörü açabilirsiniz. Sağtarafta en son geliştirici haberleri bir besleme.

![Visual Studio'da Başlangıç Sayfası](media/start-page.png)

**Başlangıç Sayfasını** kapatıp yeniden görmek isterseniz, **Dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio'da dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio'nun özelliklerini keşfetmeye devam etmek için yeni bir proje oluşturalım.

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde, **yeni bir proje oluştur'u**ve ardından adlarında veya dil türünde "javascript" bulunan proje türlerinin listesini filtrelemek için **javascript'teki** arama kutusu türünde'yi seçin.

   Visual Studio, hızlı bir şekilde kodlamaya başlamanıza yardımcı olan çeşitli proje şablonları sağlar. (Alternatif olarak, bir TypeScript geliştiricisiyseniz, bu dilde bir proje oluşturmakta çekinmeyin. Bakacağız UI tüm programlama dilleri için benzer.)

   ![Visual Studio başlangıç penceresinde proje şablonlarını arama](media/vs-2019/create-new-project.png)

1. Boş **Düğüm.js Web Uygulaması** proje şablonu seçin ve **İleri'yi**tıklatın.

1. Görünen yeni proje iletişim **kutunuzu Yapılandır'** da varsayılan proje adını kabul edin ve **Oluştur'u**seçin.

::: moniker-end

::: moniker range="vs-2017"

1. Başlangıç **Sayfasında,** **Yeni proje**altındaki arama kutusunda, adlarında veya dil türünde "javascript" bulunanproje türlerinin listesini filtrelemek için **javascript** yazın.

   ![Visual Studio Başlangıç Sayfasında proje şablonlarını ara](media/start-page-search-templates.png)

   Visual Studio, hızlı bir şekilde kodlamaya başlamanıza yardımcı olan çeşitli proje şablonları sağlar. Boş **Düğüm.js Web Uygulaması** proje şablonu seçin. (Alternatif olarak, bir TypeScript geliştiricisiyseniz, bu dilde bir proje oluşturmakta çekinmeyin. Bakacağız UI tüm programlama dilleri için benzer.)

1. Görünen **Yeni Proje** iletişim kutusunda varsayılan proje adını kabul edin ve **Tamam'ı**seçin.
::: moniker-end

   Proje oluşturulur ve **editor** penceresinde *server.js* adlı bir dosya açılır. **Editör** dosyaların içeriğini gösterir ve Visual Studio'da kodlama çalışmalarınızın çoğunu nerede yapacağınız yerdir.

   ![Visual Studio Editörü](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

Genellikle Visual Studio'nun sağ tarafında bulunan **Solution Explorer,** projenizdeki, çözümünüzdeki veya kod klasörünüzdeki dosya ve klasörhiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve **Çözüm Gezgini'ndeki**bir dosyaya gidebilirsiniz.

![Visual Studio'da Çözüm Gezgini](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio gruplarının üst kısmındaki menü çubuğu kategorilere ayrılır. Örneğin, **Proje** menüsü nde çalıştığınız projeyle ilgili komutlar içerir. **Araçlar** menüsünde, **Seçenekler'i**seçerek Visual Studio'nun nasıl bir şekilde nasıl hissettiğini özelleştirebilir veya Araçları ve **Özellikleri Al'ı**seçerek yüklemenize özellikler ekleyebilirsiniz.

![Visual Studio'da menü çubuğu](media/quickstart-IDE-menu-bar.png)

**Görünüm** menüsünü seçerek **Hata Listesi** penceresini ve ardından **Hata Listesi'ni**açalım.

## <a name="error-list"></a>Hata Listesi

**Hata Listesi,** kodunuzu geçerli durumuna ilişkin hataları, uyarıyı ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde herhangi bir hata (örneğin eksik ayraç veya yarı sütun gibi) varsa, bunlar burada listelenir.

![Visual Studio'da Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıktı** penceresi, projenizi oluşturmaktan ve kaynak denetim sağlayıcınızdan gelen çıktı iletilerini gösterir.

Biraz yapı çıktısı görmek için projeyi oluşturalım. **Yapı** menüsünden **Çözüm Oluştur'u**seçin. **Çıktı** penceresi otomatik olarak odak alır ve başarılı bir yapı iletisi görüntüler.

![Visual Studio'da çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu Visual Studio hemen hemen her şeyi yapmak için hızlı ve kolay bir yoldur. Ne yapmak istediğinizle ilgili bazı metinler girebilirsiniz ve bu metinle ilgili seçeneklerin listesini gösterir. Örneğin, yapının tam olarak ne yaptığıyla ilgili ek ayrıntıları görüntülemek için yapı çıktısının ayrıntılılığını artırmak istediğinizi düşünün. Bunu şu şekilde yapabilirsiniz:

1. Arama kutusuna **ayrıntılı lık** yazın. Görüntülenen sonuçlararasından, Seçenekler kategorisi altında **Projeler ve Çözümler > Oluştur ve Çalıştır'ı** seçin. **Options**

   ![Visual Studio'da arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu Yap **ve Çalıştır** seçenekleri sayfasına açılır.

1. **MSBuild proje altında çıkış ayrıntılı olarak yapı,** **Normal'i**seçin ve sonra **Tamam'ı**tıklatın.

1. **Solution Explorer'daki** **NodejsWebApp1** projesine sağ tıklayarak ve bağlam menüsünden **Yeniden Oluştur'u** seçerek projeyi yeniden oluşturun.

   Bu kez **Çıktı** penceresi, hangi dosyaların nerede kopyalandığı da dahil olmak üzere yapı işleminden daha ayrıntılı günlüğe kaydetmeyi gösterir.

   ![Visual Studio'da verbose çıkış oluşturmak](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri Bildirim Gönder menüsü

Visual Studio'yu kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü nasıl geliştireceğiniz konusunda önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **Geri Bildirim Gönder** menüsünü kullanabilirsiniz.

![Visual Studio'da Geri Bildirim Gönder menüsü](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimini tanımak için Visual Studio'nun özelliklerinden sadece birkaçına baktık. Daha fazla keşfetmek için:

> [!div class="nextstepaction"]
> [Kod düzenleyicisi hakkında bilgi edinin](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017'nin diğer özellikleri](../ide/advanced-feature-overview.md)
- [Tema ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
