---
description: Alanın kapalı bir türü temsil ettiğini belirler.
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47844555c2f900e46dd0218fe3763a877d9fa711b562b5601be8adc27a98b0a9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360371"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Alanın kapalı bir türü temsil ettiğini belirler.

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
 Alan kapalı bir türse döndürür; `S_OK` aksi takdirde `S_FALSE` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
