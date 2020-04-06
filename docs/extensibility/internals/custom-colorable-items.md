---
title: Özel Renklendirilebilir Ürünler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708990"
---
# <a name="custom-colorable-items"></a>Özel renklenebilir öğeler
Dil hizmetinizin bir parçası olarak özel renklenebilir öğeler uygulayarak, anahtar kelimeler ve yorumlar gibi renklendirme türlerinin listesini geçersiz kılabilirsiniz.

## <a name="user-settings-of-colorable-items"></a>Renklenebilir öğelerin kullanıcı ayarları
 **Araçlar** menüsünde **Seçenekler'i** seçip **Çevre**altında **Yazı Tipleri ve Renkler'i** seçerek Yazı Tipleri **ve Renkler** iletişim kutusunu görüntüleyebilirsiniz. **Metin Düzenleyicisi** veya **Komut Penceresi**gibi bir ekran seçtiğinizde, **Ekran öğeleri** listesi kutusu bu ekran için renklendirilebilir tüm öğeleri gösterir. Renklenebilir her öğe için yazı tipini, boyutunu, ön plan rengini ve arka plan rengini görüntüleyebilir ve değiştirebilirsiniz. Seçimleriniz kayıt defterindeki bir önbellekte depolanır ve renklenebilir madde adı tarafından erişilir.

## <a name="presentation-of-colorable-items"></a>Renklendirilebilir öğelerin sunumu
 IDE, **Yazı Tipleri ve Renkler** iletişim kutusundaki renklendirilebilir öğelerin kullanıcı geçersiz kılmalarını işlediği için, yalnızca her özel renklendirilebilir öğeyi bir adla sağlamanız gerekir. Bu ad, **Görüntü öğeleri** listesinde görünen addır. Renklendirilebilir öğeler alfabetik sırada görünür. Dil hizmetinizin özel renklenebilir öğelerini gruplandırmak için, her isme dil adınız ile başlayabilirsiniz, örneğin **NewLanguage - Comment** ve **NewLanguage - Keyword**.

> [!CAUTION]
> Varolan renklendirilebilir öğe adlarıyla çakışmayı önlemek için dil adını renklendirilebilir öğe adına eklemeniz gerekir. Geliştirme sırasında renklendirilebilir öğelerden birinin adını değiştirirseniz, renklenebilir öğelerinize ilk erişiğinde oluşturulan önbelleği sıfırlamanız gerekir. Genellikle dizinde Visual Studio SDK ile yüklenen **CreateExpInstance** aracıyla deneysel önbelleği sıfırlayabilirsiniz:
>
> *C:\Program Dosyaları (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Önbelleği sıfırlamak için **CreateExpInstance /Reset**'i girin. **CreateExpInstance**hakkında daha fazla bilgi için [createExpInstance yardımcı programı'na](../../extensibility/internals/createexpinstance-utility.md)bakın.

 Renklendirilebilir öğeler listenizdeki ilk öğeye hiçbir zaman başvurulmaz. İlk madde 0 renklendirilebilir madde dizinine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] karşılık gelir ve her zaman bu öğe için varsayılan metin renklerini ve özniteliklerini sağlar. Bu başvurulan amayan maddeyle başa çıkmanın en kolay yolu, listenizde ilk öğe olarak yer tutucu renklendirilebilir bir öğe sağlamaktır.

## <a name="implement-custom-colorable-items"></a>Özel renklendirilebilir öğeler uygulama

1. Anahtar Kelime, Operatör ve Tanımlayıcı gibi dilinizde renklendirilmesi gerekenleri tanımlayın.

2. Bu renklendirilebilir öğelerin numaralandırma oluşturun.

3. Ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerini numaralandırılmış değerlerle ilişkilendirin.

    Örneğin, belirteç türlerini temsil eden değerler, özel renklendirilebilir öğeler numaralandırmasında aynı değerler olabilir.

4. Nesnenizdeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> yöntemin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> uygulanmasında, öznitelikler listesini, ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerine karşılık gelen özel renklendirilebilir öğeler numaralandırmanızdaki değerlerle doldurun.

5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Arabirimi uygulayan aynı sınıfta, arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> ve iki yöntemini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ve. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>

6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimini gerçekleştirin.

7. 24 bit veya yüksek renk değerlerini desteklemek istiyorsanız, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi de uygulayın.

8. Dil hizmeti nesnenizde, aracınızın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> veya tarayıcınızın tanımlayabileceği her renklendirilebilir öğe için bir tane olmak üzere nesnelerinizi içeren bir liste oluşturun.

    Özel renklenebilir öğeler numaralandırmadan karşılık gelen değeri kullanarak listedeki her öğeye erişebilirsiniz. Numaralandırma değerlerini listeye dizin olarak kullanın. Listedeki ilk öğeye hiçbir zaman erişilemez, çünkü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] her zaman kendini işleyen varsayılan metin stiline karşılık gelir. Listenizin başına bir yer tutucu renklendirilebilir öğe ekleyerek bunu telafi edebilirsiniz.

9. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> Yöntemin uygulanmasında, özel renklenebilir öğeler listenizdeki öğe sayısını döndürün.

10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Yöntemin uygulanmasında, isteği edilen renklendirilebilir öğeyi listenizden döndürün.

    Arabirimlerin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> ve arabirimlerin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> nasıl uygulanacağı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>yla ilgili bir örnek için bkz.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski bir dil hizmeti modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Özel editörlerde sözdizimi boyama](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski bir dil hizmetinde sözdizimi boyama](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Sözdizimi boyama uygulama](../../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl kullanılır: Yerleşik renklendirilebilir öğeleri kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
