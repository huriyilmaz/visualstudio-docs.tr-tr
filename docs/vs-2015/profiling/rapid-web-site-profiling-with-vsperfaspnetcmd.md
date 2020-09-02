---
title: VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce5534f5723a3f0e570779939f207018cac71cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835294"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile Hızlı Web Sitesi Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfASPNETCmd** komut satırı aracı, Web uygulamalarını kolayca profillemenize olanak sağlar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla, seçenekler azalır, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekli değildir. **VSPerfASPNETCmd** kullanmak, tek başına profil Oluşturucu ile profil oluşturma için tercih edilen yöntemdir. Daha fazla bilgi için bkz. [nasıl yapılır: tek başına profil oluşturucuyu yüklemek](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Eşzamanlılık verileri toplama veya profil oluşturmayı duraklatma ve sürdürme gibi bazı senaryolarda, **VSPerfCmd** kullanılması tercih edilen profil oluşturma yöntemidir.  
  
> [!NOTE]
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, 32 bit \Team Tools\Performance Tools dizininde bulunan VSPerfASPNETCmd aracını kullanın. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>ASP.NET uygulaması profili oluşturma  
 Bir Web uygulaması profili eklemek için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve profil oluşturucu veri toplamaya başlar. Uygulamanızı alıştırma yapın ve ardından tarayıcıyı kapatın. Profil oluşturmayı durdurmak için komut istemi penceresindeki ENTER tuşuna basın.  
  
> [!NOTE]
> Varsayılan olarak, komut istemi bir **VSPerfASPNETCmd** komutundan sonra döndürmez. Komut istemi 'ni döndürmesini zorlamak için **/nowait** seçeneğini kullanabilirsiniz. Bkz. [/NoWait seçeneğini kullanma](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistikleri toplamak için  
 Örnekleme, **VSPerfASPNETCmd** aracının varsayılan profil oluşturma yöntemidir ve komut satırında belirtilmesi gerekmez. Aşağıdaki komut satırı, belirtilen Web uygulamasından uygulama istatistiklerini toplar:  
  
 **VSPerfASPNETCmd**  *WebSiteUrl 'si*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak ayrıntılı zamanlama verileri toplama  
 Dinamik olarak derlenen bir Web uygulamasından ayrıntılı zamanlama verileri toplamak için aşağıdaki komut satırını kullanın [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
 **VSPerfASPNETCmd/Trace**  *WebSiteUrl 'si*  
  
 Web uygulamanızda statik olarak derlenen. dll dosyaları profilini eklemek istiyorsanız, [vsinstr](../profiling/vsinstr.md) komut satırı aracını kullanarak dosyaları seçmeniz gerekir. VSPerfASPNETCmd/Trace komutu, Araçlı dosyalardaki verileri içerir.  
  
## <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için  
 **/Memory** seçeneği, .net bellekte nesnelerin ayrılması hakkındaki verileri toplar ve bu nesnelerin yaşam süresi hakkında veri toplayabilir. Ayırma verisi toplama, **/Memory** veri seçeneğinin varsayılan modudur ve komut satırında belirtilmesi gerekmez.  
  
 **VSPerfASPNETCmd/Memory** *WebSiteUrl 'si*  
  
 Ayırma verilerine ek olarak nesne yaşam süresi verilerini toplamak için **ömür** parametresini kullanın:  
  
 **VSPerfASPNETCmd/Memory: Lifetime** *WebSiteUrl 'si*  
  
 .NET bellek verileriyle ayrıntılı zamanlama bilgilerini eklemek için **/Trace** seçeneğini de kullanabilirsiniz:  
  
 **VSPerfASPNETCmd/Memory**[**: Lifetime**] **/Trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verilerini toplamak için  
  
> [!WARNING]
> Katman etkileşimi profil oluşturma (tıp) verileri,, veya kullanılarak toplanabilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Ancak, katman etkileşimi profil oluşturma verileri yalnızca ve ' de [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] görüntülenebilir [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
>   
> Windows 8 veya Windows Server 2012 ' de tıp verisi toplamak için, izleme (**/Trace**) seçeneğini kullanmanız gerekir.  
  
 Örnekleme verileriyle katman etkileşim verileri toplamak için:  
  
 **VSPerfASPNETCmd/tip**`websiteUrl`  
  
 Katman etkileşimi verilerini izleme verileriyle toplamak için:  
  
 **VSPerfASPNETCmd/Trace/tıp** *WebSiteUrl 'si*  
  
 .NET bellek verileriyle katman etkileşim verileri toplamak için:  
  
 **VSPerfASPNETCmd/Memory**[**: Lifetime**] **/tıp**_WebSiteUrl 'si_  
  
## <a name="using-the-nowait-option"></a><a name="UsingNoWait"></a> /NoWait seçeneğini kullanma  
 Varsayılan olarak, komut istemi bir **VSPerfASPNETCmd** komutundan sonra döndürmez. Komut istemi 'ni döndürmesini zorlamak için aşağıdaki söz dizimi seçeneğini kullanabilirsiniz. Daha sonra komut istemi penceresinde başka işlemler gerçekleştirebilirsiniz. Profil oluşturmayı sonlandırmak için, **/Shutdown** seçeneğini ayrı bir **VSPerfASPNETCmd** komutunda kullanın.  
  
 Profil oluşturmaya başlamak için:  
  
 **VSPerfASPNETCmd** [*/Options*] **/nowait**_WebSiteUrl 'si_  
  
 Profil oluşturmayı sonlandırmak için:  
  
 **VSPerfASPNETCmd/Shutdown** *WebSiteUrl 'si*  
  
## <a name="additional-options"></a>Ek Seçenekler  
 Aşağıdaki seçeneklerden herhangi birini, **VSPerfASPNETCmd/Shutdown** komutu hariç, bu bölümün önceki kısımlarında listelenen komutlara ekleyebilirsiniz.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Output:**`VspFile`|Varsayılan olarak, profil oluşturma verileri (. vsp) dosyası, geçerli dizinde performanslı dosya adı **. vsp**olacak şekilde oluşturulur. Farklı bir konum, dosya adı veya her ikisini de belirtmek için/output seçeneğini kullanın.|  
|**/PackSymbols: kapalı**|Varsayılan olarak, VsPerfASPNETCmd,. vsp dosyasındaki sembolleri (işlev ve parametre adları vb.) katıştırır. Sembolleri katıştırmak, profil oluşturma veri dosyasını çok büyük hale getirir. Verileri çözümlediğinizde sembolleri içeren. pdb dosyalarına erişebilecekse, sembolleri eklemeyi devre dışı bırakmak için/packsymbols: off seçeneğini kullanın.|
