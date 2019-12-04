---
title: WaitStart | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779863"
---
# <a name="waitstart"></a>WaitStart
WaitStart seçeneği, *VSPerfCmd. exe* Start alt komutunun yalnızca profil oluşturucu başlatıldığında veya belirtilen saniye sayısı geçtiğinde dönmesini sağlar. Varsayılan olarak start komutu hemen döndürür. Start Sub komutu, profil oluşturucuyu başlatmadan döndürürse bir hata döndürülür. Saniye sayısı belirtilmemişse, Başlat komutu süresiz olarak bekler.

 WaitStart seçeneği, profil oluşturucunun başlatıldığından emin olmak için Batch dosyalarında faydalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametreler
 Başlangıç alt komutundan dönmeden önce beklenecek saniye sayısını `Seconds`.

## <a name="required-options"></a>Gerekli seçenekler
 WaitStart seçeneği yalnızca start Sub-komutuyla birlikte kullanılabilir.

 **Çıkış:** `filename` çıkış dosyası adını belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu toplu iş dosyasında, start komutu profil oluşturucunun başlatılması için 5 saniye bekler.

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
