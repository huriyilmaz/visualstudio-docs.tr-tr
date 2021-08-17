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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 400a1db1f8a5ee5ffde7e00a428d83d170dc0d05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097602"
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
