---
title: Kullanıcı (VSPerfCmd) | Microsoft Docs
description: Kullanıcı seçeneğinin profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını nasıl belirttiğinde öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a1338b81d94b8c4b09d4f14fefa807781bd53fc52fa6eec91917453787369792
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368129"
---
# <a name="user-vsperfcmd"></a>Kullanıcı (VSPerfCmd)
**Kullanıcı** seçeneği, profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin **işlemler** sekmesinde kullanıcı adı sütununda listelenir.

 **Kullanıcı** seçeneği, yalnızca **Başlangıç** seçeneğini de içeren bir komut satırında belirtilebilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Domain` Kullanıcının etki alanının adı.

 `UserName` Kullanıcının adı.

## <a name="required-options"></a>Gerekli seçenekler
 **Kullanıcı** seçeneği yalnızca **Başlangıç** seçeneğiyle birlikte kullanılabilir.

 **Başlangıç:** `Method` Profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, **Kullanıcı** seçeneğinin kullanımını gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
