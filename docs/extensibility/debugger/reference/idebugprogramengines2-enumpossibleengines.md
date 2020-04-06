---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722437"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Bu programı hata ayıklama olabilecek tüm olası hata ayıklama motorları (DE) için GUID'leri döndürür.

## <a name="syntax"></a>Sözdizimi

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
[içinde] İade edilebilen DE GUID sayısı. Bu da `rgguidEngines` dizinin en büyük boyutunu belirtir.

`rgguidEngines`\
[içinde, dışarı] Doldurulması gereken bir dizi DE GUIDs.

`pceltEngines`\
[çıkış] Döndürülen DE GUI'lerin gerçek sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür. Arabellek yeterince `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` büyük değilse [C++] veya [C#] 0x8007007A döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaç motor olduğunu belirlemek için, `celtBuffer` parametre 0 ve `rgguidEngines` null değeri ne ayarlanmış parametre ile bir kez bu yöntemi arayın. Bu `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` döndürür (C#için 0x8007007A) ve `pceltEngines` parametre arabelleğe gerekli boyutu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
