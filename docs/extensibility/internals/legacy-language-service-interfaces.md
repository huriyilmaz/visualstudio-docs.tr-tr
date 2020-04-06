---
title: Eski Dil Hizmeti Arayüzleri | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707380"
---
# <a name="legacy-language-service-interfaces"></a>Eski Dil Hizmeti Arabirimleri
Belirli bir programlama dili için, aynı anda yalnızca bir dil hizmeti örneği olabilir. Ancak, tek bir dil hizmeti birden fazla düzenleyiciye hizmet verebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bir dil hizmetini belirli bir düzenleyiciyle ilişkilendirmez. Bu nedenle, bir dil hizmeti işlemi isteğinde, bir parametre olarak uygun düzenleyiciyi tanımlamanız gerekir.

## <a name="common-interfaces-associated-with-language-services"></a>Dil Hizmetleriyle İlişkili Ortak Arayüzler
 Editör, uygun VSPackage'ı arayarak <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> dil hizmetinizi alır. Bu çağrıda geçirilen hizmet kimliği (SID), istenen dil hizmetini tanımlar.

 Çekirdek dil hizmeti arabirimlerini herhangi bir sayıda ayrı sınıfüzerinde uygulayabilirsiniz. Ancak, ortak bir yaklaşım tek bir sınıfta aşağıdaki arabirimleri uygulamaktır:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (isteğe bağlı)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Arabirim tüm dil hizmetlerinde uygulanmalıdır. Dilin yerelleştirilmiş adı, dil hizmetiyle ilişkili dosya adı uzantıları ve bir koloratörün nasıl alınabildiğini gibi dil hizmetinizle ilgili bilgiler sağlar.

## <a name="additional-language-service-interfaces"></a>Ek Dil Hizmeti Arayüzleri
 Diğer arabirimler dil hizmetinizle sağlanabilir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]metin arabelleği her örneği için bu arabirimlerin ayrı bir örnek istiyor. Bu nedenle, bu arabirimlerin her birini kendi nesnesi üzerinde uygulamanız gerekir. Aşağıdaki tablo, metin arabellek örneği başına bir örnek gerektiren arabirimleri gösterir.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Açılır pencere çubuğu gibi kod penceresi süslemelerini yönetir. Yöntemi kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> bu arabirimi elde edebilirsiniz. Kod penceresi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> başına bir tane var.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Dil anahtar kelimelerini ve sınır aşanları renklendirin. Yöntemi kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> bu arabirimi elde edebilirsiniz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>boya zamanında denir. İçeride <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> hesaplama yoğun çalışmadan kaçının veya performans zarar görebilir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense parametre araç ipuçları sağlar. Dil hizmeti, açık bir parantez gibi yöntem verilerinin görüntülenmesi gerektiğini belirten bir karakter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> tanıdığında, metin görünümünü dil hizmetinin Parametre Bilgi Araç İpucu görüntülemeye hazır olduğunu bildirme yöntemini çağırır. Metin görünümü daha sonra araç ipucunu görüntülemek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> gerekli bilgileri almak için arabirimin yöntemlerini kullanarak dil hizmetine geri çağırır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense deyiminin tamamlanmasını sağlar. Dil hizmeti bir tamamlama listesi görüntülemeye hazır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> olduğunda, metin görünümünde yöntemi çağırır. Metin görünümü daha sonra <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> nesne üzerindeki yöntemleri kullanarak dil hizmetine geri çağırır.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Komut işleyicisini kullanarak metin görünümünün değiştirilmesine izin verir. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Arabirimi uyguladığınız sınıf da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi uygulamalıdır. Metin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> görünümü, yönteme geçirilen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nesneyi sorgulayarak nesneyi alır. Her görünüm <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> için bir nesne olmalıdır.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Kullanıcının kod penceresine yazdığı komutları keser. Özel tamamlama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> bilgileri sağlamak ve değişiklik görüntülemek için uygulamanızdan çıktıyı izleyin<br /><br /> Nesnenizi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> metin görünümüne geçirmek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>için .|

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Denetim Listesi: Eski Dil Hizmeti Oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
