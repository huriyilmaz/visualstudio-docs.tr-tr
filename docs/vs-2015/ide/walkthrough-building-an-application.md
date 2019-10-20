---
title: 'İzlenecek yol: uygulama oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 4842955d-8959-4e4e-98b8-2358360179b3
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f96909d3051e18fe3992e68b44b2948d1e23ebd6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670129"
---
# <a name="walkthrough-building-an-application"></a>İzlenecek yol: Uygulama Oluşturma

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönergeyi tamamlayarak, Visual Studio ile uygulama oluştururken yapılandırabileceğiniz çeşitli seçeneklerle daha tanıdık gelecektir. Özel bir yapı yapılandırması oluşturacak, belirli uyarı iletilerini gizleyecek ve örnek bir uygulama için diğer görevlerin yanı sıra derleme çıkış bilgilerini arttıracaksınız.

Bu konu aşağıdaki bölümleri içermektedir:

[Örnek uygulamayı yükler](../ide/walkthrough-building-an-application.md#BKMK_installapp)

[Özel derleme yapılandırması oluşturma](../ide/walkthrough-building-an-application.md#BKMK_CreateBuildConfig)

[Uygulamayı oluşturma](../ide/walkthrough-building-an-application.md#BKMK_building)

[Derleyici uyarılarını gizle](../ide/walkthrough-building-an-application.md#BKMK_hidewarning)

[Çıkış Penceresi ek derleme ayrıntılarını görüntüleme](../ide/walkthrough-building-an-application.md#BKMK_outputdetails)

[Yayın derlemesi oluşturma](../ide/walkthrough-building-an-application.md#BKMK_releasebuild)

## <a name="BKMK_installapp"></a>Örnek uygulamayı yükler

**Uzantılar ve güncelleştirmeler** iletişim kutusunu, Microsoft Web sitesindeki örnekler galerisinden [WPF uygulamalarını oluşturmaya giriş](http://code.msdn.microsoft.com/Introduction-to-Building-b8d16419?SRC=VSIDE) ' i bulmak ve yüklemek için kullanacaksınız. Örnekler Galerisi, uygulamalarınızı planlarken ve geliştirirken, indirebileceğiniz ve gözden geçirebileceğiniz çeşitli örnek projeler ve kodlar sağlar.

#### <a name="to-install-the-sample-application"></a>Örnek uygulamayı yüklemek için

1. Menü çubuğunda **Araçlar**, **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Çevrimiçi** kategorisini seçin ve ardından **örnekler Galeri** kategorisini seçin.

3. Örneği bulmak için arama kutusunda `Introduction` belirtin.

    ![Uzantılar ve güncelleştirmeler iletişim kutusu](../ide/media/buildwalk-extensionsdialogsampledownload.png "BuildWalk_ExtensionsDialogSampleDownload")

4. Sonuçlar listesinde, **WPF uygulamaları oluşturmaya giriş (görsel C#)** veya **WPF uygulamaları oluşturmaya giriş (Visual Basic)** seçeneğini belirleyin.

5. **İndir** düğmesini seçin ve sonra **Kapat** düğmesini seçin.

   WPF uygulamaları oluşturmaya giriş örneği **Yeni proje** iletişim kutusunda görünür.

#### <a name="to-create-a-solution-for-the-sample-application"></a>Örnek uygulama için bir çözüm oluşturmak için

1. **Yeni proje** iletişim kutusunu açın.

     ![Menü çubuğunda dosya, yeni, proje ' yi seçin.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. **Yüklü** KATEGORIDE, WPF uygulamaları oluşturmaya giriş örneğini göstermek için **örnekler** kategorisini seçin.

3. Visual C#için çözüm `IntroWPFcsharp` adlandırın.

     ![Yeni proje iletişim kutusu, yüklü örnekler](../ide/media/buildwalk-newprojectdlgintrotowpfsample.png "BuildWalk_NewProjectdlgIntrotoWPFsample")

     VEYA

     @No__t_0 Visual Basic için çözümü adlandırın.

     ![Yeni proje iletişim kutusu, Visual Basic örneği](../ide/media/buildwalk-newprojectdlgintrotowpfsamplevb.png "BuildWalk_NewProjectdlgIntrotoWPFsampleVB")

4. **Tamam** düğmesini seçin.

## <a name="BKMK_CreateBuildConfig"></a>Özel derleme yapılandırması oluşturma

Bir çözüm oluşturduğunuzda, hata ayıklama ve yayın yapılandırma yapılandırmalarının yanı sıra varsayılan platform hedefleri çözüm için otomatik olarak tanımlanır. Daha sonra bu konfigürasyonları özelleştirebilir veya kendinizinkini oluşturabilirsiniz. Yapı yapılandırması derleme türünü belirtir. Yapı platformları, bir uygulamanın bu yapılandırma için hedeflediği işletim sistemini belirtir. Daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md), [derleme platformlarını anlama](../ide/understanding-build-platforms.md)ve [proje yapılandırmasını hata ayıklama ve yayınlama](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

**Configuration Manager** iletişim kutusunu kullanarak, yapılandırma ve platform ayarlarını değiştirebilir veya oluşturabilirsiniz. Bu yordamda, test için bir yapı yapılandırması oluşturacaksınız.

#### <a name="to-create-a-build-configuration"></a>Yapı yapılandırması oluşturmak için

1. **Configuration Manager** iletişim kutusunu açın.

    ![Derleme menüsü, Configuration Manager komutu](../ide/media/buildwalk-configurationmanagerdialogbox.png "BuildWalk_ConfigurationManagerDialogBox")

2. **Etkin çözüm yapılandırması** listesinde **Yeni**' yi seçin.

3. **Yeni çözüm yapılandırması** iletişim kutusunda yeni yapılandırma `Test` adlandırın, mevcut hata ayıklama yapılandırmasından ayarları kopyalayın ve **Tamam** düğmesini seçin.

    ![Yeni çözüm yapılandırması Iletişim kutusu](../ide/media/buildwalk-newsolutionconfigdlgbox.png "BuildWalk_NewSolutionConfigDlgBox")

4. **Etkin çözüm platformu** listesinde **Yeni**' yi seçin.

5. **Yeni çözüm platformu** iletişim kutusunda **x64**öğesini seçin ve ayarları x86 platformundan kopyalamayın.

    ![Yeni çözüm platformu Iletişim kutusu](../ide/media/buildwalk-newsolutionplatform.png "BuildWalk_NewSolutionPlatform")

6. **Tamam** düğmesini seçin.

   Etkin çözüm yapılandırması, etkin çözüm platformunun x64 olarak ayarlandığı test olacak şekilde değiştirilmiştir.

   ![Test yapılandırmasıyla Configuration Manager](../ide/media/buildwalk-configmanagertestconfig.png "BuildWalk_ConfigManagerTestconfig")

   **Standart** araç çubuğunda **çözüm yapılandırmaları** listesini kullanarak etkin çözüm yapılandırmasını hızlı bir şekilde doğrulayabilirsiniz veya değiştirebilirsiniz.

   ![Çözüm yapılandırma seçeneği standart araç çubuğu](../ide/media/buildwalk-standardtoolbarsolutioncongfig.png "BuildWalk_StandardToolbarSolutionCongfig")

## <a name="BKMK_building"></a>Uygulamayı oluşturma

Ardından, özel yapı yapılandırmasıyla çözümü oluşturacaksınız.

#### <a name="to-build-the-solution"></a>Çözümü oluşturmak için

- Menü çubuğunda **Oluştur**, **çözüm oluştur**' u seçin.

  **Çıkış** penceresi, derleme sonuçlarını görüntüler. Derleme başarılı oldu, ancak birkaç uyarı iletisi üretildi.

  Şekil 1: Visual Basic uyarıları

  ![Çıkış Penceresi Visual Basic](../ide/media/buildwalk-vbbuildoutputwnd.png "BuildWalk_VBBuildOutputWnd")

  Şekil 2: görsel C# uyarılar

  ![Çıkış Penceresi Visual C&#35;](../ide/media/buildwalk-csharpbuildoutputwnd.png "BuildWalk_CsharpBuildOutputWnd")

## <a name="BKMK_hidewarning"></a>Derleyici uyarılarını gizle

Yapı çıkışını yığılmaları yerine, derleme sırasında belirli uyarı iletilerini geçici olarak gizleyebilirsiniz.

#### <a name="to-hide-a-specific-visual-c-warning"></a>Belirli bir görsel C# uyarıyı gizlemek için

1. **Çözüm Gezgini**' de en üst düzey proje düğümünü seçin.

2. Menü çubuğunda **Görünüm**, **Özellik sayfaları**' nı seçin.

     **Proje Tasarımcısı** açılır.

3. **Yapı** sayfasını seçin ve ardından **uyarıları bastır** kutusunda `1762` uyarı numarasını belirtin.

     ![Derleme sayfası, proje Tasarımcısı](../ide/media/buildwalk-csharpsuppresswarnings.png "BuildWalk_CsharpSuppressWarnings")

     Daha fazla bilgi için bkz. [derleme sayfası, proje TasarımcısıC#()](../ide/reference/build-page-project-designer-csharp.md).

4. Çözümü oluşturun.

     **Çıkış** penceresi yalnızca derleme için Özet bilgileri görüntüler.

     ![Çıkış Penceresi, Visual C&#35; derleme uyarıları](../ide/media/buildwalk-visualcsharpbuildwarnings.png "BuildWalk_VisualCsharpBuildWarnings")

#### <a name="to-suppress-all-visual-basic-build-warnings"></a>Tüm Visual Basic derleme uyarılarını gizlemek için

1. **Çözüm Gezgini**' de en üst düzey proje düğümünü seçin.

2. Menü çubuğunda **Görünüm**, **Özellik sayfaları**' nı seçin.

    **Proje Tasarımcısı** açılır.

3. **Derle** sayfasında **tüm uyarıları devre dışı bırak** onay kutusunu seçin.

    ![Derleme sayfası, proje Tasarımcısı](../ide/media/buildwalk-vbsuppresswarnings.png "BuildWalk_VBSuppressWarnings")

    Daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](../ide/configuring-warnings-in-visual-basic.md).

4. Çözümü oluşturun.

   **Çıkış** penceresi yalnızca derleme için Özet bilgileri görüntüler.

   ![Çıkış Penceresi, Visual Basic derleme uyarıları](../ide/media/buildwalk-visualbasicbuildwarnings.png "BuildWalk_VisualBasicBuildWarnings")

   Daha fazla bilgi için bkz. [nasıl yapılır: derleyici uyarılarını gösterme](../ide/how-to-suppress-compiler-warnings.md).

## <a name="BKMK_outputdetails"></a>Çıkış Penceresi ek derleme ayrıntılarını görüntüleme

**Çıkış** penceresinde yapı işlemi hakkındaki bilgilerin ne kadar göründüğünü değiştirebilirsiniz. Yapı ayrıntı düzeyi genellikle en az bir olarak ayarlanır. Bu, **çıktı** penceresinin yalnızca derleme işleminin bir özetini ve yalnızca herhangi bir yüksek öncelikli uyarı veya hata ile birlikte görüntülenmesini sağlar. [Seçenekler Iletişim kutusu, projeler ve çözümler, oluşturma ve çalıştırma seçeneklerini](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)kullanarak yapı hakkında daha fazla bilgi görüntüleyebilirsiniz.

> [!IMPORTANT]
> Daha fazla bilgi belirtirseniz, yapılandırmanın tamamlanması daha uzun sürer.

#### <a name="to-change-the-amount-of-information-in-the-output-window"></a>Çıkış penceresindeki bilgi miktarını değiştirmek için

1. **Seçenekler** iletişim kutusunu açın.

    ![Araçlar menüsünde Seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-araçları Seçenekseçenekleri menüsü")

2. **Projeler ve çözümler** kategorisini seçin ve ardından **Oluştur ve Çalıştır** sayfasını seçin.

3. **MSBuild proje derleme çıkışı ayrıntı** listesinde **normal**' i seçin ve ardından **Tamam** düğmesini seçin.

4. Menü çubuğunda **Oluştur**, **Çözümü Temizle**' yi seçin.

5. Çözümü oluşturun ve ardından **Çıkış** penceresindeki bilgileri gözden geçirin.

    Yapı bilgileri, yapılandırmanın başlatıldığı süreyi (başlangıcında bulunur), dosyaların işlendiği sırayı ve işlemin tamamlanması için geçen süreyi (sonunda bulunur) içerir. Bu bilgiler, Visual Studio 'Nun derleme sırasında çalıştığı gerçek derleyici söz dizimini da içerir.

    Örneğin, görsel C# derlemede, [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) seçeneği, bu konunun önceki kısımlarında yer alan üç farklı uyarıyla birlikte belirttiğiniz 1762 uyarı kodunu listeler.

    Visual Basic derlemede, [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) hariç tutulacak belirli uyarıları içermez, bu nedenle hiçbir uyarı görünmez.

   > [!TIP]
   > CTRL + F tuşlarını seçerek **bul** iletişim kutusunu görüntülediğinizde **Çıkış** penceresinin içeriğinde arama yapabilirsiniz.

   Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="BKMK_releasebuild"></a>Yayın derlemesi oluşturma

Örnek uygulamanın, gönderim için en iyi duruma getirilmiş bir sürümünü oluşturabilirsiniz. Yayın derlemesi için, yürütülebilir dosyanın derleme dışına çıkmadan önce bir ağ paylaşımında kopyalanacağını belirtirsiniz.

Daha fazla bilgi için bkz. [nasıl yapılır: derleme çıkış dizinini değiştirme](../ide/how-to-change-the-build-output-directory.md) ve [Visual Studio 'Da projeleri ve çözümleri oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

#### <a name="to-specify-a-release-build-for-visual-basic"></a>Visual Basic için bir yayın derlemesi belirtmek için

1. **Proje tasarımcısını**açın.

     ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. **Derle** sayfasını seçin.

3. **Yapılandırma** listesinde **yayın**' ı seçin.

4. **Platform** listesinde, **x86**' yı seçin.

5. **Yapı çıkış yolu** kutusunda bir ağ yolu belirtin.

     Örneğin, \ myserver\builds\\ belirtebilirsiniz.

    > [!IMPORTANT]
    > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabilir uyarısı veren bir ileti kutusu görünür. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

6. Uygulamayı derleyin.

     ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

#### <a name="to-specify-a-release-build-for-visual-c"></a>Visual C \# için bir yayın derlemesi belirtmek için

1. **Proje tasarımcısını**açın.

    ![Görünüm menüsü, özellik sayfaları komutu](../ide/media/buildwalk-viewpropertypages.png "BuildWalk_ViewPropertyPages")

2. **Yapı** sayfasını seçin.

3. **Yapılandırma** listesinde **yayın**' ı seçin.

4. **Platform** listesinde, **x86**' yı seçin.

5. **Çıkış yolu** kutusunda bir ağ yolu belirtin.

    Örneğin, \ myserver\builds\\ belirtebilirsiniz.

   > [!IMPORTANT]
   > Belirttiğiniz ağ paylaşımının güvenilir bir konum olmayabilir uyarısı veren bir ileti kutusu görünür. Belirttiğiniz konuma güveniyorsanız ileti kutusunda **Tamam** düğmesini seçin.

6. Uygulamayı derleyin.

    ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Yürütülebilir dosya, belirttiğiniz ağ yoluna kopyalanır. Yolu, \myserver\derlemeler \\*filename*. exe \\.

   Tebrikler: Bu yönergeyi başarıyla tamamladınız.

## <a name="see-also"></a>Ayrıca Bkz.

- [İzlenecek Yol: Proje Derleme (C++)](https://msdn.microsoft.com/library/d459bc03-88ef-48d0-9f9a-82d17f0b6a4d)
- [ASP.NET Web uygulaması projesi ön derlemesine genel bakış](https://msdn.microsoft.com/b940abbd-178d-4570-b441-52914fa7b887)
- [İzlenecek Yol: MSBuild Kullanma](../msbuild/walkthrough-using-msbuild.md)
