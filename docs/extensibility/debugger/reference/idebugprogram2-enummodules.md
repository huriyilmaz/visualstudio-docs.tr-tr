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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c2d24fefab1e948c636f30ed4d7764a5ab83cc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126628"
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
