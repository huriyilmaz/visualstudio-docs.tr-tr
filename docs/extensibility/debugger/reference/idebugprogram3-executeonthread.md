---
description: Hata ayıklayıcı programını yürütür.
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0e903431dbdcc4853d205ea6107ca6e70b91647
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126524"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Hata ayıklayıcı programını yürütür. İş parçacığı, hata ayıklayıcıya, kullanıcının programı yürütürken hangi iş parçacığını görüntülemektedir hakkında bilgi vermek için döndürülür.

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
[in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklayıcının durdurulduktan sonra yürütmeyi sürdürmesi için üç farklı yol vardır:

- Yürüt: Önceki herhangi bir adımı iptal edin ve sonraki kesme noktası kadar çalıştırın ve bu şekilde devam edin.

- Adım: Eski bir adımı iptal edin ve yeni adım tamamlayana kadar çalıştırın.

- Devam et: Yeniden çalıştırın ve eski herhangi bir adımı etkin bırakın.

  'a geçirilen iş `ExecuteOnThread` parçacığı, hangi adımın iptal edileceke karar verirken yararlıdır. İş parçacığını bilmiyorsanız, yürütme işleminin çalıştırılması tüm adımları iptal eder. İş parçacığı hakkında bilgi sahibi olarak yalnızca etkin iş parçacığında adımı iptal etmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
