---
title: Eski Dil Hizmeti Komutlarını Durdurma | Microsoft Docs
description: Eski dil hizmeti komutlarında araya Visual Studio ve dile özgü davranış eklemek için komut filtrelerini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6f82e3cb15b39359c78f28a42e62d65665f34dba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049967"
---
# <a name="intercepting-legacy-language-service-commands"></a>Eski Dil Hizmeti Komutlarını Kesme
ile, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metin görünümünün aksi takdirde işleyebiliyor olduğu dil hizmeti kesme komutlarına sahip olursunuz. Bu, metin görünümünün yönetmez dile özgü davranış için yararlıdır. Dil hizmetinizin metin görünümüne bir veya daha fazla komut filtresi ekleyerek bu komutların yolunu kesebilirsiniz.

## <a name="getting-and-routing-the-command"></a>Komutu Alma ve Yönlendirme
 Komut filtresi, belirli karakter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dizilerini veya anahtar komutlarını izleyen bir nesnedir. Birden fazla komut filtresini tek bir metin görünümüyle ilişkilendirilebilirsiniz. Her metin görünümü bir komut filtreleri zincirini sürdürür. Yeni bir komut filtresi oluşturdukta, uygun metin görünümü için filtreyi zincire eklersiniz.

 Komut <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> filtrenizi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zincire eklemek için üzerinde yöntemini çağırma. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>çağrısında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut filtrenizin işlemeyeceği komutları geçebilirsiniz başka bir komut filtresi döndürür.

 Komut işleme için aşağıdaki seçeneklere sahipsiniz:

- Komutu işle ve ardından komutu zincirde bir sonraki komut filtresine iletir.

- Komutu işle ve komutu bir sonraki komut filtresine geçme.

- Komutu işlemeyin, ancak komutu bir sonraki komut filtresine iletir.

- Komutunu yoksayın. Geçerli filtrede işlemeyin ve bir sonraki filtreye geçmeyin.

  Dil hizmetinizin hangi komutları işlemesi gerektiği hakkında bilgi için bkz. Dil Hizmeti [Filtreleri için Önemli Komutlar.](../../extensibility/internals/important-commands-for-language-service-filters.md)
