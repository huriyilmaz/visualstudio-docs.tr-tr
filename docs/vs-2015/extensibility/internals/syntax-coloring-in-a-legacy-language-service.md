---
title: Eski dil hizmetinde söz dizimi renklendirmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59d25c338cb0c7406c533afeceaf3675fbd16e96
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815203"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , dilin öğelerini tanımlamak ve bir düzenleyicide belirtilen renklerle göstermek için bir renklendirme hizmeti kullanır.  
  
## <a name="colorizer-model"></a>Colorizer modeli  
 Dil hizmeti, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Düzenleyici tarafından kullanılan arabirimini uygular. Bu uygulama, aşağıdaki çizimde gösterildiği gibi dil hizmetinden ayrı bir nesnedir.  
  
 ![SVC Colorizer grafiği](../../extensibility/internals/media/figlgsvccolorizer.gif "FigLgSvcColorizer")  
Basit Colorizer modeli  
  
> [!NOTE]
> Sözdizimi renklendirme hizmeti, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] metin renklendirme için genel mekanizmasından ayrıdır. Renklendirme destekleyen genel mekanizma hakkında daha fazla bilgi için [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] bkz. [yazı tipi ve renk kullanımı](../../extensibility/using-fonts-and-colors.md).  
  
 Colorizer 'ın yanı sıra dil hizmeti, özel renklenebilir öğeler sunmasının duyurularak düzenleyici tarafından kullanılan özel renklenebilir öğeler sağlayabilir. Bunu, arabirimini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> uygulayan aynı nesne üzerinde arabirimini uygulayarak yapabilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . Düzenleyici yöntemi çağırdığında özel renklenebilir öğelerin sayısını döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ve düzenleyici yöntemi çağırdığında özel renklenebilir tek bir öğe döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Yöntemi, arabirimini uygulayan bir nesne döndürür <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> . Dil hizmeti, 24 bit veya yüksek renk değerlerini destekliyorsa, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi arabirimi ile aynı nesne üzerinde uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .  
  
## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage bir dil hizmeti renklendirme özelliğini nasıl kullanır?  
  
1. VSPackage 'ın, dil hizmeti VSPackage 'ın aşağıdakileri yapması için uygun dil hizmetini alması gerekir:  
  
    1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>Renklendirilebilen metni almak için arabirimi uygulayan bir nesne kullanın.  
  
         Metin, genellikle arabirimini uygulayan bir nesne kullanılarak görüntülenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
    2. Dil hizmeti GUID 'SI için VSPackage hizmet sağlayıcısını sorgulayarak dil hizmetini alın. Dil Hizmetleri, kayıt defterinde dosya uzantısına göre tanımlanır.  
  
    3. Yöntemini çağırarak dil hizmetini ile ilişkilendirin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .  
  
2. VSPackage artık colorizer nesnesini şu şekilde alabilir ve kullanabilir:  
  
    > [!NOTE]
    > Çekirdek düzenleyiciyi kullanan VSPackages, dil hizmetinin Colorizer nesnelerini açıkça almak zorunda değildir. Temel düzenleyicinin bir örneği uygun bir dil hizmetini edindiği anda, burada gösterilen tüm renklendirme görevlerini gerçekleştirir.  
  
    1. `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Dil hizmetinin nesnesi üzerinde yöntemini çağırarak, ve arabirimlerini uygulayan dil hizmetinin colorizer nesnesini edinin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .  
  
    2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Belirli bir metin aralığı için Colorizer bilgilerini elde etmek için yöntemini çağırın.  
  
         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metin alanındaki renklendirilmiş olan her karakter için bir değer dizisi döndürür. Değerler, çekirdek Düzenleyici tarafından tutulan varsayılan renklenebilir öğe listesi ya da dil hizmetinin kendisi tarafından tutulan özel renklenebilir bir öğe listesi olan renklenebilir bir öğe listesi halinde dizinlerdir.  
  
    3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Seçili metni göstermek için yöntemi tarafından döndürülen renklendirme bilgilerini kullanın.  
  
> [!NOTE]
> Bir dil hizmeti renklendirme kullanmanın yanı sıra, VSPackage da genel amaçlı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] metin renklendirme mekanizmasını de kullanabilir. Bu mekanizma hakkında daha fazla bilgi için bkz. [yazı tiplerini ve renkleri kullanma](../../extensibility/using-fonts-and-colors.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Söz Dizimi Renklendirmesi Uygulama](../../extensibility/internals/implementing-syntax-coloring.md)  
 Bir düzenleyicinin dil hizmetinin sözdizimi renklendirmesini ve dil hizmetinin sözdizimi renklendirmesini desteklemek için ne uygulaması gerektiğini açıklar.  
  
 [Nasıl yapılır: Yerleşik Renklendirilebilir Öğeleri Kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)  
 Dil hizmetinden yerleşik renklenebilir öğelerin nasıl kullanıldığını gösterir.  
  
 [Özel Renklendirilebilir Öğeler](../../extensibility/internals/custom-colorable-items.md)  
 Özel renklenebilir öğelerin nasıl uygulanacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı Tiplerini ve Renkleri Kullanma](../../extensibility/using-fonts-and-colors.md)
