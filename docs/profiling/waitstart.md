---
title: WaitStart | Microsoft Docs
description: WaitStart seçeneğinin, VSPerfCmd.exe başlat alt komutunun yalnızca profil oluşturma başlatıcı başlatılmış veya belirtilen sayıda saniyenin geç olduğu zaman dönmesine neden olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b136b8b33d59ee2e782288d0952e0216181f2465
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140576"
---
# <a name="waitstart"></a>WaitStart
WaitStart seçeneği, *VSPerfCmd.exe* başlat alt komutunun yalnızca profil oluşturma tarafından başlatılmış veya belirtilen sayıda saniyenin geç olduğu zaman dönüşe neden olur. Varsayılan olarak Başlat komutu hemen döndürür. Alt komutu başlat komutu profil oluşturmadan döndürülürse bir hata döndürülür. Saniye sayısı belirtilmezse Başlat komutu süresiz olarak bekler.

 WaitStart seçeneği, profil işleyicinin başlatılmış olduğunu doğrularken toplu iş dosyalarında kullanışlıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametreler
 `Seconds` Başlat alt komutundan dönmeden önce beklemeniz gereken saniye sayısı.

## <a name="required-options"></a>Gerekli seçenekler
 WaitStart seçeneği yalnızca Başlat alt komutuyla kullanılabilir.

 **Çıktı:** `filename` Çıktı dosyasının adını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu toplu iş dosyası örneğinde, Başlat komutu profilleyicinin başlatılması için 5 saniye bekler.

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
