---
description: Bir kesme noktası başarısız çözümlemesi hakkında alınacak bilgileri belirtir.
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34a12b0e86b5805e97a563374506962618bf7853
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635185"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Bir kesme noktası başarısız çözümlemesi hakkında alınacak bilgileri belirtir.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Alanlar
`PERESI_BPRESLOCATION`\
Kaynak yapısının `bpResLocation` (kesme noktası çözümleme konumu) alanını [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) kullanın.

`BPERESI_PROGRAM`\
Yapı alanını `pProgram` `BP_ERROR_RESOLUTION_INFO` başlatma/kullanma.

`BPERESI_THREAD`\
Yapı alanını `pThread` `BP_ERROR_RESOLUTION_INFO` başlatma/kullanma.

`BPERESI_MESSAGE`\
Yapı alanını `bstrMessage` `BP_ERROR_RESOLUTION_INFO` başlatma/kullanma.

`BPERESI_TYPE`\
Yapının `dwType` (kesme noktası türü) alanını `BP_ERROR_RESOLUTION_INFO` başlat/kullan.

`BPERESI_ALLFIELDS`\
Yapının tüm alanlarını `BP_ERROR_RESOLUTION_INFO` başlat/kullan.

## <a name="remarks"></a>Açıklamalar
İlke yapısının hangi alanlarının başlat olacağını belirtmek için [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) parametresi olarak geçirildi.

Bu değerler, yapıda hangi alanların kullandır ve `BP_ERROR_RESOLUTION_INFO` yapı döndürülürken geçerli olduğunu belirtmek için de kullanılır.

Bu değerler bitwise ile birleştirilmiş `OR` olabilir.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.h

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
