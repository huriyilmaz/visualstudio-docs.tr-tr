---
description: Bu programın yüklediği ve yürütüldüğü modüllerin listesini alır.
title: 'IDebugProgram2:: EnumModules | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26016510856de44c07ca9a123553e82d0d2a79f4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149632"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
Bu programın yüklediği ve yürütüldüğü modüllerin listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Modüllerin listesini içeren bir [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Modül bir DLL veya derlemedir ve genellikle **modüller** hata ayıklama penceresinde listelenir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
