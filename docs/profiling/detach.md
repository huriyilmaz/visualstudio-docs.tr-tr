---
title: Detach | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b151e3ede34d0c8fa3a863d7a4e7474431ae6f4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777396"
---
# <a name="detach"></a>Ayır
VSPerfCmd.exe **Detach** seçeneği, profiloluşturucuyu belirtilen işlemlerden veya hiçbiri belirtilmemişse tüm işlemlerden keser. Örnekleme yöntemi kullanılarak profil oluşturma nın başlatılması gerekir.

 **Başlat** veya **Ekle** seçenekleriyle başlatılan profil oluşturma bağlantısı Ayırılabilir. **Detach** Profil oluşturucu sonraki **Ekle** komutları kullanılarak yeniden kullanılabilir.

 **Detach** profil oluşturma veri dosyasını kapatmaz. Profil oluşturmayı sona erdirmek ve veri dosyasını kapatmak için **Kapatma** seçeneğini kullanın.

> [!NOTE]
> **Başlangıç** seçeneği **Crosssession** seçeneğiile belirtilmişse, **VSPerfCmd /Attach veya VSPerfCmd** **/Detach'a** yapılan tüm aramalarda **Crosssession**belirtilmelidir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametreler
 `PIDs|ProcessNames``PID` - Bir veya daha fazla sürecin sayısal sistem identiferi.

 `ProcessNames`- sürecin adı. Adlandırılmış işlemin birden çok örneği çalışıyorsa, sonuçlar öngörülemez.

 Birden çok işlemi virgülle ayırın.

 Hiçbir işlem belirtilmemişse, profil oluşturucu tüm profilli işlemden ayrılır.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri, tek bir komut satırında **Ekle** seçeneğiyle birleştirilebilir.

 **Çapraz oturum** Oturum açma oturumu dışındaki oturumlarda profil oluşturma uygulamalarını sağlar. **Başlangıç** seçeneği **Çapraz Oturum** seçeneğiyle belirtilmişse gereklidir.

## <a name="example"></a>Örnek
 Bu örnekte, **Detach komutu** profil oluşturmayı askıya akar ve **Kapatma** komutu profil oluşturmayı kapatır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
