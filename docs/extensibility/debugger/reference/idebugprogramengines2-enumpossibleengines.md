---
title: 'IDebugProgramEngines2:: Trmpossıbleengines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45916edbef4368c58f83426d6c73f3c692236cb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722437"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Bu programın hatalarını ayıklayabilmesini sağlayan tüm olası hata ayıklama altyapısının (DE) GUID 'Lerini döndürür.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parametreler
`celtBuffer`\
'ndaki Döndürülecek GUID 'lerin sayısı. Bu ayrıca dizinin en büyük boyutunu belirtir `rgguidEngines` .

`rgguidEngines`\
[in, out] Doldurulacak GUID 'lerin bir dizisi.

`pceltEngines`\
dışı Döndürülen GUID 'lerin gerçek sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Arabellek yeterince büyük değilse [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` veya [C#] 0x8007007A döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaç motor olduğunu belirlemek için, `celtBuffer` parametresi 0 olarak ayarlanmış ve `rgguidEngines` parametresi null bir değere ayarlanmış bir kez bu yöntemi çağırın. Bu `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` , (C# için 0x8007007A) öğesini döndürür ve `pceltEngines` parametresi, arabelleğin gerekli boyutunu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
