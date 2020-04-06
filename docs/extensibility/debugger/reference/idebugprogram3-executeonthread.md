---
title: IDebugProgram3::ExecuteOnThread | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722654"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Hata ayıklama programını yürütür. İş parçacığı, kullanıcının programı yürüdürken görüntülediği iş parçacığı hakkında hata ayıklama bilgileri vermek için döndürülür.

## <a name="syntax"></a>Sözdizimi

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
[içinde] Bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklamanın durdurulduktan sonra yürütmeye devam edilebebileceği üç farklı yol vardır:

- Yürütme: Önceki herhangi bir adımı iptal edin ve bir sonraki kesme noktasına kadar çalıştırın ve benzeri.

- Adım: Herhangi bir eski adımı iptal edin ve yeni adım tamamlanana kadar çalıştırın.

- Devam et: Yeniden çalıştırın ve eski bir adımı etkin bırakın.

  Hangi adımı `ExecuteOnThread` iptal edin karar verirken geçirilen iş parçacığı yararlıdır. İş parçacığı bilmiyorsanız, çalıştırın tüm adımları iptal eder. Iş parçacığı bilgisi ile, sadece etkin iş parçacığı üzerinde adım iptal etmek gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmek](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
