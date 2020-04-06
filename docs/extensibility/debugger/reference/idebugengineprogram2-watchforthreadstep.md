---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730349"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Verilen iş parçacığı üzerinde gerçekleşmesi için yürütme (veya yürütme için izleme durur) için saatler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parametreler
`pOriginatingProgram`\
[içinde] Adımlanan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
[içinde] İzlenecek iş parçacığının tanımlayıcısını belirtir.

`fWatch`\
[içinde] Sıfır olmayan`TRUE`( ) tarafından `dwTid`tanımlanan iş parçacığı üzerinde yürütme için izlemeye başlamak anlamına gelir; aksi takdirde,`FALSE`sıfır ( ) `dwTid`üzerinde yürütme için izlemeyi durdurmak anlamına gelir.

`dwFrame`\
[içinde] Adım türünü denetleyen bir çerçeve dizini belirtir. Bu değer sıfır (0) olduğunda, adım türü "adım" ve program iş parçacığı `dwTid` tarafından tanımlanan zaman durdurmalısınız. Sıfır `dwFrame` olmadığında, adım türü "üzerine adım" olur ve program yalnızca dizini yığında `dwTid` `dwFrame`.'a eşit veya daha yüksek olan bir çerçevede çalışan iş parçacığı ise durdurulmalıdır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi (SDM) `pOriginatingProgram` parametre tarafından tanımlanan bir program adedine girdiğinde, bu yöntemi çağırarak diğer tüm ekli programları bildirir.

 Bu yöntem yalnızca aynı iş parçacığı adımlamak için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
