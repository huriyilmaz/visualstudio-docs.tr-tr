---
title: Visual Studio IDE turu
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596976"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Hızlı Başlangıç: Visual Studio IDE ilk bakış

Bu 5-10 dakikalık bir giriş Visual Studio tümleşik geliştirme ortamı (IDE), biz windows, menüler ve diğer kullanıcı Arabirimi özellikleri bazıları ilişkin tura katılın.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç sayfası

Visual Studio 'Yu açtıktan sonra ilk olarak **Başlangıç sayfası büyük olasılıkla başlangıç sayfasıdır**. **Başlangıç sayfası** "hub" komut bulmanıza ve proje dosyalarını daha hızlı ihtiyacınız yardımcı olmak için tasarlanmıştır. **Son** projeleri ve klasörleri, çalıştığınız üzerinde son bölümünde görüntülenir. Altında **yeni proje**, ortaya çıkarmak için bir bağlantıya tıklayabilirsiniz **yeni proje** iletişim kutusu veya altında **açın**, bir var olan kod proje veya klasör açabilirsiniz. Sağ tarafta en güncel Geliştirici haberlerini oluşan akışını ' dir.

![Visual Studio'da başlangıç sayfası](media/start-page.png)

Kapatırsanız **başlangıç sayfası** ve tekrar görmek istiyorsanız, buradan yeniden **dosya** menüsü.

![Visual Studio'da Dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Başlangıç penceresi

Visual Studio 'Yu açtıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kopyalama veya kullanıma alma, mevcut bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarını içeren bir klasörü açma seçeneklerine sahiptir.

[Visual Studio 2019 ' de ![başlangıç penceresi](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Visual Studio 'Yu ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild tabanlı olmayan kod tabanlarında çalışıyorsanız, Visual Studio 'da kodunuzu açmak için **yerel klasör aç** seçeneğini kullanacaksınız. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](develop-code-in-visual-studio-without-projects-or-solutions.md). Aksi takdirde, yeni bir proje oluşturabilir veya GitHub ya da Azure DevOps gibi bir kaynak sağlayıcıdan proje kopyalayabilirsiniz.

**Kod olmadan devam et** seçeneği, Visual Studio geliştirme ortamını belirli bir proje veya kod yüklenmeden yalnızca açar. Bir [live share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

## <a name="create-a-project"></a>Proje oluştur

Visual Studio'nun özellikleri keşfetmeye devam etmek için yeni bir proje oluşturalım.

::: moniker range="vs-2017"

1. Üzerinde **başlangıç sayfası**, arama kutusuna altında **yeni proje**, yazın **konsol** adında içeren "konsol" Bu proje türleri listesini filtrelemek için.

   ![Visual Studio Başlangıç sayfasında Proje şablonlarında Ara](media/start-page-search-templates.png)

   Visual Studio, çeşitli yardımcı olacak proje şablonları, hızlı bir şekilde kodlama başlama sağlar. C# **Konsol uygulaması (.NET Core)** proje şablonu seçin. (Visual Basic, C++, Javascript veya diğer dil Geliştirici kullanıyorsanız alternatif olarak, bir projeyi bu dillerden birinde oluşturun çekinmeyin. Biz göz atan kullanıcı Arabirimi için tüm programlama dillerinde benzer.)

1. İçinde **yeni proje** görüntülenen iletişim kutusunda varsayılan proje adını kabul edin ve **Tamam**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   **Yeni bir proje oluşturur**yazılı bir iletişim kutusu açılır. Burada, bir proje şablonunu arayabilir, filtreleyebilir ve seçebilirsiniz. Ayrıca, son kullanılan proje şablonlarının bir listesini gösterir.

1. Üstteki arama kutusunda, proje türleri listesini, adında "konsol" içeren olanlarla filtrelemek için **konsol** yazın. **C#** **Dil** seçicisinden (veya seçtiğiniz başka bir dilde) arama sonuçlarını daha da belirginleştirin.

   ![Visual Studio 2019 'de yeni proje iletişim kutusu](media/vs-2019/create-a-new-project.png)

1. Visual Basic, veya C# F# diliniz olarak seçtiyseniz **konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin. (Farklı bir dil seçtiyseniz, herhangi bir şablonu seçmeniz yeterlidir. Biz göz atan kullanıcı Arabirimi için tüm programlama dillerinde benzer.)

1. **Yeni projenizi yapılandırın** sayfasında varsayılan proje adını ve konumunu kabul edin ve **Oluştur**' u seçin.

::: moniker-end

   Proje oluşturulur ve bir dosya adlı *Program.cs* açılır **Düzenleyicisi** penceresi. **Düzenleyici** , dosyaların içeriğini gösterir ve kodlarınızın çoğunun Visual Studio 'da çalışmasını istediğiniz yerdir.

   ![Visual Studio Düzenleyicisi](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

**Çözüm Gezgini**, genellikle Visual Studio'nun sağ tarafta olduğu gösterir, dosya ve klasörlerin hiyerarşi grafik gösterimi proje, çözüm veya kod klasörü. Hiyerarşi göz atabilir ve bir dosyaya gidin **Çözüm Gezgini**.

![Visual Studio'daki Çözüm Gezgini'nde](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio'nun üst menü çubuğu komutlarını kategoriler halinde gruplandırır. Örneğin, **proje** menüsü, içinde çalışmakta olduğunuz projeye ilgili komutları içerir. Üzerinde **Araçları** menüsünde seçerek Visual Studio nasıl davranacağını özelleştirebileceğiniz **seçenekleri**, veya özelliklerini seçerek yüklemenize ekleyin **araçları ve özellikleri Al**.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de menü çubuğu](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de menü çubuğu](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Hata Listesi

**Görünüm** menüsünü seçip **hata listesi** **hata listesi** penceresini açın.

**Hata listesi** hata, uyarı ve kodunuzu geçerli durumuna ilişkin ileti gösterir. Hataları (örneğin, bir eksik küme ayracı veya noktalı virgül) dosyanızı veya herhangi bir projeniz varsa, bunlar burada listelenen.

![Visual Studio hata listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıkış** çıkış penceresi şunu gösterir, iletileri projenizi oluşturma ve kaynak denetimi sağlayıcınız.

Şimdi projeyi görmek için bazı derleme çıkışı. Gelen **derleme** menüsünde seçin **Çözümü Derle**. **Çıkış** penceresi otomatik olarak odağa gelir ve derleme başarılı iletisini görüntüler.

![Visual Studio çıktı penceresinde](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, Visual Studio 'da çok daha fazla şeye gitmeniz için hızlı ve kolay bir yoldur. Yapmak istediğiniz ilgili metin girebilir ve onu metne ait seçenekler listesini göstereceğiz. Örneğin, tam olarak ne yapı yapıyor ek bilgileri görüntülemek için derleme çıkışın ayrıntı düzeyini artırmak istediğiniz düşünün. İşte, nasıl yapabilir:

::: moniker range="vs-2017"

1. IDE 'nin sağ üst köşesindeki **Hızlı başlatma** arama kutusunu bulun. (Alternatif olarak, erişmek için **Ctrl**+**Q** tuşlarına basın.)

2. Arama kutusuna **ayrıntı düzeyi** yazın. Görüntülenen sonuçlardan seçin **projeler ve çözümler--> derleme ve çalıştırma** altında **seçenekleri** kategorisi.

   ![Visual Studio 2017 'de Hızlı Başlat arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekleri** iletişim kutusu açılır **derleme ve çalıştırma** seçenekler sayfası.

::: moniker-end

::: moniker range=">=vs-2019"

1. IDE 'nin üst kısmındaki arama kutusunu etkinleştirmek için **Ctrl**+**Q** tuşlarına basın.

2. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan **MSBuild ayrıntı düzeyini Değiştir**' i seçin.

   ![Visual Studio 2019 'de arama kutusu](media/vs-2019/quick-launch-verbosity.png)

   **Seçenekleri** iletişim kutusu açılır **derleme ve çalıştırma** seçenekler sayfası.

::: moniker-end

3. Altında **MSBuild proje oluşturması çıkış ayrıntısı**, seçin **Normal**ve ardından **Tamam**.

4. Sağ tıklayarak projeyi yeniden derleyin **ConsoleApp1** projesi **Çözüm Gezgini** seçip **yeniden** bağlam menüsünden.

   Bu süre **çıkış** penceresi, hangi dosyalar dahil olmak üzere nerede kopyalanan yapı işleminden daha ayrıntılı günlük kaydı gösterir.

   ![Visual Studio'da ayrıntılı yapı çıktısı](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menü geri bildirim gönder

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir ya da ürünü geliştirme hakkında önerileriniz varsa, Visual Studio penceresinin üst kısmındaki **geri bildirim gönder** menüsünü kullanabilirsiniz.

::: moniker range="vs-2017"

![Visual Studio 2017 ' de geri bildirim menüsü gönder](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 ' de geri bildirim menüsü gönder](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio kullanıcı arabirimi ile tanışın özelliklerinin birkaçı adresindeki inceledik. Daha iyi keşfedilebilmesi için:

> [!div class="nextstepaction"]
> [Kod Düzenleyicisi hakkında bilgi edinin](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE genel bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 'nun daha fazla özelliği](../ide/advanced-feature-overview.md)
- [Tema ve yazı tipi renkleri değiştirme](../ide/quickstart-personalize-the-ide.md)
