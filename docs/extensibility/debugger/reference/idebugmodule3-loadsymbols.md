---
description: Geçerli modülün sembollerini yükler.
title: 'IDebugModule3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0612be8ffdde8a942331a89e08298f71414a4c76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164831"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Geçerli modülün sembollerini yükler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Dönüş Değeri
 Yöntem başarılı olursa, döndürür `S_OK` . Başarısız olursa, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, geçerli arama yolundan sembolleri yükler ( [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) yöntemi çağırarak değiştirilebilir).

 Bu yöntem [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) yöntemi üzerinden tercih edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
