---
description: Program yok etme bayraklarını alır.
title: 'IDebugProgramDestroyEventFlags2:: GetFlags | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugProgramDestroyEventFlags2::GetFlags
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be871d325cd63e70fb2857ee3f89f2cc854c89fc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171847"
---
# <a name="idebugprogramdestroyeventflags2getflags"></a>IDebugProgramDestroyEventFlags2::GetFlags
Program yok etme bayraklarını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetFlags(
   PROGRAM_DESTROY_FLAGS* pdwFlags
);
```

```csharp
public int GetFlags(
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags
);
```

## <a name="parameters"></a>Parametreler
`pdwFlags`\
dışı Program yok etme bayraklarını temsil eder.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)
- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)
