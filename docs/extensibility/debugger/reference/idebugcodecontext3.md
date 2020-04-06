---
title: IDebugCodeContext3 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734192"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Modül ve işlem arabirimlerinin alınmasını sağlamak için [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimini genişletir.

## <a name="syntax"></a>Sözdizimi

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama motorları tarafından uygulanır [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ve Hata Ayıklama paketi tarafından tüketilir.

## <a name="methods"></a>Yöntemler
 `IDebugCodeContext2` Arabirimdeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Hata ayıklama modülünün arabirimine bir başvuru alır.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Hata ayıklama işleminin arabirimine bir başvuru alır.|

## <a name="remarks"></a>Açıklamalar
 Bu genellikle uygulanması gerekmez isteğe bağlı bir arabirimdir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
