---
title: VSPerfASPNETCmd ile Hızlı Web Sitesi Profilleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771698"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile hızlı web sitesi profiloluşturma

**VSPerfASPNETCmd** komut satırı aracı, web uygulamalarını [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kolayca profillemenizi sağlar. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracıyla karşılaştırıldığında seçenekler azalır, ortam değişkenlerinin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. **VSPerfASPNETCmd** kullanmak tek başına profil oluşturmada tercih edilen yöntemdir. Daha fazla bilgi [için bkz: Tek başına profil oluşturucuyu yükleyin.](../profiling/how-to-install-the-stand-alone-profiler.md)

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

 Eşzamanlı veri toplama veya profil oluşturmayı duraklatma ve devam ettirme gibi bazı senaryolarda **VSPerfCmd** kullanmak tercih edilen profil oluşturma yöntemidir.

> [!NOTE]
> Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturucu komut satırı araçlarını kullanmak için, komut istemi penceresinin PATH ortamı değişkenine araçlar yolunu eklemeniz veya komutun kendisine eklemeniz gerekir.

## <a name="profile-an-aspnet-application"></a>Bir ASP.NET uygulamasının profilini

Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulamasının profilini çıkarmak için, aşağıdaki bölümlerde açıklanan komutlardan birini yazın. Web sitesi başlatılır ve profil oluşturucu veri toplamaya başlar. Uygulamanızı yapın ve ardından tarayıcıyı kapatın. Profil oluşturmayı durdurmak için komut istemi penceresinde **Enter** tuşuna basın.

> [!NOTE]
> Varsayılan olarak, komut istemi bir **vsperfaspnetcmd** komutundan sonra dönmez. **/nowait** seçeneğini kullanarak komut istemini geri dönmeye zorlayabilirsiniz. Bkz. [/NoWait seçeneğini kullanın.](#use-the-nowait-option)

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak uygulama istatistiklerini toplamak
 Örnekleme **VSPerfASPNETCmd** aracının varsayılan profil oluşturma yöntemidir ve komut satırında belirtilmesi gerekmez. Aşağıdaki komut satırı belirtilen web uygulamasından uygulama istatistiklerini toplar:

 **vsperfaspnetcmd**  *web sitesiUrl*

 Yerel bir sunucu tarafından barındırılan *http://localhost/MySite/default.aspx* *web sitesiUrl* örneği olabilir. Harici bir sitenin *http://www.contoso.com*bir örneği. Daha fazla bilgi için Visual [Studio'da bir proje açmadan bir web sitesinin profilini çıkarmak için](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio)örnek URL'lere bakın.

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Enstrümantasyon yöntemini kullanarak ayrıntılı zamanlama verileri toplamak

Dinamik olarak derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] bir web uygulamasından ayrıntılı zamanlama verileri toplamak için aşağıdaki komut satırını kullanın:

**vsperfaspnetcmd /trace**  *websiteUrl*

Statik olarak derlenmiş profil yapmak istiyorsanız. web uygulamasında *dll* dosyaları, [VSInstr](../profiling/vsinstr.md) komut satırı aracını kullanarak dosyaları enstrüman gerekir. Vsperfaspnetcmd /trace komutu, enstrümantedilen dosyalardan gelen verileri içerir.

## <a name="to-collect-net-memory-data"></a>.NET bellek verilerini toplamak için

**/Bellek** seçeneği .NET belleğindeki nesnelerin tahsisi hakkında veri toplar ve bu nesnelerin ömrü hakkında veri toplayabilir. Ayırma veri toplama **/ Bellek** veri seçeneğinin varsayılan modudur ve komut satırında belirtilmesi gerekmez.

 **vsperfaspnetcmd /bellek** *sitesiUrl*

 Ayırma verilerine ek olarak nesne yaşam boyu verilerini toplamak için **Ömür Boyu** parametresini kullanın:

 **vsperfaspnetcmd /memory:ömür boyu** *websiteUrl*

 .NET bellek verileriyle ayrıntılı zamanlama bilgilerini eklemek için **/İzleme** seçeneğini de kullanabilirsiniz:

 **vsperfaspnetcmd /memory**[**:ömür boyu**] **/iz**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Katman etkileşim verileri toplamak için

> [!WARNING]
> Katman etkileşimi profil oluşturma (TIP) verileri Visual Studio'nun herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.
>
> Windows 8 veya Windows Server 2012'de TIP verileri toplamak için enstrümantasyon (**/trace**) seçeneğini kullanmanız gerekir.

Örnekleme verileriyle katman etkileşim verileri toplamak için:

**vsperfaspnetcmd /tip**`websiteUrl`

Enstrümantasyon verileriyle katman etkileşim verileri toplamak için:

**vsperfaspnetcmd /iz /ipucu** *websiteUrl*

.NET bellek verileriyle katman etkileşim verileri toplamak için:

**vsperfaspnetcmd /memory**[**:ömür boyu**] **/ipucu**_websiteUrl_

## <a name="use-the-nowait-option"></a>/NoWait seçeneğini kullanma

Varsayılan olarak, komut istemi bir **vsperfaspnetcmd** komutundan sonra dönmez. Komut istemini geri dönmeye zorlamak için aşağıdaki sözdizimi seçeneğini kullanabilirsiniz. Daha sonra komut istemi penceresinde diğer işlemleri gerçekleştirebilirsiniz. Profil oluşturmayı sona erdirmek için **/shutdown** seçeneğini ayrı bir **vsperfaspnetcmd** komutunda kullanın.

Profil oluşturmayı başlatmak için:

**vsperfaspnetcmd** [*/Seçenekler*] **/nowait**_websiteUrl_

Profil oluşturmayı sona erdirmek için:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Ek seçenekler

Bu bölümde daha önce listelenen komutlara **vsperfaspnetcmd /shutdown** komutu dışında aşağıdaki seçeneklerden herhangi birini ekleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/Çıktı:**`VspFile`|Varsayılan olarak, profil oluşturma verileri (.* vsp*) dosyası **performancereport.vsp**dosya adı ile geçerli dizinde oluşturulur. Farklı bir konum, dosya adı veya her ikisini belirtmek için /çıktı seçeneğini kullanın.|
|**/PackSymbols:Kapalı**|Varsayılan olarak, VsPerfASPNETCmd sembolleri (işlev ve parametre adları vb.) .) katıştırıyor. *vsp* dosyası. Sembollerin gömilmesi profil oluşturma veri dosyasını çok büyük yapabilir. Eğer erişim olacak. verileri analiz ettiğinizde sembolleri içeren *pdb* dosyaları, sembollerin katıştırma devre dışı bırakseçeneğini kullanır.|
