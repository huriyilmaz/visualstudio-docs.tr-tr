---
title: Uzak IIS 7,5 bilgisayarında uzaktan hata ayıklama ASP.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c43f392cddfd5ea36180d9b2675db82469f86ce0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807145"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir ASP.NET Web uygulamasını IIS ile Windows Server bilgisayarına dağıtabilir ve uzaktan hata ayıklama için ayarlayabilirsiniz. Bu kılavuzda, Visual Studio 2015 MVC 4.5.2 uygulamasını ayarlama ve yapılandırma, IIS 'ye dağıtma ve Visual Studio 'dan uzaktan hata ayıklayıcı iliştirme açıklanmaktadır.

Bu yordamlar, bu sunucu yapılandırmalarında test edilmiştir:
* Windows Server 2012 R2 ve IIS 10
* Windows Server 2008 R2 ve IIS 7,5

Bu makaledeki bilgilerin çoğu Ayrıca, ASP.NET Core uygulamalarının dağıtımı farklı olduğundan ve ek adımlar gerektirdiğinden ASP.NET Core bir uygulamada uzaktan hata ayıklama için de geçerlidir. IIS 'ye bir ASP.NET Core uygulaması dağıtmak için, [Bu makalenin](https://docs.asp.net/en/latest/publishing/iis.html)tüm bölümlerini doldurmanız gerekir.

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Önkoşullar: uzak hata ayıklayıcıyı Windows Server bilgisayarına yükler

Uzaktan hata ayıklayıcının Windows Server bilgisayarına nasıl indirileceği hakkında yönergeler için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

ASP.NET uygulamalarında uzaktan hata ayıklama yapmak için, uzaktan hata ayıklayıcı uygulamasını Yönetici olarak çalıştırabilir veya uzaktan hata ayıklayıcıyı bir hizmet olarak başlatabilirsiniz. Uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmaya ilişkin ayrıntılar, [Uzaktan hata ayıklama](../debugger/remote-debugging.md)bölümünde bulunabilir.

Yüklendikten sonra, uzaktan hata ayıklayıcının hedef makinede çalıştığından emin olun. (Yoksa, **Başlat** menüsünde **Uzaktan hata ayıklayıcı** için arama yapın. ) Uzaktan hata ayıklayıcı penceresi şuna benzer. (4020 varsayılan bağlantı noktası numarasıdır)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Uygulamayı Visual Studio bilgisayarda oluşturma  
  
