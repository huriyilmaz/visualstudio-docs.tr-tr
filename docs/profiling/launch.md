---
title: Başlat | Microsoft Docs
description: Başlatma seçeneğinin örnekleme yöntemini kullanarak profil oluşturucuyu nasıl başlatacağınızı öğrenin ve ayrıca belirtilen uygulamayı başlatır.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6072fe7e3387f19669861e5ede945ab3f0c417a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917987"
---
# <a name="launch"></a>Başlat
**Başlatma** seçeneği, örnekleme yöntemini kullanarak profil oluşturucuyu başlatır ve ayrıca belirtilen uygulamayı başlatır.

 **Başlatma** seçeneğini kullanmak Için, **Başlangıç** seçeneğinde **örnek** yöntemi belirtmeniz gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametreler
 `AppName` Başlatılacak uygulamanın adı. Geçerli dizinden gelen tam ve kısmi yollar desteklenir.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki VSPerfCmd seçenekleri tek bir komut satırında **başlatma** seçeneği ile birleştirilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.

 **GlobalOn** ve **globaloff** devam ettirir (**GlobalOn**) veya profil oluşturma (**globaloff**) profili oluşturma, ancak profil oluşturma oturumunu sonlandırmaz.

 **ProcessOn:** `PID` ve **ProcessOff**: `PID` belirtilen işlem için özgeçmişler (**ProcessOn**) veya duraklama (**ProcessOff**) profili oluşturma.

 **Targetclr** Profil oluşturma oturumunda birden fazla sürüm yüklendiğinde profile yapılacak .NET Framework ortak dil çalışma zamanının (CLR) sürümünü belirtir. Varsayılan olarak, ilk yüklenen sürüm profili oluşturulur.

## <a name="exclusive-options"></a>Dışlamalı seçenekler
 Aşağıdaki seçenekler yalnızca **başlatma** seçeneği ile kullanılabilir.

 **Konsol** Belirtilen komut satırı uygulamasını yeni bir pencerede başlatır.

 **Bağımsız değişkenler:** `ArgList` Uygulamaya geçirilecek bağımsız değişkenlerin listesini belirtir.

 **Satır kapalı** Satır düzeyi profil oluşturma verilerinin koleksiyonunu devre dışı bırakır.

## <a name="sampling-options"></a>Örnekleme seçenekleri
 **Başlatma** komut satırında aşağıdaki örnekleme aralığı seçeneklerinden biri belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngülerinde bulunur.

 **Süreölçer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**sayaç**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**ayırma**&#124;**ömrü**] örnekleme aralığının sayısını ve türünü belirtir.

- **Zamanlayıcı** - `Cycles` durdurulmayan her işlemci saati döngüsünü örnekler. `Cycles`Belirtilmezse, 10.000.000 döngüsü kullanılır.

- **PF** -her `Events` sayfa hatalarını örnekler. `Events`Belirtilmezse, 10 sayfa hatası.

- **Sys** - `Events` işletim sistemine yapılan her çağrının örnekleri. `Events`Belirtilmezse, 10 sistem çağrısı kullanılır.

- **Sayaç** -örnekleri `Reload` tarafından BELIRTILEN her sayıdaki CPU performans sayacı `Name` . İsteğe bağlı olarak, `FriendlyName` profil oluşturucu raporlarında sütun üst bilgisi olarak kullanılacak bir dize belirtebilir.

- **GC** -.net bellek verilerini toplar. Varsayılan olarak,veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.

## <a name="example"></a>Örnek
 Bu örnek, bir uygulamayı başlatmak için **başlatma** kullanımını gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
