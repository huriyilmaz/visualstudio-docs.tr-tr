---
title: Eski dil hizmeti modeli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726381"
---
# <a name="model-of-a-legacy-language-service"></a>Eski Dil Hizmetinin Modeli
Dil hizmeti, belirli bir dilin öğelerini ve özelliklerini tanımlar ve düzenleyiciye bu dile özgü bilgiler sağlamak için kullanılır. Örneğin, düzenleyicinin sözdizimi renklendirmesini desteklemek için, dilin öğelerini ve dil anahtar sözcüklerini bilmesi gerekir.

 Dil hizmeti, düzenleyici tarafından yönetilen metin arabelleği ve düzenleyiciyi içeren görünüm ile yakından birlikte çalışmaktadır. Microsoft IntelliSense **hızlı bilgi** seçeneği, dil hizmeti tarafından sunulan bir özelliğin örneğidir.

## <a name="a-minimal-language-service"></a>En düşük dil hizmeti
 En temel dil hizmeti aşağıdaki iki nesneyi içerir:

- *Dil hizmeti* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimini uygular. Dil hizmeti, dil hakkında, adı, dosya adı uzantıları, kod penceresi Yöneticisi ve renk Oluşturucu dahil olmak üzere bilgiler içerir.

- *Colorizer* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini uygular.

  Aşağıdaki kavramsal çizim, temel dil hizmetinin bir modelini göstermektedir.

  ![Dil hizmeti modeli grafiği](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Temel dil hizmet modeli

  Belge penceresi, bu durumda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyicisi olan düzenleyicinin *belge görünümünü* barındırır. Belge görünümü ve metin arabelleğinin, düzenleyiciye aittir. Bu nesneler, *kod penceresi*olarak adlandırılan özelleştirilmiş bir belge penceresi aracılığıyla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çalışır. Kod penceresi, IDE tarafından oluşturulup denetlenen bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> nesnesi içinde bulunur.

  Belirli bir uzantıya sahip bir dosya yüklendiğinde, düzenleyici bu uzantıyla ilişkili dil hizmetini bulur ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> yöntemini çağırarak kodu penceresine geçirir. Dil hizmeti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> arabirimini uygulayan bir *kod penceresi Yöneticisi*döndürür.

  Aşağıdaki tabloda, modeldeki nesnelere genel bir bakış sağlanmaktadır.

| Bileşen | Nesne | İşlev |
|------------------| - | - |
| Metin arabelleği | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode okuma/yazma metin akışı. Metnin diğer kodlamaları kullanabilmesi mümkündür. |
| Kod penceresi | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Bir veya daha fazla metin görünümü içeren bir belge penceresi. @No__t_0 birden çok belge arabirimi (MDI) modundayken, kod penceresi bir MDI alt öğesidir. |
| Metin görünümü | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Kullanıcının klavye ve fareyi kullanarak gezinerek metin görüntülemesine imkan tanıyan bir pencere. Kullanıcıya düzenleyici olarak bir metin görünümü görüntülenir. Metin görünümlerini normal düzenleyici pencereleri, çıkış penceresi ve acil pencere ' de kullanabilirsiniz. Ayrıca, bir kod penceresi içinde bir veya daha fazla metin görünümü yapılandırabilirsiniz. |
| Metin Yöneticisi | @No__t_0 hizmeti tarafından yönetilir ve bu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> bir işaretçi elde edersiniz | Daha önce açıklanan tüm bileşenler tarafından paylaşılan ortak bilgileri tutan bir bileşen. |
| Dil hizmeti | Uygulamaya bağımlı; <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> uygular | Düzenleyiciyi sözdizimi vurgulama, ifade tamamlama ve ayraç eşleştirme gibi dile özgü bilgilerle sağlayan bir nesne. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)