---
title: User (VSPerfCmd) | Microsoft Docs
description: Kullanıcı seçeneğinin profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını nasıl belirtir?
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
ms.openlocfilehash: 015cca1c11050f2bd34fa5b6eb8292b014b61856
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140810"
---
# <a name="user-vsperfcmd"></a>Kullanıcı (VSPerfCmd)
Kullanıcı  seçeneği, profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Görev Yöneticisi'nin İşlemler **sekmesindeki** Kullanıcı Adı Windows listelenir.

 Kullanıcı  seçeneği yalnızca Başlat seçeneğini de içeren bir komut satırı üzerinde **belirtilebilir.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Domain` Kullanıcının etki alanının adı.

 `UserName` Kullanıcının adı.

## <a name="required-options"></a>Gerekli seçenekler
 Kullanıcı  seçeneği yalnızca Başlat **seçeneğiyle** kullanılabilir.

 **Başlat:** `Method` Profil oluşturma yöntemini belirtilen profil oluşturma yöntemiyle başlatılır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, Kullanıcı seçeneğinin **kullanımını** gösteriyor.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
