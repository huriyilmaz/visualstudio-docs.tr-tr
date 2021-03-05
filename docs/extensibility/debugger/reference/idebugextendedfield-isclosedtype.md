---
description: Alanın kapalı bir türü temsil edip etmediğini belirler.
title: 'Idebugextendedfield:: ısclosedtype | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f13fa0f143ac6adb8fb3493621b7ef638a394ca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152123"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Alanın kapalı bir türü temsil edip etmediğini belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Dönüş Değeri
 Alan kapalı bir tür ise, öğesini döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
