---
title: İşlem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153661"
---
# <a name="processes"></a>İşlemler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından bir **işlem**:  
  
- , Bir program kümesi için bir kapsayıcıdır. Bir dizi iş parçacığı için kapsayıcı olan bir Windows işlemine yakından benzer.  
  
- Kendisini ada, tanımlayıcıya veya fiziksel tanımlayıcıya göre tanımlayabilir.  
  
- Çalışan tüm programları (ve bunların iş parçacıklarını) numaralandırabilirler.  
  
- Kendisini, üzerinde çalıştığı bağlantı noktasını ve onu içeren makineyi açıklayabilir.  
  
- Bir veya daha fazla program oluşturabilir, oluşturduğu programlardan herhangi birini sonlandırabilir veya bir programın durmasına neden olabilir.  
  
- , İşlem başlatıldığında oluşturulan bir [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) arabirimi tarafından temsil edilir. Bir işlem, oturum hata ayıklama Yöneticisi (SDM) ya da [Launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)tarafından başlatılır.  
  
  Hata ayıklama paketi, [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)'i çağırarak bir işleme hata ayıklama ALTYAPıSı (de) ekleyebilir. Diğer bir deyişle, bunun işleyebileceği işlemde çalışan tüm olası programları iliştirir anlamına gelir. Örneğin, ortak dil çalışma zamanı bir işleme DE iliştiriyorsa, yalnızca yönetilen kodu çalıştıran programlara iliştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlarınız](../../extensibility/debugger/programs.md)   
 [Akışları](../../extensibility/debugger/threads.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [Hata ayıklama paketi](../../extensibility/debugger/debug-package.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [Launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [İliştir](../../extensibility/debugger/reference/idebugprocess2-attach.md)
