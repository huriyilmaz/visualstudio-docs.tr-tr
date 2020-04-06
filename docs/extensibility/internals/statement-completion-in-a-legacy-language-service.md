---
title: Eski Dil Hizmetinde İfade Tamamlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704938"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Deyim Tamamlama
Bildirimin tamamlanması, dil hizmetinin kullanıcıların çekirdek düzenleyicide yazmaya başladıkları bir dil anahtar sözcüklerini veya öğeyi bitirmelerine yardımcı olan işlemdir. Bu konu, deyim tamamlamanın nasıl çalıştığını ve dil hizmetinizde nasıl uygulanacağını tartışır.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. İfade tamamlamayı uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Bkz. Walkthrough: İfade Tamamlama'yı Görüntüleme](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementing-statement-completion"></a>Ekstre Tamamlamanın Uygulanması
 Çekirdek düzenleyicide, deyim tamamlama, etkileşimli olarak kod yazmanıza daha kolay ve hızlı bir şekilde yardımcı olan özel bir ara birimi etkinleştirir. Ekstre tamamlama, ilgili nesneleri veya sınıfları gerektiğinde görüntüleyerek yardımcı olur ve bu da belirli öğeleri hatırlamak zorunda kalmanızı veya bunları bir Yardım başvuru konusuna bakmanızı önler.

 İfade tamamlamayı uygulamak için, dilinizin ayrıştırılabilen bir deyim tamamlama tetikleyicisi olması gerekir. Örneğin, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir nokta (.) işleci [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kullanırken, bir ok (->) işleci kullanır. Bir dil hizmeti, deyim tamamlamayı başlatmak için birden fazla tetikleyici kullanabilir. Bu tetikleyiciler komut filtresinde programlanır.

## <a name="command-filters-and-triggers"></a>Komut Filtreleri ve Tetikleyiciler
 Komut filtreleri tetikleyicinizin veya tetikleyicilerinizin oluşlarını keser. Komut filtresini görünüme eklemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi uygulayın ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi çağırarak görünüme takın. İfade tamamlama, hata işaretçileri ve yöntem ipuçları gibi dil hizmetinizin tüm yönleri için aynı komut filtresini (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) kullanabilirsiniz. Daha fazla bilgi için [bkz.](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Tetikleyici düzenleyiciye girildiğinde - özellikle metin arabelleği - dil <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> hizmetiniz yöntemi çağırır. Bu, kullanıcının deyimi tamamlama adaylarından seçim yapabilmesi için editörün Kullanıcı Arabirimi'ni gündeme getirmesine neden olur. Bu yöntem, uygulamanızı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> ve bayrakları parametreler olarak gerektirir. Tamamlama öğeleri listesi kaydırma listesi kutusunda görünür. Kullanıcı yazmaya devam ettikçe, liste kutusundaki seçim en son yazılan karakterlere en yakın eşleşmeyi yansıtacak şekilde güncelleştirilir. Çekirdek düzenleyici, bildirimin tamamlanması için UI'yi uygular, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ancak dil hizmeti, deyim için aday tamamlama öğeleri kümesini tanımlamak için arabirimi uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Komutlarını Kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
