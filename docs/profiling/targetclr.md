---
title: TargetCLR | Microsoft Docs
description: Bir uygulamada CLR'nin birden fazla sürümü yüklendiğinde TargetCLR seçeneğinin profil oluşturmak için ortak dil çalışma zamanı sürümünü nasıl belirtir?
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 083f650992a931686e49d878df1e2c323bd45f3d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141265"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** seçeneği, clR'nin bir uygulamada birden fazla sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanı (CLR) sürümünü belirtir.

 Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları uygulama tarafından yüklenen ilk CLR sürümünü hedefler.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametreler
 `ClrVersion` CLR'nin sürüm numarası. **vN.N.NNNNN sürüm biçimini kullanın.**

## <a name="required-options"></a>Gerekli seçenekler
 **TargetCLR seçeneği** yalnızca Başlatma veya Ekleme **seçenekleriyle** kullanılabilir. 

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve profil oluşturmaya başlar.

 **Ekleme:** `PID` Belirtilen işlem profilini oluşturmak için başlar.

## <a name="example"></a>Örnek
 Bu örnekte, CLR sürüm 4.0.11003'in profilinin doğru olduğundan emin olmak için TargetCLR seçeneği kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
