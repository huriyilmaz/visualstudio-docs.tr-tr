---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738547"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Yığın çerçeve türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Öğeler
`FrameTypeFPO` çerçeve işaretçisi atlandı; Mi bilgileri kullanılabilir.

Çekirdek tuzak çerçevesini `FrameTypeTrap`.

Çekirdek tuzak çerçevesini `FrameTypeTSS`.

Standart EBP yığın çerçevesini `FrameTypeStandard`.

`FrameTypeFrameData` çerçeve işaretçisi atlandı; Çerçeve veri bilgileri kullanılabilir.

herhangi bir hata ayıklama bilgisi olmayan `FrameTypeUnknown` çerçeve.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) yöntemi çağrısıyla döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
