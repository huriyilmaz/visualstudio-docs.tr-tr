---
title: WaitStart | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1cbabcf86afa9770f1616c7e4e508af1c9afa1ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779863"
---
# <a name="waitstart"></a>WaitStart
WaitStart *seçeneği, VSPerfCmd.exe* Başlat alt komutunun yalnızca profil oluşturucu başlatıldığında veya belirtilen saniye sayısı geçtiğinde dönmesine neden olur. Varsayılan olarak, Başlat komutu hemen döner. Profil oluşturucuyu başlatmadan Başlat alt komutu dönerse, bir hata döndürülür. Saniye sayısı belirtilmemişse, Başlat komutu süresiz olarak bekler.

 WaitStart seçeneği, profil oluşturucunun başlatıldığını sigortalamak için toplu dosyalarda yararlıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametreler
 `Seconds`Başlat alt komutundan dönmeden önce bekleyecek saniye sayısı.

## <a name="required-options"></a>Gerekli seçenekler
 WaitStart seçeneği yalnızca Başlat alt komutuyla kullanılabilir.

 **Çıktı:** `filename` Çıktı dosya adını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu toplu iş dosyası örneğinde, Profil oluşturucunun başlatılması için Başlat komutu 5 saniye bekler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
