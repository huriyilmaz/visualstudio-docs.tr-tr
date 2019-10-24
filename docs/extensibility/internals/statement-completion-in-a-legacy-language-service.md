---
title: Eski dil hizmetinde deyimin tamamlanması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4c813052892c21a6a3e04560452b503205df117
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723227"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Deyim Tamamlama
İfade tamamlama, dil hizmetinin, kullanıcıların temel düzenleyicide yazmaya başladıkları bir dil anahtar sözcüğünü veya öğesini tamamlamada yardımcı olduğu işlemdir. Bu konuda, deyimin tamamlanmasının nasıl çalıştığı ve dil hizmetinize nasıl uygulanacağı açıklanmaktadır.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Deyimden tamamlama işleminin yeni yolu hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: Using Ifadesinin tamamlanmasını gösterme](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="implementing-statement-completion"></a>Ekstre tamamlamayı uygulama
 Çekirdek düzenleyicide, deyimin tamamlanması etkileşimli olarak daha kolay ve hızlı bir şekilde kod yazmanıza yardımcı olan özel bir kullanıcı arabirimi etkinleştirir. Deyimin tamamlanması, gerek duyulduklarında ilgili nesneleri veya sınıfları görüntüleyerek yardımcı olur. Bu, belirli öğeleri anımsamanıza veya bir yardım başvurusu konusunda bunları aramak zorunda olmanızı önler.

 Deyimin tamamlanmasını uygulamak için, dilinizin ayrıştırılabilen bir ifade tamamlama tetikleyicisi olması gerekir. Örneğin, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir nokta (.) işleci kullanır, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bir ok (->) işleci kullanır. Bir dil hizmeti, deyimin tamamlanmasını başlatmak için birden fazla tetikleyici kullanabilir. Bu Tetikleyiciler komut filtresinde programlanır.

## <a name="command-filters-and-triggers"></a>Komut filtreleri ve Tetikleyiciler
 Komut filtreleri tetikleyicinizin veya tetikleyicilerinin tekrarlamalarını durdurur. Görünüme komut filtresi eklemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimini uygulayın ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemini çağırarak görünüme ekleyin. Dil hizmetinizin ifade tamamlama, hata işaretçileri ve yöntem ipuçları gibi tüm yönleri için aynı komut filtresini (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) kullanabilirsiniz. Daha fazla bilgi için bkz. [eski dil hizmeti komutlarını önleme](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Tetikleyici düzenleyiciye girildiğinde — özellikle de metin arabelleği — dil hizmetiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemini çağırır. Bu, düzenleyicinin Kullanıcı arabirimi tamamlanma adaylarından seçim yapabilmesi için Kullanıcı arabirimini almasına neden olur. Bu yöntem, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ve <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> bayraklarını parametre olarak uygulamanızı gerektirir. Tamamlama öğelerinin listesi, kaydırılan liste kutusunda görünür. Kullanıcı yazmaya devam ettiğinde, liste kutusu içindeki seçim, en son yazılan karakterlerle en yakın eşleşmeyi yansıtacak şekilde güncelleştirilir. Çekirdek Düzenleyici, deyimin tamamlanmasını Kullanıcı arabirimini uygular, ancak dil hizmeti, ifadeye yönelik bir aday tamamlama öğeleri kümesi tanımlamak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> arabirimini uygulamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Komutlarını Kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)