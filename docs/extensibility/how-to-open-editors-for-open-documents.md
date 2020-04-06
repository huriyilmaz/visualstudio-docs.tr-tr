---
title: 'Nasıl yapılsın: Açık Belgeler için Editörler Aç | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710924"
---
# <a name="how-to-open-editors-for-open-documents"></a>Nasıl yapilir: Açık belgeler için editörleri açın
Proje bir belge penceresini açmadan önce, projenin önce dosyanın başka bir düzenleyici için belge penceresinde zaten açık olup olmadığını belirlemesi gerekir. Dosya, projeye özgü bir düzenleyicide veya kayıtlı standart düzenleyicilerden birinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]açılabilir.

## <a name="open-a-project-specific-editor"></a>Projeye özel bir düzenleyici açma
 Zaten açık olan bir dosya için projeye özel bir düzenleyiciyi açmak için aşağıdaki yordamı kullanın.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Açık bir dosya için projeye özgü bir düzenleyici açmak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Yöntemi ara.

    Bu çağrı, uygunsa belgenin hiyerarşisi, hiyerarşi öğesi ve pencere çerçevesi için işaretçiler döndürür.

2. Belge açıksa, proje yalnızca bir belge veri nesnesi var mı yoksa belge görünümü nesnesi de var mı görmek için denetlemelidir.

   - Belge görünümü nesnesi varsa ve bu görünüm farklı bir hiyerarşi veya hiyerarşi öğesi içinse, proje varolan pencereyi yeniden gün yüzüne çıkarmak için görünümün pencere çerçevesiiçin işaretçiyi kullanır.

   - Belge görünümü nesnesi varsa ve bu görünüm aynı hiyerarşi ve hiyerarşi öğesi içinse, proje, temel belge veri nesnesine ekleyebiliyorsa ikinci bir görünüm açabilir. Aksi takdirde, proje varolan pencereyi yeniden suyüzüne çıkarmak için görünümün pencere çerçevesiiçin işaretçi kullanmalıdır.

   - Yalnızca belge veri nesnesi varsa, proje, görünüm için belge veri nesnesini kullanıp kullanamayacağını belirlemelidir. Belge veri nesnesi uyumluysa, projeye [özgü düzenleyiciyi aç'ta](../extensibility/how-to-open-project-specific-editors.md)tartışılan adımları tamamlayın.

     Belge veri nesnesi uyumlu değilse, dosyanın şu anda kullanımda olduğunu belirten bir hata kullanıcıya görüntülenmelidir. Bu hata yalnızca, kullanıcının [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] temel metin düzenleyicisi dışındaki bir düzenleyici kullanarak dosyayı açmaya çalıştığı anda bir dosyanın derlenmesi gibi geçici durumlarda görüntülenmelidir. Çekirdek metin düzenleyicisi belge veri nesnesini derleyiciyle paylaşabilir.

3. Belge veri nesnesi veya belge görünümü nesnesi olmadığı için belge açık değilse, [projeye özgü düzenleyiciyi aç'taki](../extensibility/how-to-open-project-specific-editors.md)adımları tamamlayın.

## <a name="open-a-standard-editor"></a>Standart bir düzenleyici açma
 Zaten açık olan bir dosya için standart bir düzenleyici açmak için aşağıdaki yordamı kullanın.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Açık bir dosya için standart bir düzenleyici açmak için

1. Arayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

     Bu yöntem ilk olarak, belgenin zaten <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>açık olmadığını. Belge zaten açıksa, düzenleyici penceresi yeniden su yüzüne çıkar.

2. Belge açık değilse, nasıl yapılır' daki adımları [tamamlayın: Standart düzenleyicileri açın.](../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl açılır: Projeye özel düzenleyicileri açın](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapılsın: Standart düzenleyicileri açın](../extensibility/how-to-open-standard-editors.md)
