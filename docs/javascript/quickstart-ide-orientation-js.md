---
title: Visual Studio IDE turu
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 713e7319618b42e2cdc4b8c0951bd79c225ac1b6
ms.sourcegitcommit: f9f389e72787de30eb869a55ef7725a10a4011f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73636580"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Visual Studio IDE’ye ilk bakış

Bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (IDE) giriş bölümünde bazı pencereler, menüler ve diğer kullanıcı arabirimi özellikleri için bir tura çıkacağız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Başlangıç penceresi

Visual Studio 'Yu başlattıktan sonra ilk olarak göreceğiniz şey başlangıç penceresidir. Başlangıç penceresi, "koda ulaşmak" için daha hızlı yardımcı olacak şekilde tasarlanmıştır. Kodu kapatma veya kullanıma alma, var olan bir projeyi veya çözümü açma, yeni bir proje oluşturma veya yalnızca bazı kod dosyalarını içeren bir klasörü açma seçeneklerine sahiptir.

[Visual Studio 2019 ' de başlangıç penceresini ![](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Visual Studio 'Yu ilk kez kullanıyorsanız, son projeler listeniz boş olur.

MSBuild tabanlı olmayan kod tabanlarında çalışıyorsanız, Visual Studio 'da kodunuzu açmak için **yerel klasör aç** seçeneğini kullanacaksınız. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](develop-javascript-code-without-solutions-projects.md). Aksi takdirde, yeni bir proje oluşturabilir veya GitHub ya da Azure DevOps gibi bir kaynak sağlayıcıdan proje kopyalayabilirsiniz.

**Kod olmadan devam et** seçeneği, Visual Studio geliştirme ortamını belirli bir proje veya kod yüklenmeden yalnızca açar. Bir [live share](/visualstudio/liveshare/) oturumuna katmak veya hata ayıklama için bir işleme iliştirmek üzere bu seçeneği belirleyebilirsiniz. Başlangıç penceresini kapatmak ve IDE 'yi açmak için **ESC** tuşuna da basabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Visual Studio 'Yu başlattıktan sonra göreceğiniz ilk şey, büyük olasılıkla **başlangıç sayfasıdır**. **Başlangıç sayfası** , ihtiyacınız olan komutları ve proje dosyalarını hızlı bir şekilde bulmanıza yardımcı olmak için "Hub" olarak tasarlanmıştır. **Son** bölümde, son zamanlarda çalıştığınız projeler ve klasörler görüntülenir. **Yeni proje**' nin altında, **Yeni proje** iletişim kutusunu açmak için bir bağlantıya tıklayabilir veya **Aç**' ın altında varolan bir kod projesini veya klasörünü açabilirsiniz. Sağ tarafta en son geliştirici haberlerinin bir akışı bulunur.

![Visual Studio 'da başlangıç sayfası](media/start-page.png)

**Başlangıç sayfasını** kapatır ve yeniden görmek Isterseniz **dosyayı dosya** menüsünden yeniden açabilirsiniz.

![Visual Studio 'da Dosya menüsü](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Studio 'nun özelliklerini araştırmaya devam etmek için yeni bir proje oluşturalım.

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde, **Yeni proje oluştur**' u seçin ve ardından Proje türleri listesini ad veya dil türünde "JavaScript" içeren olanlarla filtrelemek için **JavaScript** 'teki arama kutusuna yazın.

   Visual Studio, hızla kodlamaya başlamanıza yardımcı olan çeşitli türlerde proje şablonları sağlar. (Alternatif olarak, bir TypeScript geliştiricisiyseniz bu dilde bir proje oluşturmayı ücretsiz olarak kullanabilirsiniz. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

   ![Visual Studio başlangıç penceresinde proje şablonları ara](media/vs-2019/create-new-project.png)

1. Boş bir **Node. js web uygulaması** projesi şablonu seçin ve **İleri**' ye tıklayın.

1. Görüntülenen **yeni projeyi Yapılandır** iletişim kutusunda, varsayılan proje adını kabul edin ve **Oluştur**' u seçin.

::: moniker-end

::: moniker range="vs-2017"

1. **Başlangıç sayfasında**, **Yeni proje**altındaki arama kutusuna, proje türleri listesini ad veya dil türlerine "JavaScript" içeren olanlarla filtrelemek için **JavaScript** yazın.

   ![Visual Studio başlangıç sayfasında proje şablonları ara](media/start-page-search-templates.png)

   Visual Studio, hızla kodlamaya başlamanıza yardımcı olan çeşitli türlerde proje şablonları sağlar. Boş bir **Node. js web uygulaması** proje şablonu seçin. (Alternatif olarak, bir TypeScript geliştiricisiyseniz bu dilde bir proje oluşturmayı ücretsiz olarak kullanabilirsiniz. Bakılacak Kullanıcı arabirimi tüm programlama dilleri için benzerdir.)

1. Görüntülenen **Yeni proje** iletişim kutusunda, varsayılan proje adını kabul edin ve **Tamam**' ı seçin.
::: moniker-end

   Proje oluşturulur ve **Düzenleyici** penceresinde *Server. js* adlı bir dosya açılır. **Düzenleyici** , dosyaların içeriğini gösterir ve kodlarınızın çoğunun Visual Studio 'da çalışmasını istediğiniz yerdir.

   ![Visual Studio 'da düzenleyici](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

Genellikle Visual Studio 'nun sağ tarafındaki **Çözüm Gezgini**, projenizde, çözümünüzde veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafik bir gösterimini gösterir. Hiyerarşiye gözatabilir ve **Çözüm Gezgini**bir dosyaya gidebilirsiniz.

![Visual Studio 'da Çözüm Gezgini](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Visual Studio gruplarının üst kısmında bulunan menü çubuğu, kategoriler halinde komutları. Örneğin, **Proje** menüsü, çalışmakta olduğunuz projeyle ilgili komutları içerir. **Araçlar** menüsünde, **Seçenekler**' i seçerek Visual Studio 'Nun davranışını özelleştirebilir veya **Araçlar ve Özellikler al**' ı seçerek yüklemenize özellikler ekleyebilirsiniz.

![Visual Studio 'da menü çubuğu](media/quickstart-IDE-menu-bar.png)

**Görünüm** menüsünü seçip **hata listesi** **hata listesi** penceresini açalım.

## <a name="error-list"></a>Hata Listesi

**Hata listesi** , kodunuzun geçerli durumuyla ilgili hataları, uyarıları ve iletileri gösterir. Dosyanızda veya projenizde herhangi bir yerde bir hata (eksik küme ayracı veya noktalı virgül) varsa, burada listelenir.

![Visual Studio 'da Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

**Çıkış** penceresinde, projenizi ve kaynak denetimi sağlayıcınızdan oluşturduğunuz çıkış iletileri görüntülenir.

Ayrıca, bazı derleme çıktısını görmek için projeyi derlim. **Build** menüsünde **Build Solution**öğesini seçin. **Çıkış** penceresi, odağı otomatik olarak edinir ve başarılı bir derleme iletisi görüntüler.

![Visual Studio 'da çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, Visual Studio 'da oldukça çok şey yapmanın hızlı ve kolay bir yoludur. Yapmak istediğiniz konuyla ilgili bir metin girebilirsiniz ve bu, metne ait seçeneklerin bir listesini gösterir. Örneğin, yapı çıkışının ayrıntı düzeyini arttırmak istediğinizi, tam olarak oluşturma işlemi hakkında ek ayrıntılar görüntüleyecek şekilde düşünün. Şunları yapabilirsiniz:

1. Arama kutusuna **ayrıntı düzeyi** yazın. Görünen sonuçlardan projeler ve çözümler ' i seçin. > **Seçenekler** kategorisi altında **derleyin ve çalıştırın** .

   ![Visual Studio 'da arama kutusu](media/quickstart-IDE-quick-launch.png)

   **Seçenekler** iletişim kutusu, **derleme ve çalıştırma** seçenekleri sayfasına açılır.

1. **MSBuild proje derlemesi çıkış ayrıntı düzeyi**altında **normal**' i seçin ve ardından **Tamam**' a tıklayın.

1. **Çözüm Gezgini** ' de **NodejsWebApp1** projesine sağ tıklayıp bağlam menüsünden **yeniden oluştur** ' u seçerek projeyi yeniden derleyin.

   Bu kez **Çıkış** penceresinde, hangi dosyaların nereye kopyalandığı de dahil olmak üzere yapı işleminden daha ayrıntılı günlük gösterilir.

   ![Visual Studio 'da ayrıntılı derleme çıkışı](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri bildirim Gönder menüsü

Visual Studio kullanırken herhangi bir sorunla karşılaşmanız gerekir ya da ürünü geliştirme hakkında önerileriniz varsa, Visual Studio penceresinin en üstündeki **geri bildirim gönder** menüsünü kullanabilirsiniz.

![Visual Studio 'da geri bildirim menüsü gönder](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimiyle tanışmanız için Visual Studio 'nun yalnızca birkaç özelliğine baktık. Daha fazla incelemek için:

> [!div class="nextstepaction"]
> [Kod Düzenleyicisi hakkında bilgi edinin](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017 ' nin daha fazla özelliği](../ide/advanced-feature-overview.md)
- [Temayı ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
