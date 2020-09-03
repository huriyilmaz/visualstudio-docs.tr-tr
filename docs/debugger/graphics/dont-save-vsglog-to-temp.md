---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736086"
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
