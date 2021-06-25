---
title: Program Denetimi | Microsoft Docs
description: İş parçacıklarını yürütme Visual Studio adımlama, devam etme ve askıya alma/devam etme gibi program düzeyinde oluşan hata ayıklama yordamları hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900725"
---
# <a name="program-control"></a>Program denetimi
Hata Visual Studio, aşağıdaki adımlama ve devam eden yordamların hepsi program düzeyinde gerçekleşir:

- Sonraki deyimi, yani bilgisayarınızı belirli bir çerçeve ortamında yürütülecek sonraki yönergeye ayarlama

- Yürütme, yani adımlama modundan çıkmak için devam ediyor

- Sonraki yönergeye adımlama

- Geçerli adımlama moduna devam edin

- Programın içerdiği iş parçacıklarını askıya alma

- Programın içerdiği iş parçacıklarını devam ediyor

> [!NOTE]
> Çağrı yığınını görüntüleme iş parçacığı düzeyinde uygulanır. Bir iş parçacığı için çağrı yığınını görüntülerken çerçeve bilgilerini numaralandırarak [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabiriminin tüm yöntemlerini uygulamalısiniz.

## <a name="methods-of-program-control"></a>Program denetimi yöntemleri
 Aşağıdaki tabloda, en az işlevsel hata ayıklama altyapısı (DE) ve yürütme denetimi için uygulanması gereken [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) yöntemleri gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bir program tarafından bulunan tüm iş parçacıklarını durdurulmuş durumdan çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bir program tarafından bulunan tüm iş parçacıklarını durdurulmuş durumdan çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Verilen iş parçacığında bir adım gerçekleştirir. Programın içerdiği diğer tüm iş parçacıklarını çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|

 Çok iş parçacıklı programlar için [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini ve [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) arabiriminin tüm yöntemlerini de uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
