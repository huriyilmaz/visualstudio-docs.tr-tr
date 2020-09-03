---
title: 'İzlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6192eb5583e7d0bc37518e995aacccad643cc9ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850343"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>İzlenecek yol: Temel Yalıtılmış Kabuk Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, yalıtılmış bir kabuk çözümünün nasıl oluşturulduğunu, yardım hakkında araç penceresini özelleştirmeyi ve yalıtılmış Kabuğu yükleyen bir kurulum programı oluşturmayı gösterir.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Yalıtılmış Kabuğu dağıtmak için, Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paketini de kullanmanız gerekir.  
  
## <a name="creating-an-isolated-shell-solution"></a>Yalıtılmış Kabuk çözümü oluşturma  
 Bu bölümde, yalıtılmış bir kabuk çözümü oluşturmak için Visual Studio Kabuğu yalıtılmış proje şablonunun nasıl kullanılacağı gösterilmektedir. Çözüm aşağıdaki projeleri içerir:  
  
- *SolutionName*. Yardım/hakkında kutusunun görünümünü özelleştirmenizi sağlayan AboutBoxPackage projesi.  
  
- Yalıtılmış Kabuk uygulamasının farklı bileşenlerini tanımlayan Source. Extension. valtmanifest dosyasını içeren ShellExtensionsVSIX projesi.  
  
- Yalıtılmış kabuk uygulamasını çağıran yürütülebilir dosyayı üreten *SolutionName* projesi. Bu proje, yalıtılmış Kabuk uygulamasının görünümünü ve davranışını özelleştirmenizi sağlayan kabuk özelleştirme klasörünü içerir.  
  
- Etkin menü komutlarını ve yerelleştirilebilir dizeleri tanımlayan bir uydu derlemesi üreten *SolutionName* Kullanıcı Arabirimi projesi.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Temel yalıtılmış bir kabuk çözümü oluşturmak için  
  
1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.  
  
2. **Yeni proje** penceresinde **diğer proje türleri** ' ni ve ardından **genişletilebilirlik**' i genişletin. **Visual Studio Kabuğu yalıtılmış** proje şablonunu seçin.  
  
3. Projeyi adlandırın `MyVSShellStub` ve bir konum belirtin. **Çözüm için dizin oluşturma** 'nın işaretli olduğundan emin olun ve ardından **Tamam**' a tıklayın.  
  
     Yeni çözüm **Çözüm Gezgini**görüntülenir.  
  
4. Çözümü oluşturun ve yalıtılmış Kabuk uygulamasında hata ayıklamayı başlatın.  
  
     Visual Studio yalıtılmış Kabuğu görüntülenir. Başlık çubuğu **MyVSShellStub**'ı okur. Başlık çubuğu simgesi \MyVSShellStub\Resource Files\applicationicon.exe adresinden oluşturulur.  
  
## <a name="customizing-the-application-name-and-icon"></a>Uygulama adı ve simgesini özelleştirme  
 Şirketinizin adını ve başlık çubuğundaki logosunu kullanarak uygulamanıza marka eklemek isteyebilirsiniz. Aşağıdaki adımlarda, MyVSShellStub. Application. pkgdef paket tanım dosyasını değiştirerek özel uygulama başlık çubuğunda görüntülenen ad ve simgenin nasıl değiştirileceği gösterilmektedir.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Uygulama adını ve simgesini özelleştirmek için  
  
1. MyVSShellStub projesinde \Shell Customization\MyVSShellStub.Application.pkgdef. öğesini açın.  
  
2. `AppName`Öğe değerini **"AppName" = "Fabrikam Music Düzenleyicisi"** olarak değiştirin  
  
3. Uygulama simgesini değiştirmek için, \MyVSShellStub\MyVSShellStub\MyVSShellStub\ dizinine farklı bir simge kopyalayın. Mevcut ApplicationIcon. ico dosyasını ApplicationIcon1. ico olarak yeniden adlandırın. Yeni dosyayı ApplicationIcon. ico olarak yeniden adlandırın.  
  
4. Çözümü oluşturun ve hata ayıklamayı başlatın. Yalıtılmış Kabuk IDE belirir. Başlık çubuğu, **fabrikam Music Düzenleyicisi**sözcüklerinin yanında yeni simgenizi içerir.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Varsayılan Web tarayıcısı giriş sayfasını özelleştirme  
 Bu bölümde, paket tanımı dosyasını değiştirerek **Web tarayıcısı** penceresinin varsayılan giriş sayfasının nasıl değiştirileceği gösterilmektedir.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Varsayılan Web tarayıcısı giriş sayfasını özelleştirmek için  
  
