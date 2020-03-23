---
title: Çıktı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ab01f67d44e8c6e0cc13eaf9b0046695a0132e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778511"
---
# <a name="output"></a>Çıktı
**Çıktı** seçeneği, performans oturumu için profil oluşturma veri dosyasının adını belirtir. **Çıktı** **Başlat** seçeneği yle kullanılmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `FileName`Veri dosyasının adı. Tam ve kısmi yollar kabul edilir. Bir yol belirtilmemişse, dosya geçerli dizinde oluşturulur.

## <a name="required-options"></a>Gerekli seçenekler
 **Çıktı** seçeneği **Başlat** seçeneğiyle kullanılmalıdır.

 **Başlangıç:** `Method` Çıktı dosya adını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, profil oluşturma veri dosyası geçerli dizinde oluşturulur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
