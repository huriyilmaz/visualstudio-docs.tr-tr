---
description: Yığın çerçeve türünü belirtir.
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155308"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Yığın çerçeve türünü belirtir.

## <a name="syntax"></a>Syntax

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
`FrameTypeFPO` Çerçeve işaretçisi atlandı; Mi bilgileri kullanılabilir.

`FrameTypeTrap` Çekirdek Tuzak Çerçevesi.

`FrameTypeTSS` Çekirdek Tuzak Çerçevesi.

`FrameTypeStandard` Standart EBP yığın çerçevesi.

`FrameTypeFrameData` Çerçeve işaretçisi atlandı; Çerçeve veri bilgileri kullanılabilir.

`FrameTypeUnknown` Herhangi bir hata ayıklama bilgisi olmayan çerçeve.

## <a name="remarks"></a>Açıklamalar
Bu Numaralandırmadaki değerler, [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) metoduna yapılan bir çağrı tarafından döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
