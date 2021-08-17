---
title: Program Düğümleri | Microsoft Docs
description: Bu makalede, Visual Studio'de hata ayıklayıcı mimarisinde program düğümünün tanımı ve rolü Visual Studio.
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
ms.openlocfilehash: e0066f6b8ee17591620af896c753dbd9b29a5948790d024c5b505be76f34cb75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417775"
---
# <a name="program-nodes"></a>Program düğümleri
Hata ayıklayıcısı mimarisinde bir *program düğümü:*

- Bir programın basit bir açıklamasıdır.

- Kendisini ve içinde çalıştır olduğu işlemi tanımlayabilir. Bir program düğümüne bağlı olabilir, düğümden ayrılabilir ve varsa onu oluşturan hata ayıklama altyapısını (DE) açıklar.

- Genellikle DE veya bağlantı noktası [tarafından oluşturulan bir IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimiyle temsil edilen. Program [düğümleri, AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)çağrılarak bir bağlantı noktasına eklenir. Bir bağlantı noktasına program düğümü ekleniyorsa, bu program düğümünün temsil ettiği programı içeren işleme eklenir.

  Hata ayıklama oturumu başlatıldıktan bir süre sonra, hata ayıklama paketinin uygulanmasına bağlı olarak, ilgili programları oluşturmak için program düğümleri kullanılır. Bir işlem programları için sorgulanan programlar, her bir program düğümü için bir tane olacak şekilde numaralandırıldı.

  Bir program bağlanmadan önce IDE'ye programın yalnızca basit bir açıklaması gerekir. Bu bilgiler program düğümünden edinebilirsiniz. Program ekli olduktan sonra IDE, programda çalışan tüm iş parçacıklarının listesi gibi daha ayrıntılı bilgiler görüntüler. Bu bilgiler programın kendi tarafından elde edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [İşlemler](../../extensibility/debugger/processes.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
