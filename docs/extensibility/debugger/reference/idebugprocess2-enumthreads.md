---
description: İşlemde çalışan tüm iş parçacıklarının bir listesini alır.
title: 'IDebugProcess2:: EnumThreads | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ebb96bd93796b7320d5e41ef879ac723a197027
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050786"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
İşlemde çalışan tüm iş parçacıklarının bir listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı İşlemdeki tüm programlardaki tüm iş parçacıklarının listesini içeren bir [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, her bir programda çalışan iş parçacıklarını numaralandırır ve ardından bunları iş parçacıklarının işlem görünümünde birleştirir. Tek bir iş parçacığı birden çok programda çalıştırılabilir; Bu yöntem, iş parçacığını yalnızca bir kez numaralandırır.

 Bu yöntem, işlemin iş parçacıklarının bir listesini yinelemeler olmadan gösterir. Aksi takdirde, belirli bir programda çalışan iş parçacıklarını numaralandırmak için [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
