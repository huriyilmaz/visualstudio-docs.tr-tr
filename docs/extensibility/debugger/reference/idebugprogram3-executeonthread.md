---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722654"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Hata ayıklayıcı programını yürütür. İş parçacığı, Kullanıcı tarafından program yürütürken hangi iş parçacığının görüntülemekte olduğunu hata ayıklayıcı bilgilerini vermek üzere döndürülür.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametreler
`pThread`\
'ndaki Bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklayıcının çalışmayı durdurduktan sonra sürdürüleceği üç farklı yol vardır:

- Yürüt: önceki adımları Iptal edin ve sonraki kesme noktasına kadar çalıştırın.

- Adım: herhangi bir eski adımı Iptal edin ve yeni adım tamamlanana kadar çalıştırın.

- Devam: tekrar çalıştırın ve eski bir adımı etkin bırakın.

  Öğesine geçirilen iş parçacığı, `ExecuteOnThread` hangi adımın iptal edildiğini saptarken yararlı olur. İş parçacığını bilinmediğinizde yürütme çalıştırıldığında tüm adımlar iptal edilir. İş parçacığı hakkında bilgi sahibi olarak yalnızca etkin iş parçacığında adımı iptal etmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
