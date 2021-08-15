---
title: VSPerfASPNETCmd ile Hızlı Web Sitesi Profili | Microsoft Docs
description: VSPerfASPNETCmd komut satırı aracının web uygulamalarının profilini kolayca ASP.NET öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e9b86f1d5733e92488937a7a0bb608343d9091e1190baee4f3a1f3d18c63dbd1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315856"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma

**VSPerfASPNETCmd** komut satırı aracı, web uygulamalarının profilini kolayca [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oluşturmanizi sağlar. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla seçenekler azaltıldı, ortam değişkeni ayarlanmaz ve bilgisayarı yeniden başlatma gerekli değildir. Tek **başına profil oluşturma için tercih edilen yöntem VSPerfASPNETCmd'nin** kullanımıdır. Daha fazla bilgi için, [bkz. How to: Install the stand-alone profiler](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

 Eşzamanlılık verileri toplama, profil oluşturma ve duraklatma gibi bazı senaryolarda, tercih edilen profil oluşturma yöntemi **VSPerfCmd'nin** kullanımıdır.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="profile-an-aspnet-application"></a>Bir ASP.NET profili oluşturma

Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasının profilini oluşturmak için aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve profil oluşturma verileri toplamaya başlar. Uygulama alıştırması yapın ve tarayıcıyı kapatın. Profil oluşturmayı durdurmak için komut istemi **penceresinde Enter** tuşuna basın.

> [!NOTE]
> Varsayılan olarak, komut istemi **vsperfaspnetcmd komutuyla birlikte dönmez.** Komut istemini **geri dönmeye zorlamak için /nowait** seçeneğini kullanabilirsiniz. Bkz. [/NoWait seçeneğini kullanma.](#use-the-nowait-option)

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistikleri toplamak için
 Örnekleme, **VSPerfASPNETCmd** aracının varsayılan profil oluşturma yöntemidir ve komut satırına belirtilmelidir. Aşağıdaki komut satırı, belirtilen web uygulamasından uygulama istatistiklerini toplar:

 **vsperfaspnetcmd**  *websiteUrl*

 Sunucu tarafından barındırılan yerel bir web sitesi *ÖrneğiUrl* *http://localhost/MySite/default.aspx* olabilir. Dış sitenin bir *http://www.contoso.com* örneğidir. Daha fazla bilgi için, Visual Studio içinde proje açmadan bir web sitesi profili [oluşturmak için içinde örnek URL'ler Visual Studio.](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio)

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Ölçüm ölçüm yöntemini kullanarak ayrıntılı zamanlama verileri toplamak için

Dinamik olarak derlenmiş bir web uygulamasından ayrıntılı zamanlama verileri toplamak için aşağıdaki [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] komut satırı kullanın:

**vsperfaspnetcmd /trace**  *websiteUrl*

Statik olarak derlenmiş profilini oluşturmak için . *web* uygulamanıza dll dosyaları, [VSInstr](../profiling/vsinstr.md) komut satırı aracını kullanarak dosyaları izletebilirsiniz. vsperfaspnetcmd /trace komutu, izlemeli dosyalardan verileri içerir.

## <a name="to-collect-net-memory-data"></a>.NET bellek verilerini toplamak için

**/Memory seçeneği** . NET belleğinde nesnelerin ayırması hakkında veri toplar ve bu nesnelerin yaşam süresi hakkında veri toplayabilirsiniz. Ayırma veri koleksiyonu, /Memory data **seçeneğinin** varsayılan modudur ve komut satırına belirtilmelidir.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Ayırma **verilerine** ek olarak nesne yaşam süresi verilerini toplamak için Yaşam Süresi parametresini kullanın:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 .NET bellek verileriyle ayrıntılı zamanlama bilgileri eklemek için **/Trace** seçeneğini de kullanabilirsiniz:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verilerini toplamak için

> [!WARNING]
> Katman etkileşim profili oluşturma (TIP) verileri, uygulamanın herhangi bir sürümü kullanılarak Visual Studio. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise.
>
> Veri kaynağında veya Windows 8 Windows Server 2012 için izleme ( /trace )**seçeneğini kullansanız** iyi olur.

Örnekleme verileriyle katman etkileşim verilerini toplamak için:

**vsperfaspnetcmd /tip**`websiteUrl`

Ölçüm ölçüm verileriyle katman etkileşim verilerini toplamak için:

**vsperfaspnetcmd /trace /tip** *websitesiUrl*

.NET bellek verileriyle katman etkileşim verileri toplamak için:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websitesiUrl_

## <a name="use-the-nowait-option"></a>/NoWait seçeneğini kullanın

Varsayılan olarak, komut istemi **vsperfaspnetcmd komutuyla birlikte dönmez.** Komut istemini geri dönmeye zorlamak için aşağıdaki söz dizimi seçeneğini kullanabilirsiniz. Daha sonra komut istemi penceresinde diğer işlemleri gerçekleştirebilirsiniz. Profil oluşturmayı sona erdirip **/shutdown** seçeneğini ayrı bir **vsperfaspnetcmd komutunda** kullanın.

Profil oluşturmayı başlamak için:

**vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_

Profil oluşturmayı sona erdirin:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Ek seçenekler

**Vsperfaspnetcmd /shutdown** komutu dışında, bu bölümün önceki kısımlarında listelenen komutlara aşağıdaki seçeneklerden herhangi birini eklersiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/Output:**`VspFile`|Varsayılan olarak, profil oluşturma verileri (.*vsp*) dosyası geçerli dizinde **PerformanceReport.vsp** dosya adıyla oluşturulur. Farklı bir konum, dosya adı veya her ikisini birden belirtmek için /output seçeneğini kullanın.|
|**/PackSymbols:Off**|Varsayılan olarak VsPerfASPNETCmd içinde sembolleri (işlev ve parametre adları gibi) katıştırıyor. *vsp* dosyası. Sembolleri eklemek, profil oluşturma veri dosyasını çok büyük hale içerebilir. erişimine sahip olacaksanız. Verileri analiz ederken sembolleri içeren *pdb* dosyaları, simgelerin eklenmesini devre dışı bırakmak için /packsymbols:off seçeneğini kullanın.|
