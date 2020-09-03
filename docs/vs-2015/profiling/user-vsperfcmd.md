---
title: Kullanıcı (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 311d02ad3e15f184f8b7e21b5794d73c41a8d4fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145385"
---
# <a name="user-vsperfcmd"></a>Kullanıcı (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kullanıcı** seçeneği, profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.  
  
 **Kullanıcı** seçeneği yalnızca, **Başlat** seçeneği seçeneğini de içeren bir komut satırında belirtilebilir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Domain`  
 Kullanıcının etki alanının adı.  
  
 `UserName`  
 Kullanıcının adı.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **Kullanıcı** seçeneği yalnızca **Başlangıç** seçeneğiyle birlikte kullanılabilir.  
  
 **Başlangıç:**`Method`  
 Profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, **Kullanıcı** seçeneğinin kullanımını gösterir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
