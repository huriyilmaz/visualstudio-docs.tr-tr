---
title: 'Nasıl yapılır: açık belgeler için düzenleyiciler açma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6e565e026ca49825a7b00a82e4e5c62a2f6c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204141"
---
# <a name="how-to-open-editors-for-open-documents"></a>Nasıl Yapılır: Açık Belgeler için Düzenleyicileri Açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proje bir belge penceresini açmadan önce, projenin, dosyanın zaten başka bir düzenleyicinin belge penceresinde açık olup olmadığını belirlemesi gerekir. Dosya projeye özgü bir düzenleyicide veya ile kaydedilen standart düzenleyicilerden birinde açılabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="opening-a-project-specific-editor"></a>Projeye özgü bir düzenleyici açma  
 Zaten açık olan bir dosya için projeye özgü bir düzenleyici açmak için aşağıdaki yordamı kullanın.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Açık bir dosya için projeye özgü bir düzenleyici açmak için  
  
1. Yöntemini çağırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .  
  
    Bu çağrı, uygunsa belgenin hiyerarşisine, hiyerarşi öğesine ve pencere çerçevesine işaretçiler döndürür.  
  
2. Belge açıksa, proje yalnızca bir belge veri nesnesinin bulunup bulunmadığını ya da bir belge görünümü nesnesi olup olmadığını kontrol etmelidir.  
  
   - Bir belge görünümü nesnesi varsa ve bu görünüm farklı bir hiyerarşi veya hiyerarşi öğesi için ise, proje, var olan pencereyi yeniden göstermek için görünümün pencere çerçevesine yönelik işaretçiyi kullanır.  
  
   - Bir belge görünümü nesnesi varsa ve bu görünüm aynı hiyerarşi ve hiyerarşi öğesi için ise, proje temel alınan belge verisi nesnesine iliştiriuygunsa ikinci bir görünüm açabilir. Aksi takdirde, projenin var olan pencereyi yeniden göstermek için görünümün pencere çerçevesine yönelik işaretçiyi kullanması gerekir.  
  
   - Yalnızca belge verileri nesnesi varsa, proje, görünümü için belge veri nesnesini kullanıp kullanamayacağını belirlemelidir. Belge veri nesnesi uyumluysa, [projeye özgü bir düzenleyici açma](../extensibility/how-to-open-project-specific-editors.md)bölümünde açıklanan adımları uygulayın.  
  
     Belge veri nesnesi uyumlu değilse, kullanıcıya dosyanın kullanımda olduğunu belirten bir hata görüntülenmelidir. Bu hata yalnızca, kullanıcının çekirdek metin Düzenleyicisi dışında bir düzenleyici kullanarak dosyayı açmaya çalıştığı sırada bir dosya derlenirken olduğu gibi geçici durumlarda görüntülenmelidir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Çekirdek metin Düzenleyicisi, belge veri nesnesini derleyici ile paylaşabilir.  
  
3. Belge verisi nesnesi veya belge görünümü nesnesi olmadığından belge açık değilse, [projeye özgü bir düzenleyici açma](../extensibility/how-to-open-project-specific-editors.md)adımlarını izleyin.  
  
## <a name="opening-a-standard-editor"></a>Standart bir düzenleyiciyi açma  
 Zaten açık olan bir dosya için standart bir düzenleyici açmak üzere aşağıdaki yordamı kullanın.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Açık bir dosya için standart bir düzenleyici açmak için  
  
1. Çağrısı yapın <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
     Bu yöntem ilk olarak, belgenin çağırarak zaten açık olmadığını doğrular <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Belge zaten açıksa, düzenleyici penceresi yeniden açılır.  
  
2. Belge açık değilse, [nasıl yapılır: Standart düzenleyicilerin nasıl açılacağı hakkında](../extensibility/how-to-open-standard-editors.md)adımları doldurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)   
 [Nasıl yapılır: projeye özgü düzenleyiciler açma](../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../extensibility/how-to-open-standard-editors.md)
