---
title: Programlar | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir programın tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf0d3adb174e9b13cb09f9506927217326890c32
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606521"
---
# <a name="programs"></a>Programlar
Hata ayıklayıcı mimarisinde, bir *Program*:

- , Bir dizi iş parçacığı ve bir modül kümesi için bir kapsayıcıdır. Windows işletim sisteminde bir programın tek bir benzerleme vurguladı yok.

     Program bir tür alt işlem. Örneğin, bir Web sitesinde hata ayıklarken, bir komut dosyası program olarak görülebilir. Betik altyapısı işleminde, diğer betiklerin bağımsız olarak çalışırken, kendi iş parçacığı kümesine de sahiptir. Hata ayıklama altyapısı (DE) bir işleme veya bir iş parçacığına değil, bir programa iliştirir.

- , Kendisini ve üzerinde çalıştığı işlemi tanımlayabilir. Bir program öğesine iliştirilebilir, öğesinden ayrılabilir ve bu öğeyi oluşturan, varsa tanımlayabilir. Ayrıca, bir program yürütebilir, durdurabilir, devam edebilir ve sonlandırılabilir.

- Tüm iş parçacıklarını numaralandırabilirler. Ayrıca, bir program kendi ayrıştırma akışını da sağlayabilir ve belirli bir belge konumunun tüm kod bağlamlarını numaralandırabilirler.

- , Uygulamaya bağlı olarak, program iliştirilmeye veya iliştirme sürecinin bir parçası olarak oluşturulan bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi tarafından temsil edilir. Bir bağlantı noktası bir işlemin programlarını Numaralandırdığınızda, her program [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)'a bağımsız değişken olarak geçirilen karşılık gelen bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimine uygun olarak oluşturulur. Hata ayıklama motorları `IDebugProgram2` programları temsil eden arabirimler de oluştururken, bu programlar bir program düğümüne uygun olarak oluşturulmaz. `IDebugProgramNode2`Bır de tarafından oluşturulan arabirimler gerçek hata ayıklama için kullanılır, ancak bir bağlantı noktası tarafından oluşturulan bir işlem, yalnızca bir işlemde çalışan programları bulmak için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [İşlemler](../../extensibility/debugger/processes.md)
- [Program düğümleri](../../extensibility/debugger/program-nodes.md)
- [Modül](../../extensibility/debugger/modules.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Belge konumu](../../extensibility/debugger/document-position.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
