---
title: VSPerfCmd | Microsoft Docs
description: Performans verilerini toplamayı VSPerfCmd.exe ve durdurmak için VSPerfCmd.exe aracının nasıl olduğunu öğrenin. Ayrıca çeşitli VSPerfCmd araç seçenekleri hakkında bilgi edinebilirsiniz.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, VSPerfCmd tool
- command-line tools, VSPerfCmd tool
- command line, tools
- profiling tools,VSPerfCmd
- VSPerfCmd tool
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 90345169af67118a9184f91afc3984ca9b915c0ebe104feecf9455523d27bde0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121353987"
---
# <a name="vsperfcmd"></a>VSPerfCmd
Performans *VSPerfCmd.exe* toplamayı başlatmak ve durdurmak için aşağıdaki araç kullanılır. Aşağıdaki söz dizimlerini kullanır:

```cmd
VSPerfCmd [/U] [/options]
```

 Aşağıdaki tablolarda, *VSPerfCmd.exe* seçenekleri açıktır.

|Seçenek|Açıklama|
|------------|-----------------|
|**U**|Yeniden yönlendirilen konsol çıkışı Unicode olarak yazılır. Belirtilen ilk seçenek olması gerekir.|
|[Başlat:](../profiling/start.md) `mode`|Profil oluşturma hizmetini belirtilen modda başlatır.|
|[Çıktı:](../profiling/output.md) `filename`|Çıktı dosyasının adını belirtir. Yalnızca Başlat ile **kullanın.**|
|[CS'de çapraz&#124;çapraz geçiş](../profiling/crosssession.md)|Farklı oturumlarda profil Windows sağlar. Yalnızca Başlat, **Ekle** veya **Başlat** **ile kullanın.**|
|[Kullanıcı:](../profiling/user-vsperfcmd.md) [ `domain\` ]`username`|Belirtilen hesabın profil oluşturma hizmetine erişimini sağlar. Yalnızca Başlat ile **kullanın.**|
|[WaitStart](../profiling/waitstart.md)[**:** `n` ]|Veri toplama günlükleyicinin başlatılmasını bekler. belirtilirse `n` **VSPerfCmd** en fazla saniye `n` bekler. `n`Belirtilmezse **VSPerfCmd** süresiz olarak bekler. Bu, **vsPerfCmd'nin bir** toplu işlem kapsamında kullanımını kolaylaştırıyor.|
|[Sayaç:](../profiling/counter.md) `cfg`|Örnek profil oluşturma yöntemi kullanılırken, bir CPU sayacı ve örnekleme aralığı olarak kullanılacak olay sayısını belirtir. Yalnızca bir sayaç değerini örnekleysiniz.<br /><br /> Ölçüm aracı profil oluşturma yöntemi kullanılırken, her bir ölçüm noktasında toplanacak bir CPU sayacı belirtir. Yalnızca **Başlangıç:** `Trace` , Ekleme veya **Başlatma** ile **kullanın.**|
|[QueryCounters](../profiling/querycounters.md)|Geçerli makine için geçerli CPU sayaçlarının listesini görüntüler.|
|[WinCounter:](../profiling/wincounter.md)  *path*|Profil işareti Windows dahil etmek için bir performans sayacı olayı belirtir. Yalnızca Başlat ile **kullanın.**|
|[AutoMark:](../profiling/automark.md)  *n*|Performans sayacı veri toplama olayları arasındaki zaman aralığını (Windows cinsinden) belirtir. **WinCounter ile kullanın.**|
|[Olaylar:](../profiling/events-vsperfcmd.md) `option`|Windows (ETW) olayları için belirtilen Olay İzleme koleksiyonunu kontrol eder. ETW verileri bir için toplanır. profil oluşturma verileri ( değil *itl* dosyası.*vsp*) dosyasını seçin.|
|[Durum](../profiling/status.md)|Profil oluşturmanın durumunu, profili şu anda profili yapılan işlemlerle ilgili bilgileri ve profilleyiciyi denetleme yetkisi olan hesapları görüntüler.|
|[Kapatma](../profiling/shutdown.md)[**:** `n` ]|Profil oluşturma veri dosyasını kapatır ve profilleyiciyi kapatır.|
|[GlobalOn](../profiling/globalon-and-globaloff.md)|**VSPerfCmdGlobalOff çağrısından sonra veri toplamayı sürdürür.**|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Tüm veri toplamayı durdurur, ancak profil oluşturma oturumunu sona erer.|
|[ProcessOn:](../profiling/processon-and-processoff.md) `pid`|Profil oluşturma **VSPerfCmdProcessOff** çağrısı tarafından duraklatıldıktan sonra belirtilen işlem için veri toplamayı sürdürür.|
|[ProcessOff:](../profiling/processon-and-processoff.md) `pid`|Belirtilen işlem için veri toplamayı durdurur.|
|[ThreadOn ve ThreadOff:](../profiling/threadon-and-threadoff.md)  *tid*|Profil oluşturma **vsPerfCmdThreadOff** çağrısı tarafından duraklatıldıktan sonra belirtilen işlem için profil oluşturmayı sürdürür. Yalnızca ölçümleme yöntemiyle profil oluşturmada **ThreadOn** kullanın.|
|[ThreadOn ve ThreadOff:](../profiling/threadon-and-threadoff.md)  *tid*|Belirtilen iş parçacığı için profil oluşturmayı duraklatıyor. Yalnızca ölçümleme yöntemiyle profil oluşturmada **ThreadOff** kullanın.|
|[İşaret:](../profiling/mark.md)  _MarkNum_[**,**_MarkText_**]**|Profil oluşturma veri dosyasına isteğe bağlı metinle bir işaret ekler.|

## <a name="sample-method-options"></a>Örnek yöntem seçenekleri
 Aşağıdaki seçenekler yalnızca örnekleme profil oluşturma yöntemini kullanırken kullanılabilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[Başlatma:](../profiling/launch.md) **Yürütülebilir** |Belirtilen uygulamayı başlatır ve profil oluşturmayı başlatır.|
|[Args:](../profiling/args.md)  *Bağımsız Değişkenler*|Başlatılan uygulamaya geçilen komut satırı bağımsız değişkenlerini belirtir.|
|[Konsol](../profiling/console.md)|Belirtilen komutu yeni bir komut istemi penceresinde başlatır.|
|[Ekleme:](../profiling/attach.md)  *PID*[**,**_PID_]|Belirtilen işlemlerin profilini oluşturmayı başlar. İşlemler, işlem kimliği veya işlem adıyla tanımlandı.|
|[Ayırma](../profiling/detach.md)[**:**_PID_[,_PID_]]|Belirtilen işlemlerin profilini oluşturmayı durdurur. İşlemler, işlem kimliği veya işlem adıyla tanımlandı. Hiçbir işlem belirtilmezse, profil oluşturma tüm işlemler için durdurulr.|
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Ayırma** `&#124;` **Ömrü**}]|.NET bellek ayırma ve nesne yaşam süresi verilerini toplar. Yalnızca **VSPerfCmdLaunch seçeneğiyle** kullanın.|

### <a name="sample-interval-options"></a>Örnek aralık seçenekleri
 Aşağıdaki seçenekler örnekleme aralıklarının türünü ve süresini belirtir. Varsayılan değer **Zamanlayıcı'dır.** Ayrıca Sayaç seçeneğini kullanarak bir CPU sayacını aralık olarak **belirtebilirsiniz.** Bu seçenekler yalnızca Başlat ile veya **profil** oluşturma oturumunun **ilk Eklemesi** ile belirtilebilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|Her n-th sayfa hatasıyla ilgili örnekler (default=10).|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Her n-th sistem çağrısıyla ilgili örnekler (default=10).|
|[Zamanlayıcı](../profiling/timer.md)[**:**_n_]|Her n-th işlemci döngüsünde örnekler (default=10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Hizmet bileşeni ve çekirdek modu cihaz seçenekleri
 Aşağıdaki Yönetici seçenekleri hizmet bileşenlerinin veya çekirdek modu cihaz sürücülerinin profilini oluşturmayı destekler. Yönetici seçenekleri profil oluşturma izinlerini ayarlayın ve profili profili yapılan hizmet veya cihaz sürücüsünü denetleyin.

 Yönetici seçeneklerinin, yönetici kimlik bilgileriyle çalışan bir komut isteminde yürütülmesi gerekir.

|Seçenek|Açıklama|
|------------|-----------------|
|**Yönetici: güvenlik**, \<**ALLOW&#124;DENY**> *sağ*[ *sağ*], \<*User*&#124;*Group*>|Profil oluşturma hizmetleri için belirtilen kullanıcı veya grup erişimine izin verir veya reddeder.<br /><br /> `Right` şunları yapabilirsiniz:<br /><br /> CrossSession-oturum açmaya yönelik profili oluşturmak için kullanıcıya hizmete erişim sağlar.<br /><br /> Sampleprofil oluşturma-örnekleme profil oluşturmayı etkinleştirmek için kullanıcıya sürücüye erişim sağlar. İzleme profili oluşturma sırasında çekirdek geçiş bilgilerine erişmek için de kullanılır.<br /><br /> FullAccess-kullanıcıya hem CrossSession hem de Sampleprofil oluşturma erişimi verir.|
|**Yönetici: güvenlik, liste**|Profil oluşturma hizmetlerinin geçerli durumunu listeler ve Kullanıcı izinlerini listeler.|
|**Yönetici:**\<*Service*&#124;*Driver*>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**>|Profil oluşturma hizmeti bileşenini (hizmet) veya çekirdek modu cihaz sürücüsünü (sürücü) başlatır, sonlandırır, kaldırır veya kaldırır.|
|**Yönetici:** \<*Service*&#124;*Driver*> Otomatik **Başlat**\<**ON**&#124;**OFF**>|Yeniden başlatmadan sonra profil oluşturma hizmeti 'nin (hizmet) veya çekirdek modu cihaz sürücüsünün (sürücü) otomatik olarak başlatılmasını etkinleştirilir veya devre dışı bırakır.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd/Driver
 **VSPerfCmd/Driver** seçeneği artık kullanılmıyor. Bu işlev için **VSPerfCmd yönetici** seçeneklerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