1. MyVSShellStub. Application. pkgdef dosyasında, `DefaultHomePage` öğe değerini "" olarak değiştirin <https://www.microsoft.com> .  
  
2. MyVSShellStub projesini yeniden derleyin.  
  
3. Çözümü oluşturun ve hata ayıklamayı başlatın.  
  
4. **Görünüm/diğer pencereler**' de **Web tarayıcısı**' na tıklayın. **Web tarayıcısı** penceresi, Microsoft Corporation giriş sayfasını görüntüler.  
  
## <a name="removing-the-print-command"></a>Print komutunu kaldırma  
 Yalıtılmış bir kabuk Kullanıcı arabirimi projesindeki. vsct dosyası form öğesinin bir bildirim kümesinden oluşur; `<Define name=No_` *Element* `>` burada *öğe* standart Visual Studio menülerinin ve komutlarının biridir.  
  
 Bir bildirimin açıklama kaldırmazsa, bu menü veya komut yalıtılmış kabuktan çıkarılır. Buna karşılık, bir bildirime açıklama eklendiğinde, menü veya komut yalıtılmış kabuğa dahil edilir.  
  
 Aşağıdaki adımlarda,. vsct dosyanızdaki print komutunun açıklamasını kaldırın.  
  
#### <a name="to-remove-the-print-command"></a>Print komutunu kaldırmak için  
  
1. Yalıtılmış Kabuk uygulamasındaki **Dosya** menüsünde **Yazdır** komutunun göründüğünü doğrulayın.  
  
2. MyVSShellStubUI projesinde, düzenlenecek \Resource Files\myvsshellstubui.exe ' i açın.  
  
3. Bu satırın açıklamasını kaldırın:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Bu, Print komutunu kaldırır.  
  
5. Yalıtılmış Kabuk uygulamasında hata ayıklamayı başlatın. **Dosya/Print** komutunun kaybolduğunu doğrulayın.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Yalıtılmış kabuktan Özellikler kaldırılıyor  
 Özel yalıtılmış Kabuk uygulamanızda bu özellikleri istemiyorsanız. pkgundef dosyasını düzenleyerek Visual Studio ile yüklenen paketlerin bazılarını kaldırabilirsiniz. Paketi, $RootKey $ \Packages kayıt defteri anahtarının alt anahtarlarından birinde belirtirsiniz.  
  
