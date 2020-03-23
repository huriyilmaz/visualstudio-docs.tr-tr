---
title: 'İzlenecek yol: Uygulama oluşturma'
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d94a525f9938b6845584b6d5872bd486e947025d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115402"
---
# <a name="walkthrough-build-an-application"></a>İzlenecek yol: Uygulama oluşturma

Bu izbiyi tamamlayarak, Visual Studio ile uygulama oluştururken yapılandırabileceğiniz birkaç seçenek hakkında daha fazla bilgi edinebilirsiniz. Özel bir yapı yapılandırması oluşturur, belirli uyarı iletilerini gizler ve örnek bir uygulama için yapı çıktısı bilgilerini artırırsınız.

## <a name="install-the-sample-application"></a>Örnek uygulamayı yükleme

[WPF uygulamaları](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) örneğini oluşturmak için Giriş'i indirin. C# veya Visual Basic'i seçin. *.zip* dosyası indirildikten sonra, ayıklayın ve Visual Studio kullanarak *ExpenseItIntro.sln* dosyasını açın.

## <a name="create-a-custom-build-configuration"></a>Özel yapı yapılandırması oluşturma

Bir çözüm oluşturduğunuzda, hata ayıklama ve sürüm yapı yapılandırmaları ve bunların varsayılan platform hedefleri çözüm için otomatik olarak tanımlanır. Daha sonra bu yapılandırmaları özelleştirebilir veya kendi yapılandırmanızı oluşturabilirsiniz. Yapı yapılandırmaları yapı türünü belirtir. Yapı platformları, bir uygulamanın bu yapılandırma için hedeflenebilen işletim sistemini belirtir. Daha fazla bilgi için bkz. [yapı yapılandırmalarını anlayın,](../ide/understanding-build-configurations.md) [yapı platformlarını anlayın](../ide/understanding-build-platforms.md)ve [nasıl anlaşılır: Hata ayıklama ve sürüm yapılandırmalarını ayarlayın.](../debugger/how-to-set-debug-and-release-configurations.md)

**Configuration Manager** iletişim kutusunu kullanarak yapılandırmaları ve platform ayarlarını değiştirebilir veya oluşturabilirsiniz. Bu yordamda, sınama için bir yapı yapılandırması oluşturursunuz.

### <a name="create-a-build-configuration"></a>Yapı yapılandırması oluşturma

