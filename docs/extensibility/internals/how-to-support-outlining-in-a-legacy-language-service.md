---
title: 'Nasıl yapilir: Eski Dil Hizmetinde Anahat Oluşturmayı Destekleme | Microsoft Dokümanlar'
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
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707914"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Nasıl yapilir: Eski bir dil hizmetinde anahat oluşturmayı destekleme
Anahat oluşturma, metnin farklı bölgelerini genişletmek veya daraltmak için kullanılır. Anahat oluşturma şekli farklı diller tarafından farklı şekilde tanımlanabilir. Daha fazla bilgi için [Anahat'a](../../ide/outlining.md)bakın.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Ana hatoluşturmayı uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Bkz. Walkthrough: Anahat.](../../extensibility/walkthrough-outlining.md)

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Aşağıda, dil hizmetiniz için bu komutun nasıl destekleneceği gösterilmektedir.

## <a name="to-support-outlining"></a>Anahat oluşturmayı desteklemek için

1. Dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> hizmeti nesnenize uygulayın.

2. Yeni <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> anahat bölgeleri eklemek için geçerli anahat oturumu nesnesini arayın.

## <a name="robust-programming"></a>Sağlam programlama
 Bir kullanıcı **Anahat** menüsünde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> **Tanımlara Karşı Daralt'ı** seçtiğinde, IDE dil hizmetinizi çağırır.

 Bu yöntem çağrıldığında, IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> bir işaretçi (metin arabelleği <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> için bir işaretçi) ve bir (geçerli anahat oturumu için bir işaretçi) geçer.

 `rgOutlnReg` Parametrede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> bu bölgeleri belirterek, birden çok anahat bölgesi için yöntemi arayabilirsiniz. `rgOutlnReg` Parametre bir <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> yapıdır. Bu işlem, belirli bir bölgenin genişletilip genişletilmediği veya daraltılmış olması gibi gizli bölgenin farklı özelliklerini belirtmenize olanak tanır.

> [!NOTE]
> Yeni çizgi karakterleri gizleme konusunda dikkatli olun. Gizli metin, ilk satırın başından bir bölümdeki son satırın son karakterine kadar uzanarak son yeni satır karakterini görünür bırakmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapilir: Eski bir dil hizmetinde gizli metin desteği sağlayın](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Nasıl?](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
