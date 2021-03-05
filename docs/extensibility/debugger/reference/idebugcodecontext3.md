---
description: Modül ve işlem arabirimlerinin alınmasını sağlamak için IDebugCodeContext2 arabirimini genişletir.
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db806a4b45e855533e4ded1419f2d2117fb4f912
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164025"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Modül ve işlem arabirimlerinin alınmasını sağlamak için [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimini genişletir.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama motorları tarafından uygulanır ve [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata ayıklama paketi tarafından kullanılır.

## <a name="methods"></a>Yöntemler
 Bu arabirim, arabirimindeki yöntemlere ek olarak `IDebugCodeContext2` aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Hata ayıklama modülünün arabirimine bir başvuru alır.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Hata ayıklama işleminin arabirimine bir başvuru alır.|

## <a name="remarks"></a>Açıklamalar
 Bu, genellikle uygulanması gereken isteğe bağlı bir arabirimdir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
