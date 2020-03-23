---
title: TargetCLR | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771612"
---
# <a name="targetclr"></a>TargetCLR
**TargetCLR** seçeneği, clr'nin birden fazla sürümü bir uygulamaya yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.

 Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları clr uygulama tarafından yüklenen ilk sürümünü hedeflemektedir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]
```

#### <a name="parameters"></a>Parametreler
 `ClrVersion`CLR'nin sürüm numarası. **vN.N.NNNNN**sürüm biçimini kullanın.

## <a name="required-options"></a>Gerekli seçenekler
 **TargetCLR** seçeneği yalnızca **Başlat** veya **Ekle** seçenekleriyle kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve profilini çekmeye başlar.

 **Ekle:** `PID` Belirtilen işlemin profilini atmaya başlar.

## <a name="example"></a>Örnek
 Bu örnekte, ClR sürüm 4.0.11003 profilli olduğundan emin olmak için TargetCLR seçeneği kullanılır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003
```
