---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 835e2cec19e36418091e094abd2ec76bd6403398
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734838"
---
# <a name="vsg_default_run_filename"></a>VSG_DEFAULT_RUN_FILENAME
Grafik günlük dosyasının varsayılan dosya adını tanımlar.

## <a name="syntax"></a>Sözdizimi

```C++
#define VSG_DEFAULT_FILENAME filename
```

#### <a name="parameters"></a>Parametreler
 grafik bilgileri programlı olarak yakalanarak grafik günlüğü dosyasına varsayılan olarak verilen dosya adını `filename`.

## <a name="value"></a>Değer
 Grafik günlük dosyasının dosya adını temsil eden bir dize sabit değeri. Varsayılan olarak, L "default. vsglog".

```C++
#define VSG_DEFAULT_FILENAME L"default.vsglog"
```

## <a name="remarks"></a>Açıklamalar
 Önişlemci sembol `DONT_SAVE_VSGLOG_TO_TEMP` tanımlanmışsa, dosya adı yakalanan uygulamanın geçerli dizinine göre değişir veya mutlak bir yoldur; Aksi takdirde, kullanıcının geçici dosyalar dizinine göredir ve mutlak bir yol olamaz.

 Tanımlı dosya adını değiştirmek için, programınıza `vsgcapture.h` dahil etmeden önce onu yeniden tanımlamanız gerekir.

## <a name="example"></a>Örnek
 Bu örnek, yakalama dosyasının varsayılan dosya adının nasıl değiştirileceğini gösterir:

```C++
// Redefine the default capture filename before including vsgcapture.h
#define VSG_DEFAULT_FILENAME L"capture.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>Ayrıca bkz.
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)