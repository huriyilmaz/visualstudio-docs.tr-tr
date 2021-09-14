---
description: Modül ve işlem arabirimlerinin alınmasını sağlamak için IDebugCodeContext2 arabirimini genişletmektedir.
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 502867256f90574c2a75791b447b76b56af3a638
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635134"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Modül ve işlem arabirimlerinin alınmasını sağlamak için [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimini genişletmektedir.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapıları tarafından uygulanır ve Hata Ayıklama [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] paketi tarafından tüketilir.

## <a name="methods"></a>Yöntemler
 Bu arabirim, arabirimde `IDebugCodeContext2` yöntemlerine ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Hata ayıklama modülünün arabirimine bir başvuru verir.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Hata ayıklama işleminin arabirimine bir başvuru verir.|

## <a name="remarks"></a>Açıklamalar
 Bu, genellikle uygulanması gereken isteğe bağlı bir arabirimdir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
