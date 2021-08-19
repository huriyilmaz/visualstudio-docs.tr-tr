---
description: Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedip kaydedile olmadığını varlığıyla tanımlar.
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 44ffbba52a09c5d2874e51014cec9e1b755c5f32
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154258"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedip kaydedile olmadığını varlığıyla tanımlar.

## <a name="syntax"></a>Syntax

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>Değer
 Varlığı veya yokluğuna göre grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedip kaydedilemeyişini belirleyen bir önişlemci simgesi. Bu simge tanımlanmışsa, tarafından tanımlanan dosya adı yakalanan uygulamanın geçerli diziniyle görelidir veya mutlak bir yoldur; aksi takdirde, tarafından tanımlanan dosya adı kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol `VSG_DEFAULT_RUN_FILENAME` `VSG_DEFAULT_RUN_FILENAME` değildir.

## <a name="remarks"></a>Açıklamalar
 Kullanıcının ayrıcalıklarına bağlı olarak grafik günlüğü dosyası rastgele bir konuma kaydedilemiyor olabilir. Seçtiğiniz konumun kullanıcı tarafından yazıp yazılanamayyabilirsiniz konusunda emin değilseniz grafik günlüklerini kullanıcının geçici dosyalar dizinine veya bilinen başka bir iyi konuma kaydetmeyi tercih edersiniz.

 Grafik günlüğü dosyasının geçici dosyalar dizinine kaydedilene kadar, eklemeden önce `DONT_SAVE_VSGLOG_TO_TEMP` `vsgcapture.h` tanımlanmalıdır.

## <a name="example"></a>Örnek
 Bu örnek, grafik günlük dosyasının konak makinede mutlak bir yola nasıl kaydedile bir yolunu gösterir.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
