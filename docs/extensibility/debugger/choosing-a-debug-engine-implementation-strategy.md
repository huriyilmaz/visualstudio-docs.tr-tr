---
title: Hata Ayıklama Motoru Uygulama Stratejisi Nin Seçilmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739134"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Hata ayıklama motoru uygulama stratejisi ni seçin
Hata ayıklama altyapınızı (DE) uygulama stratejinizi belirlemek için çalışma zamanı mimarisini kullanın. Hata ayıklama altyapısını hata ayıklama programı için işlem içinde oluşturabilirsiniz. İşlem hata ayıklama altyapısını Visual Studio oturum hata ayıklama yöneticisine (SDM) oluşturun. Veya, her ikisi için de işlem dışı hata ayıklama motoru oluşturun. Aşağıdaki yönergeler, bu üç strateji arasından seçim yapmanızı sağlar.

## <a name="guidelines"></a>Yönergeler
 DE'nin hem SDM hem de hata ayıklama programını işlemedışı olması mümkün olsa da, genellikle bunu yapmak için bir neden yoktur. İşlem sınırları nın ötesindeki aramalar nispeten yavaş.

 Hata ayıklama motorları zaten Win32 yerel çalışma zamanı ortamı ve ortak dil çalışma zamanı ortamı için sağlanmaktadır. Her iki ortam için de değiştirmeniz gerekiyorsa, DE in-process'i SDM ile oluşturmanız gerekir.

 Aksi takdirde, Hata ayıklama programı için SDM'ye de proses veya işlem de oluşturursunuz. DE ifade değerlendiricisi program sembol deposuna sık sık erişim gerektirip gerektirdiğini göz önünde bulundurmanız gerekir. Veya, sembol deposu hızlı erişim için belleğe yüklenebilir. Ayrıca, aşağıdaki yaklaşımları göz önünde bulundurun:

- İfade değerlendiricisi ile sembol deposu arasında çok fazla çağrı yoksa veya sembol deposu SDM bellek alanına okunabiliyorsa, SDM'ye DE in-process'i oluşturun. Hata ayıklama altyapısının CLSID'sini programınıza bağlandığında SDM'ye döndürmeniz gerekir. SDM, DE'nin işlem içi bir örneğini oluşturmak için bu CLSID'yi kullanır.

- De sembol deposuna erişmek için programı aramak gerekiyorsa, program ile DE in-process oluşturun. Bu durumda, program DE örneğini oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio hata ayıklama genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
