---
title: 'IDebugEngineProgram2:: WatchForThreadStep | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8168b0813eb99f4f70c8a5d8ffbdae4f6fce2094
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892625"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Verilen iş parçacığında yürütmeyi izler (veya yürütme için izlemeyi Durdur).

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
'ndaki Bulanan programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
'ndaki İzlenecek iş parçacığının tanımlayıcısını belirtir.

`fWatch`\
'ndaki Sıfır olmayan ( `TRUE` ), tarafından tanımlanan iş parçacığında yürütme için izlemeye başlayan anlamına gelir `dwTid` ; Aksi takdirde, sıfır ( `FALSE` ), üzerinde yürütme İzlemeyi Durdur anlamına gelir `dwTid` .

`dwFrame`\
'ndaki Adım türünü denetleyen bir çerçeve dizini belirtir. Bu değer sıfır (0) olduğunda, adım türü "adımla" ve program her iş parçacığının yürütüldüğü her seferinde durdurulmalıdır `dwTid` . `dwFrame`Sıfır dışında bir adım türü "adımla" olur ve program yalnızca tarafından tanımlanan iş parçacığı, `dwTid` dizini yığına eşit veya daha yüksek olan bir çerçevede çalışıyorsa durmalıdır `dwFrame` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama Yöneticisi (SDM), parametre tarafından tanımlanan bir programın yaptığı adımlarda, `pOriginatingProgram` Bu yöntemi çağırarak diğer tüm ekli programları bilgilendirir.

 Bu yöntem yalnızca aynı iş parçacığı adımlaması için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
