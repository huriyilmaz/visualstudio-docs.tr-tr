---
title: Eski Dil Hizmeti Komutlarını Engelleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707447"
---
# <a name="intercepting-legacy-language-service-commands"></a>Eski Dil Hizmeti Komutlarını Kesme
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], metin görünümünün başka şekilde işleyeceğini dil hizmeti engelleme komutlarına sahip olabilirsiniz. Bu, metin görünümünün yönetmediği dile özgü davranışlar için yararlıdır. Dil hizmetinizden metin görünümüne bir veya daha fazla komut filtresi ekleyerek bu komutları kesebilirsiniz.

## <a name="getting-and-routing-the-command"></a>Komutu Alma ve Yönlendirme
 Komut filtresi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> belirli karakter dizilerini veya anahtar komutlarını izleyen bir nesnedir. Birden fazla komut filtresini tek bir metin görünümüyle ilişkilendirebilirsiniz. Her metin görünümü bir komut zinciri filtreleri tutar. Yeni bir komut filtresi oluşturduktan sonra, uygun metin görünümü için filtreyi zincire eklersiniz.

 Komut <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> filtrenizi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zincire eklemek için yönteme çağrı. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>Aradığınızda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut filtrenizin işlemediği komutları geçirebileceğiniz başka bir komut filtresi döndürür.

 Komut kullanımı için aşağıdaki seçeneklere sahipsiniz:

- Komutu işleyin ve ardından komutu zincirdeki bir sonraki komut filtresine geçirin.

- Komutu işleyin ve komutu bir sonraki komut filtresine geçirmeyin.

- Komutu işlemeyin, ancak komutu bir sonraki komut filtresine geçirin.

- Komutu yoksay. Geçerli filtrede işlemeyin ve bir sonraki filtreye geçirmeyin.

  Dil hizmetinizin hangi komutları işlemesi gerektiği hakkında bilgi için, [Dil Hizmeti Filtreleri için Önemli Komutlar'a](../../extensibility/internals/important-commands-for-language-service-filters.md)bakın.
