---
title: 'Nasıl yapılır: eski dil hizmetinde anahat oluşturmayı destekleme | Microsoft Docs'
description: Eski dil hizmetinde, farklı metin bölgelerini seviyelendirme, genişletme veya daraltma desteği sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9d1d7b7a74b6565c666e4d5e3293caaef3c7732
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761328"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Nasıl yapılır: eski dil hizmetinde anahat oluşturmayı destekleme
Ana hat, metnin farklı bölgelerini genişletmek veya daraltmak için kullanılır. Ana hat kullanım şekli farklı diller tarafından farklı şekilde tanımlanabilir. Daha fazla bilgi için bkz. [anahat oluşturma](../../ide/outlining.md).

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Anahat oluşturmanın yeni yolu hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: Ana hat](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Dil hizmetiniz için bu komutun nasıl destekleyeceği aşağıda gösterilmiştir.

## <a name="to-support-outlining"></a>Anahat oluşturmayı desteklemek için

1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>Dil hizmeti nesneniz üzerinde uygulama.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Yeni ana hat bölgeleri eklemek için geçerli anahat oturumu nesnesinde çağırın.

## <a name="robust-programming"></a>Güçlü programlama
 Bir Kullanıcı ana **hat** menüsündeki **tanımlardan Daralt** ' ı seçtiğinde, IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> dil hizmetinize çağrı yapar.

 Bu yöntem çağrıldığında, IDE bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> işaretçiye (bir metin arabelleğinin işaretçisi) ve bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (geçerli ana hat oturumunun işaretçisi) geçer.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>Bu bölgeleri parametresinde belirterek birden çok ana hat bölgesi için yöntemini çağırabilirsiniz `rgOutlnReg` . `rgOutlnReg`Parametresi bir <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> yapıdır. Bu işlem, belirli bir bölgenin genişletilip daraltılmayacağı gibi gizli bölgenin farklı özelliklerini belirtmenize olanak tanır.

> [!NOTE]
> Yeni satır karakterlerini gizleme konusunda dikkatli olun. Gizli metin, son yeni satır karakterini görünür bırakarak, ilk satırın başından itibaren bir bölümdeki son satırın son karakterine kadar genişlemelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: eski dil hizmetinde gizli metin desteği sağlama](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Nasıl yapılır: eski dil hizmetinde genişletilmiş anahat desteği sağlama](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
