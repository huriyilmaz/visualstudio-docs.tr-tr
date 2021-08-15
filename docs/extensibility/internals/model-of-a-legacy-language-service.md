---
title: Eski Dil Hizmeti Hizmeti | Microsoft Docs
description: Kendi dil hizmetinizi oluşturmak için bir kılavuz olarak Visual Studio temel düzenleyici için en düşük dil hizmetinin bu modelini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 02a1fd8316e3fcb048169fdbaf635116e677389e8f417fb47a3d2be5bd654f68
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432753"
---
# <a name="model-of-a-legacy-language-service"></a>Eski Dil Hizmetinin Modeli
Dil hizmeti, belirli bir dil için öğeleri ve özellikleri tanımlar ve düzenleyiciye bu dile özgü bilgileri sağlamak için kullanılır. Örneğin, söz dizimi renklendirmeyi desteklemek için düzenleyicinin dilin öğelerini ve anahtar sözcüklerini biliyor olması gerekir.

 Dil hizmeti, düzenleyici tarafından yönetilen metin arabelleği ve düzenleyiciyi içeren görünümle yakından çalışır. Microsoft IntelliSense **Hızlı Bilgi seçeneği,** bir dil hizmeti tarafından sağlanan bir özellik örneğidir.

## <a name="a-minimal-language-service"></a>En Az Dil Hizmeti
 En temel dil hizmeti aşağıdaki iki nesne içerir:

- Dil *hizmeti* arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> uygulayan bir hizmettir. Dil hizmeti adı, dosya adı uzantıları, kod penceresi yöneticisi ve renklandırıcı gibi dil hakkında bilgi içerir.

- *Renklandırıcı* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimini uygulamaya ekler.

  Aşağıdaki kavramsal çizimde temel dil hizmetinin bir modeli yer amektedir.

  ![Dil Hizmeti Modeli grafiği](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Temel dil hizmeti modeli

  Belge penceresi, *düzenleyicinin belge görünümünü* (bu durumda temel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] düzenleyici) barındırr. Belge görünümü ve metin arabelleği düzenleyiciye aittir. Bu nesneler kod [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] penceresi olarak adlandırılan özel bir belge penceresi aracılığıyla *çalışır.* Kod penceresi, IDE tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oluşturulan ve denetlenen bir nesnede yer alan bir nesnedir.

  Belirli bir uzantıya sahip bir dosya yüklendiğinde düzenleyici, bu uzantıyla ilişkili dil hizmetini bulup yöntemini çağırarak kod penceresine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> geçer. Dil hizmeti, *arabirimini uygulayan* bir kod penceresi yöneticisi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> döndürür.

  Aşağıdaki tablo, modeldeki nesnelere genel bir bakış sağlar.

| Bileşen | Nesne | İşlev |
|------------------| - | - |
| Metin arabelleği | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode okuma/yazma metin akışı. Metnin diğer kodlamaları kullanması mümkündür. |
| Kod penceresi | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Bir veya daha fazla metin görünümleri içeren bir belge penceresi. Çok [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belgeli arabirim (MDI) modunda olduğunda, kod penceresi bir MDI alt penceresidir. |
| Metin görünümü | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Kullanıcının klavyeyi ve fareyi kullanarak metinde gezinmesini ve görüntülemesini sağlayan bir pencere. Kullanıcıya düzenleyici olarak bir metin görünümü görünür. Normal düzenleyici pencerelerde, Çıkış penceresinde ve Anında penceresinde metin görünümlerini kullanabilirsiniz. Ayrıca, bir kod penceresi içinde bir veya daha fazla metin görünümleri yapılandırabilirsiniz. |
| Metin yöneticisi | <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>İşaretçiyi elde etmek için hizmet tarafından <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> yönetilen | Daha önce açıklanan tüm bileşenler tarafından paylaşılan ortak bilgileri sürdüren bir bileşen. |
| Dil hizmeti | Uygulamaya bağımlı; Uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Söz dizimi vurgulama, deyim tamamlama ve küme ayracı eşleştirme gibi dile özgü bilgileri düzenleyiciye sağlayan nesne. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Düzenleyicilerde Belge Verileri ve Belge Görünümü](../../extensibility/document-data-and-document-view-in-custom-editors.md)
