---
title: Eski Dil Hizmetinde Hızlı Bilgi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705939"
---
# <a name="quick-info-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Hızlı Bilgiler
IntelliSense Hızlı Bilgi, kullanıcı bakıcıyı tanımlayıcıya yerleştirdiğinde ve **IntelliSense** menüsünden **Hızlı Bilgi'yi** seçtiğinde veya tanımlayıcının üzerinde fare imlecini tuttuğunda kaynaktaki bir tanımlayıcı hakkındaki bilgileri gösterir. Bu, bir araç ipucunun tanımlayıcı hakkında bilgiyle birlikte görünmesine neden olur. Bu bilgiler genellikle tanımlayıcı türünden oluşur. Hata ayıklama altyapısı etkin olduğunda, bu bilgiler geçerli değeri içerebilir. Hata ayıklama altyapısı ifade değerlerini sağlarken, dil hizmeti yalnızca tanımlayıcıları işler.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi edinmek için [Walkthrough: QuickInfo Araç İpuçlarını Görüntüleme'](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)ye bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

 Yönetilen paket çerçevesi (MPF) dil hizmeti sınıfları, IntelliSense Hızlı Bilgi aracı ipucunu görüntülemek için tam destek sağlar. Tek yapmanız gereken görüntülenecek metni sağlamak ve hızlı bilgi özelliğini etkinleştirmektir.

 Görüntülenecek metin, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırıcı neden değeri ne kadar dırdır <xref:Microsoft.VisualStudio.Package.ParseReason>eden yöntem parer'i arayarak elde edilir. Bu nedenle, <xref:Microsoft.VisualStudio.Package.ParseRequest> arayıcıya, nesnede belirtilen konumdaki tanımlayıcı için tür bilgilerini (veya Hızlı Bilgi aracı ipucunda görüntülenmesi uygun olan her şeyi) elde etmesini söyler. Nesne <xref:Microsoft.VisualStudio.Package.ParseRequest> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteme geçirilen dir.

 Ayrıştırıcı, tüm tanımlayıcıların türlerini <xref:Microsoft.VisualStudio.Package.ParseRequest> belirlemek için nesneydeki konuma kadar her şeyi ayrıştırmalıdır. Sonra ayrıştırıcı ayrıştırma isteği konumunda tanımlayıcı almak gerekir. Son olarak, arayıcı, nesnenin metni <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> yöntemden döndürebilmeleri için bu tanımlayıcıyla ilişkili araç ipucu verilerini nesneye aktarmalıdır.

## <a name="enabling-the-quick-info-feature"></a>Hızlı Bilgi Özelliğini Etkinleştirme
 Hızlı Bilgi özelliğini etkinleştirmek `CodeSense` için, `QuickInfo` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>'nin ve adı geçen parametreleri ayarlamanız gerekir. Bu öznitelikler <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> ve özellikleri ayarlayın.

## <a name="implementing-the-quick-info-feature"></a>Hızlı Bilgi Özelliğinin Uygulanması
 Sınıf, <xref:Microsoft.VisualStudio.Package.ViewFilter> IntelliSense Hızlı Bilgi işlemini yönetir. <xref:Microsoft.VisualStudio.Package.ViewFilter> Sınıf <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> komutu <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> aldığında, <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> sınıf, ayrışma nedeni ve komutun gönderildiği anda bakıcının konumu yla yöntemi çağırır. Yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ayrıştırıcısı daha sonra kaynağı verilen konuma ayrıştırmalı ve ardından Hızlı Bilgi aracı ipucunda ne görüntüleneceğini belirlemek için tanımlayıcıyı verilen konumdaki ayrıştırmalıdır.

 Çoğu ayrıştıcı, tüm kaynak dosyanın ilk ayrıştını yapar ve sonuçları ayrışdırıcı bir ağaçta saklar. Tam ayrıştırış yönteme <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> geçirildiğinde gerçekleştirilir. Ayrışma diğer tür sonra istenen bilgileri elde etmek için ayrışma ağacı kullanabilirsiniz.

 Örneğin, ayrışma nedeni değeri <xref:Microsoft.VisualStudio.Package.ParseReason> kaynak konumda tanımlayıcıyı bulabilir ve tür bilgilerini elde etmek için ayrışma ağacında inceleyebilir. Bu tür bilgiler daha <xref:Microsoft.VisualStudio.Package.AuthoringScope> sonra sınıfa aktarılır <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> ve yöntemle döndürülür.