> [!NOTE]
> Visual Studio özelliklerinin GUID 'Lerini bulmak için bkz. [Visual Studio özelliklerinin paket GUID 'leri](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Aşağıdaki yordamda, yalıtılmış kabuktan XML düzenleyicisinin nasıl kaldırılacağı gösterilmektedir.  
  
#### <a name="to-remove-the-xml-editor"></a>XML düzenleyicisini kaldırmak için  
  
1. MyVSShellStub. pkgundef dosyasını MyVSShellStub projesinin Shell customization klasöründe açın.  
  
2. Aşağıdaki satırın açıklamasını kaldırın:  
  
     [$RootKey $ \Packages \\ {87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Çözümü yeniden derleyin ve yalıtılmış kabukta hata ayıklamayı başlatın. Bir XML dosyası açın, örneğin, \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Dosyadaki XML anahtar kelimelerin renklendirilmediğinden ve bir satırdaki "<" yazarak XML araç ipuçları getirmediğinden emin olun.  
  
## <a name="customizing-the-helpabout-box"></a>Yardım/hakkında kutusunu özelleştirme  
 Yalıtılmış Kabuk proje şablonunun bir parçası olarak oluşturulan yardım/hakkında kutusunu özelleştirebilirsiniz.  
  
#### <a name="to-customize-the-company-name"></a>Şirket adını özelleştirmek için  
  
1. Şirket adı, telif hakkı bilgileri, ürün sürümü ve ürün açıklaması, \Properties\AssemblyInfo.cs dosyasındaki MyVSShellStub. AboutBoxPackage projesinde bulunur. Bu dosyayı açın.  
  
2. Fabrikam `AssemblyCompany` 2015 © değeri **fabrikam**, `AssemblyProduct` ve değerlerini fabrikam `AssemblyTitle` **Music Düzenleyicisi**olarak değiştirin ve `AssemblyCopyright` **telif hakkı**değeri:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3. Ürünün açıklamasını eklemek için, `AssemblyDescription` değeri **fabrikam Music Düzenleyicisi 'nin açıklamasıyla değiştirin.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Hata ayıklamayı Başlat ve yalıtılmış Kabuk uygulamasında **Yardım/hakkında** kutusunu açın. Değiştirilen dizeleri görmeniz gerekir. Yardım/hakkında kutusunun başlığı, `AssemblyTitle` AssemblyInfo.cs ' deki değerle aynıdır.  
  
5. **Yardım/hakkında** kutusunun kendi özellikleri MyVSShellStub. Aboutboxpackage\aboutboxpackage.xml dosyasında bulunur. Yardım/hakkında kutusunun genişliğini değiştirmek için, `AboutDialogStyle` bloğa gidin ve `Width` özelliği 200 olarak ayarlayın:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6. Çözümü yeniden derleyin ve yalıtılmış kabukta hata ayıklamayı başlatın. Yardım/hakkında kutusu yaklaşık kare olmalıdır.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Yalıtılmış kabuk uygulamasını dağıtmadan önce  
 Yalıtılmış Kabuk uygulamanız, Visual Studio Kabuğu (yalıtılmış) yeniden dağıtılabilir paketi olan herhangi bir bilgisayara yüklenebilir. Yeniden dağıtılabilir paket hakkında daha fazla bilgi için bkz. [Visual Studio genişletilebilirlik indirmeleri](https://msdn.microsoft.com/vstudio/bb984878.aspx) Web sitesi.  
  
## <a name="deploying-the-isolated-shell-application"></a>Yalıtılmış kabuk uygulamasını dağıtma  
 Yalıtılmış Kabuk uygulamanızı bir hedef bilgisayara bir kurulum projesi oluşturarak dağıtırsınız. Şunları belirtmeniz gerekir:  
  
- Hedef bilgisayardaki klasörlerin ve dosyaların yerleşimi.  
  
- .NET Framework ve Visual Studio Kabuğu çalışma zamanının hedef bilgisayarda yüklü olduğundan emin olan başlatma koşulları.  
  
  Aşağıdaki yordamda, InstallShield Limited Edition 'ı bilgisayarınıza yüklemeniz gerekir.  
  
#### <a name="to-create-the-setup-project"></a>Kurulum projesi oluşturmak için  
  
1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve ardından **Yeni Proje Ekle**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda, **diğer proje türleri** ' ni genişletin ve ardından **Kurulum ve dağıtım**' ı seçin. InstallShield şablonunu seçin. Yeni projeyi adlandırın `MySetup` ve ardından **Tamam**' a tıklayın.  
  
3. InstallShield Limited Edition zaten yüklüyse, sonraki adımla devam edin.  
  
    InstallShield Limited Edition zaten yüklü değilse InstallShield indirme sayfası açılır. Visual Studio sürümünüz ile uyumlu InstallShield sürümünü seçerek ürünü indirme ve yükleme yönergelerini izleyin. InstallShield yüklemenizi kaydetme veya değerlendirme olarak kullanma kararı vermeniz gerekir. Yüklemeyi tamamladıktan sonra Visual Studio 'Yu yeniden başlatmanız gerekir.  
  
   > [!IMPORTANT]
   > InstallShield projesi oluşturmadan önce Visual Studio 'Yu yönetici olarak başlatmalısınız. Bunu yapmazsanız, projeyi oluştururken bir hata alırsınız.  
  
   Sonraki adımlarda Kurulum projesinin nasıl yapılandırılacağı gösterilmektedir.  
  
> [!IMPORTANT]
> Kurulum projesini yapılandırmadan önce yalıtılmış Kabuk projenizin yayın yapılandırmasını en az bir kez derlediğinizden emin olun.  
  
#### <a name="to-configure-the-setup-project"></a>Kurulum projesini yapılandırmak için  
  
1. **Çözüm Gezgini**, **MySetup** projesi altında **Proje Yardımcısı**' nı seçin. **Proje Yardımcısı** penceresinin alt satırında **uygulama bilgileri**' ni seçin. Uygulamanızın adı olarak **fabrikam** 'ı şirketinizin adı ve **fabrikam Music Düzenleyicisi** olarak girin. **Proje yardımcısının**sağ alt tarafındaki ileri oku seçin.  
  
2. **Uygulamanızın makinede herhangi bir yazılımın yüklü olmasını istiyor musunuz?** altında **Evet** ' i seçin ve ardından **Microsoft .NET Framework 4,5 tam paket**' i seçin.  
  
3. Pencerenin alt kısmındaki **uygulama dosyaları** düğmesini seçin ve **fabrikam Music Düzenleyicisi** klasörünün seçili olduğundan emin olun.  
  
4. **Dosya Ekle** düğmesini seçin. **Dosya Ekle** iletişim kutusunda, **MyVSShellStub\Release** klasöründen aşağıdaki dosyaları ekleyin:  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll. manifest  
  
    4. MyVSShellStub. pkgdef  
  
    5. MyVSShellStub. pkgundef  
  
    6. MyVSShellStub. winprf  
  
    7. Splash.bmp  
  
5. **Proje çıktıları Ekle** düğmesine tıklayın ve **MyVSShellStub/birincil çıkış**ekleyin. **Tamam**’a tıklayın.  
  
6. Sol bölmede, **hedef bilgisayar**altında **fabrikam musıc DÜZENLEYICISI [INSTALLDİR]** düğümüne sağ tıklayın ve **Uzantılar**adlı **Yeni bir klasör** ekleyin.  
  
7. Sol bölmedeki **Uzantılar** düğümüne sağ tıklayın ve **uygulama**adlı yeni bir klasör ekleyin.  
  
8. **Uygulama** klasörünü seçin ve **proje çıktıları Ekle** düğmesine tıklayın ve ardından MyVSShellStub. AboutBoxPackage projesinden birincil çıktıyı seçin.  
  
9. **Dosya Ekle** düğmesine tıklayın ve \MyVSShellStub\Release\Extensions\Application\ klasöründen aşağıdaki dosyaları ekleyin:  
  
    - MyVSShellStub. AboutBoxPackage. pkgdef  
  
    - MyVSShellStub. Application. pkgdef  
  
10. Sol bölmedeki **fabrikam Music Düzenleyicisi [ıNSTALLDIR]** düğümüne sağ tıklayın ve **1033**adlı yeni bir klasör ekleyin.  
  
11. 1033 klasörünü seçin ve ardından **proje çıktıları Ekle** düğmesine tıklayın ve MyVSShellStubUI projesinden birincil çıktıyı seçin.  
  
12. **Uygulama kısayolları** penceresine gidin.  
  
13. Kısayol oluşturmak için **Yeni** ' ye tıklayın ve **[ProgramFilesFolder] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary output**öğesini seçin.  
  
14. **Yükleme görüşmesi** bölmesine gidin.  
  
15. Tüm öğeleri **Hayır**olarak ayarlayın.  
  
16. **Çözüm Gezgini**, MySetup projesinde, **kurulum gereksinimlerini tanımla ve eylemler \ gereksinimler**' i açın. **Gereksinimler** penceresi açılır.  
  
17. **Sistem yazılımı gereksinimleri** ' ne sağ tıklayıp **Yeni başlatma koşulu oluştur**' u seçin. **Sistem Arama Sihirbazı** görüntülenir.  
  
18. **Ne bulmak istiyorsunuz?** bölmesinde, açılan listeden **kayıt defteri girişi** ' ni seçin ve **İleri**' ye tıklayın.  
  
19. **Nasıl aramak istiyorsunuz?** bölmesinde kayıt defteri kökü olarak **HKEY_LOCAL_MACHINE** ' yi seçin. 64 bit sistemler için **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** veya 32-bit sistemler için **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** girin ve kayıt defteri değeri olarak **Install** yazın. **İleri**’ye tıklayın.  
  
20. Bu **değerle ne yapmak istiyorsunuz?** bölmesine, **Bu ürünün yüklenmesi için Visual Studio 2015 yalıtılmış Kabuk yeniden dağıtılabilir gereklidir.** görüntülenecek metin ve **son**' a tıklayın.  
  
21. Kurulum projesini oluşturmak için yalıtılmış Kabuk çözümünü yeniden derleyin.  
  
     setup.exe dosyasını aşağıdaki klasörde bulabilirsiniz:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Yükleme programını test etme  
 Kurulumu test etmek için setup.exe dosyasını farklı bir bilgisayara kopyalayın ve kurulum yürütülebilirini çalıştırın. Yalıtılmış kabuk uygulamasını çalıştırabilmelisiniz.
