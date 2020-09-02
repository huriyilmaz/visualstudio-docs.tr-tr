---
title: Program denetimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858630"
---
# <a name="program-control"></a>Program Denetimi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme Denetimi ve Durum Değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
