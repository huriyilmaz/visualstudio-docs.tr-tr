---
title: Çıkış | Microsoft Docs
description: Çıktı seçeneğinin performans oturumu için profil oluşturma veri dosyasının adını nasıl belirtir? Çıkış Başlat seçeneğiyle kullanılmalıdır.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c521362ecde12a5b996062f6f1e0d07992e26e06
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107114"
---
# <a name="output"></a>Çıktı
Çıktı  seçeneği, performans oturumu için profil oluşturma veri dosyasının adını belirtir. **Çıkış** Başlat seçeneğiyle **kullanılmalıdır.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `FileName` Veri dosyasının adı. Tam ve kısmi yollar kabul edilir. Bir yol belirtilmezse, dosya geçerli dizinde oluşturulur.

## <a name="required-options"></a>Gerekli seçenekler
 Çıkış  seçeneği Başlat seçeneğiyle **birlikte kullanılmalıdır.**

 **Başlat:** `Method` Çıktı dosyasının adını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, profil oluşturma veri dosyası geçerli dizinde oluşturulur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
