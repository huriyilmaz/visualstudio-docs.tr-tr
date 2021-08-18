---
description: Bu programda hata ayıklaması başlatan tüm olası hata ayıklama altyapıları (DE) için GUID'leri döndürür.
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3bbcd034c2d0a9cd6314281a6bdd47e24983b5e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132619"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Bu programda hata ayıklaması başlatan tüm olası hata ayıklama altyapıları (DE) için GUID'leri döndürür.

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
[in] İade etmek için DE GUID sayısı. Bu, dizinin en büyük boyutunu `rgguidEngines` da belirtir.

`rgguidEngines`\
[in, out] Doldurulması gereken DE GUID'leri dizisi.

`pceltEngines`\
[out] Döndürülen GERÇEK DE GUID sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. Arabellek yeterince büyük `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` 0x8007007A [C++] veya [C#] hatasını döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaç altyapı olduğunu belirlemek için, parametresi 0 olarak ayarlanmış ve parametre null değere ayarlanmış şekilde bu `celtBuffer` `rgguidEngines` yöntemi bir kez çağır. Bu değer `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A C# için `pceltEngines` geçerli olur) ve parametresi arabellek için gerekli boyutu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
