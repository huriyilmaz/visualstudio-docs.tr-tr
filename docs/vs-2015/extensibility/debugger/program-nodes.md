---
title: Program düğümleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153652"
---
# <a name="program-nodes"></a>Program Düğümleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından, bir **program düğümü**:  
  
- , Bir programın hafif bir açıklamasıdır.  
  
- Kendisini ve üzerinde çalıştığı işlemi tanımlayabilir ve öğesine eklenebilir, öğesinden ayrılabilir ve varsa hata ayıklama altyapısını (DE) betimlenebilir.  
  
- Genellikle bir DE veya bağlantı noktası tarafından oluşturulan bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi tarafından temsil edilir. Program düğümleri, [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)çağırarak bir bağlantı noktasına eklenir. Bir bağlantı noktasına bir program düğümü eklendiğinde, bu program düğümünün temsil ettiği programı içeren işleme eklenir.  
  
  Hata ayıklama oturumu başlatıldıktan sonra, hata ayıklama paketinin uygulamasına bağlı olarak, program düğümleri ilgili programları oluşturmak için kullanılır. Bir işlem, programları için sorgulandığında, her program düğümü için bir tane olmak üzere programlar numaralandırılır.  
  
  Bir programın öğesine iliştirilmesi için IDE 'nin yalnızca bir basit açıklaması olması gerekir. Bu bilgiler program düğümünden elde edilebilir. Program öğesine eklendikten sonra IDE 'nin programda çalışan tüm iş parçacıklarının listesi gibi daha ayrıntılı bilgiler görüntülemesi gerekir. Bu bilgiler programın kendisinden elde edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlarınız](../../extensibility/debugger/programs.md)   
 [Lerse](../../extensibility/debugger/processes.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
