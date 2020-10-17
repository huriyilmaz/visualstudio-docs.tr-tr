---
title: 'İzlenecek yol: Uygulama oluşturma'
description: Visual Studio ile uygulama oluştururken yapılandırabileceğiniz çeşitli seçeneklerle daha tanıdık olun.
ms.custom: SEO-VS-2020
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a281b90b3dabe2b1d91c43a27ee5f9c858f96c
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136621"
---
# <a name="walkthrough-build-an-application"></a>İzlenecek yol: Uygulama oluşturma

Bu yönergeyi tamamlayarak, Visual Studio ile uygulama oluştururken yapılandırabileceğiniz çeşitli seçeneklerle daha tanıdık gelecektir. Özel bir yapı yapılandırması oluşturacak, belirli uyarı iletilerini gizleyecek ve örnek bir uygulama için derleme çıkış bilgilerini artıracaksınız.

## <a name="install-the-sample-application"></a>Örnek uygulamayı yükler

[WPF uygulamalarını oluşturmaya giriş](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419) örneği ' ni indirin. C# veya Visual Basic seçin. *. Zip* dosyası indirildikten sonra ayıklayın ve Visual Studio 'Yu kullanarak *expenseitgiriş. sln* dosyasını açın.

## <a name="create-a-custom-build-configuration"></a>Özel derleme yapılandırması oluşturma

Bir çözüm oluşturduğunuzda, hata ayıklama ve yayın yapılandırma yapılandırmalarının yanı sıra varsayılan platform hedefleri çözüm için otomatik olarak tanımlanır. Daha sonra bu konfigürasyonları özelleştirebilir veya kendinizinkini oluşturabilirsiniz. Yapı yapılandırması derleme türünü belirtir. Yapı platformları, bir uygulamanın bu yapılandırma için hedeflediği işletim sistemini belirtir. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md), [derleme platformlarını anlama](../ide/understanding-build-platforms.md)ve [nasıl yapılır: hata ayıklama ve yayın yapılandırmasını belirleme](../debugger/how-to-set-debug-and-release-configurations.md).

**Configuration Manager** iletişim kutusunu kullanarak, yapılandırma ve platform ayarlarını değiştirebilir veya oluşturabilirsiniz. Bu yordamda, test için bir yapı yapılandırması oluşturacaksınız.

### <a name="create-a-build-configuration"></a>Yapı yapılandırması oluşturma

