---
title: 'Nasıl kullanılır: Açık Belgeler için Düzenleyicileri Açma | Microsoft Docs'
description: Standart veya projeye özgü bir düzenleyicide dosya açmayı öğrenin. Proje bir belge penceresi açtığında dosyanın zaten açık olup olmadığını belirlemesi gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aa669bae8cd178f70ff843c309fdbdaf9ed1bed9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124951"
---
# <a name="how-to-open-editors-for-open-documents"></a>Nasıl kullanılır: Açık belgeler için düzenleyicileri açma
Proje bir belge penceresi açmadan önce, projenin önce dosyanın başka bir düzenleyici için belge penceresinde zaten açık olup olmadığını belirlemesi gerekir. Dosya, projeye özgü bir düzenleyicide veya ile kayıtlı standart düzenleyicilerden biri olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açabilirsiniz.

## <a name="open-a-project-specific-editor"></a>Projeye özgü düzenleyiciyi açma
 Zaten açık olan bir dosya için projeye özgü bir düzenleyiciyi açmak üzere aşağıdaki yordamı kullanın.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Projeye özgü bir düzenleyiciyi açık bir dosya için açmak için

1. yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> çağırma.

    Bu çağrı, uygunsa belgenin hiyerarşisine, hiyerarşi öğesine ve pencere çerçevesine işaretçiler döndürür.

2. Belge açıksa, proje yalnızca bir belge veri nesnesinin var olup olmadığını veya bir belge görünümü nesnesinin de mevcut olup olmadığını denetlemesi gerekir.

   - Bir belge görünümü nesnesi varsa ve bu görünüm farklı bir hiyerarşi veya hiyerarşi öğesi içinse proje, mevcut pencereyi yeniden ortaya değiştirmek için görünümün pencere çerçevesinin işaretçisini kullanır.

   - Bir belge görünümü nesnesi varsa ve bu görünüm aynı hiyerarşi ve hiyerarşi öğesi içinse, proje temel alınan belge veri nesnesine iliştirenin ikinci bir görünümü açabilir. Aksi takdirde proje, mevcut pencereye yeniden yüzey yapmak için görünümün pencere çerçevesinin işaretçisini kullandır.

   - Yalnızca belge veri nesnesi varsa proje, görünümü için belge veri nesnesini kullanıp kullana olmadığını belirlemeli. Belge veri nesnesi uyumlu ise, Projeye özgü bir düzenleyiciyi açma [konusunda ele alan adımları tamamlayın.](../extensibility/how-to-open-project-specific-editors.md)

     Belge veri nesnesi uyumlu değilse, kullanıcıya dosyanın şu anda kullanımda olduğunu belirten bir hata görüntüleniyor olmalıdır. Bu hata yalnızca geçici durumlarda (örneğin, kullanıcının çekirdek metin düzenleyicisi dışında bir düzenleyici kullanarak dosyayı açmaya çalıştığı sırada bir dosya derlendiğinde) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görüntüleniyor. Çekirdek metin düzenleyicisi, belge veri nesnesini derleyiciyle paylaşabilir.

3. Belge veri nesnesi veya belge görünümü nesnesi yoksa, Projeye özgü düzenleyiciyi açma [adımlarını tamamlayın.](../extensibility/how-to-open-project-specific-editors.md)

## <a name="open-a-standard-editor"></a>Standart düzenleyiciyi açma
 Zaten açık olan bir dosyanın standart düzenleyicisini açmak için aşağıdaki yordamı kullanın.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Açık bir dosya için standart düzenleyiciyi açmak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> çağrısı yapın.

     Bu yöntem öncelikle çağrısıyla belgenin açık olmadığını <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> doğrular. Belge zaten açıksa düzenleyici penceresi yeniden açılır.

2. Belge açık değilse, Nasıl ekleyebilirsiniz: Standart düzenleyicileri [açma adımlarını tamamlayın.](../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıllı: Projeye özgü düzenleyicileri açma](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl: Standart düzenleyicileri açma](../extensibility/how-to-open-standard-editors.md)