1. Configuration **Manager** iletişim kutusunu açın.

   ![Yapı menüsü, Configuration Manager komutu](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. Etkin **çözüm yapılandırma** listesinde ** \<Yeni... \>**.

1. Yeni **Çözüm Yapılandırması** iletişim kutusunda, yeni `Test`yapılandırmayı adlandırın, ayarları varolan **Hata Ayıklama** yapılandırmasından kopyalayın ve ardından **Tamam** düğmesini seçin.

   ![Yeni Çözüm Yapılandırma İletişim Kutusu](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. Etkin **çözüm platformu** listesinde ** \<Yeni... \>**.

1. Yeni **Çözüm Platformu** iletişim kutusunda **x64'u**seçin ve x86 platformundan ayarları kopyalamayın.

   ![Yeni Çözüm Platformu İletişim Kutusu](../ide/media/buildwalk_newsolutionplatform.png)

1. **Tamam** düğmesini seçin.

   Etkin çözüm yapılandırması x64 olarak ayarlanmış etkin çözüm platformu ile **Test** olarak değiştirildi.

   ![Test yapılandırmalı Configuration Manager](../ide/media/buildwalk_configmanagertestconfig.png)

1. **Kapat'ı**seçin.

**Standart** araç çubuğundaki **Çözüm Yapılandırmaları** listesini kullanarak etkin çözüm yapılandırmasını hızlı bir şekilde doğrulayabilir veya değiştirebilirsiniz.

![Çözüm Yapılandırma seçeneği Standart Araç Çubuğu](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Uygulama oluşturma

Ardından, çözümü özel yapı yapılandırmasıyla oluşturursunuz.

### <a name="build-the-solution"></a>Çözümü derleme

- Menü çubuğunda **Yapı** > **Çözümü'nü**seçin veya **Ctrl**+**Shift**+**B**tuşuna basın.

    **Çıktı** penceresi yapının sonuçlarını görüntüler. Yapı başarılı oldu.

## <a name="hide-compiler-warnings"></a>Derleyici uyarılarını gizle

Daha sonra derleyici tarafından oluşturulacak bir uyarıya neden olan bazı kodlar tanıtacağız.

1. C# projesinde *ExpenseReportPage.xaml.cs* dosyasını açın. **ExpenseReportPage** yönteminde aşağıdaki kodu ekleyin: `int i;`.

    OR

    Visual Basic projesinde *ExpenseReportPage.xaml.vb* dosyasını açın. Özel yapıcı **Kamu Alt Yeni ...**, aşağıdaki `Dim i`kodu ekleyin: .

1. Çözümü derleyin.

**Çıktı** penceresi yapının sonuçlarını görüntüler. Yapı başarılı oldu, ancak uyarılar oluşturuldu:

![Çıkış Penceresi Görsel Temel](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Çıkış Penceresi Görsel C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Yapı çıktısını darmadağın etmek yerine, bir yapı sırasında belirli uyarı iletilerini geçici olarak gizleyebilirsiniz.

### <a name="hide-a-specific-c-warning"></a>Belirli bir C# uyarısını gizleme

1. **Çözüm Gezgini'nde,** üst düzey proje düğümlerini seçin.

1. Menü çubuğunda**Özellik Sayfalarını** **Görüntüle'yi** > seçin.

     **Proje Tasarımcısı** açılır.

1. **Yapı** sayfasını seçin ve ardından **Uyarıları Bastır** kutusunda **0168**numaralı uyarı numarasını belirtin.

     ![Yapı sayfası, Proje Tasarımcısı](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Daha fazla bilgi için Bkz. [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Çözümü derleyin.

     **Çıktı** penceresi yalnızca yapı için özet bilgileri görüntüler.

     ![Çıkış Penceresi, Görsel C&#35; Yapı Uyarıları](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Tüm Visual Basic yapı uyarılarını bastırma

1. **Çözüm Gezgini'nde,** üst düzey proje düğümlerini seçin.

2. Menü çubuğunda**Özellik Sayfalarını** **Görüntüle'yi** > seçin.

     **Proje Tasarımcısı** açılır.

3. **Derle** sayfasında, tüm **uyarıları devre dışı bırakma** onay kutusunu seçin.

     ![Derleme sayfası, Proje Tasarımcısı](../ide/media/buildwalk_vbsuppresswarnings.png)

     Daha fazla bilgi için [Visual Basic'teki uyarıları yapılandır' a](../ide/configuring-warnings-in-visual-basic.md)bakın.

4. Çözümü derleyin.

   **Çıktı** penceresi yalnızca yapı için özet bilgileri görüntüler.

   ![Çıkış Penceresi, Visual Basic Yapı Uyarıları](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Daha fazla bilgi için [bkz: Derleyici uyarılarını bastırın.](../ide/how-to-suppress-compiler-warnings.md)

## <a name="display-additional-build-details-in-the-output-window"></a>Çıktı penceresinde ek yapı ayrıntılarını görüntüleme

Oluşturma işlemi yle ilgili bilgilerin **Çıktı** penceresinde ne kadar göründüğünü değiştirebilirsiniz. Yapı ayrıntılılığı genellikle **Minimal**olarak ayarlanır, bu da **Çıkış** penceresinin yüksek öncelikli uyarılar veya hatalarla birlikte yapı işleminin yalnızca bir özetini görüntülediği anlamına gelir. [Seçenekler iletişim kutusunu, Projeler ve Çözümleri, Oluştur ve Çalıştır'ı](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)kullanarak yapı hakkında daha fazla bilgi görüntüleyebilirsiniz.

> [!IMPORTANT]
> Daha fazla bilgi görüntülerseniz, yapının tamamlanması daha uzun sürer.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Çıktı penceresindeki bilgi miktarını değiştirme

1. **Seçenekler** iletişim kutusunu açın.

     ![Araçlar menüsünde seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png)

1. Projeler **ve Çözümler** kategorisini seçin ve ardından **Yap ve Çalıştır** sayfasını seçin.

1. **MSBuild projesinde çıktı ayrıntılı liste oluşturun,** **Normal'i**seçin ve ardından **Tamam** düğmesini seçin.

1. Menü çubuğunda, **Çözüm** > **Oluştur'u**seçin.

1. Çözümü oluşturun ve **çıktı** penceresindeki bilgileri gözden geçirin.

     Yapı bilgileri, yapının başladığı zamanı (başlangıçta bulunan) ve dosyaların işlenme sırasını içerir. Bu bilgiler, Visual Studio'nun yapı sırasında çalıştırdığı gerçek derleyici sözdizimini de içerir.

     Örneğin, C# yapısında [,/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) seçeneği, bu konuda daha önce belirttiğiniz **0168**uyarı kodunu ve diğer üç uyarıyı listeler.

     Visual Basic yapısında, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) hariç tutmak için belirli uyarılar içermez, bu nedenle hiçbir uyarı görünmez.

    > [!TIP]
    > + **Ctrl****F** tuşlarını seçerek **Bul** iletişim kutusunu görüntülerseniz **Çıkış** penceresinin içeriğini arayabilirsiniz.

Daha fazla bilgi için [bkz: Yapı günlüğü dosyalarını görüntülemek, kaydetmek ve yapılandırmak.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="create-a-release-build"></a>Yayın Derlemesi Oluşturma

Örnek uygulamanın gönderim için en iyi duruma getirilmiş bir sürümünü oluşturabilirsiniz. Sürüm yapısı için, yürütülebilir yapı başlamadan önce bir ağ payına kopyalanır belirtin.

Daha fazla bilgi [için bkz: Yapı çıktı dizini](../ide/how-to-change-the-build-output-directory.md) ve Yapı'yı değiştirin [ve Visual Studio'da projeleri ve çözümleri temizleyin.](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

### <a name="specify-a-release-build-for-visual-basic"></a>Visual Basic için sürüm oluşturma

1. Proje **Tasarımcısını**açın.

     ![Menüyü görüntüle, Özellik Sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. **Derle** sayfasını seçin.

1. **Yapılandırma** **listesinde, Release'i**seçin.

1. **Platform** listesinde **x86'yı**seçin.

1. Yapı **çıktıyol** kutusunda bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz. `\\myserver\builds`

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabileceği konusunda sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız, ileti kutusundaki **Tamam** düğmesini seçin.

1. Uygulamayı derleyin.

     ![Yapı menüsünde Çözüm Oluşturma komutu](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>C için sürüm oluşturma belirtin\#

1. Proje **Tasarımcısını**açın.

     ![Menüyü görüntüle, Özellik Sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. **Yapı** sayfasını seçin.

1. **Yapılandırma** **listesinde, Release'i**seçin.

1. **Platform** listesinde **x86'yı**seçin.

1. Çıktı **yolu** kutusunda bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz. `\\myserver\builds`

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabileceği konusunda sizi uyaran bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız, ileti kutusundaki **Tamam** düğmesini seçin.

1. Standart **araç çubuğunda,** Çözüm Yapılandırmalarını **Serbest Bırakmak** için ve Çözüm Platformlarını **x86**olarak ayarlayın.

1. Uygulamayı derleyin.

     ![Yapı menüsünde Çözüm Oluşturma komutu](../ide/media/exploreide-buildsolution.png)

   Çalıştırılabilir dosya belirttiğiniz ağ yoluna kopyalanır. Onun `\\myserver\builds\\FileName.exe`yolu.

Tebrikler! Bu gözden geçirme yi başarıyla tamamladınız.

## <a name="see-also"></a>Ayrıca bkz.

- [İzim: Proje oluşturma (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET web uygulaması proje precompilation genel bakış](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Walkthrough: MSBuild'i kullan](../msbuild/walkthrough-using-msbuild.md)
