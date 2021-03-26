---
title: Özel Renklenebilir öğeler | Microsoft Docs
description: Anahtar sözcükler ve açıklamalar gibi yazı tipi ve renkler iletişim kutusunda öğeleri geçersiz kılarak dil hizmetinin bir parçası olarak özel renklenebilir öğeler oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f08c5c9e533e3a21ec4b87e7d148c3022ee0fed1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056810"
---
# <a name="custom-colorable-items"></a>Özel renklenebilir öğeler
Dil hizmetinizin bir parçası olarak özel renklenebilir öğeler uygulayarak, anahtar sözcükler ve açıklamalar gibi renklendirime için tür listesini geçersiz kılabilirsiniz.

## <a name="user-settings-of-colorable-items"></a>Renklenebilir öğelerin Kullanıcı ayarları
 **Araçlar** menüsünde **Seçenekler** ' i ve ardından **ortam** altında **yazı tipi ve renkler** ' i seçerek **yazı tipi ve renkler** iletişim kutusunu görüntüleyebilirsiniz. **Metin düzenleyici** veya **komut penceresi** gibi bir görüntü seçtiğinizde, **öğeleri görüntüle** liste kutusu bu ekran için renklenebilir tüm öğeleri gösterir. Renklenebilir her öğe için yazı tipi, boyut, ön plan rengi ve arka plan rengini görüntüleyebilir ve değiştirebilirsiniz. Seçimleriniz kayıt defterindeki bir önbellekte depolanır ve renklenebilir öğe adı tarafından erişilir.

## <a name="presentation-of-colorable-items"></a>Renklenebilir öğelerin sunumu
 IDE, **yazı tipi ve renkler** iletişim kutusunda renklenebilir öğelerin Kullanıcı geçersiz kılmalarını işlediği için, yalnızca bir özel renklenebilir öğeyi bir adla sağlamanız gerekir. Bu ad, **görüntüleme öğeleri** listesinde görünür. Renklenebilir öğeler alfabetik sırada görünür. Dil hizmetinizin özel renklenebilir öğelerini gruplandırmak için, her bir adı dil adınızla başlatabilir, örneğin **NewLanguage-Comment** ve **NewLanguage-anahtar sözcüğü**.

> [!CAUTION]
> Var olan renklenebilir öğe adlarıyla çarpışmalardan kaçınmak için renklendirilebilir öğe adına dil adını dahil etmelisiniz. Geliştirme sırasında renklenebilir öğelerinizin birinin adını değiştirirseniz, renksiz öğelerinize erişildiği sırada oluşturulan önbelleği sıfırlamanız gerekir. Deneysel önbelleği, genellikle dizininde Visual Studio SDK ile yüklenen **CreateExpInstance** aracıyla sıfırlayabilirsiniz:
>
> *C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Önbelleği sıfırlamak için **CreateExpInstance/Reset** girin. **CreateExpInstance** hakkında daha fazla bilgi için bkz. [CreateExpInstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md).

 Renklenebilir öğeler listenizdeki ilk öğeye hiçbir şekilde başvurulmuyor. İlk öğe, 0 renklenebilir bir öğe dizinine karşılık gelir ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bu öğe için her zaman varsayılan metin renkleri ve özniteliklerini sağlar. Başvurulmayan bu öğeyle ilgilenmenin en kolay yolu, listenizde ilk öğe olarak yer tutucu renklenebilir bir öğe sağlamadır.

## <a name="implement-custom-colorable-items"></a>Özel renklenebilir öğeler uygulama

1. Dilinizde renk sözcük, Işleç ve tanımlayıcı gibi renklendirilmiş olması gereken öğeleri tanımlayın.

2. Renklenebilir bu öğelerin bir listesini oluşturun.

3. Bir Ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerini numaralandırılmış değerlerle ilişkilendirin.

    Örneğin, belirteç türlerini temsil eden değerler özel renklenebilir öğeler numaralandırmasında aynı değerler olabilir.

4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>Nesnenizin içindeki yöntemi uygulamanızda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> , öznitelikler listesini, Ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerine karşılık gelen özel renksiz öğelerinizdeki değerlerle birlikte doldurabilirsiniz.

5. Arabirimini uygulayan sınıfta, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> arabirimini ve iki yöntemini uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimini gerçekleştirin.

7. 24 bit veya yüksek renk değerlerini desteklemek istiyorsanız, arabirimi de uygulayın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

8. Dil hizmeti nesneniz ' nde, tek yapmanız gereken <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> , ayrıştırıcılarınızın veya tarayıcınızın tanımlayabilecek her renksiz öğe için, nesnelerinizi içeren bir liste oluşturun.

    Özel renklenebilir öğeler numaralandırmasından karşılık gelen değeri kullanarak listedeki her öğeye erişebilirsiniz. Liste içinde numaralandırma değerlerini bir dizin olarak kullanın. Her zaman kendisini işleyen varsayılan metin stiline karşılık geldiğinden, listedeki ilk öğeye hiçbir zaman erişilmez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Listenizin başlangıcına yer tutucu renklenebilir bir öğe ekleyerek bunu dengeleyerek yapabilirsiniz.

9. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A>Yöntemi uygulamanızda, özel renklenebilir öğeler listenizdeki öğelerin sayısını döndürün.

10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>Yöntemi uygulamanızda, istenen renklenebilir öğeyi listenizden döndürün.

    Ve arabirimlerinin nasıl uygulanacağı hakkında bir örnek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> bkz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> ..

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmeti modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Sözdizimi renklendirmesini Uygula](../../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl yapılır: yerleşik renklenebilir öğeleri kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
