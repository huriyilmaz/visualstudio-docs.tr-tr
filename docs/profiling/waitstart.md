---
title: WaitStart | Microsoft Docs
description: WaitStart seçeneğinin, VSPerfCmd.exe Başlat alt komutunun yalnızca profil oluşturma başlatıcı başlatılmış olduğunda veya belirtilen saniye sayısı geçilende dönüşe neden olduğunu öğrenin.
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
ms.openlocfilehash: 726d77b41b5ab48cb1c82ba434a74c1940b54ccf8eaa57591bea9542f23b70d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121269853"
---
# <a name="waitstart"></a>WaitStart
WaitStart seçeneği, *VSPerfCmd.exe* başlat alt komutunun yalnızca profil oluşturma tarafından başlatılmış veya belirtilen sayıda saniyenin geç olduğu zaman dönüşe neden olur. Varsayılan olarak Başlat komutu hemen döndürür. Alt komutu başlat komutu profil oluşturmadan döndürülürse bir hata döndürülür. Saniye sayısı belirtilmezse Başlat komutu süresiz olarak bekler.

 WaitStart seçeneği, profil oluşturma işleminin başlatılmış olduğunu doğrularken toplu iş dosyalarında kullanışlıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametreler
 `Seconds` Başlat alt komutundan dönmeden önce beklemeniz gereken saniye sayısı.

## <a name="required-options"></a>Gerekli seçenekler
 WaitStart seçeneği yalnızca Başlat alt komutuyla kullanılabilir.

 **Çıkış:** `filename` Çıktı dosyasının adını belirtir.

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
