---
title: Programlar | Microsoft Dokümanlar
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
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738200"
---
# <a name="programs"></a>Programlar
Hata ayıklama mimarisinde, bir *program:*

- Hem bir dizi iş parçacığı hem de bir modül kümesi için bir kapsayıcıdır. Bir programın Windows işletim sisteminde tek bir benzetme yoktur.

     Program bir tür alt işlemdir. Örneğin, bir Web sitesini hata ayıklarken, bir komut dosyası program olarak görülebilir. Komut dosyası, diğer komut dosyalarından bağımsız olarak komut dosyası altyapısı işleminde çalışırken, kendi iş parçacıkları kümesi de vardır. Hata ayıklama altyapısı (DE) bir programa bağlanır, bir işleme veya iş parçacığına iliştirmez.

- Kendini ve içinde yürüttüğü süreci tanımlayabilir. Bir programa eklenebilir, ayrılabilir ve varsa onu oluşturan DE'yi açıklayabilir. Bir program yürütülebilir, durdurabilir, devam edebilir ve sonlandırılabilir.

- Tüm iş parçacığı sayısalatabilir. Bir program kendi sökme akışını da sağlayabilir ve belirli bir belge konumunun tüm kod bağlamlarını sayısalatabilir.

- Program eklenmeden önce oluşturulan veya uygulamaya bağlı olarak ekleme işleminin bir parçası olarak oluşturulan bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi tarafından temsil edilir. Bir bağlantı noktası bir işlemin programlarını sıraladığında, her program [AddProgramNode'ye](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)bağımsız değişken olarak geçirilen karşılık gelen Bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimine uygun olarak oluşturulur. Hata ayıklama motorları `IDebugProgram2` da programları temsil edecek arabirimler oluştururken, bu programlar bir program düğümüne uygun olarak oluşturulmaz. Bir `IDebugProgramNode2` DE tarafından oluşturulan arabirimler gerçek hata ayıklama için kullanılırken, bir bağlantı noktası tarafından oluşturulanlar yalnızca bir işlemde hangi programların çalıştığını keşfetmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Süreç](../../extensibility/debugger/processes.md)
- [Program düğümleri](../../extensibility/debugger/program-nodes.md)
- [Modüller](../../extensibility/debugger/modules.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [Belge konumu](../../extensibility/debugger/document-position.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
