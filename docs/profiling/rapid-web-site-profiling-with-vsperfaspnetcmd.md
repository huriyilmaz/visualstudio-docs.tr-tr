---
title: VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fff2486c4197cbbe28c3b5deb0099e264805e12b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771698"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma

**VSPerfASPNETCmd** komut satırı aracı, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarını kolayca profilinize olanak sağlar. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla, seçenekler azalır, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekli değildir. **VSPerfASPNETCmd** kullanmak, tek başına profil Oluşturucu ile profil oluşturma için tercih edilen yöntemdir. Daha fazla bilgi için bkz. [nasıl yapılır: tek başına profil oluşturucuyu yüklemek](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Eşzamanlılık verileri toplama veya profil oluşturmayı duraklatma ve sürdürme gibi bazı senaryolarda, **VSPerfCmd** kullanılması tercih edilen profil oluşturma yöntemidir.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

## <a name="profile-an-aspnet-application"></a>ASP.NET uygulaması profili oluşturma

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması profilini almak için aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve profil oluşturucu veri toplamaya başlar. Uygulamanızı alıştırma yapın ve ardından tarayıcıyı kapatın. Profil oluşturmayı durdurmak için komut istemi penceresindeki **ENTER** tuşuna basın.

> [!NOTE]
> Varsayılan olarak, komut istemi bir **VSPerfASPNETCmd** komutundan sonra döndürmez. Komut istemi 'ni döndürmesini zorlamak için **/nowait** seçeneğini kullanabilirsiniz. Bkz. [/NoWait seçeneğini kullanma](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistikleri toplamak için
 Örnekleme, **VSPerfASPNETCmd** aracının varsayılan profil oluşturma yöntemidir ve komut satırında belirtilmesi gerekmez. Aşağıdaki komut satırı, belirtilen Web uygulamasından uygulama istatistiklerini toplar:

 **VSPerfASPNETCmd**  *WebSiteUrl 'si*

 Yerel sunucu tarafından barındırılan bir *WebSiteUrl 'si* örneği *http://localhost/MySite/default.aspx* olabilir. Dış siteye bir örnek *http://www.contoso.com* . Daha fazla bilgi için, [Visual Studio 'da bir proje açmadan bir Web sitesi profili oluşturma](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio)' daki örnek URL 'ler bölümüne bakın.

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak ayrıntılı zamanlama verileri toplama

Dinamik olarak derlenen bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasından ayrıntılı zamanlama verileri toplamak için aşağıdaki komut satırını kullanın:

**VSPerfASPNETCmd/Trace**  *WebSiteUrl 'si*

Statik olarak derlenen profil eklemek istiyorsanız. *DLL* dosyaları Web uygulamanızda, [VSInstr](../profiling/vsinstr.md) komut satırı aracını kullanarak dosyaları seçmeniz gerekir. VSPerfASPNETCmd/Trace komutu, Araçlı dosyalardaki verileri içerir.

## <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için

**/Memory** seçeneği, .net bellekte nesnelerin ayrılması hakkındaki verileri toplar ve bu nesnelerin yaşam süresi hakkında veri toplayabilir. Ayırma verisi toplama, **/Memory** veri seçeneğinin varsayılan modudur ve komut satırında belirtilmesi gerekmez.

 **VSPerfASPNETCmd/Memory** *WebSiteUrl 'si*

 Ayırma verilerine ek olarak nesne yaşam süresi verilerini toplamak için **ömür** parametresini kullanın:

 **VSPerfASPNETCmd/Memory: Lifetime** *WebSiteUrl 'si*

 .NET bellek verileriyle ayrıntılı zamanlama bilgilerini eklemek için **/Trace** seçeneğini de kullanabilirsiniz:

 **VSPerfASPNETCmd/Memory**[ **: Lifetime**] **/Trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verilerini toplamak için

> [!WARNING]
> Katman etkileşimi profil oluşturma (tıp) verileri, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.
>
> Windows 8 veya Windows Server 2012 ' de tıp verisi toplamak için, izleme ( **/Trace**) seçeneğini kullanmanız gerekir.

Örnekleme verileriyle katman etkileşim verileri toplamak için:

**VSPerfASPNETCmd/tip** `websiteUrl`

Katman etkileşimi verilerini izleme verileriyle toplamak için:

**VSPerfASPNETCmd/Trace/tıp** *WebSiteUrl 'si*

.NET bellek verileriyle katman etkileşim verileri toplamak için:

**VSPerfASPNETCmd/Memory**[ **: Lifetime**] **/tıp**_WebSiteUrl 'si_

## <a name="use-the-nowait-option"></a>/NoWait seçeneğini kullanın

Varsayılan olarak, komut istemi bir **VSPerfASPNETCmd** komutundan sonra döndürmez. Komut istemi 'ni döndürmesini zorlamak için aşağıdaki söz dizimi seçeneğini kullanabilirsiniz. Daha sonra komut istemi penceresinde başka işlemler gerçekleştirebilirsiniz. Profil oluşturmayı sonlandırmak için, **/Shutdown** seçeneğini ayrı bir **VSPerfASPNETCmd** komutunda kullanın.

Profil oluşturmaya başlamak için:

**VSPerfASPNETCmd** [ */Options*] **/nowait**_WebSiteUrl 'si_

Profil oluşturmayı sonlandırmak için:

**VSPerfASPNETCmd/Shutdown** *WebSiteUrl 'si*

## <a name="additional-options"></a>Ek seçenekler

Aşağıdaki seçeneklerden herhangi birini, **VSPerfASPNETCmd/Shutdown** komutu hariç, bu bölümün önceki kısımlarında listelenen komutlara ekleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/Output:** `VspFile`|Varsayılan olarak, profil oluşturma verileri (. *VSP*) dosyası, geçerli dizinde, bu dosya adı **PerformanceReport. vsp**olarak oluşturulur. Farklı bir konum, dosya adı veya her ikisini de belirtmek için/output seçeneğini kullanın.|
|**/PackSymbols: kapalı**|Varsayılan olarak, VsPerfASPNETCmd, içindeki sembolleri (işlev ve parametre adları vb.) katıştırır. *VSP* dosyası. Sembolleri katıştırmak, profil oluşturma veri dosyasını çok büyük hale getirir. Öğesine erişiminiz varsa. sembolleri içeren *pdb* dosyaları verileri çözümlediğinizde, sembollerin gömülmesini devre dışı bırakmak için/packsymbols: off seçeneğini kullanın.|
