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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed068e3f0a5e1a595b9f93fec5d19de8b30690fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126727024"
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
