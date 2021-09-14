---
description: Yönetilen kod genel türü için bir parametreyi temsil eder.
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6960983be5b71162f95a0fcbd5a3152ee4c7362d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725189"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Yönetilen kod genel türü için bir parametreyi temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Genel tür desteği için kullanılır.

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminde yöntemlerine ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Bu genel parametreyle ilişkili kısıtlamaların sayısını döndürür.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Bu genel parametreyle ilişkili kısıtlamaları alın.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Bu genel parametre için bayrakları alın.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Bu genel parametrenin dizinini alan.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Bu genel parametrenin adını alan.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Bu genel parametrenin türünü veya yöntem sahibini alın.|

## <a name="requirements"></a>Gereksinimler
 Üst Bilgi: Sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
