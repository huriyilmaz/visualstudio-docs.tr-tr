---
title: Eski Dil Hizmeti Arabirimleri | Microsoft Docs
description: Eski dil hizmeti özellikleri sağlayan Visual Studio SDK'sı ile kullanılabilen arabirimler hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 670e8d5f8509aa3d61a23f674e2d584c9ce04c8f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725052"
---
# <a name="legacy-language-service-interfaces"></a>Eski Dil Hizmeti Arabirimleri
Belirli bir programlama dili için aynı anda dil hizmetinin yalnızca bir örneği olabilir. Ancak, tek bir dil hizmeti birden fazla düzenleyiciye hizmet olabilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir dil hizmetini belirli bir düzenleyiciyle ilişkilendirmez. Bu nedenle dil hizmeti işlemi isteğinde bulundurarak uygun düzenleyiciyi parametre olarak tanımlamanız gerekir.

## <a name="common-interfaces-associated-with-language-services"></a>Dil Hizmetleriyle İlişkili Ortak Arabirimler
 Düzenleyici, uygun <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> VSPackage'ı çağırarak dil hizmetinizi alır. Bu çağrıda geçirilen hizmet kimliği (SID), istenen dil hizmetini tanımlar.

 Çekirdek dil hizmeti arabirimlerini herhangi bir sayıda ayrı sınıfa uygulayabilirsiniz. Ancak, yaygın bir yaklaşım aşağıdaki arabirimleri tek bir sınıfta uygulamaktır:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (isteğe bağlı)

  Arabirimin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> tüm dil hizmetlerinde uygulanması gerekir. Dil hizmetiniz hakkında, dilin yerelleştirilmiş adı, dil hizmetiyle ilişkili dosya adı uzantıları ve bir renklandırıcının nasıl alın olduğu gibi bilgiler sağlar.

## <a name="additional-language-service-interfaces"></a>Ek Dil Hizmeti Arabirimleri
 Diğer arabirimler dil hizmetinize sağlanıyor olabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , metin arabelleğinin her örneği için bu arabirimlerin ayrı bir örneğini talep ediyor. Bu nedenle, bu arabirimlerin her birini kendi nesnesine uygulamalısiniz. Aşağıdaki tabloda, metin arabelleği örneği başına bir örnek gerektiren arabirimler yer almaktadır.

|Arabirim|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Açılan çubuk gibi kod penceresi donatmalarını yönetir. bu arabirimi almak için yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> kullanabilirsiniz. Kod penceresi başına <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> bir tane vardır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Dil anahtar sözcüklerini ve sınırlayıcıları renklendirme. bu arabirimi almak için yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> kullanabilirsiniz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> boya zamanında çağrılır. İşlem yoğun işlerden kaçının veya <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> performans düşük olabilir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense parametre araç ipucu sağlar. Dil hizmeti, açık parantez gibi yöntem verilerini görüntülemesi gerektiğini belirten bir karakter tanırsa, dil hizmetinin Parametre Bilgisi Araç İpucu görüntülemeye hazır olduğunu metin görünümüne bildirmek için yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> çağırır. Metin görünümü daha sonra araç ipucu görüntülemek için gerekli bilgileri almak için arabiriminin yöntemlerini kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> dil hizmetine geri çağrılar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense deyiminin tamamlanmasını sağlar. Dil hizmeti tamamlanma listesini görüntülemeye hazır olduğunda metin görünümünde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemini çağırtır. Metin görünümü daha sonra nesnede yöntemleri kullanarak dil hizmetine geri <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> çağrır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Komut işleyicisi kullanılarak metin görünümünün değiştirilmesine izin verir. Arabirimini uygulayan sınıf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> da arabirimini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulamalı. Metin görünümü, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> yöntemine geçirilen nesneyi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> sorgular. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Her görünüm için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> bir nesne olması gerekir.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Kullanıcının kod penceresine türemiş olduğu komutları kesme noktası. Özel tamamlama bilgileri sağlamak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ve değişikliği görüntülemek için uygulama çıkışınızı izleme<br /><br /> Nesnenizi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> metin görünümüne geçmek için çağrısına <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> tıklayın.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Yapılacaklar listesi: Eski Dil Hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
