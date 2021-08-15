---
title: Ayırma | Microsoft Docs
description: Profil oluşturmanın belirtilen VSPerfCmd.exe bağlantısını kesmek veya hiçbiri belirtilmemişse tüm işlemlerden ayırmak için Ayırma seçeneğini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5738548f5a06804ab6405606b02dbcb1cfcb76f2a8784ac61b4dd9f9f873e7b6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333203"
---
# <a name="detach"></a>Ayır
Ayırma VSPerfCmd.exe **seçeneği,** profil oluşturmanın belirtilen işlemlerden veya hiçbiri belirtilmemişse tüm işlemlerden bağlantısını keser. Profil oluşturma, örnekleme yöntemi kullanılarak başlatılmış olması gerekir.

 Başlat veya Ekle seçenekleriyle başlayan profil **oluşturma** **bağlantısını Ayır** seçeneğiyle **kesebilirsiniz.** Profil oluşturma, sonraki Attach komutları kullanılarak  yeniden iliştirilebiliyor.

 **Ayır,** profil oluşturma veri dosyasını kapatmaz. Profil oluşturmayı **sona** erdir ve veri dosyasını kapatmak için Kapat seçeneğini kullanın.

> [!NOTE]
> Çapraz **Geçiş** seçeneğiyle Başlat  seçeneği belirtilmişse **VSPerfCmd /Attach veya VSPerfCmd** **/Detach** çağrıları da Çapraz Geçiş seçeneğini **belirtilmelidir.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametreler
 `PIDs|ProcessNames``PID`- Bir veya daha fazla işleme yönelik sayısal sistem kimliği.

 `ProcessNames` - sürecin adı. Adlandırılmış sürecin birden çok örneği çalışıyorsa, sonuçlar tahmin edilemez.

 Birden çok işlemi virgülle ayırma.

 Hiçbir işlem belirtilmezse, profil oluşturma işlemi profili yapılan tüm işlemlerden ayrılır.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri, tek bir komut satırı **üzerinde Ekle** seçeneğiyle bir araya kullanılabilir.

 **Çapraz geçiş** Oturum açma oturumu dışında oturumlarda uygulamaların profilini oluşturmayı sağlar. Başlat seçeneği **Çapraz** Geçiş **seçeneğiyle belirtilmişse** gereklidir.

## <a name="example"></a>Örnek
 Bu örnekte, **Ayır komutu** profil oluşturmayı askıya alır ve **Kapat** komutu profil oluşturma veri dosyasını kapatır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
