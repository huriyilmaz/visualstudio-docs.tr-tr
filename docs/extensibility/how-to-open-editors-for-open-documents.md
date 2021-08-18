---
title: 'Nasıl yapılır: açık belgeler için düzenleyiciler açma | Microsoft Docs'
description: Standart veya projeye özgü bir düzenleyicide dosya açmayı öğrenin. Bir proje bir belge penceresi açtığında, dosyanın zaten açık olup olmadığını belirlemesi gerekir.
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
ms.openlocfilehash: bcc01a90c058e53a461b3e5d21d9f11fe0cd8c18d0ac84ee9b90e6154feee7fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432726"
---
# <a name="how-to-open-editors-for-open-documents"></a>Nasıl yapılır: açık belgeler için düzenleyiciler açma
Proje bir belge penceresini açmadan önce, projenin, dosyanın zaten başka bir düzenleyicinin belge penceresinde açık olup olmadığını belirlemesi gerekir. Dosya projeye özgü bir düzenleyicide veya ile kaydedilen standart düzenleyicilerden birinde açılabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Projeye özgü bir düzenleyici açın
 Zaten açık olan bir dosya için projeye özgü bir düzenleyici açmak için aşağıdaki yordamı kullanın.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Açık bir dosya için projeye özgü bir düzenleyici açmak için

1. Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Bu çağrı, uygunsa belgenin hiyerarşisine, hiyerarşi öğesine ve pencere çerçevesine işaretçiler döndürür.

2. Belge açıksa, proje yalnızca bir belge veri nesnesinin bulunup bulunmadığını ya da bir belge görünümü nesnesi olup olmadığını kontrol etmelidir.

   - Bir belge görünümü nesnesi varsa ve bu görünüm farklı bir hiyerarşi veya hiyerarşi öğesi için ise, proje, var olan pencereyi yeniden göstermek için görünümün pencere çerçevesine yönelik işaretçiyi kullanır.

   - Bir belge görünümü nesnesi varsa ve bu görünüm aynı hiyerarşi ve hiyerarşi öğesi için ise, proje temel alınan belge verisi nesnesine iliştiriuygunsa ikinci bir görünüm açabilir. Aksi takdirde, projenin var olan pencereyi yeniden göstermek için görünümün pencere çerçevesine yönelik işaretçiyi kullanması gerekir.

   - Yalnızca belge verileri nesnesi varsa, proje, görünümü için belge veri nesnesini kullanıp kullanamayacağını belirlemelidir. Belge veri nesnesi uyumluysa, [projeye özgü düzenleyici açma](../extensibility/how-to-open-project-specific-editors.md)bölümünde açıklanan adımları uygulayın.

     Belge veri nesnesi uyumlu değilse, kullanıcıya dosyanın kullanımda olduğunu belirten bir hata görüntülenmelidir. Bu hata yalnızca, kullanıcının çekirdek metin Düzenleyicisi dışında bir düzenleyici kullanarak dosyayı açmaya çalıştığı sırada bir dosya derlenirken olduğu gibi geçici durumlarda görüntülenmelidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Çekirdek metin Düzenleyicisi, belge veri nesnesini derleyici ile paylaşabilir.

3. Belge verisi nesnesi veya belge görünümü nesnesi olmadığından belge açık değilse, [projeye özgü bir düzenleyici açma](../extensibility/how-to-open-project-specific-editors.md)bölümündeki adımları uygulayın.

## <a name="open-a-standard-editor"></a>Standart bir düzenleyici açın
 Zaten açık olan bir dosya için standart bir düzenleyici açmak üzere aşağıdaki yordamı kullanın.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Açık bir dosya için standart bir düzenleyici açmak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> çağrısı yapın.

     Bu yöntem ilk olarak, belgenin çağırarak zaten açık olmadığını doğrular <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Belge zaten açıksa, düzenleyici penceresi yeniden açılır.

2. Belge açık değilse, [nasıl yapılır: Standart düzenleyicilerin nasıl açılacağı hakkında](../extensibility/how-to-open-standard-editors.md)adımları doldurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini aç ve Kaydet](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl yapılır: projeye özgü düzenleyiciler açma](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapılır: standart düzenleyiciler açma](../extensibility/how-to-open-standard-editors.md)
