---
title: IDebugProcess2::EnumThreads | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724062"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
İşlemde çalışan tüm iş parçacıklarının listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
[çıkış] İşlemdeki tüm programlardaki tüm iş parçacıklarının listesini içeren bir [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, her programda çalışan iş parçacıklarını sayısalhale getirir ve bunları iş parçacıklarının işlem görünümünde birleştirir. Tek bir iş parçacığı birden çok programda çalışabilir; bu yöntem bu iş parçacığını yalnızca bir kez omlekarşılar.

 Bu yöntem, yinelemeleri olmayan işlemin iş parçacıklarının bir listesini sunar. Aksi takdirde, belirli bir programda çalışan iş parçacığı sayısala, [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
