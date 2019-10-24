---
title: Eski dil hizmeti arabirimleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726855"
---
# <a name="legacy-language-service-interfaces"></a>Eski Dil Hizmeti Arabirimleri
Belirli programlama dilleri için aynı anda bir dil hizmetinin yalnızca bir örneği olabilir. Ancak, tek bir dil hizmeti birden fazla düzenleyiciye hizmet verebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], bir dil hizmetini belirli düzenleyiciyle ilişkilendirmez. Bu nedenle, bir dil hizmeti işlemi istediğinizde uygun düzenleyiciyi parametre olarak tanımlamalısınız.

## <a name="common-interfaces-associated-with-language-services"></a>Dil hizmetleriyle Ilişkili ortak arabirimler
 Düzenleyici, uygun VSPackage üzerinde <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> çağırarak dil hizmetinizi alır. Bu çağrıda geçirilen hizmet KIMLIĞI (SID), istenen dil hizmetini tanımlar.

 Çekirdek dil hizmeti arabirimlerini istediğiniz sayıda ayrı sınıfa uygulayabilirsiniz. Ancak, yaygın bir yaklaşım, aşağıdaki arabirimlerin tek bir sınıfta uygulanması olur:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (isteğe bağlı)

  @No__t_0 arabiriminin tüm dil hizmetlerinde uygulanması gerekir. Dil hizmetiniz hakkında, dilin yerelleştirilmiş adı, dil hizmetiyle ilişkilendirilmiş dosya adı uzantıları ve bir Colorizer alma gibi bilgiler sağlar.

## <a name="additional-language-service-interfaces"></a>Ek dil hizmeti arabirimleri
 Dil hizmetinize başka arabirimler de sağlayabilirsiniz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], metin arabelleğinin her örneği için bu arabirimlerin ayrı bir örneğini ister. Bu nedenle, bu arabirimlerin her birini kendi nesnesi üzerinde uygulamalısınız. Aşağıdaki tabloda, metin arabelleği örneği başına bir örnek gerektiren arabirimler gösterilmektedir.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Açılan çubuk gibi kod penceresi dontiğini yönetir. Bu arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> yöntemini kullanarak alabilirsiniz. Kod penceresi başına bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> vardır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Dil anahtar sözcüklerini ve sınırlandırıcıları renklendirir. Bu arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> yöntemini kullanarak alabilirsiniz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, boyama sırasında çağrılır. @No__t_0 içinde hesaplama yoğun çalışmaktan kaçının veya performans düşebilir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense parametre araç ipuçları sağlar. Dil hizmeti, açık bir parantez gibi Yöntem verilerinin gösterilmesi gerektiğini belirten bir karakter algıladığında, dil hizmetinin bir parametre bilgisi araç Ipucunu görüntülemeye hazırlandığını metin görünümüne bildirmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> yöntemini çağırır. Metin görünümü daha sonra araç ipucunu görüntülemek için gerekli bilgileri almak üzere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> arabiriminin yöntemlerini kullanarak dil hizmetine geri çağrı yapılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense ifadesinin tamamlanmasını sağlar. Dil hizmeti bir tamamlanma listesini görüntülemeye hazırsa, metin görünümünde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemini çağırır. Metin görünümü daha sonra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> nesnesindeki yöntemleri kullanarak dil hizmetine geri çağrı yapılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Komut işleyicisini kullanarak metin görünümü değişikliğine izin verir. @No__t_0 arabirimini uyguladığınız sınıf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimini de uygulamalıdır. Metin görünümü <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemine geçirilen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nesnesini sorgulayarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> nesnesini alır. Her görünüm için bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> nesnesi olmalıdır.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Kullanıcının kod penceresine yazdığında komutları keser. Özel tamamlanma bilgileri sağlamak ve değişiklik görüntülemek için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulamanızdaki çıktıyı izleyin<br /><br /> @No__t_0 nesneniz metin görünümüne geçirmek için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> çağırın.|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Denetim Listesi: Eski Dil Hizmeti Oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)