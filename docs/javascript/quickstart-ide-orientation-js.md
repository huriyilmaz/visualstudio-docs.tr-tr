---
title: Visual Studio IDE’ye ilk bakış
description: Windows, menüler ve en Visual Studio kullanıcı arabirimi özellikleri dahil olmak üzere tümleşik geliştirme ortamı (IDE) hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
ms.workload:
- multiple
ms.openlocfilehash: 724c6bb1a106fad6d6ceac0cae6f6e7968175447
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085851"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Visual Studio IDE’ye ilk bakış

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte windows, menüler ve diğer kullanıcı arabirimi özelliklerinden bazılarında bir tura çıkarsınız.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a> Başlangıç penceresi

Uygulamayı başlattıktan sonra göreceğimiz ilk şey Visual Studio penceresidir. Başlangıç penceresi, "koda daha hızlı" başlamanıza yardımcı olmak için tasarlanmıştır. Kodu kapatma veya denetleme, mevcut bir proje veya çözümü açma, yeni proje oluşturma veya yalnızca bazı kod dosyaları içeren bir klasörü açma seçenekleri vardır.

[![Visual Studio 2019'daki başlangıç penceresi](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

İlk kez bir uygulama kullanıyorsanız Visual Studio proje listeniz boş olur.

Veri tabanlı olmayan kod MSBuild çalışıyorsanız, kodunuzu yerel klasör  aç seçeneğini kullanarak Visual Studio. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](develop-javascript-code-without-solutions-projects.md) Aksi takdirde, yeni bir proje oluşturabilir veya kaynak sağlayıcısından yeni bir proje kopya GitHub veya Azure DevOps.

Kod **olmadan devam seçeneği,** herhangi bir Visual Studio veya kod yüklenmeden geliştirme ortamını açar. Bir oturuma katılmak veya hata ayıklama [Live Share](/visualstudio/liveshare/) eklemek için bu seçeneği kullanabilirsiniz. Başlangıç penceresini  kapatıp IDE'ye açmak için Esc tuşuna da basabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Başlangıç Sayfası

Uygulamayı başlattıktan sonra göreceğimiz ilk şey Visual Studio büyük olasılıkla Başlangıç **Sayfası'dır.** Başlangıç **Sayfası,** ihtiyacınız olan komutları ve proje dosyalarını daha hızlı bulmanıza yardımcı olmak için bir "hub" olarak tasarlanmıştır. Son **bölüm,** son zamanlarda üzerinde çalıştığın projeleri ve klasörleri görüntüler. Yeni **proje altında** bir bağlantıya tıklayarak Yeni  Project iletişim kutusunu açabilir veya Aç'ın altında mevcut bir kod projesini veya klasörünü açabilirsiniz. Sağda, en son geliştirici haberlerinin akışı yer alan bir akış yer alan.

![Visual Studio'de Başlangıç Sayfası](media/start-page.png)

Başlangıç Sayfasını kapatıp **yeniden** görmek için Dosya menüsünden yeniden **açabilirsiniz.**

![Dosya menüsündeki Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Bu özelliklerin Visual Studio devam etmek için yeni bir proje oluştur o zaman.

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje oluştur'a tıklayın ve ardından arama kutusuna **javascript** yazarak proje türleri listesini adlarında veya dil türlerinde "javascript" ifadesini içerenlere filtre ekleyin.

   Visual Studio hızla kodlamaya başlamanıza yardımcı olacak çeşitli türlerde proje şablonları sağlar. (Alternatif olarak, TypeScript geliştiricisiyseniz, bu dilde bir proje oluşturabilirsiniz. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

   ![Başlangıç penceresinde proje Visual Studio arama](media/vs-2019/create-new-project.png)

1. Web Uygulaması **proje Node.js boş bir** şablon seçin ve Ardından'ya **tıklayın.**

1. Görüntülenen **Yeni projenizi yapılandır iletişim** kutusunda varsayılan proje adını kabul et ve Oluştur'a **tıklayın.**

::: moniker-end

::: moniker range="vs-2017"

1. Başlangıç **Sayfasında,** Yeni proje'nin altındaki arama kutusuna **javascript** yazarak proje türleri listesini adlarında veya dil türlerinde "javascript" ifadesini içerenlerle filtreleyebilirsiniz.

   ![Başlangıç Sayfasında proje Visual Studio arama](media/start-page-search-templates.png)

   Visual Studio hızla kodlamaya başlamanıza yardımcı olacak çeşitli türlerde proje şablonları sağlar. Boş Bir **Node.js Web Uygulaması proje** şablonu seçin. (Alternatif olarak, TypeScript geliştiricisiyseniz, bu dilde bir proje oluşturabilirsiniz. Bakarak tüm programlama dillerinde de benzer bir kullanıcı arabirimine sahip oluruz.)

1. Görüntülenen **Yeni Project** iletişim kutusunda varsayılan proje adını kabul et ve Tamam'ı **seçin.**
::: moniker-end

   Proje oluşturulur ve Düzenleyici penceresinde *server.js* adlı bir **dosya** açılır. **Düzenleyici,** dosyaların içeriğini gösterir ve kod yazma çalışmanızı büyük bir Visual Studio.

   ![Visual Studio'de düzenleyici](media/editor.png)

## <a name="solution-explorer"></a>Çözüm Gezgini

**Çözüm Gezgini** genellikle Visual Studio'nin sağ tarafında yer alan Visual Studio proje, çözüm veya kod klasörünüzdeki dosya ve klasörler hiyerarşisinin grafiksel bir gösterimini gösterir. Hiyerarşiye göz atabilir ve içinde bir dosyaya **Çözüm Gezgini.**

![Çözüm Gezgini Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüler

Komutların üst kısmında yer alan menü Visual Studio kategorilere ayrılır. Örneğin, **Project** menüsünde çalışmakta olan projeyle ilgili komutlar vardır. Araçlar **menüsünde Seçenekler'i** seçerek Visual Studio özelliklerini özelleştirebilirsiniz veya Araçları ve Özellikleri Al'ı seçerek **yüklemenize özellikler ekleyebilirsiniz.**

![Visual Studio'de menü çubuğu](media/quickstart-IDE-menu-bar.png)

Görünüm menüsünü ve ardından **Hata Listesi'ne** **seçerek** Hata Listesi penceresini **açabilirsiniz.**

## <a name="error-list"></a>Hata Listesi

Hata **Listesi,** kodunuzun geçerli durumuyla ilgili hataları, uyarıyı ve iletileri gösterir. Dosyanız veya projenizin herhangi bir yerinde hatalar (eksik ayraç veya noktalı virgül gibi) varsa bunlar burada listelenir.

![Visual Studio'de Hata Listesi](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Çıktı penceresi

Çıkış **penceresi,** projenizi ve kaynak denetim sağlayıcınızdan gelen çıkış iletilerini gösterir.

Bazı derleme çıkışlarını görmek için projeyi derlemeye bakalım. Derleme **menüsünden** Çözümü **Derleme'yi seçin.** Çıkış **penceresi** otomatik olarak odağı alır ve başarılı bir derleme iletisi görüntüler.

![Visual Studio'da çıkış penceresi](media/build-output-minimal.png)

## <a name="search-box"></a>Arama kutusu

Arama kutusu, herhangi bir şey yapmak için hızlı ve kolay bir Visual Studio. Yapmak istediğinizle ilgili bazı metinler girebilirsiniz ve metinle ilgili seçeneklerin listesini gösterir. Örneğin, tam olarak derlemenin ne yaptığı hakkında ek ayrıntılar görüntülemek için derleme çıkışının ayrıntısını artırmak istediğinizi düşünün. Bunu şu şekilde yapabiliriz:

1. Arama **kutusuna ayrıntılı** yazın. Görüntülenen sonuçlardan, Seçenekler kategorisi **altında Projeler ve Çözümler --> Ve Çalıştır'ı** seçin. 

   ![Visual Studio'de arama kutusu](media/quickstart-IDE-quick-launch.png)

   Seçenekler **iletişim** kutusu, Oluşturma ve **Çalıştırma seçenekleri** sayfası açılır.

1. Proje **MSBuild çıkış ayrıntılılığı altında Normal**'i seçin ve ardından Tamam'a **tıklayın.** 

1. Projenizi yeniden derlemek için **nodejsWebApp1** projesine sağ **tıklayın Çözüm Gezgini** menüden **Yeniden** Oluştur'a tıklayın.

   Bu kez **Çıkış** penceresi, hangi dosyaların nereye kopyalanmış olduğu da dahil olmak üzere derleme sürecinden daha ayrıntılı günlük kaydı gösterir.

   ![Derlemede ayrıntılı derleme çıkışı Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Geri Bildirim Gönder menüsü

Visual Studio kullanırken herhangi bir sorunla karşılaşırsanız veya ürünü geliştirme hakkında önerileriniz varsa, ürün penceresinin üst kısmında yer alan Geri Bildirim Gönder Visual Studio kullanabilirsiniz. 

![Visual Studio'da Geri Bildirim Gönder menüsü](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcı arabirimi hakkında bilgi almak için Visual Studio özelliklerini inceledik. Daha fazla bilgi için:

> [!div class="nextstepaction"]
> [Kod düzenleyicisi hakkında bilgi](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017'nin diğer özellikleri](../ide/advanced-feature-overview.md)
- [Tema ve yazı tipi renklerini değiştirme](../ide/quickstart-personalize-the-ide.md)
