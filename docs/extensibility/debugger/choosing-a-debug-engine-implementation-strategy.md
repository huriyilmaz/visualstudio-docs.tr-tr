---
title: Hata ayıklama altyapısı uygulama stratejisi seçme | Microsoft Docs
description: Çalışma zamanı mimarisinin hata ayıklama altyapısı uygulamasının çeşitli stratejileri arasından seçim yapmanıza nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2b87d61586fb4acc360b5f5202b1219199c6a24b
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914302"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Hata ayıklama altyapısı uygulama stratejisi seçin
Hata ayıklama altyapısı (DE) uygulama stratejinizi öğrenmek için çalışma zamanı mimarisini kullanın. Hata ayıklama altyapısını işlem içi hata ayıklaması yaptığınız programa oluşturabilirsiniz. Visual Studio oturumu hata ayıklama Yöneticisi (SDM) için işlem içi hata ayıklama altyapısını oluşturun. Ya da hata ayıklama altyapısını her ikisine de işlem dışı bir şekilde oluşturun. Aşağıdaki kılavuzlar bu üç strateji arasından seçim yapmanıza yardımcı olmalıdır.

## <a name="guidelines"></a>Yönergeler
 Ayrıca, hem SDM 'nin hem de hata ayıklamanın bulunduğu programın işlem dışı olması mümkün olsa da genellikle bunun için bir neden yoktur. İşlem sınırları genelinde çağrılar nispeten düşüktür.

 Win32 yerel çalışma zamanı ortamı ve ortak dil çalışma zamanı ortamı için hata ayıklama motorları zaten sağlanmış. İki ortamın DE yerine öğesini değiştirmeniz gerekiyorsa, SDM ile de işlem içi oluşturmalısınız.

 Aksi halde, hata ayıklama yaptığınız programa SDM veya işlem içi işlem içi oluştururun. Bunun DE, program sembol deposuna sık erişim gerektirip gerektirmediğini göz önünde bulundurmanız gerekir. Ya da, sembol deposu hızlı erişim için belleğe yüklenebiliyorsanız. Ayrıca, aşağıdaki yaklaşımları de göz önünde bulundurun:

- İfade değerlendiricisi ve sembol deposu arasında çok sayıda çağrı yoksa veya sembol deposu SDM bellek alanına okunıyorsa, SDM 'de DE işlem içi oluşturun. Hata ayıklama altyapısının CLSID 'sini programınıza iliştirdiğinden SDM 'ye döndürmelidir. SDM, bu CLSID 'in bir işlem içi örneğini oluşturmak için kullanır.

- Sembol deposuna erişmek için DE programı çağırmanız gerekiyorsa, programla birlikte işlem içi oluşturun. Bu durumda program, DE örneğini oluşturur.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
