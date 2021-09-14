---
title: Çıkış | Microsoft Docs
description: Çıktı seçeneğinin, performans oturumu için profil oluşturma veri dosyasının adını nasıl belirttiğinde öğrenin. Çıkışın başlangıç seçeneğiyle birlikte kullanılması gerekir.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725687"
---
# <a name="output"></a>Çıktı
**Output** seçeneği, performans oturumu için profil oluşturma veri dosyasının adını belirtir. **Çıkışın** **Başlangıç** seçeneğiyle birlikte kullanılması gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `FileName` Veri dosyasının adı. Tam ve kısmi yollar kabul edilir. Bir yol belirtilmemişse dosya geçerli dizinde oluşturulur.

## <a name="required-options"></a>Gerekli seçenekler
 **Output** seçeneği **Start** seçeneğiyle birlikte kullanılmalıdır.

 **Başlangıç:** `Method` Çıkış dosyası adını belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, profil oluşturma veri dosyası geçerli dizinde oluşturulur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
