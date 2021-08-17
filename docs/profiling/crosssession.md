---
title: Çapraz Geçiş | Microsoft Docs
description: Profil oluşturmanın herhangi bir konsol oturumundan VSPerfCmd.exe için Çapraz Geçiş seçeneğini nasıl kullanabileceğini öğrenin. Başlat seçeneğini de belirtmeniz gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4dffc4946f0476bb9b93f39392d310ced5c8e824
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039065"
---
# <a name="crosssession"></a>CrossSession
Çapraz *VSPerfCmd.exe* **seçeneği, profil oluşturmanın** herhangi bir konsol oturumundan veri toplaması için olanak sağlar. **Çapraz Geçiş seçeneği** Başlat seçeneğiyle **birlikte kullanılmalıdır.**

 CrossSession yerine **CS** **kısaltmasını kullanabilirsiniz.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="valid-options"></a>Geçerli Seçenekler
 Başka bir oturumda profil oluşturmayı **etkinleştirmek için, Çapraz Geçiş** seçeneğinin Başlat seçeneğiyle **belirtilmelidir.** **CrossSession,** sonraki **vsPerfCmd** Attach ve Detach komutlarında **da belirtilmelidir.**

 **Başlat:** `Method` Başlat **seçeneği,** profilleyiciyi belirtilen profil oluşturma yöntemiyle başlatıyor.

 **Ekleme:** _PID_[**,**_PID_] Belirtilen işlemlerin profilini oluşturmayı başlar.

 **Detach**[**:**_PID_[,_PID_]] Belirtilen işlemlerin profilini oluşturmayı durdurur.

## <a name="example"></a>Örnek
 Bu örnekte, **başka bir konsol oturumunda** başlatan bir uygulamaya eklemek için Çapraz Geçiş seçeneği kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
