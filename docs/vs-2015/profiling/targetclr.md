---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145616"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Targetclr** seçeneği, BIR uygulamaya CLR 'nin birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanı (CLR) sürümünü belirtir.  
  
 Profil Oluşturma Araçları, varsayılan olarak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulama tarafından yüklenen CLR 'nin ilk sürümünü hedefleyin.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Parametreler  
 `ClrVersion`  
 CLR sürüm numarası. **Vn. N.** 2 sürüm biçimini kullanın.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 **Targetclr** seçeneği yalnızca **başlatma** veya **iliştirme** seçenekleriyle kullanılabilir.  
  
 **Başlatma:**`AppName`  
 Belirtilen uygulamayı başlatır ve profile başlar.  
  
 **Ekle:**`PID`  
 Belirtilen işlemi profil olarak başlatır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, CLR Version 4.0.11003 'ın profili oluşturulmuş olduğundan emin olmak için TargetCLR seçeneği kullanılır.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
