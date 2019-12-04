---
title: VSPerfCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 53378c3d210ef9666df251d68a3eec570f8caa2f
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778004"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd. exe* Aracı, performans verileri toplamayı başlatmak ve durdurmak için kullanılır. Aşağıdaki sözdizimini kullanır:

```cmd
VSPerfCmd [/U] [/options]
```

 Aşağıdaki tablolarda *VSPerfCmd. exe* araç seçenekleri açıklanır.

|Seçenek|Açıklama|
|------------|-----------------|
|**Larınız**|Yeniden yönlendirilen konsol çıkışı Unicode olarak yazılmıştır. Belirtilen ilk seçenek olmalıdır.|
|[Başlangıç](../profiling/start.md) **:** `mode`|Profil oluşturma hizmetini belirtilen modda başlatır.|
|[Çıkış](../profiling/output.md) **:** `filename`|Çıkış dosyası adını belirtir. Yalnızca **Start**ile kullanın.|
|[Çapraz oturum&#124;CS](../profiling/crosssession.md)|Windows oturumlarında profil oluşturmayı etkinleştirilir. Yalnızca **Start**, **Attach** **veya Launch**ile kullanın.|
|[Kullanıcı](../profiling/user-vsperfcmd.md) **:** [`domain\`]`username`|Profil Oluşturucu hizmetine belirtilen hesabın erişimini sağlar. Yalnızca **Start**ile kullanın.|
|[WaitStart](../profiling/waitstart.md)[ **:** `n`]|Veri toplama günlükçüsü 'nin başlatılmasını bekler. `n` belirtilirse, **VSPerfCmd** en fazla `n` saniye bekler. `n` belirtilmemişse **VSPerfCmd** süresiz olarak bekleyecektir. Bu, **VSPerfCmd** 'nin toplu işlemin bir parçası olarak kullanılmasını kolaylaştırır.|
|[Sayaç](../profiling/counter.md) **:** `cfg`|Örnek profil oluşturma yöntemi kullanıldığında, bir CPU sayacı ve örnekleme aralığı olarak kullanılacak olay sayısını belirtir. Yalnızca bir sayaç değeri örnekleyebilirsiniz.<br /><br /> İzleme profili oluşturma yöntemi kullanıldığında, her bir izleme noktasında toplanacak bir CPU sayacı belirtir. Yalnızca **Start:** `Trace`, **Attach**veya **Launch**ile kullanın.|
|[QueryCounters](../profiling/querycounters.md)|Geçerli makine için geçerli CPU sayaçlarının listesini görüntüler.|
|[WinCounter](../profiling/wincounter.md) **:** *yol*|Profil işaretleme verileriyle birlikte içerilecek bir Windows performans sayacı olayı belirtir. Yalnızca **Start**ile kullanın.|
|[Otomatik işaret](../profiling/automark.md) **:** *n*|Windows performans sayacı veri toplama olayları arasındaki zaman aralığını (milisaniye olarak) belirtir. **WinCounter**ile kullanın.|
|[Olaylar](../profiling/events-vsperfcmd.md) **:** `option`|Windows için belirtilen olay Izleme (ETW) olayları koleksiyonunu denetler. ETW verileri bir öğesine toplanır. profil oluşturma verileri olmayan *ITIL* dosyası (. *VSP*) dosyası.|
|[Status](../profiling/status.md)|Profil oluşturucunun durumunu, şu anda profili oluşturulan süreçler hakkındaki bilgileri ve profil oluşturucuyu denetleme yetkisine sahip hesapları görüntüler.|
|[Kapanıyor](../profiling/shutdown.md)[ **:** `n`]|Profil oluşturma veri dosyasını kapatır ve profil oluşturucuyu kapatır.|
|[GlobalOn](../profiling/globalon-and-globaloff.md)|**Vsperfcmdglobaloff**çağrısından sonra veri toplamayı sürdürür.|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Tüm veri toplamayı durduruyor, ancak profil oluşturma oturumunu sonlandırmaz.|
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Profil oluşturma, **Vsperfcmdprocessoff**çağrısı tarafından duraklatıldıktan sonra belirtilen işlem için veri toplamayı sürdürür.|
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Belirtilen işlem için veri toplamayı durduruyor.|
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Profil oluşturma, **VSPerfCmdThreadOff**çağrısıyla duraklatıldıktan sonra belirtilen işlem için profil oluşturmayı sürdürür. Yalnızca izleme yöntemiyle profil oluşturma sırasında **ThreadOn üzerinde** kullanın.|
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *TID*|Belirtilen iş parçacığı için profil oluşturmayı duraklatır. **ThreadOff** ' i yalnızca izleme yöntemiyle profil oluşturma sırasında kullanın.|
|[Mark](../profiling/mark.md) **:** _marknum_[ **,** _MarkText_ **]**|Profil oluşturma veri dosyasına isteğe bağlı metin ile bir işaret ekler.|

## <a name="sample-method-options"></a>Örnek Yöntem seçenekleri
 Aşağıdaki seçenekler yalnızca örnekleme profili oluşturma yöntemi kullanılırken kullanılabilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[Başlatma](../profiling/launch.md) **:** *yürütülebilir*|Belirtilen uygulamayı başlatır ve profil oluşturmaya başlar.|
|[Args](../profiling/args.md) **:** *bağımsız değişkenler*|Başlatılan uygulamaya geçirilecek komut satırı bağımsız değişkenlerini belirtir.|
|[Console](../profiling/console.md)|Yeni komut istemi penceresinde belirtilen komutu başlatır.|
|[İliştirme](../profiling/attach.md) **:** *pid*[ **,** _pid_]|Belirtilen işlemlerin profilini oluşturmaya başlıyor. İşlemler işlem KIMLIĞI veya işlem adı ile tanımlanabilir.|
|[Ayır](../profiling/detach.md)[ **:** _pid_[,_pid_]]|Belirtilen işlemlerin profilini oluşturmayı durduruyor. İşlemler işlem KIMLIĞI veya işlem adı ile tanımlanabilir. Hiçbir işlem belirtilmemişse, tüm işlemler için profil oluşturma durdurulur.|
|[GC](../profiling/gc-vsperfcmd.md)[ **:** {**ayırma**`&#124;`**ömrü**}]|.NET bellek ayırma ve nesne yaşam süresi verilerini toplar. Yalnızca **VSPerfCmdLaunch** seçeneğiyle kullanın.|

### <a name="sample-interval-options"></a>Örnek Aralık seçenekleri
 Aşağıdaki seçenekler, örnekleme aralıklarının türünü ve süresini belirtir. Varsayılan değer **Zamanlayıcı**' dır. Ayrıca, **sayaç** seçeneğini kullanarak Aralık olarak bir CPU sayacı belirtebilirsiniz. Bu seçenekler yalnızca **başlatma** ile veya profil oluşturma oturumunun ilk **iliştirme** ile belirtilebilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[PF](../profiling/pf.md)[ **:** _n_]|Her n. sayfa hatasında örnekler (varsayılan = 10).|
|[Sys](../profiling/sys-vsperfcmd.md)[ **:** _n_]|Her n. sistem çağrısında örnekler (varsayılan = 10).|
|[Süreölçer](../profiling/timer.md)[ **:** _n_]|Her n. işlemci döngüsünün örnekleri (varsayılan = 10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Hizmet bileşeni ve çekirdek modu cihaz seçenekleri
 Aşağıdaki yönetici seçenekleri, profil oluşturma hizmeti bileşenlerini veya çekirdek modu cihaz sürücülerini destekler. Yönetici seçenekleri profil oluşturma izinlerini ayarlar ve profili oluşturulmuş hizmeti ya da cihaz sürücüsünü denetler.

 Yönetici seçeneklerinin, yönetici kimlik bilgileriyle çalışan bir komut isteminde yürütülmesi gerekir.

|Seçenek|Açıklama|
|------------|-----------------|
|**Yönetici: güvenlik**, \<**izin&#124;** verme >, *sağ*[ *sağ*] \<*Kullanıcı*&#124;*grubu*>|Profil oluşturma hizmetleri için belirtilen kullanıcı veya grup erişimine izin verir veya reddeder.<br /><br /> `Right` şu olabilir:<br /><br /> CrossSession-oturum açmaya yönelik profili oluşturmak için kullanıcıya hizmete erişim sağlar.<br /><br /> Sampleprofil oluşturma-örnekleme profil oluşturmayı etkinleştirmek için kullanıcıya sürücüye erişim sağlar. İzleme profili oluşturma sırasında çekirdek geçiş bilgilerine erişmek için de kullanılır.<br /><br /> FullAccess-kullanıcıya hem CrossSession hem de Sampleprofil oluşturma erişimi verir.|
|**Yönetici: güvenlik, liste**|Profil oluşturma hizmetlerinin geçerli durumunu listeler ve Kullanıcı izinlerini listeler.|
|**Yönetici:** \<*hizmet*&#124;*sürücüsü* **>\<** &#124;&#124;yüklemeyi&#124;**kaldırmayı** durdur>|Profil oluşturma hizmeti bileşenini (hizmet) veya çekirdek modu cihaz sürücüsünü (sürücü) başlatır, sonlandırır, kaldırır veya kaldırır.|
|**Yönetici:** \<*hizmet*&#124;*sürücüsü*>**autostart**\<&#124;**kapalı**>|Yeniden başlatmadan sonra profil oluşturma hizmeti 'nin (hizmet) veya çekirdek modu cihaz sürücüsünün (sürücü) otomatik olarak başlatılmasını etkinleştirilir veya devre dışı bırakır.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd/Driver
 **VSPerfCmd/Driver** seçeneği artık kullanılmıyor. Bu işlev için **VSPerfCmd yönetici** seçeneklerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
