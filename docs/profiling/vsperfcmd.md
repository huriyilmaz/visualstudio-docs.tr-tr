---
title: VSPerfCmd | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778004"
---
# <a name="vsperfcmd"></a>VSPerfCmd
*VSPerfCmd.exe* aracı, performans veri toplamayı başlatmak ve durdurmak için kullanılır. Aşağıdaki sözdizimini kullanır:

```cmd
VSPerfCmd [/U] [/options]
```

 Aşağıdaki tablolar *DAPPerfCmd.exe* araç seçeneklerini açıklayınız.

|Seçenek|Açıklama|
|------------|-----------------|
|**U**|Yönlendirilen konsol çıktısı Unicode olarak yazılır. Belirtilen ilk seçenek olmalıdır.|
|[Başlangıç](../profiling/start.md) **:**`mode`|Profil oluşturma hizmetini belirtilen modda başlatır.|
|[Çıktı](../profiling/output.md) **:**`filename`|Çıktı dosyası adını belirtir. Yalnızca **Başlangıç**ile kullanın.|
|[Çapraz Oturum&#124;CS](../profiling/crosssession.md)|Windows oturumları arasında profil oluşturmayı sağlar. Yalnızca **Başlat,** **Ekle** **veya Başlat**'la kullanın.|
|[Kullanıcı](../profiling/user-vsperfcmd.md) **:**:`domain\`[ ]`username`|Profiloluşturucu hizmetine belirtilen hesap erişimini sağlar. Yalnızca **Başlangıç**ile kullanın.|
|[WaitStart](../profiling/waitstart.md)[**:**`n`]|Veri toplama kaydedicisinin başlatılmasını bekler. `n` **Belirtilirse, VSPerfCmd** en `n` çok saniye bekleyecek. `n` Belirtilmemişse, **VSPerfCmd** süresiz olarak bekleyecek. Bu, **vsPerfCmd'nin** toplu iş bir parçası olarak kullanımını kolaylaştırır.|
|[Sayaç](../profiling/counter.md) **:**`cfg`|Örnek profil oluşturma yöntemi kullanıldığında, bir CPU sayacı ve örnekleme aralığı olarak kullanılacak olay sayısını belirtir. Yalnızca bir sayaç değerini örnekleyebilirsiniz.<br /><br /> Enstrümantasyon profilleme yöntemi kullanıldığında, her enstrümantasyon noktasında toplanacak bir CPU sayacı belirtir. Yalnızca **Başlat ile kullanın:**`Trace`, **Ekle**, veya **Başlat**.|
|[QueryCounters](../profiling/querycounters.md)|Geçerli makine için geçerli CPU sayaçlarının listesini görüntüler.|
|[WinCounter](../profiling/wincounter.md) **:** *yol*|Profil işareti verilerine dahil olacak bir Windows performans sayacı olayı belirtir. Yalnızca **Başlangıç**ile kullanın.|
|[AutoMark](../profiling/automark.md) **:** *n*|Windows performans sayacı veri toplama olayları arasındaki zaman aralığını (milisaniye cinsinden) belirtir. **WinCounter**ile kullanın.|
|[Etkinlikler](../profiling/events-vsperfcmd.md) **:**`option`|Belirtilen Windows (ETW) olayları için Olay İzleme'nin toplanmasını denetler. ETW verileri bir . profil oluşturma verileri olmayan *itl* dosyası (.* vsp*) dosyası.|
|[Durum](../profiling/status.md)|Profiloluşturcunun durumunu, şu anda profili olan işlemler le ilgili bilgileri ve profil oluşturucuyu denetleme yetkisine sahip hesapları görüntüler.|
|[Kapatma](../profiling/shutdown.md)[**:**`n`]|Profil oluşturma veri dosyasını kapatır ve profil oluşturucuyu kapatır.|
|[Globalon](../profiling/globalon-and-globaloff.md)|**VSPerfCmdGlobalOff'a**yapılan bir çağrıdan sonra veri toplamaya devam eder.|
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Tüm veri toplamayı durdurur, ancak profil oluşturma oturumunu sona erdirmez.|
|[ProcessOn](../profiling/processon-and-processoff.md) **:**`pid`|Profil oluşturma **VSPerfCmdProcessOff'a**yapılan bir çağrı yla duraklatıldıktan sonra belirtilen işlem için veri toplamayı devam ettiriyor.|
|[İşlem Dışı](../profiling/processon-and-processoff.md) **:**`pid`|Belirtilen işlem için veri toplamayı durdurur.|
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Profil oluşturma **VSPerfCmdThreadOff**bir çağrı ile duraklatıldı sonra belirtilen işlem için profil leme devam eder. **ThreadOn'u** yalnızca enstrümantasyon yöntemiyle profil yaparken kullanın.|
|[ThreadOn ve ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Belirtilen iş parçacığı için profil oluşturma duraklar. **ThreadOff'u** yalnızca enstrümantasyon yöntemiyle profil çıkarırken kullanın.|
|[İşaret](../profiling/mark.md) **:** _MarkNum_[**,**_MarkText_**]**|Profil oluşturma veri dosyasına isteğe bağlı metinle birlikte bir işaret ekler.|

## <a name="sample-method-options"></a>Örnek yöntem seçenekleri
 Aşağıdaki seçenekler yalnızca örnekleme profil oluşturma yöntemini kullandığınızda kullanılabilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[Başlat](../profiling/launch.md) **:** *Çalıştırılabilir*|Belirtilen uygulamayı başlatır ve profil oluşturmabaşlar.|
|[Args](../profiling/args.md) **:** *Bağımsız değişkenler*|Başlatılan uygulamaya geçmek için komut satırı bağımsız değişkenlerini belirtir.|
|[Konsol](../profiling/console.md)|Yeni bir komut istemi penceresinde belirtilen komutu başlatır.|
|[Ekle](../profiling/attach.md) **:** *PID*[**,**_PID_]|Belirtilen işlemlerin profilini çıkarmaya başlar. İşlemler işlem kimliği yle veya işlem adı ile tanımlanabilir.|
|[Detach](../profiling/detach.md)[**:**_PID_[,_PID_]]|Belirtilen işlemlerin profilini çıkarmayı durdurur. İşlemler işlem kimliği yle veya işlem adı ile tanımlanabilir. Hiçbir işlem belirtilmemişse, profil oluşturma tüm işlemler için durdurulur.|
|[GC](../profiling/gc-vsperfcmd.md)[**:**{**Ayırma**`&#124;`**Ömrü**}]|.NET bellek ayırma ve nesne yaşam boyu verilerini toplar. Yalnızca **VSPerfCmdLaunch** seçeneği ile kullanın.|

### <a name="sample-interval-options"></a>Örnek aralığı seçenekleri
 Aşağıdaki seçenekler, örnekleme aralıklarının türünü ve süresini belirtir. Varsayılan **Zamanlayıcı'dır.** **Sayaç** seçeneğini kullanarak bir CPU sayacını da aralık olarak belirtebilirsiniz. Bu seçenekler yalnızca **Başlat'la** veya profil oluşturma oturumunun ilk **Ekle'siyle** belirtilebilir.

|Seçenek|Açıklama|
|------------|-----------------|
|[PF](../profiling/pf.md)[**:**_n_]|Her n-inci sayfa hatasındaki örnekler (varsayılan=10).|
|[Sys](../profiling/sys-vsperfcmd.md)[**:**_n_]|Her n-th sistem çağrısındaki örnekler (varsayılan=10).|
|[Zamanlayıcı](../profiling/timer.md)[**:**_n_]|Her n-th işlemci döngüsündeki örnekler (varsayılan=10000000).|

## <a name="service-component-and-kernel-mode-device-options"></a>Servis bileşeni ve çekirdek modu cihaz seçenekleri
 Aşağıdaki Yönetici seçenekleri profil oluşturma hizmeti bileşenlerini veya çekirdek modu aygıt sürücülerini destekler. Yönetici seçenekleri profil oluşturma izinlerini ayarlar ve profilli hizmeti veya aygıt sürücüsünü denetler.

 Yönetici seçenekleri, yönetim kimlik bilgileriyle çalışan bir komut isteminde yürütülmelidir.

|Seçenek|Açıklama|
|------------|-----------------|
|**Admin:Güvenlik** \<, **>&#124;İnKAR EDİn,** *Sağ*[ *Sağ* \<], *Kullanıcı*&#124;*Grubu*>|Profil oluşturma hizmetlerine belirtilen kullanıcı veya grup erişimine izin verir veya reddeder.<br /><br /> `Right`olabilir:<br /><br /> CrossSession - kullanıcının oturumlar arası profil oluşturma yapmak için hizmete erişimini sağlar.<br /><br /> SampleProfiling - örnekleme profiloluşturma etkinleştirmek için sürücüye kullanıcı erişim sağlar. İzleme profiloluşturma sırasında çekirdek geçiş bilgilerine erişmek için de kullanılır.<br /><br /> FullAccess - kullanıcıya hem CrossSession hem de SampleProfiling erişimi sağlar.|
|**Admin:Güvenlik, Liste**|Profil oluşturma hizmetlerinin geçerli durumunu listeler ve kullanıcı izinlerini listeler.|
|**Admin:** \< *Servis*&#124;*Sürücü*>\<**BAŞLAT**&#124;**STOP**&#124;**INSTALL**&#124;**INSTALL**>|Profil oluşturma hizmeti bileşenini (hizmet) veya çekirdek modu aygıt sürücüsünü (sürücü) başlatır, durdurur, yükler veya yükler.|
|**Admin:** \< *Servis*&#124;*Sürücü*>**AutoStart**\<**ON**&#124;**KAPALI**>|Yeniden başlatmadan sonra profil oluşturma hizmetini (hizmeti) veya çekirdek modu aygıt sürücüsünü (sürücü) otomatik olarak çalıştırır veya devre dışı kılabilir.|

## <a name="vsperfcmd-driver"></a>VSPerfCmd / Sürücü
 **VSPerfCmd /Driver** seçeneği artık kullanılmaz hale geldi. Bu işlevsellik için **VsPerfCmd Yönetici** seçeneklerini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfReport](../profiling/vsperfreport.md)
