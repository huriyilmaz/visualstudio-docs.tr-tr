---
description: Kaynak belgedeki işlevin konumunu alır.
title: 'IDebugFunctionPosition2:: GetOffset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetOffset
helpviewer_keywords:
- IDebugFunctionPosition2::GetOffset
ms.assetid: 60943782-aec7-4be2-b222-1984ed53a543
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c21f2f69a8995d3b1467c4a77d1b782894b8f325947877bc1b34014770ab6074
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121451959"
---
# <a name="idebugfunctionposition2getoffset"></a>IDebugFunctionPosition2::GetOffset
Kaynak belgedeki işlevin konumunu alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetOffset( 
   TEXT_POSITION* pPosition
);
```

```csharp
int GetOffset(
   TEXT_POSITION[] pPosition
);
```

## <a name="parameters"></a>Parametreler
`pPosition`\
[in, out] Bir belgedeki işlevin konumuyla doldurulmuş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