1. **Configuration Manager** iletişim kutusunu açın.

   ![Derleme menüsü, Configuration Manager komutu](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. **Etkin çözüm yapılandırması** listesinde, öğesini seçin **\<New...\>** .

1. **Yeni çözüm yapılandırması** iletişim kutusunda, yeni yapılandırmayı adlandırın `Test` , mevcut **hata ayıklama** yapılandırmasından ayarları kopyalayın ve **Tamam** düğmesini seçin.

   ![Yeni çözüm yapılandırması Iletişim kutusu](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. **Etkin çözüm platformu** listesinde, öğesini seçin **\<New...\>** .

1. **Yeni çözüm platformu** iletişim kutusunda **x64**öğesini seçin ve ayarları x86 platformundan kopyalamayın.

   ![Yeni çözüm platformu Iletişim kutusu](../ide/media/buildwalk_newsolutionplatform.png)

1. **Tamam** düğmesini seçin.

   Etkin çözüm yapılandırması, etkin çözüm platformunun x64 olarak ayarlandığı **Test** olacak şekilde değiştirilmiştir.

   ![Test yapılandırmasıyla Configuration Manager](../ide/media/buildwalk_configmanagertestconfig.png)

1. **Kapat**' ı seçin.

**Standart** araç çubuğunda **çözüm yapılandırmaları** listesini kullanarak etkin çözüm yapılandırmasını hızlı bir şekilde doğrulayabilirsiniz veya değiştirebilirsiniz.

![Çözüm yapılandırma seçeneği standart araç çubuğu](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Uygulama oluşturma

Ardından, özel yapı yapılandırmasıyla çözümü oluşturacaksınız.

### <a name="build-the-solution"></a>Çözümü derleme

- Menü **çubuğunda Build**  >  **Build Solution**' ı seçin veya **CTRL** + **SHIFT** + **B**' ye basın.

    **Çıkış** penceresi, derleme sonuçlarını görüntüler. Derleme başarılı oldu.

## <a name="hide-compiler-warnings"></a>Derleyici uyarılarını gizle

Ardından, derleyici tarafından bir uyarının oluşturulmasına neden olan bazı kodlar tanıtılcağız.

1. C# projesinde, *ExpenseReportPage.xaml.cs* dosyasını açın. **ExpenseReportPage** yönteminde aşağıdaki kodu ekleyin: `int i;` .

    VEYA

    Visual Basic projesinde *ExpenseReportPage. xaml. vb* dosyasını açın. Özel Oluşturucu **genel Sub New...**' da şu kodu ekleyin: `Dim i` .

1. Çözümü derleyin.

**Çıkış** penceresi, derleme sonuçlarını görüntüler. Derleme başarılı oldu, ancak uyarılar oluşturuldu:

![Çıkış Penceresi Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Çıkış Penceresi Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

Yapı çıkışını yığılmaları yerine, derleme sırasında belirli uyarı iletilerini geçici olarak gizleyebilirsiniz.

### <a name="hide-a-specific-c-warning"></a>Belirli bir C# uyarısını gizleme

1. **Çözüm Gezgini**' de en üst düzey proje düğümünü seçin.

1. Menü çubuğunda, **View**  >  **özellik sayfalarını**görüntüle ' yi seçin.

     **Proje Tasarımcısı** açılır.

1. **Yapı** sayfasını seçin ve ardından **uyarıları bastır** kutusunda **0168**uyarı numarasını belirtin.

     ![Derleme sayfası, proje Tasarımcısı](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Çözümü derleyin.

     **Çıkış** penceresi yalnızca derleme için Özet bilgileri görüntüler.

     ![Çıkış Penceresi, Visual C&#35; derleme uyarıları](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Tüm Visual Basic derleme uyarılarını gösterme

1. **Çözüm Gezgini**' de en üst düzey proje düğümünü seçin.

2. Menü çubuğunda, **View**  >  **özellik sayfalarını**görüntüle ' yi seçin.

     **Proje Tasarımcısı** açılır.

3. **Derle** sayfasında **tüm uyarıları devre dışı bırak** onay kutusunu seçin.

     ![Derleme sayfası, proje Tasarımcısı](../ide/media/buildwalk_vbsuppresswarnings.png)

     Daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

4. Çözümü derleyin.

   **Çıkış** penceresi yalnızca derleme için Özet bilgileri görüntüler.

   ![Çıkış Penceresi, Visual Basic derleme uyarıları](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Daha fazla bilgi için bkz. [nasıl yapılır: derleyici uyarılarını gösterme](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Çıkış penceresinde ek derleme ayrıntılarını görüntüleme

**Çıkış** penceresinde yapı işlemi hakkındaki bilgilerin ne kadar göründüğünü değiştirebilirsiniz. Yapı ayrıntı düzeyi genellikle **en az**bir olarak ayarlanır. Bu, **çıktı** penceresinin yalnızca derleme işleminin bir özetini ve yalnızca herhangi bir yüksek öncelikli uyarı veya hata ile birlikte görüntülenmesini sağlar. [Seçenekler iletişim kutusu, projeler ve çözümler, oluşturma ve çalıştırma seçeneklerini](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)kullanarak yapı hakkında daha fazla bilgi görüntüleyebilirsiniz.

> [!IMPORTANT]
> Daha fazla bilgi belirtirseniz, yapılandırmanın tamamlanması daha uzun sürer.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Çıkış penceresindeki bilgi miktarını değiştirme

1. **Seçenekler** iletişim kutusunu açın.

     ![Araçlar menüsünde Seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png)

1. **Projeler ve çözümler** kategorisini seçin ve ardından **Oluştur ve Çalıştır** sayfasını seçin.

1. **MSBuild proje derleme çıkışı ayrıntı** listesinde **normal**' i seçin ve ardından **Tamam** düğmesini seçin.

1. Menü çubuğunda, **Build**  >  **temiz çözüm**oluştur ' u seçin.

1. Çözümü oluşturun ve ardından **Çıkış** penceresindeki bilgileri gözden geçirin.

     Yapı bilgileri, yapılandırmanın başlatıldığı saati (başlangıcında bulunur) ve dosyaların işlendiği sırayı içerir. Bu bilgiler, Visual Studio 'Nun derleme sırasında çalıştığı gerçek derleyici söz dizimini da içerir.

     Örneğin, C# derlemesinde, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) seçeneği, bu konunun önceki kısımlarında yer alan üç farklı uyarıyla birlikte belirttiğiniz **0168**uyarı kodunu listeler.

     Visual Basic derlemede, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) hariç tutulacak belirli uyarıları içermez, bu nedenle hiçbir uyarı görünmez.

    > [!TIP]
    > **CTRL**F tuşlarını seçerek **bul** iletişim kutusunu görüntülediğinizde **Çıkış** penceresinin içeriğinde arama yapabilirsiniz + **F** .

Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Yayın Derlemesi Oluşturma

Örnek uygulamanın, gönderim için en iyi duruma getirilmiş bir sürümünü oluşturabilirsiniz. Yayın derlemesi için, yürütülebilir dosyanın derleme dışına çıkmadan önce bir ağ paylaşımında kopyalanacağını belirtirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: derleme çıkış dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md) ve [Visual Studio 'da projeleri ve çözümleri oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Visual Basic için bir yayın derlemesi belirtin

1. **Proje tasarımcısını**açın.

     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. **Derle** sayfasını seçin.

1. **Yapılandırma** listesinde **yayın**' ı seçin.

1. **Platform** listesinde, **x86**' yı seçin.

1. **Yapı çıkış yolu** kutusunda bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz `\\myserver\builds` .

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabilir uyarısı veren bir ileti kutusu görünür. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

1. Uygulamayı derleyin.

     ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>C için bir yayın derlemesi belirtin\#

1. **Proje tasarımcısını**açın.

     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk_viewpropertypages.png)

1. **Yapı** sayfasını seçin.

1. **Yapılandırma** listesinde **yayın**' ı seçin.

1. **Platform** listesinde, **x86**' yı seçin.

1. **Çıkış yolu** kutusunda bir ağ yolu belirtin.

     Örneğin, belirtebilirsiniz `\\myserver\builds` .

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabilir uyarısı veren bir ileti kutusu görünür. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

1. **Standart araç çubuğunda**çözüm konfigürasyonlarını **Sürüm** ve çözüm platformlarını **x86**olarak ayarlayın.

1. Uygulamayı derleyin.

     ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png)

   Yürütülebilir dosya, belirttiğiniz ağ yoluna kopyalanır. Yolu şöyle olur `\\myserver\builds\\FileName.exe` .

Tebrikler! Bu yönergeyi başarıyla tamamladınız.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: proje derleme (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [ASP.NET Web uygulaması projesi ön derlemesine genel bakış](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [İzlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md)
