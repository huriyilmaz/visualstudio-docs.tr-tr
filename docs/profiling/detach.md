---
title: Ayır | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3251836959f41a4349851716f58f917943f10b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330247"
---
# <a name="detach"></a>Ayır
VSPerfCmd.exe **ayırma** seçeneği, profil oluşturucunun belirtilen işlemlerden veya hiçbiri belirtilmemişse tüm işlemlerden bağlantısını keser. Profil oluşturma, örnekleme yöntemi kullanılarak başlatılmış olmalıdır.

 **Başlatma** ya da **iliştirme** seçenekleriyle başlatılan profil oluşturma, **ayırma**ile kesilebilir. Profil Oluşturucu, sonraki **iliştirme** komutları kullanılarak yeniden dağıtılabilir.

 **Ayırma** , profil oluşturma veri dosyasını kapatmaz. Profil oluşturmayı sonlandırmak ve veri dosyasını kapatmak için **Kapat** seçeneğini kullanın.

> [!NOTE]
> **Başlangıç** seçeneği **CrossSession** seçeneğiyle belirtilmişse, **VSPerfCmd/Attach** veya **VSPerfCmd/detach** öğesine yapılan çağrılar de **CrossSession**belirtmelidir.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]
```

#### <a name="parameters"></a>Parametreler
 `PIDs|ProcessNames``PID`-Bir veya daha fazla işlemin sayısal sistem tanımlayıcısı.

 `ProcessNames` -işlemin adı. Adlandırılmış işlemin birden fazla örneği çalışıyorsa, sonuçlar tahmin edilemez.

 Birden çok işlemi virgülle ayırın.

 Hiçbir işlem belirtilmemişse profil oluşturucu, profili oluşturulmuş tüm işlemden ayrılır.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri tek bir komut satırında **Attach** seçeneğiyle birleştirilebilir.

 **CrossSession** , Oturum açma oturumu dışındaki oturumlarda profil oluşturma uygulamalarına izin vermez. **CrossSession** seçeneğiyle **Start** seçeneği belirtilmişse gereklidir.

## <a name="example"></a>Örnek
 Bu örnekte, **Detach** komutu profil oluşturmayı askıya alır ve **kapatma** komutu profil oluşturucu veri dosyasını kapatır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
;REM Excercise the application
VSPerfCmd.exe /Detach
VSPerfCmd.exe /Shutdown
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
