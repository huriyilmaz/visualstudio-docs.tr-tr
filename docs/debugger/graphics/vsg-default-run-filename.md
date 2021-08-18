---
description: Grafik günlüğü dosyasının varsayılan dosya adını tanımlar.
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ae91dc2022c1d2a56699610e8a676f9d5dcc8987
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030821"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Grafik günlüğü dosyasının varsayılan dosya adını tanımlar.

## <a name="syntax"></a>Sözdizimi

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametreler
 `filename` Grafik bilgileri program aracılığıyla yakalanırken varsayılan olarak grafik günlük dosyasına verilen dosya adı.

## <a name="value"></a>Değer
 Grafik günlüğü dosyasının dosya adını temsil eden bir dize değişmez değeri. Varsayılan olarak, L"default.vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Açıklamalar
 Önişlemci simgesi tanımlanmışsa, dosya adı yakalanan uygulamanın geçerli diziniyle görelidir veya mutlak bir yoldur; aksi takdirde, kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol `DONT_SAVE_VSGLOG_TO_TEMP` değildir.

 Tanımlanan dosya adını değiştirmek için programınıza dahilmeden önce dosyayı yeniden `vsgcapture.h` tanımlamanız gerekir.

## <a name="example"></a>Örnek
 Bu örnekte, yakalama dosyasının varsayılan dosya adını nasıl değiştiryebilirsiniz:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Ayrıca bkz.
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
