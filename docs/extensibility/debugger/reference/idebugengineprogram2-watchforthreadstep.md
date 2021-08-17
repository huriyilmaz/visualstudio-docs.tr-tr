---
description: Verilen iş parçacığında yürütmeyi izler (veya yürütmeyi izlemeyi durdurur).
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6acb6dfe32adba3dccd30e38e2bb3b18d4dc5d2c190a966c05beb34df7395a3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390001"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Verilen iş parçacığında yürütmeyi izler (veya yürütmeyi izlemeyi durdurur).

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
[in] Basan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
[in] İz eklenecek iş parçacığının tanımlayıcısını belirtir.

`fWatch`\
[in] Sıfır olmayan ( ), tarafından tanımlanan iş parçacığında yürütmeyi izlemeye başlama anlamına gelir; aksi takdirde sıfır ( ) üzerinde yürütmeyi `TRUE` `dwTid` izlemeyi durdurma anlamına `FALSE` `dwTid` gelir.

`dwFrame`\
[in] Adım türünü kontrol eden bir çerçeve dizini belirtir. Bu değer sıfır olduğunda (0), adım türü "adım içine" olur ve yürütülürken tanımlanan iş parçacığı her zaman program `dwTid` dursa. Sıfır dışında olduğunda, adım türü "adım at" olur ve yalnızca tarafından tanımlanan iş parçacığı, dizini yığında değerine eşit veya daha yüksek olan bir çerçevede çalışıyorsa `dwFrame` program `dwTid` `dwFrame` duracak.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi (SDM) parametresiyle tanımlanan bir programı adımlatırsa, bu yöntemi çağırarak diğer tüm ekli `pOriginatingProgram` programları bilgili olarak bilgi sağlar.

 Bu yöntem yalnızca aynı iş parçacığı adımlama için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
