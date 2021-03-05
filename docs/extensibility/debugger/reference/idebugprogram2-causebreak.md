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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef10a714b6e65b40edb83cb0547ae1a28720d328
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166040"
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
