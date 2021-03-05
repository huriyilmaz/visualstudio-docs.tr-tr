---
description: Yönetilen kod genel türlerini desteklemek için kullanılabilir alan türlerini genişletir.
title: Idebugextendedfield | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5da66ddab0f485587ac5779187384a749459419e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152110"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
Yönetilen kod genel türlerini desteklemek için kullanılabilir alan türlerini genişletir.

## <a name="syntax"></a>Syntax

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>Yöntemler
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Belirtilen genişletilmiş alan türünü alır.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Alanın kapalı bir türü temsil edip etmediğini belirler.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
