---
description: Yığın çerçevesi türünü belirtir.
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
ms.openlocfilehash: 383f6f5144eb9be777fc76af145d2e07a8ac1086101f44893173dd833237f79c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379644"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Yığın çerçevesi türünü belirtir.

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
`FrameTypeFPO` Çerçeve işaretçisi atlandı; FPO bilgileri kullanılabilir.

`FrameTypeTrap` Çekirdek Yakalama çerçevesi.

`FrameTypeTSS` Çekirdek Yakalama çerçevesi.

`FrameTypeStandard` Standart EBP yığın çerçevesi.

`FrameTypeFrameData` Çerçeve işaretçisi atlandı; Çerçeve verisi bilgileri kullanılabilir.

`FrameTypeUnknown` Hata ayıklama bilgisi olan çerçeve.

## <a name="remarks"></a>Açıklamalar
Bu numaralamada yer alan değerler, [IDiaStackFrame::get_type yöntemine yapılan bir çağrıyla](../../debugger/debug-interface-access/idiastackframe-get-type.md) döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst.h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
