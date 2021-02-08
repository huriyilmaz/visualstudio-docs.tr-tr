---
title: Eski dil hizmeti komutlarını kesintiye uğratan | Microsoft Docs
description: Eski dil hizmeti komutlarını ele almak ve dile özgü davranış eklemek için Visual Studio 'da komut filtrelerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839800"
---
# <a name="intercepting-legacy-language-service-commands"></a>Eski Dil Hizmeti Komutlarını Kesme
İle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , metin görünümünün daha sonra işleyememesi için dil hizmeti kesme komutlarının de olmasını sağlayabilirsiniz. Bu, metin görünümünün yönetmediğinden dile özgü davranış için yararlıdır. Dil hizmetinizdeki metin görünümüne bir veya daha fazla komut filtresi ekleyerek bu komutları ele alabilirsiniz.

## <a name="getting-and-routing-the-command"></a>Komutu alma ve yönlendirme
 Komut filtresi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> belirli karakter dizilerini veya anahtar komutları izleyen bir nesnedir. Birden fazla komut filtresini tek bir metin görünümüyle ilişkilendirebilirsiniz. Her metin görünümü bir komut filtreleri zinciri saklar. Yeni bir komut filtresi oluşturduktan sonra, uygun metin görünümü için filtreyi zincire eklersiniz.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Komut filtrenizi zincire eklemek için üzerinde yöntemini çağırın. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>' İ çağırdığınızda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut filtreniz tarafından işlemeyen komutları geçirebilmeniz için başka bir komut filtresi döndürür.

 Komut işleme için aşağıdaki seçenekleriniz vardır:

- Komutu işleyin ve ardından zincirindeki sonraki komut filtresine komutunu geçirin.

- Komutu işleyin ve komutu bir sonraki komut filtresine iletmeyin.

- Komutu işlemez, ancak komutunu bir sonraki komut filtresine geçirin.

- Komutu yoksayın. Geçerli filtrede işlemeyin ve sonraki filtreye geçirmeyin.

  Dil hizmetinizin hangi komutları işlemesi gerektiği hakkında daha fazla bilgi için bkz. [dil hizmeti filtreleri Için önemli komutlar](../../extensibility/internals/important-commands-for-language-service-filters.md).
