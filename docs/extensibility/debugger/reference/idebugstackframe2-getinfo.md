---
description: Yığın çerçevesinin açıklamasını alır.
title: IDebugStackFrame2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d03223e4571a6792dacf0de413a4caaced08ba3c7c53266dfbe004f5434bbfc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448942"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Yığın çerçevesinin açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parametreler
`dwFieldSpec`\
[in] Parametrenin hangi [alanlarının doldurulacaklarını](../../../extensibility/debugger/reference/frameinfo-flags.md) belirten FRAMEINFO_FLAGS `pFrameInfo` bayrağının bir birleşimi.

`nRadix`\
[in] Herhangi bir sayısal bilgiyi biçimlendirmek için kullanılacak radyan.

`pFrameInfo`\
[out] Yığın çerçevesinin açıklamasıyla doldurulmuş bir [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
