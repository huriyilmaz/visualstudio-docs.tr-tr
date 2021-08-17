---
title: Program düğümleri | Microsoft Docs
description: Bu makalede, Visual Studio hata ayıklayıcı mimarisinde bir program düğümünün tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: da57e9379d46bfbb5194b59d91baa7a2ef342f74
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080175"
---
# <a name="program-nodes"></a>Program düğümleri
Hata ayıklayıcı mimarisinde, bir *program düğümü*:

- , Bir programın hafif bir açıklamasıdır.

- , Kendisini ve üzerinde çalıştığı işlemi tanımlayabilir. Bir program düğümü öğesine iliştirilebilir, öğesinden ayrılabilir ve varsa, onu oluşturan hata ayıklama altyapısını (DE) tanımlayabilirsiniz.

- Genellikle bir DE veya bağlantı noktası tarafından oluşturulan bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi tarafından temsil edilir. Program düğümleri, [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)çağırarak bir bağlantı noktasına eklenir. Bir bağlantı noktasına bir program düğümü eklendiğinde, bu program düğümünün temsil ettiği programı içeren işleme eklenir.

  Hata ayıklama oturumu başlatıldıktan sonra, hata ayıklama paketinin uygulamasına bağlı olarak, program düğümleri ilgili programları oluşturmak için kullanılır. Bir işlem, programları için sorgulandığında, her program düğümü için bir tane olmak üzere programlar numaralandırılır.

  Bir programın öğesine iliştirilmesi için IDE 'nin yalnızca bir basit açıklaması olması gerekir. Bu bilgiler program düğümünden elde edilebilir. Program öğesine iliştirildikten sonra IDE, programda çalışan tüm iş parçacıklarının listesi gibi daha ayrıntılı bilgiler görüntüler. Bu bilgiler programın kendisinden elde edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [İşlemler](../../extensibility/debugger/processes.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
