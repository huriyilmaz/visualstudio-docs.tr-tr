---
title: Programlar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153638"
---
# <a name="programs"></a>Programlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından, bir **Program**:  
  
- , Bir dizi iş parçacığı ve bir modül kümesi için bir kapsayıcıdır. Windows işletim sisteminde bir programın tek bir benzerleme vurguladı yok.  
  
     Program bir tür alt işlem. Örneğin, bir Web sitesinde hata ayıklarken, bir komut dosyası program olarak görülebilir. Betik altyapısı işleminde, diğer betiklerin bağımsız olarak çalışırken, kendi iş parçacığı kümesine de sahiptir. Hata ayıklama altyapısı (DE) bir işleme veya bir iş parçacığına değil, bir programa iliştirir.  
  
- Kendisini ve üzerinde çalıştığı işlemi tanımlayabilir, öğesine eklenebilir, öğesinden ayrılabilir, ve varsa onu oluşturan DE tanımlayabilir. Bir program yürütebilir, durdurabilir, devam edebilir ve sonlandırılabilir.  
  
- Tüm iş parçacıklarını numaralandırabilirler. Ayrıca, bir program kendi ayrıştırma akışını da sağlayabilir ve belirli bir belge konumunun tüm kod bağlamlarını numaralandırabilirler.  
  
- , Uygulamaya bağlı olarak, program iliştirilmeye veya iliştirme sürecinin bir parçası olarak oluşturulan bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi tarafından temsil edilir. Bir bağlantı noktası bir işlemin programlarını Numaralandırdığınızda, her program [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)'a bağımsız değişken olarak geçirilen karşılık gelen bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimine uygun olarak oluşturulur. Hata ayıklama motorları `IDebugProgram2` programları temsil eden arabirimler de oluştururken, bu programlar bir program düğümüne uygun olarak oluşturulmaz. `IDebugProgramNode2`Bır de tarafından oluşturulan arabirimler gerçek hata ayıklama için kullanılır, ancak bir bağlantı noktası tarafından oluşturulan bir işlem, yalnızca bir işlemde çalışan programları bulmak için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lerse](../../extensibility/debugger/processes.md)   
 [Program düğümleri](../../extensibility/debugger/program-nodes.md)   
 [Modüler](../../extensibility/debugger/modules.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [Belge konumu](../../extensibility/debugger/document-position.md)   
 [Kod bağlamı](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
