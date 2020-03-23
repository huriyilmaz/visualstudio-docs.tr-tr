---
title: Çapraz Oturum | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de982643a08e1af88073dde0fb0a9abc029900
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779460"
---
# <a name="crosssession"></a>CrossSession
*VSPerfCmd.exe* **CrossSession** seçeneği, profil oluşturucunun herhangi bir konsol oturumundan veri toplamasını sağlar. **Çapraz Oturum** seçeneği **Başlat** seçeneğiyle kullanılmalıdır.

 **CrossSession**yerine **CS** kısaltmasını kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="valid-options"></a>Geçerli Seçenekler
 Başka bir oturumda profil oluşturmayı etkinleştirmek **için, Çapraz Oturum** **seçeneği** başlangıç seçeneğiyle belirtilmelidir. **CrossSession** da sonraki **VSPerfCmd Ekle** ve **Ayırma** komutlarında belirtilmelidir.

 **Başlangıç:** `Method` **Başlat** seçeneği profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatir.

 **Ekle:** _PID_[**,**_PID_] Belirtilen işlemlerin profilini çıkarmaya başlar.

 **[**:**:**_PID_[,_PID_]] Belirtilen işlemlerin profilini çıkarmayı durdurur.

## <a name="example"></a>Örnek
 Bu örnekte, **Çapraz Oturum** seçeneği başka bir konsol oturumunda başlatılan bir uygulamaya eklemek için kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
