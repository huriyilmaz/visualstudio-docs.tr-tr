---
description: Programdan bir hata ayıklama altyapısını ayırır.
title: IDebugProgram2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Detach
helpviewer_keywords:
- IDebugProgram2::Detach
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e9e7527ee13c703bbf7e1ba5a15ae225cf87c0b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076101"
---
# <a name="idebugprogram2detach"></a>IDebugProgram2::Detach
Programdan bir hata ayıklama altyapısını ayırır.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Ayrılmış bir program çalışmaya devam ediyor, ancak artık hata ayıklama oturumunun bir parçası değil. Hata ayıklama altyapısı ayrıldıktan sonra başka program hata ayıklama olayı gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
