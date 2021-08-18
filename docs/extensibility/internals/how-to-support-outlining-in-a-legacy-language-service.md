---
title: 'Nasıl olur: Eski Dil Hizmeti Hizmet HizmetLerinde Açıklama | Microsoft Docs'
description: Eski dil hizmetlerinde farklı metin bölgelerini genişletme, genişletme veya daraltma desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cef8f5520ebd0034ff5d8852129b1f076bf53b28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050019"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Nasıl yapılanlar: Eski dil hizmetlerinde açıklamayı destekleme
Metnin farklı bölgelerini genişletmek veya daraltmak için altı çizili metin kullanılır. Açıklama dilinin kullanılama yolu farklı dillere göre farklı tanımlanabilir. Daha fazla bilgi için [bkz. Outlining](../../ide/outlining.md).

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. İlkeyi uygulamanın yeni yolu hakkında daha fazla bilgi için bkz. [Adım adım kılavuz: Açıklama.](../../extensibility/walkthrough-outlining.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Aşağıda bu komutu dil hizmetiniz için nasıl destekleyebilirsiniz?

## <a name="to-support-outlining"></a>Açıklamayı desteklemek için

1. Dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> hizmeti nesnenize uygulama.

2. Yeni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> ana hat bölgeleri eklemek için geçerli ana hat oluşturma oturumu nesnesi üzerinde çağrısı.

## <a name="robust-programming"></a>Güçlü programlama
 Kullanıcı Ana Açıklama menüsünde **Tanımları** **Daralt'ı seçerken,** dil hizmetiniz IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> tarafından çağrılır.

 Bu yöntem çağrıldığnda, IDE bir işaretçi (metin arabelleğinin işaretçisi) ve bir (geçerli ana satırlama oturumunun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> işaretçisi) iletir.

 parametresinde bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> bölgeleri belirterek birden çok ana hat bölgesi için yöntemini `rgOutlnReg` çağırebilirsiniz. parametresi `rgOutlnReg` bir <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> yapıdır. Bu işlem, belirli bir bölgenin genişletilen veya daraltılmış olduğu gibi gizli bölgenin farklı özelliklerini belirtmenize olanak sağlar.

> [!NOTE]
> Yeni satır karakterlerini gizleme konusunda dikkatli olun. Gizli metin, ilk satırın başından bir bölümdeki son satırın son karakterine kadar genişletir ve son yeni satır karakterini görünür durumda bıraktır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl olur: Eski dil hizmetlerinde gizli metin desteği sağlama](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Nasıl olur: Eski dil hizmetlerinde genişletilmiş açıklama desteği sağlama](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
