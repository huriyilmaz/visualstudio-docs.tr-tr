---
title: Özel Renklendirmeli Öğeler | Microsoft Docs
description: Yazı Tipleri ve Renkler iletişim kutusundaki anahtar sözcükler ve açıklamalar gibi öğeleri geçersiz karak dil hizmetinin bir parçası olarak özel renklenebilir öğeler oluşturma hakkında bilgi.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 662b440b716eed2f878f6ede3e21e7339ab209ded5055e8dbd0dcca02017d408
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121261378"
---
# <a name="custom-colorable-items"></a>Özel renkleştirilebilir öğeler
Dil hizmetinizin bir parçası olarak özel renklendirme öğeleri uygulayarak anahtar sözcükler ve açıklamalar gibi renklendirme türleri listesini geçersiz kılabilirsiniz.

## <a name="user-settings-of-colorable-items"></a>Renkleştirilebilir öğelerin kullanıcı ayarları
 Araçlar menüsünde **Seçenekler'i ve** ardından  Ortam'ın  altında Yazı Tipleri ve Renkler'i seçerek Yazı Tipleri ve **Renkler iletişim kutusunu** **görüntüebilirsiniz.** Metin Düzenleyici veya Komut  Penceresi gibi bir görüntü  **seçerek** Öğeleri görüntüle liste kutusu söz konusu görüntü için tüm renkleştirilebilir öğeleri gösterir. Renkleştirilebilir her öğe için yazı tipini, boyutu, ön plan rengini ve arka plan rengini görüntüp değiştirebilirsiniz. Seçimleriniz kayıt defterindeki bir önbellekte depolanır ve renklenebilir öğe adıyla erişilir.

## <a name="presentation-of-colorable-items"></a>Renkleştirilebilir öğelerin sunumu
 IDE, Yazı Tipleri ve Renkler iletişim kutusundaki  renkleştirilebilir öğelerin kullanıcı geçersiz kılmalarını işleyene kadar her özel renklenebilir öğeyi yalnızca bir adla birlikte sağlarsınız. Bu ad, Öğeleri görüntüle listesinde **görünen addır.** Renklendirmek öğeler alfabetik sırada görünür. Dil hizmetinizin özel renklendirme öğelerini gruplandırarak her bir adı kendi dil adınızla (örneğin, **NewLanguage - Comment** ve **NewLanguage - Anahtar Sözcüğü) başlatabilirsiniz.**

> [!CAUTION]
> Mevcut renklenebilir öğe adlarında çakışmaları önlemek için dil adını renklendirmeli öğe adına dahil etmek gerekir. Geliştirme sırasında renklendirmek istediğiniz öğelerden birinin adını değiştirirsanız, renkleştirilebilir öğelerinize ilk kez erişilirken oluşturulan önbelleği sıfırlamanız gerekir. Deneysel önbelleği, genellikle Visual Studio SDK'sı ile yüklenmiş **createExpInstance** aracıyla sıfırlayabilirsiniz. Bu araç genellikle Visual Studio klasöründedir:
>
> *VSSDK\VisualStudioIntegration\Tools\Bin*
>
> Önbelleği sıfırlamak için **CreateExpInstance /Reset girin.** **CreateExpInstance hakkında daha fazla bilgi için** bkz. [CreateExpInstance yardımcı programı.](../../extensibility/internals/createexpinstance-utility.md)

 Renkleştirilebilir öğeler listenizdeki ilk öğeye hiçbir zaman başvurulamaz. İlk öğe 0 renkleştirilebilir öğe dizinine karşılık geliyor ve her zaman bu öğe için varsayılan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metin renklerini ve özniteliklerini sağlar. Bu çıkarımsız öğeyle ilgilenmenin en kolay yolu, ilk öğe olarak listenize renklenebilir bir yer tutucu öğesi sağlamaktır.

## <a name="implement-custom-colorable-items"></a>Özel renkleştirilebilir öğeler uygulama

1. Anahtar Sözcük, İşleç ve Tanımlayıcı gibi, dilinize renklendirmesi gerekenleri tanımlayın.

2. Bu renkleştirilebilir öğelerin bir numaralama oluşturun.

3. Ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerini numaralandı değerlerle ilişkilendirme.

    Örneğin, belirteç türlerini temsil eden değerler, özel renklenebilir öğe numaralamada aynı değerler olabilir.

4. Nesnenize yöntemi uygulamanıza, öznitelikler listesini ayrıştırıcıdan veya tarayıcıdan döndürülen belirteç türlerine karşılık gelen özel renkleştirilebilir öğe numaralama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> değerleriyle doldurun.

5. Arabirimini uygulayan aynı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> sınıfta, arabirimini ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> iki yöntemini (ve) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> kullanın.

6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> arabirimini gerçekleştirin.

7. 24 bit veya yüksek renk değerlerini desteklemek için arabirimini de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> kullanın.

8. Dil hizmeti nesnesinde, ayrıştırıcınız veya tarayıcınız tarafından tanımlanılabilir her öğe için bir tane olmak için nesnelerinizi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> içeren bir liste oluşturun.

    Özel renklendirmeli öğeler listesinden karşılık gelen değeri kullanarak listede yer alan her öğeye erişebilirsiniz. Listede dizin olarak numaralama değerlerini kullanın. Listede yer alan ilk öğeye hiçbir zaman erişilemez çünkü her zaman kendisini ele alan varsayılan metin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stiline karşılık gelir. Listenizin başına renklenebilir bir yer tutucu öğesi ekerek bunu telafi edilebilirsiniz.

9. yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> uygulamanıza, özel renkleştirilebilir öğeler listenizdeki öğe sayısını girin.

10. yöntemi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> uygulamanıza, istenen renklendirmeli öğeyi listenizden geri girin.

    ve arabirimlerinin nasıl <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> uygulandığının bir örneği için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .

## <a name="see-also"></a>Ayrıca bkz.
- [Eski dil hizmetinin modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [Özel düzenleyicilerde söz dizimi renklendirmesi](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Eski dil hizmetlerinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Söz dizimi renklendirmesi uygulama](../../extensibility/internals/implementing-syntax-coloring.md)
- [Nasıl kullanılır: Yerleşik renklenebilir öğeleri kullanma](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
