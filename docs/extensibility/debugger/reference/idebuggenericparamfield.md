---
title: IDebugGenericParamField | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727847"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Yönetilen kod genel türü için bir parametreyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Jenerik desteği için kullanılır.

## <a name="methods"></a>Yöntemler
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Bu genel parametreyle ilişkili kısıtlamaların sayısını verir.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Bu genel parametreyle ilişkili kısıtlamaları alır.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Bu genel parametre için bayrakları alır.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Bu genel parametrenin dizinini alır.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Bu genel parametrenin adını alır.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Bu genel parametrenin türünü veya yöntem sahibini alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Ş.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
