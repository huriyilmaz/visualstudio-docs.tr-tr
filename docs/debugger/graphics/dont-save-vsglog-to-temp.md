---
description: Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedilip kaydedilmediğini kendi varlığına göre tanımlar.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 06152c79859a34e604ffc4e5227e2dd11ebbeaca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146203"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedilip kaydedilmediğini kendi varlığına göre tanımlar.

## <a name="syntax"></a>Syntax

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Değer
 Durumu veya devamsızlığı tarafından kullanılan bir ön işlemci sembolü, grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedilip kaydedilmediğini belirler. Bu simge tanımlanmışsa, tarafından tanımlanan dosya adı `VSG_DEFAULT_RUN_FILENAME` yakalanan uygulamanın geçerli dizinine göre veya mutlak bir yoldur; Aksi takdirde, tarafından tanımlanan dosya adı `VSG_DEFAULT_RUN_FILENAME` kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol olamaz.

## <a name="remarks"></a>Açıklamalar
 Kullanıcının ayrıcalıklarına bağlı olarak, grafik günlük dosyası rastgele bir konuma kaydedilemeyebilir. Seçtiğiniz konumun Kullanıcı tarafından yazılıp yazılamayacağını bilmiyorsanız, grafik günlüklerini kullanıcının geçici dosyalar dizinine veya bilinen ve iyi bir konuma kaydetmeyi tercih etmenizi öneririz.

 Grafik günlük dosyasının geçici dosyalar dizinine kaydedilmesini engellemek için, ' yi dahil etmeden önce tanımlanması gerekir `DONT_SAVE_VSGLOG_TO_TEMP` `vsgcapture.h` .

## <a name="example"></a>Örnek
 Bu örnekte, grafik günlük dosyasının ana makinedeki mutlak bir yola nasıl kaydedileceği gösterilmektedir.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
