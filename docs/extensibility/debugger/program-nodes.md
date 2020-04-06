---
title: Program Düğümleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738224"
---
# <a name="program-nodes"></a>Program düğümleri
Hata ayıklama mimarisinde, bir *program düğümü:*

- Bir programın hafif bir açıklamasıdır.

- Kendini ve içinde yürüttüğü süreci tanımlayabilir. Bir program düğümüne eklenebilir, ayrılabilir ve varsa onu oluşturan hata ayıklama altyapısı (DE) açıklanabilir.

- Genellikle bir DE veya bağlantı noktası tarafından oluşturulan bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi tarafından temsil edilir. Program düğümleri [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)çağırarak bir bağlantı noktasına eklenir. Bir bağlantı noktasına bir program düğümü eklendiğinde, bu program düğümünün temsil ettiği programı içeren işleme eklenir.

  Hata ayıklama oturumu başladıktan sonra, hata ayıklama paketinin uygulanmasına bağlı olarak, program düğümleri ilgili programlar oluşturmak için kullanılır. Bir işlem programları için sorgulandığında, programlar numaralandırılır, her program düğümü için bir tane.

  Bir programa bağlanmadan önce, IDE'nin programın yalnızca hafif bir açıklamasına ihtiyacı vardır. Bu bilgiler program düğümünden elde edilebilir. Program bağlandıktan sonra, IDE programda çalışan tüm iş parçacıklarının listesi gibi daha ayrıntılı bilgiler görüntüler. Bu bilgiler programın kendisinden elde edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Süreç](../../extensibility/debugger/processes.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
