---
description: Bu hata ayıklama altyapısı (DE) tarafından hata ayıklamakta olan tüm programları, iş parçacıklarından birinin bir sonraki çalıştırılışında yürütmeyi durdurmak için ister.
title: 'IDebugEngine2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a320cbe9f2414de754b5844aa645bffb857568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093905"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Bu hata ayıklama altyapısı (DE) tarafından hata ayıklamakta olan tüm programları, iş parçacıklarından birinin bir sonraki çalıştırılışında yürütmeyi durdurmak için ister.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem zaman uyumsuz: program, bu yöntemden sonra bir sonraki yürütmeyi denediğinde bir [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) olayı gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
