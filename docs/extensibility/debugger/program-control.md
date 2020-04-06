---
title: Program Kontrolü | Microsoft Dokümanlar
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
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738236"
---
# <a name="program-control"></a>Program kontrolü
Visual Studio hata ayıklama, aşağıdaki adımlama ve devam rutinleri tüm program düzeyinde oluşur:

- Bir sonraki ifadeyi ayarlama, diğer bir deyişle, bilgisayarınızı belirli bir çerçeve ortamında yürütülecek bir sonraki yönergeye ayar

- Yürütme, diğer bir süre, atlama modundan çıkmaya devam

- Bir sonraki yönergeye adım atma

- Geçerli adımlama moduna devam etme

- Programın içerdiği iş parçacıklarını askıya alma

- Programın içerdiği iş parçacıklarına devam etme

> [!NOTE]
> Arama yığınının görüntülenmesi iş parçacığı düzeyinde uygulanır. Bir iş parçacığı için çağrı yığınını görüntülerken çerçeve bilgilerini sayısallandırmak [için, IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabiriminin tüm yöntemlerini uygulamanız gerekir.

## <a name="methods-of-program-control"></a>Program kontrol yöntemleri
 Aşağıdaki tablo, en az işlevsel hata ayıklama altyapısı (DE) ve yürütme denetimi için uygulanması gereken [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) yöntemlerini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Bir program tarafından bulunan tüm iş parçacıklarını durmuş durumdan çalıştırmaya devam eder. Yürütme kontrolü için gereklidir.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Bir program tarafından bulunan tüm iş parçacıklarını durmuş durumdan çalıştırmaya devam eder. Yürütme kontrolü için gereklidir.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Verilen iş parçacığı üzerinde bir adım gerçekleştirir. Program tarafından bulunan diğer tüm iş parçacıklarını çalıştırmaya devam eder. Yürütme kontrolü için gereklidir.|

 Çok iş parçacığı lı programlar için, [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) yöntemini ve [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) arabiriminin tüm yöntemlerini de uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme kontrolü ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