1. Yeni bir MVC ASP.NET uygulaması oluşturun. (**Dosya/yeni/proje**, sonra **Visual C#/web/ASP.NET Web uygulaması** ' nı seçin. **ASP.NET 4.5.2** Templates bölümünde **MVC**' yi seçin. **Bulutta konağın** Azure bölümünde seçili olmadığından emin olun. Projeyi **Mymvc**olarak adlandırın.)
1. HomeController.cs dosyasını açın ve yönteminde bir kesme noktası ayarlayın `About()` .
1. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Yayımla**' yı seçin.
1. **Bir yayımlama hedefi seç**için **özel** ' i seçin ve profili **mymvc**olarak adlandırın. **İleri**’ye tıklayın.
1. **Bağlantı** sekmesinde, **Yayımlama yöntemi** alanını **dosya sistemi** ve **hedef konum** alanı olarak bir yerel dizine ayarlayın. **İleri**’ye tıklayın.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Yapılandırmayı **hata ayıklama**olarak ayarlayın. **Yayımla**’ya tıklayın.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Uygulamanın yerel dizine yayımlanması gerekir.

## <a name="deploy-the-aspnet-application-on-the-windows-server-remote-computer"></a><a name="BKMK_deploy_asp_net"></a> ASP.NET uygulamasını Windows Server uzak bilgisayarda dağıtma

 Bu bölümde, Windows Server bilgisayarında zaten IIS etkinleştirilmiş olduğu varsayılır. Windows Server 2012 R2 'de IIS 'yi etkinleştirmek için [IIS yapılandırması](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) bölümüne bakın. (Bir ASP.NET Core uygulaması dağıtmaya çalışmadıkça, bu makalenin diğer bölümlerini atlayabilirsiniz. ASP.NET Core için, burada açıklanan adımlar yerine, uygulamayı dağıtmak için makalesindeki adımları izleyin.)
1. ASP.NET 'yi yüklemek için Web Platformu bileşenlerini kullanın ASP.NET 4,5 (Windows Server 2012 R2 'deki sunucu düğümünden, **Yeni Web platformu bileşenleri al** ' ı seçin ve ardından ASP.NET için arama yapın)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Windows Server 2008 R2 'de, bu komutu kullanmak yerine ASP.NET 4 ' ü   **\v4.0.30319\aspnet_regiis.exe: C:\Windows\Microsoft.NET\Framework (64)-IR**
1. ASP.NET proje dizinini, Visual Studio bilgisayarından Windows Server bilgisayarında yerel bir dizine ( **C:\publish**çağıracağız) kopyalayın. Projeyi el ile kopyalayabilir, xcopy, Web Dağıtımı, Robocopy, PowerShell veya diğer seçenekleri kullanabilirsiniz.

    > [!CAUTION]
    > Kodda değişiklik yapmanız veya yeniden oluşturmanız gerekiyorsa, bu adımı yeniden yayımlamanız ve yinelemeniz gerekir. Uzak makineye kopyaladığınız yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir.
1. web.config dosyasının .NET Framework doğru sürümünü listelediğinden emin olun.  Örneğin, Windows Server 2008 R2 'de varsayılan olarak yüklenen .NET Framework sürümü 4.0.30319 'dir, ancak bir ASP.NET 4.5.2 sürümü oluşturduk. Windows Server bilgisayarında bir ASP.NET 4,0 uygulaması çalışıyorsa, sürümü değiştirmeniz gerekir:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```

1. **Internet Information Services (IIS) Yöneticisi** ' ni açın ve **siteler**' e gidin.
1. **Varsayılan Web sitesi** düğümüne sağ tıklayın ve **Uygulama Ekle**' yi seçin.
1. **Diğer ad** alanını **Mymvc** ve uygulama havuzu alanı olarak **ASP.net v 4.0** olarak ayarlayın (ASP.NET 4,5, uygulama havuzu için bir seçenek değildir). **Fiziksel yolu** **C:\publish** olarak ayarlayın (ASP.NET proje dizinini kopyaladığınız yerdir).

    >[!NOTE] 
    > ASP.NET Core uygulamalar için uygulama havuzu alanını **yönetilen kod yok**olarak ayarlayın.
1. **Varsayılan Web sitesi** ' ne sağ tıklayıp, ardından da **Araştır**' ı seçerek dağıtımı test edin.
    Uygulamayı başarıyla dağıttıysanız, Web sayfasını görürsünüz.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Visual Studio bilgisayarından ASP.NET uygulamasına iliştirme

1. Visual Studio bilgisayarında, **Mymvc** çözümünü açın.
1. Visual Studio 'da **Hata Ayıkla/Işleme Ekle** (**Ctrl + Alt + P**) seçeneğine tıklayın.
1. Niteleyici alanını şu şekilde ayarlayın ** \<remote computer name> : 4020**.
1. **Yenile**'ye tıklayın.
    **Kullanılabilir süreçler** penceresinde bazı işlemlerin göründüğünü görmeniz gerekir.

    Herhangi bir işlem görmüyorsanız, uzak bilgisayar adı yerine IP adresini kullanmayı deneyin (bağlantı noktası gereklidir). `ipconfig`IPv4 adresini almak için bir komut satırında kullanın.
1. **Tüm kullanıcıların süreçlerini göster**' i işaretleyin.
1. **w3wp.exe** bulun ve **Ekle**' ye tıklayın.

     İşlem adını hızlı bir şekilde bulmak için işlemin ilk harfini yazın.
     
    >[!NOTE]
    > ASP.NET Core bir uygulama için w3wp.exe yerine dnx.exe sürecini seçin. (Bu işlem adı yaklaşan bir sürümde değişebilir.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda **http:// \<remote computer name> **adresine gidin.
    
    ASP.NET Web sayfasını görmeniz gerekir.
1. ASP.NET Web sayfasında, **hakkında** sayfasının bağlantısına tıklayın.

    Kesme noktası Visual Studio 'da isabet almalıdır.
