---
title: Programlar | Microsoft Docs
description: Bu makalede, Visual Studio'da hata ayıklayıcı mimarisinde bir programın tanımı ve rolü Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0fcbd1d6ac01d4d67ad03193c1fa2b2e75ded6d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160341"
---
# <a name="programs"></a>Programlar
Hata ayıklayıcısı mimarisinde bir *program:*

- Hem bir dizi iş parçacığı hem de modül kümesi için bir kapsayıcıdır. Bir programın işletim sisteminde tek bir Windows yoktur.

     Program bir tür alt işlemdir. Örneğin, bir Web sitesinde hata ayıklarken betik bir program olarak görülebilir. Betik, diğer betiklerden bağımsız olarak betik altyapısı sürecinde çalışırken kendi iş parçacığı kümesine de sahip olur. Hata ayıklama altyapısı (DE), bir işleme veya iş parçacığına değil bir programa iliştirer.

- Kendisini ve içinde çalıştır olduğu işlemi tanımlayabilir. Bir program ekli olabilir, programdan ayrılabilir ve varsa onu oluşturan DE'i açıklar. Bir program ayrıca yürütülür, durdurabilir, devam eder ve sonlandırılır.

- Tüm iş parçacıklarını numaralarına numara olarak yer ve olabilir. Program ayrıca kendi ayrık akışını da sağlar ve verilen belge konumunun tüm kod bağlamlarını numaralandırabilir.

- Uygulamaya bağlı olarak, program ekli olmadan önce veya ekleme işleminin bir parçası olarak oluşturulan [bir IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimiyle temsil edilen. Bir bağlantı noktası bir işlem programlarını numaralandırıyorsa, her program [AddProgramNode'a](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)bağımsız değişken olarak geçirilen karşılık gelen [bir IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimine uygun olarak oluşturulur. Hata ayıklama altyapıları programları temsil eden arabirimler de oluştursa da, bu programlar bir program `IDebugProgram2` düğümüne uygun olarak oluşturulmaz. DE tarafından oluşturulan arabirimler gerçek hata ayıklama için kullanılırken, bağlantı noktası tarafından oluşturulan arabirimler yalnızca bir işlemde çalışan programları `IDebugProgramNode2` bulmak için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [İşlemler](../../extensibility/debugger/processes.md)
- [Program düğümleri](../../extensibility/debugger/program-nodes.md)
- [Modül](../../extensibility/debugger/modules.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Belge konumu](../../extensibility/debugger/document-position.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
