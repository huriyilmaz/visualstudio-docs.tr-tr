---
title: TargetCLR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fffcab1d841840c15957e8dae0ff0f87b20de28d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74771612"
---
# <a name="targetclr"></a>TargetCLR
**Targetclr** seçeneği, BIR uygulamaya CLR 'nin birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanı (CLR) sürümünü belirtir.

 Profil Oluşturma Araçları, varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uygulama tarafından yüklenen CLR 'nin ilk sürümünü hedefleyin.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametreler
 `ClrVersion` CLR sürüm numarası. **Vn. N.** 2 sürüm biçimini kullanın.

## <a name="required-options"></a>Gerekli seçenekler
 **Targetclr** seçeneği yalnızca **başlatma** veya **iliştirme** seçenekleriyle kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve profile başlar.

 **Ekle:** `PID` Belirtilen işlemi profil olarak başlatır.

## <a name="example"></a>Örnek
 Bu örnekte, CLR Version 4.0.11003 'ın profili oluşturulmuş olduğundan emin olmak için TargetCLR seçeneği kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
