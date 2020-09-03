---
title: Uzaktan hata ayıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300553"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı bir bilgisayara dağıtılmış bir Visual Studio uygulamasında hata ayıklaması yapabilirsiniz.  Bunu yapmak için, Visual Studio uzaktan hata ayıklayıcı 'yı kullanırsınız.  
  
 Buradaki bilgiler Windows Masaüstü uygulamaları ve ASP.NET uygulamaları için geçerlidir.  Windows Mağazası uygulamaları ve Azure uygulamalarında uzaktan hata ayıklama hakkında bilgi için bkz. [Windows Mağazası ve Azure uygulamalarında uzaktan hata ayıklama](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Uzak Araçları alın  
Uzak araçları doğrudan hata ayıklamak istediğiniz cihaza veya sunucuya indirebilir veya Visual Studio yüklü olan ana makineli uzak araçları edinebilirsiniz.

### <a name="to-download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme
  
1. Hata ayıklamak istediğiniz cihaz veya sunucu makinesinde (Visual Studio çalıştıran makine yerine), uzak araçların doğru sürümünü alın.

    |Sürüm|Bağlantı|Notlar|
    |-|-|-|
    |Visual Studio 2015 Güncelleştirme 3|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials grubuna katılarak veya geçerli bir Visual Studio aboneliğiyle oturum açmanız yeterlidir. Gerekirse bağlantıyı yeniden açın. Cihaz işletim sisteminizle (x86, x64 veya ARM sürümü) eşleşen sürümü her zaman indirin|
    |Visual Studio 2015 (eski)|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials grubuna katılarak veya geçerli bir Visual Studio aboneliğiyle oturum açmanız yeterlidir. Gerekirse bağlantıyı yeniden açın.|
    |Visual Studio 2013|[Uzak araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 belgelerine indirme sayfası|
    |Visual Studio 2012|[Uzak araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2012 belgelerinde karşıdan yükleme sayfası|
  
2. İndirme sayfasında, işletim sisteminizle (x86, x64 veya ARM sürümü) eşleşen araçların sürümünü seçin ve uzak araçları indirin.
  
    > [!IMPORTANT]
    > Visual Studio sürümünüz ile eşleşen uzak araçların en son sürümünü yüklemenizi öneririz. Eşleşmeyen sürümler önerilmez.  
    >   
    >  Ayrıca, yüklemek istediğiniz işletim sistemiyle aynı mimariye sahip uzak araçları yüklemelisiniz. Diğer bir deyişle, 64 bit işletim sistemi çalıştıran uzak bir bilgisayarda 32 bitlik bir uygulamada hata ayıklamak istiyorsanız, uzak araçların 64 bit sürümünü uzak bilgisayara yüklemelisiniz.  
  
3. Yürütülebilir dosyayı indirmeyi bitirdiğinizde, uygulamayı uzak bilgisayara yüklemek için yönergeleri izleyin. Bkz. [Kurulum yönergeleri](#bkmk_setup)

Uzaktan hata ayıklayıcıyı (msvsmon.exe) uzak bilgisayara kopyalamaya ve çalıştırmaya çalışırsanız, **Uzaktan hata ayıklayıcı yapılandırma Sihirbazı** 'nın (**rdbgwiz.exe**) yalnızca araçları indirdiğinizde yüklendiğini ve özellikle de uzaktan hata ayıklayıcının bir hizmet olarak çalışmasını istiyorsanız Sihirbazı daha sonra yapılandırmanız gerektiğini unutmayın. Daha fazla bilgi için, bkz. [(Isteğe bağlı) uzaktan hata ayıklayıcıyı aşağıdan bir hizmet olarak yapılandırın](#bkmk_configureService) .

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak için

Uzaktan hata ayıklayıcı 'yı (**msvsmon.exe**) Visual Studio 2015 Community, Professional veya Enterprise 'ın zaten yüklü olduğu bir bilgisayara bulabilirsiniz. Birçok senaryoda, uzaktan hata ayıklamayı ayarlamanın en kolay yolu, uzaktan hata ayıklayıcıyı (msvsmon.exe) bir dosya paylaşımından çalıştırmalıdır. Kullanım sınırlamaları için bkz. uzaktan hata ayıklayıcı Yardım sayfası (uzaktan hata ayıklayıcı 'da**Yardım/kullanım** ).

1. Visual Studio sürümünüz ile eşleşen dizinde **msvsmon.exe** bulun. Visual Studio 2015 için:

      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Visual Studio bilgisayarında **Uzaktan hata ayıklayıcı** klasörünü paylaşma.

3. Uzak bilgisayarda **msvsmon.exe**' yi çalıştırın. [Kurulum yönergelerini](#bkmk_setup)izleyin.

> [!TIP] 
> Komut satırı yüklemesi ve komut satırı başvurusu için, **msvsmon.exe** ``msvsmon.exe /?`` Visual Studio 'nun yüklü olduğu bilgisayardaki komut satırına yazarakmsvsmon.exeiçin yardım sayfasına bakın (veya uzaktan hata ayıklayıcı 'Da **Yardım/kullanım** bölümüne gidin).

## <a name="supported-operating-systems"></a>Desteklenen İşletim Sistemleri  
 Uzak bilgisayarın aşağıdaki işletim sistemlerinden birini çalıştırıyor olması gerekir:  
  
- Windows 10  
  
- Windows 8 veya 8,1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 veya Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Desteklenen donanım yapılandırması  
  
- 1,6 GHz veya daha hızlı işlemci  
  
- 1 GB RAM (sanal makinede çalıştırılıyorsa 1,5 GB)  
  
- 1 GB kullanılabilir sabit disk alanı  
  
- 5400 RPM sabit sürücü  
  
- 1024 x 768 veya daha yüksek görüntü çözünürlüğünde çalışan DirectX 9 uyumlu ekran kartı  
  
## <a name="network-configuration"></a>Ağ yapılandırması  
 Uzak bilgisayar ve Visual Studio bilgisayar bir ağ, çalışma grubu veya ev grubu üzerinden bağlanmış veya başka bir Ethernet kablosu üzerinden doğrudan bağlanmış olmalıdır. Internet üzerinden hata ayıklama desteklenmez.  
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Uzaktan hata ayıklayıcıyı ayarlama  
 Uzak bilgisayarda yönetici izinlerinizin olması gerekir  
  
1. Uzaktan hata ayıklayıcı uygulamasını bulun. (Başlat menüsünü açın ve **Uzaktan hata ayıklayıcı**için arama yapın.)
  
    Uzaktan hata ayıklayıcı 'yı uzak bir sunucuda çalıştırıyorsanız, uzaktan hata ayıklayıcı uygulamasına sağ tıklayıp **yönetici olarak çalıştır** ' ı (veya uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırabilirsiniz) seçebilirsiniz. Uzak bir sunucuda çalıştırmıyorsanız, normal olarak başlatmanız yeterlidir.
  
2. Uzak araçları ilk kez başlattığınızda (veya yapılandırmadan önce), **Uzaktan hata ayıklama yapılandırması** DALOG kutusu görüntülenir.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Windows hizmeti API 'SI yüklü değilse (yalnızca Windows Server 2008 R2 'de gerçekleşir), **yükleme** düğmesini seçin.  
  
4. Üzerinde Uzak araçları kullanmak istediğiniz ağ türlerini seçin. En az bir ağ türü seçilmelidir. Bilgisayarlar bir etki alanı üzerinden bağlandıysa, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlandıysa, ikinci veya üçüncü öğeyi uygun şekilde seçmeniz gerekir.  
  
5. Güvenlik duvarını yapılandırmak ve aracı başlatmak için **Uzaktan hata ayıklamayı Yapılandır** ' ı seçin.  
  
6. Yapılandırma tamamlandığında, uzaktan hata ayıklayıcı penceresi görüntülenir.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Uzaktan hata ayıklayıcı artık bir bağlantı bekliyor. Daha sonra Visual Studio 'da yapılandırma için gerekli olacak şekilde, görüntülenen sunucu adını ve bağlantı noktası numarasını bir yere göz önünde bulabilirsiniz.  
  
   Hata ayıklamayı bitirdiğinizde ve uzaktan hata ayıklayıcıyı durdurmanız gerekiyorsa, penceredeki **dosya/çıkış** ' a tıklayın. **Başlat** menüsünden veya komut satırından yeniden başlatabilirsiniz:  
  
   ** \<Visual Studio installation directory> \Common7\IDE\Remote Debugger \\<x86, x64 veya Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Uzaktan hata ayıklayıcıyı yapılandırma  
 Uzaktan hata ayıklayıcı yapılandırmasının bazı yönlerini ilk kez başlattıktan sonra değiştirebilirsiniz.
  
- Diğer kullanıcıların uzaktan hata ayıklayıcıya bağlanmasını sağlamak için **Araçlar/izinler**' i seçin. İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

  > [!IMPORTANT]
  > Uzaktan hata ayıklayıcıyı, Visual Studio bilgisayarında kullandığınız kullanıcı hesabından farklı bir kullanıcı hesabı altında çalıştırabilirsiniz, ancak uzak hata ayıklayıcının izinlerine farklı kullanıcı hesabını eklemeniz gerekir. 

   Alternatif olarak, uzaktan hata ayıklayıcıyı **/Allow \<username> ** parametresi: ** \<username@computer> msvsmon/Allow **ile komut satırından başlatabilirsiniz.
  
- Kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmek veya uzak Araçlar için bir zaman aşımı değeri belirtmek için: **Araçlar/Seçenekler**' i seçin.  
  
   Varsayılan olarak kullanılan bağlantı noktası numaralarının listesi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Yalnızca ağın kötü amaçlı veya tehlikeli trafikten risk altında olmadığından eminseniz kimlik doğrulaması yok modunu seçin.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Seçim Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma
 ASP.NET ve diğer sunucu ortamlarında hata ayıklama için, uzaktan hata ayıklayıcıyı yönetici olarak çalıştırmanız veya her zaman çalışmasını istiyorsanız, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmanız gerekir.
  
 Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırmak istiyorsanız, bu adımları izleyin.  
  
1. **Uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı** (rdbgwiz.exe) bulun. (Bu, uzaktan hata ayıklayıcı 'dan ayrı bir uygulamadır.) Yalnızca uzak araçları yüklediğinizde kullanılabilir. Visual Studio ile birlikte yüklenmez.  
  
2. Yapılandırma sihirbazını çalıştırmaya başlayın. İlk sayfa geldiğinde **İleri**' ye tıklayın.  
  
3. **Visual Studio 2015 uzaktan hata ayıklayıcı 'yı hizmet olarak çalıştır** onay kutusunu işaretleyin.  
  
4. Kullanıcı hesabının adını ve parolasını ekleyin.  
  
    Bu hesaba **bir hizmet olarak oturum** açma kullanıcısı eklemeniz gerekebilir. (Ya da bir komut isteminde **secpol** yazın) **Başlangıç** sayfasında veya penceresinde **yerel güvenlik ilkesi** (secpol. msc) bulun. Pencere göründüğünde, **Kullanıcı hakları ataması**' na çift tıklayın ve ardından sağ bölmede **hizmet olarak oturum aç** ' ı bulun. Çift tıklayın. Kullanıcı hesabını **Özellikler** penceresine ekleyin ve **Tamam**' a tıklayın.) **İleri**' ye tıklayın.  
  
5. Uzak araçların iletişim kurmasını istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarlar bir etki alanı üzerinden bağlandıysa, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlandıysa, ikinci veya üçüncü öğeleri seçmeniz gerekir. **İleri**’ye tıklayın.  
  
6. Hizmet başlatılabiliyorsanız, **Visual Studio uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı başarıyla tamamladınız**görürsünüz. Hizmet başlatılmazsa, **Visual Studio uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı tamamlamadığına**Ilişkin bir hata görürsünüz. Bu sayfa, hizmetin başlamasını sağlamak için izlenecek bazı ipuçları da sunar.  
  
7. **Son**'a tıklayın.  
  
   Bu noktada, uzaktan hata ayıklayıcı bir hizmet olarak çalışır. Bunu, **Denetim Masası/hizmetler** 'e giderek ve **Visual Studio 2015 uzaktan hata ayıklayıcı**için arayarak doğrulayabilirsiniz.  
  
   Uzaktan hata ayıklayıcı hizmetini **Denetim Masası/hizmetler**'den durdurabilir ve başlatabilirsiniz.  

## <a name="remote-debug-an-aspnet-application"></a>Bir ASP.NET uygulamasının uzaktan hata ayıklaması  
 Bir ASP.NET uygulamasının IIS çalıştıran uzak bir bilgisayara dağıtımı, IIS 'nin işletim sistemine ve sürümüne bağlı olarak farklı adımlara sahiptir. IIS 7,5 veya üzeri yüklü Windows Server 2008 veya Windows Server 2012 çalıştıran uzak bilgisayarlarda, lütfen uzak [BIR IIS bilgisayarında uzak hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)bakın.
 
 ASP.NET Core bir uygulamada hata ayıklıyorsanız lütfen bkz. [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html). IIS 'de ASP.NET Core yayımlamak için farklı adımlar gerekir. Bir ASP.NET Core uygulamasını başarılı bir şekilde yayımladıktan sonra, dnx.exe eklemek için gereken işlemin w3wp.exe yerine olması dışında, [diğer ASP.NET uygulamaları gibi](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)uzak hata ayıklaması yapabilirsiniz.

## <a name="remote-debug-a-visual-c-project"></a>Visual C++ bir projede uzaktan hata ayıklama  
 Aşağıdaki yordamda, projenin adı ve yolu C:\remotetemp\MyMfc olur ve uzak bilgisayarın adı **Mjo-DL**' dir.  
  
1. **Mymfc** ADLı bir MFC uygulaması oluşturun.  
  
2. Uygulamasının başlangıcında, **MainFrm. cpp**gibi kolayca ulaşılan uygulamada herhangi bir yere bir kesme noktası ayarlayın `CMainFrame::OnCreate` .  
  
3. Çözüm Gezgini, projeye sağ tıklayın ve **Özellikler**' i seçin. **Hata ayıklama** sekmesini açın.  
  
4. Hata ayıklayıcıyı **uzak Windows hata ayıklayıcıya** **başlatılacak şekilde** ayarlayın.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Özelliklerde aşağıdaki değişiklikleri yapın:  
  
   |Ayar|Değer|
   |-|-|  
   |Uzak komut|C:\remotetemp\mymfc.exe|  
   |Çalışma dizini|C:\remotetemp|  
   |Uzak sunucu adı|MJO-DL:*BağlantıNoktasıNumarası*|  
   |Bağlantı|Windows kimlik doğrulaması ile uzaktan|  
   |Hata ayıklayıcı türü|Yalnızca yerel|  
   |Dağıtım dizini|Ni c:\remotetemp|  
   |Dağıtılacak ek dosyalar|C:\data\mymfcdata.txt.|  
  
    Ek dosyalar dağıtırsanız (isteğe bağlı), klasörün her iki makinede de mevcut olması gerekir.  
  
6. Çözüm Gezgini, çözüme sağ tıklayın ve **Configuration Manager**' i seçin.  
  
7. **Hata ayıklama** yapılandırması için **Dağıt** onay kutusunu seçin.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Hata ayıklamayı Başlat (**Hata Ayıkla/hata ayıklamayı Başlat**veya **F5**).  
  
9. Yürütülebilir dosya otomatik olarak uzak bilgisayara dağıtılır.  
  
10. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına özgüdür. Örneğin, bir etki alanı bilgisayarında bir güvenlik sertifikası seçebilir veya etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede makine adı ve doğru parolayla birlikte geçerli bir kullanıcı hesabı adı girebilirsiniz <strong>MJO-DL\name@something.com</strong> .  
  
11. Visual Studio bilgisayarında yürütmenin kesme noktasında durdurulduğunu görmeniz gerekir.  
  
    > [!TIP]
    > Alternatif olarak, dosyaları ayrı bir adım olarak dağıtabilirsiniz. **Çözüm Gezgini,** **mymfc** düğümüne sağ tıklayın ve ardından **Dağıt**' ı seçin.  
  
    Uygulama tarafından kullanılması gereken kod olmayan dosyalarınız varsa, bunları Visual Studio projesine dahil etmeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun ( **Çözüm Gezgini**, **Ekle/yeni klasör**' e tıklayın.) Ardından dosyaları klasöre ekleyin ( **Çözüm Gezgini**, **Ekle/var olan öğe**' ye tıklayın ve ardından dosyalar ' ı seçin.). Her bir dosyanın **Özellikler** sayfasında, her **zaman kopyalamak**için **Çıkış Dizinine Kopyala** ' yı ayarlayın.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Visual C# veya Visual Basic projesi üzerinde uzaktan hata ayıklama  
 Hata ayıklayıcı, Visual C# veya Visual Basic masaüstü uygulamalarını uzak bir makineye dağıtabamaz, ancak yine de aşağıdaki gibi uzaktan hata ayıklaması yapabilirsiniz. Aşağıdaki yordamda, önceki çizimde gösterildiği gibi **Mjo-DL**adlı bir bilgisayarda bu sayfada hata ayıklamak istediğinizi varsayılmaktadır.
  
1. **MyWpf**ADLı bir WPF projesi oluşturun.  
  
2. Kodu kolayca erişilen kodda bir yere kesme noktası ayarlayın.  
  
    Örneğin, bir düğme işleyicisinde bir kesme noktası ayarlayabilirsiniz. Bunu yapmak için, MainWindow. xaml ' yi açın ve araç kutusundan bir düğme denetimi ekleyin, ardından düğmeye çift tıklayarak işleyiciyi açın.
  
3. Çözüm Gezgini, projeye sağ tıklayın ve **Özellikler**' i seçin.  
  
4. **Özellikler** sayfasında **Hata Ayıkla** sekmesini seçin.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. **Çalışma dizini** metin kutusunun boş olduğundan emin olun.  
  
6. **Uzak makine kullan**' ı seçin ve metin kutusuna **MJO-DL: 4020** yazın. (4020, uzaktan hata ayıklayıcı penceresinde gösterilen bağlantı noktası numarasıdır).  
  
7. **Yerel kod hata ayıklamasını etkinleştir** ' in seçili olmadığından emin olun.  
  
8. Projeyi derleyin.  
  
9. Uzak bilgisayarda, Visual Studio bilgisayarınızdaki **hata ayıklama** klasörüyle aynı yol olan bir klasör oluşturun: ** \<source path> \MyWPF\MyWPF\bin\Debug**.  
  
10. Visual Studio bilgisayarınızdan oluşturduğunuz yürütülebilir dosyayı uzak bilgisayardaki yeni oluşturulan klasöre kopyalayın.
  
    > [!CAUTION]
    > Kodda değişiklik yapmayın veya yeniden derleyin (veya bu adımı tekrarlamanız gerekir). Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir.

    Projeyi el ile kopyalayabilir, xcopy, Robocopy, PowerShell veya diğer seçenekleri kullanabilirsiniz.
  
11. Uzaktan hata ayıklayıcının hedef makinede çalıştığından emin olun. (Yoksa, **Başlat** menüsünde **Uzaktan hata ayıklayıcı** için arama yapın. ) Uzaktan hata ayıklayıcı penceresi şuna benzer.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. Visual Studio 'da hata ayıklamayı başlatın (**Hata Ayıkla/hata ayıklamayı Başlat**veya **F5**).  
  
13. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgileri ağınızın güvenlik yapılandırmasına bağlı olarak farklılık gösterir. Örneğin, bir etki alanı bilgisayarında etki alanı adınızı ve parolanızı girebilirsiniz. Etki alanı olmayan bir makinede makine adı ve doğru parolayla birlikte geçerli bir kullanıcı hesabı adı girebilirsiniz <strong>MJO-DL\name@something.com</strong> .

     Uzak bilgisayarda WPF uygulamasının ana penceresinin açık olduğunu görmeniz gerekir.
  
14. Gerekirse, kesme noktasına isabet eden işlem yapın. Kesme noktasının etkin olduğunu görmeniz gerekir. Değilse, uygulamanın sembolleri yüklenmez. Yeniden deneyin ve bu işe yaramazsa sembolleri yükleme ve [sembol dosyalarını ve Visual Studio 'nun sembol ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)hakkında bilgi alın.
  
15. Visual Studio makinesinde yürütmenin kesme noktasında durdurulduğunu görmeniz gerekir.
  
    Uygulama tarafından kullanılması gereken kod olmayan dosyalarınız varsa, bunları Visual Studio projesine dahil etmeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun ( **Çözüm Gezgini**, **Ekle/yeni klasör**' e tıklayın.) Ardından dosyaları klasöre ekleyin ( **Çözüm Gezgini**, **Ekle/var olan öğe**' ye tıklayın ve ardından dosyalar ' ı seçin.). Her bir dosyanın **Özellikler** sayfasında, her **zaman kopyalamak**için **Çıkış Dizinine Kopyala** ' yı ayarlayın.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgelerle hata ayıklamayı ayarlama  
 Visual Studio bilgisayarında oluşturduğunuz simgelerle kodunuzda hata ayıklaması yapabiliyor olmanız gerekir. Yerel sembolleri kullandığınızda uzaktan hata ayıklayıcının performansı çok daha iyidir.  Uzak sembolleri kullanmanız gerekiyorsa, uzak makinede sembolleri aramak için uzaktan hata ayıklama izleyicisine söylemeniz gerekir.  
  
 Visual Studio 2013 güncelleştirme 2 ' den başlayarak, yönetilen kod için uzak sembolleri kullanmak üzere aşağıdaki msvsmon komut satırı anahtarını kullanabilirsiniz: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Daha fazla bilgi için bkz. uzaktan hata ayıklama yardımı (uzaktan hata ayıklayıcı penceresinde **F1** 'e basın veya **Yardım/kullanım**' a tıklayın). [Visual Studio 2012 ve 2013 ' de daha fazla bilgi için .NET uzak sembol yükleme değişikliklerini](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/) bulabilirsiniz  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Windows Mağazası ve Azure uygulamalarında uzaktan hata ayıklama  
 Windows Mağazası uygulamalarıyla uzaktan hata ayıklama hakkında bilgi için bkz. [Visual Studio 'dan uzak bir cihazdaki Windows Mağazası uygulamalarını hata ayıklama ve test](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx)etme.  
  
 Azure 'da hata ayıklama hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
- [Visual Studio 'da bir bulut hizmetinde veya sanal makinede hata ayıklama](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Visual Studio 'da .NET arka ucunda hata ayıklama](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Azure Web sitelerinde uzaktan hata ayıklama konusuna giriş (bölüm[1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Bölüm 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Bölüm 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio 'da hata ayıklama](../debugger/debugging-in-visual-studio.md)   
 [Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)   
 [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
