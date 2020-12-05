---
title: Program denetimi | Microsoft Docs
description: Visual Studio hata ayıklamada, iş parçacıklarını yürütme, Adımlama, devam ettirme ve askıya alma/sürdürme gibi program düzeyinde oluşan yordamlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 640b09620022d17fd6b7c8758f1dec4f9a3936eb
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606534"
---
# <a name="program-control"></a>Program denetimi
Visual Studio Hata ayıklamasında, aşağıdaki Adımlama ve devam etme yordamlarının hepsi program düzeyinde oluşur:

- Sonraki ifadeyi ayarlama, diğer bir deyişle, bilgisayarınızı belirli bir çerçeve ortamında yürütülecek sonraki yönergeye ayarlama

- Yürütme, diğer bir deyişle, Adımlama modundan çıkmadan devam ediyor

- Sonraki yönergeye adımla

- Geçerli Adımlama moduna devam etme

- Programın içerdiği iş parçacıklarını askıya alma

- Programın içerdiği iş parçacıklarını sürdürme

> [!NOTE]
> Çağrı yığınını görüntülemek iş parçacığı düzeyinde uygulanır. Bir iş parçacığının çağrı yığınını görüntülerken çerçeve bilgilerini numaralandırmak için, [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabiriminin tüm yöntemlerini uygulamanız gerekir.

## <a name="methods-of-program-control"></a>Program denetimi yöntemleri
 Aşağıdaki tabloda, en düşük düzeyde işlevsel hata ayıklama altyapısı (DE) ve yürütme denetimi için uygulanması gereken [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bir programın içerdiği tüm iş parçacıklarını durdurulmuş bir durumdan çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bir programın içerdiği tüm iş parçacıklarını durdurulmuş bir durumdan çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Verilen iş parçacığında bir adım gerçekleştirir. Programın içerdiği tüm diğer iş parçacıklarını çalıştırmaya devam eder. Yürütme denetimi için gereklidir.|

 Çok iş parçacıklı programlar için, [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini ve [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) arabiriminin tüm yöntemlerini de uygulamalısınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
