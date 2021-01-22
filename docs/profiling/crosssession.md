---
title: CrossSession | Microsoft Docs
description: Profiler 'ın herhangi bir konsol oturumundan veri toplamasına izin vermek için VSPerfCmd.exe CrossSession seçeneğini nasıl kullanacağınızı öğrenin. Başlat seçeneğini de belirtmeniz gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7a20ada8a7ca8d0ca8c34c2c6d730c37cdca09b7
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686225"
---
# <a name="crosssession"></a>CrossSession
*VSPerfCmd.exe* **CrossSession** seçeneği, profil oluşturucunun herhangi bir konsol oturumundan veri toplamasını sağlar. **CrossSession** seçeneği **Start** seçeneğiyle birlikte kullanılmalıdır.

 **CrossSession** yerine **CS** kısaltması kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametreler
 Hiçbiri

## <a name="valid-options"></a>Geçerli seçenekler
 Başka bir oturumda profil oluşturmayı etkinleştirmek için, **CrossSession** seçeneğinin **Start** seçeneğiyle belirtilmesi gerekir. **CrossSession** , sonraki **VSPerfCmd Attach** ve **Detach** komutlarında de belirtilmelidir.

 **Başlangıç:** `Method` **Başlat** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.

 **Attach:** _PID_[**,**_pid_] belirtilen işlemlerin profilini oluşturmaya başlıyor.

 **Detach**[**:**_PID_[,_pid_]] belirtilen işlemlerin profilini oluşturmayı durduruyor.

## <a name="example"></a>Örnek
 Bu örnekte, **CrossSession** seçeneği, başka bir konsol oturumunda başlatılan bir uygulamaya eklemek için kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
