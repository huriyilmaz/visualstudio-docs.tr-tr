---
title: Kullanıcı (VSPerfCmd) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dbb1a155e8e0ffd2690b5850299b8075a63ea3d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779967"
---
# <a name="user-vsperfcmd"></a>Kullanıcı (VSPerfCmd)
**Kullanıcı** seçeneği, profilli işlemin sahibi hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, yalnızca işlem kullanıcı da oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin **İşlemler** sekmesinde Kullanıcı Adı sütununda listelenir.

 **Kullanıcı** seçeneği yalnızca **Başlat** seçeneğini de içeren bir komut satırında belirtilebilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Domain`Kullanıcının etki alanının adı.

 `UserName`Kullanıcının adı.

## <a name="required-options"></a>Gerekli seçenekler
 **Kullanıcı** seçeneği yalnızca **Başlat** seçeneği yle kullanılabilir.

 **Başlangıç:** `Method` Profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, **Kullanıcı** seçeneğinin kullanımını göstermektedir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
