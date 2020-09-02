---
title: Eski dil hizmeti modeli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d51df6dd11509b86e6648d59978b87d9cd8a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157647"
---
# <a name="model-of-a-legacy-language-service"></a>Eski Dil Hizmetinin Modeli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dil hizmeti, belirli bir dilin öğelerini ve özelliklerini tanımlar ve düzenleyiciye bu dile özgü bilgiler sağlamak için kullanılır. Örneğin, düzenleyicinin sözdizimi renklendirmesini desteklemek için, dilin öğelerini ve dil anahtar sözcüklerini bilmesi gerekir.  
  
 Dil hizmeti, düzenleyici tarafından yönetilen metin arabelleği ve düzenleyiciyi içeren görünüm ile yakından birlikte çalışmaktadır. Microsoft IntelliSense **hızlı bilgi** seçeneği, dil hizmeti tarafından sunulan bir özelliğin örneğidir.  
  
## <a name="a-minimal-language-service"></a>En düşük dil hizmeti  
 En temel dil hizmeti aşağıdaki iki nesneyi içerir:  
  
- *Dil hizmeti* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimini uygular. Dil hizmeti, dil hakkında, adı, dosya adı uzantıları, kod penceresi Yöneticisi ve renk Oluşturucu dahil olmak üzere bilgiler içerir.  
  
- *Colorizer* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini uygular.  
  
  Aşağıdaki kavramsal çizim, temel dil hizmetinin bir modelini göstermektedir.  
  
  ![Dil hizmeti modeli grafiği](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Temel dil hizmet modeli  
  
  Belge penceresi, bu örnekte çekirdek Düzenleyici olan düzenleyicinin *belge görünümünü* barındırır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Belge görünümü ve metin arabelleğinin, düzenleyiciye aittir. Bu nesneler, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] *kod penceresi*olarak adlandırılan özelleştirilmiş bir belge penceresi aracılığıyla ile çalışır. Kod penceresi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> IDE tarafından oluşturulup denetlenen bir nesne içindedir.  
  
  Belirli bir uzantıya sahip bir dosya yüklendiğinde, düzenleyici bu uzantıyla ilişkili dil hizmetini bulur ve yöntemini çağırarak kodu penceresine geçirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> . Dil hizmeti, arabirimini uygulayan bir *kod penceresi Yöneticisi*döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  
  
  Aşağıdaki tabloda, modeldeki nesnelere genel bir bakış sağlanmaktadır.  
  
|Bileşen|Nesne|İşlev|  
|---------------|------------|--------------|  
|Metin arabelleği|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Unicode okuma/yazma metin akışı. Metnin diğer kodlamaları kullanabilmesi mümkündür.|  
|Kod penceresi|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Bir veya daha fazla metin görünümü içeren bir belge penceresi. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Birden çok belge arabirimi (MDI) modundayken, kod penceresi BIR MDI alt öğesidir.|  
|Metin görünümü|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Kullanıcının klavye ve fareyi kullanarak gezinerek metin görüntülemesine imkan tanıyan bir pencere. Kullanıcıya düzenleyici olarak bir metin görünümü görüntülenir. Metin görünümlerini normal düzenleyici pencereleri, çıkış penceresi ve acil pencere ' de kullanabilirsiniz. Ayrıca, bir kod penceresi içinde bir veya daha fazla metin görünümü yapılandırabilirsiniz.|  
|Metin Yöneticisi|<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Bir işaretçi elde ettiğiniz hizmet tarafından yönetiliyor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>|Daha önce açıklanan tüm bileşenler tarafından paylaşılan ortak bilgileri tutan bir bileşen.|  
|Dil hizmeti|Uygulamaya bağımlı; uygular <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Düzenleyiciyi sözdizimi vurgulama, ifade tamamlama ve ayraç eşleştirme gibi dile özgü bilgilerle sağlayan bir nesne.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)
