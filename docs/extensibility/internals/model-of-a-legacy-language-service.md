---
title: Eski dil hizmeti modeli | Microsoft Docs
description: Visual Studio Core Düzenleyicisi için en düşük dil hizmetinin bu modelini kendi dil hizmetinizi oluşturmaya yönelik bir kılavuz olarak kullanın.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2928d3c09a54ea8e9548f7751381279f153643e5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876746"
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

  Belge penceresi, bu örnekte çekirdek Düzenleyici olan düzenleyicinin *belge görünümünü* barındırır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Belge görünümü ve metin arabelleğinin, düzenleyiciye aittir. Bu nesneler, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *kod penceresi* olarak adlandırılan özelleştirilmiş bir belge penceresi aracılığıyla ile çalışır. Kod penceresi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> IDE tarafından oluşturulup denetlenen bir nesne içindedir.

  Belirli bir uzantıya sahip bir dosya yüklendiğinde, düzenleyici bu uzantıyla ilişkili dil hizmetini bulur ve yöntemini çağırarak kodu penceresine geçirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> . Dil hizmeti, arabirimini uygulayan bir *kod penceresi Yöneticisi* döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .

  Aşağıdaki tabloda, modeldeki nesnelere genel bir bakış sağlanmaktadır.

| Bileşen | Nesne | İşlev |
|------------------| - | - |
| Metin arabelleği | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode okuma/yazma metin akışı. Metnin diğer kodlamaları kullanabilmesi mümkündür. |
| Kod penceresi | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Bir veya daha fazla metin görünümü içeren bir belge penceresi. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Birden çok belge arabirimi (MDI) modundayken, kod penceresi BIR MDI alt öğesidir. |
| Metin görünümü | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Kullanıcının klavye ve fareyi kullanarak gezinerek metin görüntülemesine imkan tanıyan bir pencere. Kullanıcıya düzenleyici olarak bir metin görünümü görüntülenir. Metin görünümlerini normal düzenleyici pencereleri, çıkış penceresi ve acil pencere ' de kullanabilirsiniz. Ayrıca, bir kod penceresi içinde bir veya daha fazla metin görünümü yapılandırabilirsiniz. |
| Metin Yöneticisi | <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Bir işaretçi elde ettiğiniz hizmet tarafından yönetiliyor <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Daha önce açıklanan tüm bileşenler tarafından paylaşılan ortak bilgileri tutan bir bileşen. |
| Dil hizmeti | Uygulamaya bağımlı; uygular <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Düzenleyiciyi sözdizimi vurgulama, ifade tamamlama ve ayraç eşleştirme gibi dile özgü bilgilerle sağlayan bir nesne. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)
