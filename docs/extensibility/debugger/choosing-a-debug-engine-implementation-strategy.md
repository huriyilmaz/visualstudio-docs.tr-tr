---
title: Hata Ayıklama Altyapısı Uygulama Stratejisi | Microsoft Docs
description: Çalışma zamanı mimarisinin, hata ayıklama altyapısı uygulaması için çeşitli stratejiler arasında seçim seçmenize nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 22077acd9e669f82d274a11a2b983c01afd1f746
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111794"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Hata ayıklama altyapısı uygulama stratejisi seçme
Hata ayıklama altyapısı (DE) uygulama stratejinizi belirlemek için çalışma zamanı mimarisini kullanın. Hata ayıklama sırasında hata ayıklama altyapısını hata ayıklamakta olduğu programda oluşturabilirsiniz. Oturum hata ayıklama yöneticisine (SDM) Visual Studio hata ayıklama altyapısını oluşturun. Veya her ikisinde de işlem dışı hata ayıklama altyapısını oluşturun. Aşağıdaki yönergeler bu üç stratejiden birini seçmenize yardımcı olmalıdır.

## <a name="guidelines"></a>Yönergeler
 DE'nin hem SDM'de hem de hata ayıklarken programda işlem dışı olması mümkünken, bunu yapmak için genellikle bir neden yoktur. İşlem sınırları genelinde çağrılar görece yavaştır.

 Hata ayıklama altyapıları Win32 yerel çalışma zamanı ortamı ve ortak dil çalışma zamanı ortamı için zaten sağlanmıştır. Her iki ortam için de'i değiştirmeniz gerekirse, SDM ile işlem içinde DE oluşturmanız gerekir.

 Aksi takdirde, SDM'de işlem içinde DE'i veya hata ayıklamakta olduğu program için işlem içinde oluşturun. DE'nin ifade değerlendiricisi program sembol deposuna sık erişim gerektiriyorsa göz önünde bulundurabilirsiniz. Veya sembol deposu hızlı erişim için belleğe yüklenebilirse. Ayrıca aşağıdaki yaklaşımları da göz önünde bulundurarak:

- İfade değerlendiricisi ile sembol deposu arasında çok fazla çağrı yoksa veya sembol deposu SDM bellek alanı içine okunabilirse, SDM'ye işlem içinde DE oluşturun. Hata ayıklama altyapısının CLSID'lerini, programınıza ekli olduğunda SDM'ye geri dönmeniz gerekir. SDM, DE'nin işlem içinde bir örneğini oluşturmak için bu CLSID'i kullanır.

- DE'nin sembol deposuna erişmek için programı çağırması gerekirse, programla birlikte işlem sırasında DE'i oluşturun. Bu durumda, program DE örneğini oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
