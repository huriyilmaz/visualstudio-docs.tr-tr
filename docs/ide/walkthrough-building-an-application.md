---
title: 'İzlenecek yol: Uygulama oluşturma'
description: Uygulama derleme ve yapılandırma seçenekleri hakkında daha fazla bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f6ad22c1cffb04c73765a14b56b4c3f1801b0732
ms.sourcegitcommit: 56ffe075ea321809a5b0e6bdc12cf3323b3482ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135958882"
---
# <a name="walkthrough-build-an-application"></a>İzlenecek yol: Uygulama oluşturma
Bu makalede, uygulama derlemek için yapılandırılan çeşitli seçenekler hakkında daha fazla bilgi sahibi Visual Studio. Özel bir derleme yapılandırması oluşturacak, belirli uyarı iletilerini gizleyecek ve örnek bir uygulama için derleme çıkış bilgilerini artırabilirsiniz.

## <a name="install-the-sample-application"></a>Örnek uygulamayı yükleme

[WPF uygulamalarına giriş örneğini](https://github.com/microsoft/wpf-samples/tree/main/Getting%20Started/Concepts) indirin. C# veya Visual Basic. Dosya *.zip* indirdikten sonra, dosyayı ayıklar ve Visual Studio *kullanarak ExpenseItIntro.sln* dosyasını açın.

## <a name="create-a-custom-build-configuration"></a>Özel derleme yapılandırması oluşturma

Bir çözüm sanız, hata ayıklama ve yayın derleme yapılandırmaları ve bunların varsayılan platform hedefleri çözüm için otomatik olarak tanımlanır. Daha sonra bu yapılandırmaları özelleştirilebilir veya kendi yapılandırmanızı oluşturabilirsiniz. Derleme yapılandırmaları derleme türünü belirtir. Derleme platformları, bir uygulamanın bu yapılandırma için hedeflemektedir işletim sistemini belirtir. Daha fazla bilgi için [bkz. Derleme yapılandırmalarını anlama,](../ide/understanding-build-configurations.md) [Derleme platformlarını anlama](../ide/understanding-build-platforms.md)ve Nasıl kullanılır: Hata ayıklama [ve sürüm yapılandırmalarını ayarlama.](../debugger/how-to-set-debug-and-release-configurations.md)

Yapılandırmaları ve platform ayarlarını değiştirmek veya  oluşturmak için Yapılandırma Yöneticisi kullanabilirsiniz. Bu yordamda, test etmek için bir derleme yapılandırması oluştur.

### <a name="create-a-build-configuration"></a>Derleme yapılandırması oluşturma

1. Yapılandırma Yöneticisi **kutusunu** açın.

   ![Derleme menüsü, Yapılandırma Yöneticisi komutu](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. Etkin çözüm **yapılandırma listesinde'yi** **\<New...\>** seçin.

1. Yeni Çözüm **Yapılandırması iletişim kutusunda,** yeni yapılandırmaya adını ve ardından mevcut Hata Ayıklama yapılandırmasından ayarları kopyalayın ve `Test` ardından Tamam **düğmesini** seçin. 

   ![Yeni Çözüm Yapılandırması İletişim Kutusu](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. Etkin çözüm **platformu listesinde'yi** **\<New...\>** seçin.

1. Yeni **Çözüm Platformu iletişim** kutusunda **x64'ü** seçin ve x86 platformundan ayarları kopyalamayın.

   ![Yeni Çözüm Platformu İletişim Kutusu](../ide/media/buildwalk_newsolutionplatform.png)

1. Tamam **düğmesini** seçin.

   Etkin çözüm yapılandırması, etkin çözüm **platformu** x64 olarak ayarlanmış şekilde Test'e değiştirildi.

   ![Yapılandırma Yöneticisi yapılandırma ile yapılandırma](../ide/media/buildwalk_configmanagertestconfig.png)

1. **Kapat'ı seçin.**

Standart araç çubuğundaki Çözüm Yapılandırmaları listesini kullanarak etkin çözüm **yapılandırmasını hızla doğrulayın** **veya değiştirebilirsiniz.**

![Çözüm Yapılandırması seçeneği Standart Araç Çubuğu](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Uygulama oluşturma

Ardından, çözümü özel derleme yapılandırmasıyla derlemek için bir çözüme sahip oluruz.

### <a name="build-the-solution"></a>Çözümü derleme

- Menü çubuğunda Derleme **Çözümü'yü**  >  **seçin veya** **Ctrl** Shift B + **tuşlarına** + **basın.**

    Çıkış **penceresinde** derlemenin sonuçları görüntülenir. Derleme başarılı oldu.

## <a name="hide-compiler-warnings"></a>Derleyici uyarılarını gizleme

Daha sonra derleyici tarafından bir uyarının oluşturularak neden olan bazı kodlar tanıtıldı.

1. C# projesinde *ExpenseReportPage.xaml.cs dosyasını* açın. **ExpenseReportPage yöntemine** şu kodu ekleyin: `int i;` .

    VEYA

    Visual Basic *ExpenseReportPage.xaml.vb dosyasını* açın. Özel oluşturucu ortak **alt yeni...** içinde aşağıdaki kodu ekleyin: `Dim i` .

1. Çözümü derleyin.

Çıkış **penceresinde** derlemenin sonuçları görüntülenir. Derleme başarılı oldu, ancak uyarılar oluşturulmuş:

![Çıkış Penceresi Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Çıkış Penceresi Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Derleme çıkışında dağınıklık oluşturmak yerine derleme sırasında belirli uyarı iletilerini geçici olarak gizleyebilirsiniz.

### <a name="hide-a-specific-c-warning"></a>Belirli bir C# uyarıyı gizleme

1. Bu **Çözüm Gezgini** üst düzey proje düğümünü seçin.

1. Menü çubuğunda Özellik Sayfalarını **Görüntüle'yi**  >  **seçin.**

     Project **Tasarımcısı** açılır.

1. Derleme **sayfasını** seçin ve ardından Uyarıları bastır **kutusunda** **0168 uyarı numarasını belirtin.**

     ![Derleme sayfası, Project Tasarımcısı](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Daha fazla bilgi için [bkz. Derleme Sayfası, Project Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Çözümü derleyin.

     Çıkış **penceresi** yalnızca derlemenin özet bilgilerini görüntüler.

     ![Çıkış Penceresi, Visual C&#35; Derleme Uyarıları](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Tüm derleme Visual Basic uyarılarını gizleme

1. Bu **Çözüm Gezgini** üst düzey proje düğümünü seçin.

2. Menü çubuğunda Özellik Sayfalarını **Görüntüle'yi**  >  **seçin.**

     Project **Tasarımcısı** açılır.

3. Derle **sayfasında** Tüm uyarıları devre **dışı bırak onay** kutusunu seçin.

     ![Derleme sayfası, Project Tasarımcısı](../ide/media/buildwalk_vbsuppresswarnings.png)

     Daha fazla bilgi için [bkz. Visual Basic.](../ide/configuring-warnings-in-visual-basic.md)

4. Çözümü derleyin.

   Çıkış **penceresi** yalnızca derlemenin özet bilgilerini görüntüler.

   ![Çıkış Penceresi, Visual Basic Uyarıları](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Daha fazla bilgi için [bkz. Nasıl: Derleyici uyarılarını gizleme.](../ide/how-to-suppress-compiler-warnings.md)

## <a name="display-additional-build-details-in-the-output-window"></a>Çıkış penceresinde ek derleme ayrıntılarını görüntüleme

Çıkış penceresinde derleme işlemi hakkında ne kadar bilgi görüntülendiğinden **bunu değiştirebilirsiniz.** Derleme ayrıntılılığı genellikle Minimum olarak **ayarlanır.** Bu, Çıkış penceresinin derleme işleminin yalnızca bir özetini ve tüm yüksek öncelikli uyarıları veya hataları görüntülemesi anlamına gelir.  Seçenekler iletişim kutusunu, Projeler ve Çözümler'i, Derlemeyi ve Çalıştırmayı [kullanarak derleme hakkında daha fazla bilgi görüntüebilirsiniz.](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)

> [!IMPORTANT]
> Daha fazla bilgi görüntülersiniz, derlemenin tamamlanması daha uzun sürer.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Çıkış penceresindeki bilgi miktarını değiştirme

1. Seçenekler **iletişim** kutusunu açın.

     ![Araçlar menüsündeki Seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png)

1. Projeler **ve Çözümler kategorisini** ve ardından Derleme ve **Çalıştırma sayfasını** seçin.

1. Proje **MSBuild çıkış ayrıntılılığı listesinde Normal'i** ve ardından Tamam **düğmesini** seçin.

1. Menü çubuğunda Çözümü **Temizle'yi**  >  **seçin.**

1. Çözümü derleme ve çıkış penceresindeki bilgileri **gözden** geçirme.

     Derleme bilgileri, derlemenin başladığı zamanı (başlangıçta bulunur) ve dosyaların işlenme sıralarını içerir. Bu bilgiler ayrıca derleme sırasında çalışan gerçek derleyici Visual Studio söz dizimlerini de içerir.

     Örneğin, C# derlemesinde [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) seçeneği, bu konuda daha önce belirttiğiniz uyarı kodu **olan 0168'i** ve diğer üç uyarıyı listeler.

     Derleme Visual Basic, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) dışlamak için belirli uyarılar içermez, bu nedenle hiçbir uyarı görünmez.

    > [!TIP]
    > Ctrl F tuşlarını **seçerek** Bul iletişim  kutusunu görüntülerken Çıkış penceresinin **içeriklerini** + **arayabilirsiniz.**

Daha fazla bilgi için [bkz. Nasıl yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma.](../ide/how-to-view-save-and-configure-build-log-files.md)

## <a name="create-a-release-build"></a>Yayın Derlemesi Oluşturma

Örnek uygulamanın gönderim için iyileştirilmiş bir sürümünü derlemek için. Yayın derlemesi için, derleme başlamadan önce yürütülebilir dosyanın bir ağ paylaşımına kopyalanmış olduğunu belirtebilirsiniz.

Daha fazla bilgi için [bkz. Nasıl kullanılır: Derleme çıkış dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md) [ve](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)Visual Studio.

### <a name="specify-a-release-build-for-visual-basic"></a>Visual Basic için yayın derlemesi belirtme

1. Project **Designer'Project açın.**

     ![Görünüm menüsü, Özellik Sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. Derle **sayfasını** seçin.

1. Yapılandırma listesinde **Yayın'ı** **seçin.**

1. Platform **listesinde** **x86'yi seçin.**

1. Derleme **çıkış yolu kutusunda** bir ağ yolu belirtin.

     Örneğin, `\\myserver\builds` belirtesiniz.

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmadığını belirten bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

1. Uygulamayı derleyin.

     ![Derleme menüsünde Çözümü Derleme komutu](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>C için yayın derlemesi belirtme\#

1. Project **Designer'Project açın.**

     ![Görünüm menüsü, Özellik Sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. Derleme **sayfasını** seçin.

1. Yapılandırma listesinde **Yayın'ı** **seçin.**

1. Platform **listesinde** **x86'yi seçin.**

1. Çıkış **yolu kutusunda** bir ağ yolu belirtin.

     Örneğin, `\\myserver\builds` belirtesiniz.

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmadığını belirten bir ileti kutusu görünebilir. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

1. Standart araç **çubuğunda Çözüm** Yapılandırmaları'nın Yayın ve **Çözüm** Platformları'nın **x86 olarak ayarlayın.**

1. Uygulamayı derleyin.

     ![Derleme menüsünde Çözümü Derleme komutu](../ide/media/exploreide-buildsolution.png)

   Yürütülebilir dosya, belirttiğiniz ağ yoluna kopyalanır. Yolu `\\myserver\builds\\FileName.exe` olur.

Tebrikler! Bu izlenecek yolu başarıyla tamamladın.

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Proje derleme (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET web uygulaması proje ön derlemeye genel bakış](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Adım adım kılavuz: MSBuild](../msbuild/walkthrough-using-msbuild.md)
