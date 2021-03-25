---
description: İş parçacıklarından birinin bir sonraki çalıştırılışında programın yürütmeyi durdurmasını ister.
title: 'IDebugProgram2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64ad2a22a06cc18595aabb37e3c244c7ea0c0be1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076166"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
İş parçacıklarından birinin bir sonraki çalıştırılışında programın yürütmeyi durdurmasını ister.

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
 Program bir sonraki kodu bu yöntemden sonra çalıştırmaya çalıştığında bir [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) olayı gönderilir.

 Bu yöntem, yönteminin programın durdurulmasını beklemeden hemen döndürdüğü zaman uyumsuzdur.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
