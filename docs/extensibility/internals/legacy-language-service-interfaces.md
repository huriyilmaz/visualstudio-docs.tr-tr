---
title: Eski dil hizmeti arabirimleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707380"
---
# <a name="legacy-language-service-interfaces"></a>Eski Dil Hizmeti Arabirimleri
Belirli programlama dilleri için aynı anda bir dil hizmetinin yalnızca bir örneği olabilir. Ancak, tek bir dil hizmeti birden fazla düzenleyiciye hizmet verebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , bir dil hizmetini belirli düzenleyiciyle ilişkilendirmez. Bu nedenle, bir dil hizmeti işlemi istediğinizde uygun düzenleyiciyi parametre olarak tanımlamalısınız.

## <a name="common-interfaces-associated-with-language-services"></a>Dil hizmetleriyle Ilişkili ortak arabirimler
 Düzenleyici, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> uygun VSPackage 'ı çağırarak dil hizmetinizi alır. Bu çağrıda geçirilen hizmet KIMLIĞI (SID), istenen dil hizmetini tanımlar.

 Çekirdek dil hizmeti arabirimlerini istediğiniz sayıda ayrı sınıfa uygulayabilirsiniz. Ancak, yaygın bir yaklaşım, aşağıdaki arabirimlerin tek bir sınıfta uygulanması olur:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (isteğe bağlı)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>Arabirimin tüm dil hizmetlerinde uygulanması gerekir. Dil hizmetiniz hakkında, dilin yerelleştirilmiş adı, dil hizmetiyle ilişkilendirilmiş dosya adı uzantıları ve bir Colorizer alma gibi bilgiler sağlar.

## <a name="additional-language-service-interfaces"></a>Ek dil hizmeti arabirimleri
 Dil hizmetinize başka arabirimler de sağlayabilirsiniz. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Metin arabelleğinin her örneği için bu arabirimlerin ayrı bir örneğini ister. Bu nedenle, bu arabirimlerin her birini kendi nesnesi üzerinde uygulamalısınız. Aşağıdaki tabloda, metin arabelleği örneği başına bir örnek gerektiren arabirimler gösterilmektedir.

|Arabirim|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Açılan çubuk gibi kod penceresi dontiğini yönetir. Yöntemini kullanarak bu arayüzü edinebilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>Kod penceresi başına bir tane vardır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Dil anahtar sözcüklerini ve sınırlandırıcıları renklendirir. Yöntemini kullanarak bu arayüzü edinebilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> , boyama sırasında çağrılır. Hesaplamanın yoğun <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> çalışmasından kaçının veya performans düşebilir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense parametre araç ipuçları sağlar. Dil hizmeti, açık bir parantez gibi Yöntem verilerinin gösterilmesi gerektiğini belirten bir karakter algıladığında, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> dil hizmetinin bir parametre bilgisi araç ipucunu görüntülemeye hazırlandığını metin görünümüne bildirmek için yöntemini çağırır. Metin görünümü daha sonra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> araç ipucunu görüntülemek üzere gerekli bilgileri almak için arabirimin yöntemlerini kullanarak dil hizmetine geri çağrı yapılır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense ifadesinin tamamlanmasını sağlar. Dil hizmeti bir tamamlanma listesini görüntülemeye hazırsanız, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi metin görünümünde çağırır. Metin görünümü daha sonra nesne üzerindeki yöntemleri kullanarak dil hizmetine geri çağrı yapılır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Komut işleyicisini kullanarak metin görünümü değişikliğine izin verir. Arabirimini uyguladığınız sınıf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Ayrıca arabirimini de uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Metin görünümü, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> yöntemine geçirilen nesneyi sorgulayarak nesneyi alır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>Her görünüm için bir nesne olmalıdır.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Kullanıcının kod penceresine yazdığında komutları keser. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Özel tamamlanma bilgileri sağlamak ve değişiklik görüntülemek için uygulamanızdaki çıktıyı izleyin<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Nesneniz metin görünümüne geçirmek için çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Yapılacaklar listesi: Eski Dil Hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
