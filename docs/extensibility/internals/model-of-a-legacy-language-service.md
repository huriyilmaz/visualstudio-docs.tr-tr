---
title: Eski Dil Hizmeti Modeli | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707044"
---
# <a name="model-of-a-legacy-language-service"></a>Eski Dil Hizmetinin Modeli
Bir dil hizmeti, belirli bir dilin öğelerini ve özelliklerini tanımlar ve editöre o dile özgü bilgileri sağlamak için kullanılır. Örneğin, sözdizimi boyama desteklemek için düzenleyicinin dilin öğelerini ve anahtar kelimelerini bilmesi gerekir.

 Dil hizmeti, düzenleyici tarafından yönetilen metin arabelleği ve düzenleyiciyi içeren görünümle yakından çalışır. Microsoft IntelliSense **Hızlı Bilgi** seçeneği, bir dil hizmeti tarafından sağlanan bir özelliğe örnektir.

## <a name="a-minimal-language-service"></a>Minimal Dil Hizmeti
 En temel dil hizmeti aşağıdaki iki nesneyi içerir:

- *Dil hizmeti* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> arabirimi uygular. Bir dil hizmeti, adı, dosya adı uzantıları, kod penceresi yöneticisi ve colorizer dahil olmak üzere dil hakkında bilgi vardır.

- *Renklendirici* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi uygular.

  Aşağıdaki kavramsal çizim, temel bir dil hizmetinin modelini gösterir.

  ![Dil Hizmeti Modeli grafiği](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Temel dil hizmet modeli

  Belge penceresi, *document view* bu durumda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temel düzenleyici, düzenleyicinin belge görünümünü barındırr. Belge görünümü ve metin arabelleği düzenleyiciye aittir. Bu *nesneler,* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kod penceresi olarak adlandırılan özel bir belge penceresi aracılığıyla çalışır. Kod penceresi, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> tarafından oluşturulan ve denetlenen bir nesnede bulunur.

  Belirli bir uzantılı bir dosya yüklendiğinde, düzenleyici bu uzantıyla ilişkili dil hizmetini bulur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> ve yöntemi çağırarak kod penceresini ona geçirir. Dil hizmeti, *code window manager* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> arabirimi uygulayan bir kod penceresi yöneticisi döndürür.

  Aşağıdaki tablo, modeldeki nesnelerin genel görünümünü sağlar.

| Bileşen | Nesne | İşlev |
|------------------| - | - |
| Metin arabelleği | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode okuma/yazma metin akışı. Metnin diğer kodlamaları kullanması mümkündür. |
| Kod penceresi | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Bir veya daha fazla metin görünümü içeren belge penceresi. Birden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çok belge arabirimi (MDI) modundayken, kod penceresi bir MDI alt tır. |
| Metin görünümü | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Klavye ve fareyi kullanarak kullanıcının metinde gezinmesini ve görüntülemesini sağlayan bir pencere. Metin görünümü kullanıcıya düzenleyici olarak görünür. Sıradan düzenleyici pencerelerinde metin görünümlerini, Çıktı penceresinde ve Hemen penceresinde metin görünümlerini kullanabilirsiniz. Ayrıca, bir kod penceresinde bir veya daha fazla metin görünümleri yapılandırabilirsiniz. |
| Metin yöneticisi | Bir <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> işaretçi elde ettiğiniz hizmet tarafından yönetilir | Daha önce açıklanan tüm bileşenler tarafından paylaşılan ortak bilgileri koruyan bir bileşen. |
| Dil hizmeti | Uygulamaya bağlı; Uygulayan<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Düzenleyiciye sözdizimi vurgulama, deyim tamamlama ve ayraç eşleştirmegibi dile özgü bilgiler sağlayan bir nesne. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)
