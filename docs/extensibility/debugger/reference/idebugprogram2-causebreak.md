---
title: IDebugProgram2::CauseBreak | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e96db32d7ba5a01f89530623c949500a265cdb60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723104"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
İş iş parçacığıbir sonraki çalışma çalıştığında programın yürütmeyi durdurmasını ister.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Program sonraki bu yöntemden sonra kod çalıştırmak için çalışır çağrıldığında bir [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) olay gönderilir.

 Bu yöntem, yöntemmutlaka programın durdurmak için beklemeden hemen döner olduğu asynchronous olduğunu.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
