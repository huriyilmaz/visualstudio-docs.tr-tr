---
title: 'Nasıl yapılır: model 3-b Teryağmur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: f779b1fd-82a9-4a11-8ab7-c1c9caabc883
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ab202ed97ce2056313eb661d51d7150bb9689829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664421"
---
# <a name="how-to-model-3-d-terrain"></a>Nasıl Yapılır: Model 3B Arazi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede 3B teryağmm modeli oluşturmak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilir.

 Bu belge Şu etkinlikleri gösterir:

- Sahneye nesne ekleme

- Yüzeyleri ve noktaları seçme

- Seçimleri çevirme

- Alt **bölüte yüzey** aracını kullanma

- Tasarım yüzeyinde bir nesneyi çerçevelendirme

## <a name="creating-a-3-d-terrain-model"></a>3B teryağmm modeli oluşturma
 Ek yüzler oluşturmak için bir düzlemi bölerek 3-b bir termi oluşturabilirsiniz, sonra da köşelerini düzenleyerek ilginç terde özellikler oluşturabilirsiniz.

 İşiniz bittiğinde, modelin şöyle görünmesi gerekir:

 ![bir teryağmm modeli gösteren 3&#45;D sahneyi](../designers/media/digit-terrain-model.png "Basamak Teryağmur-model")

 Başlamadan önce, **Özellikler** penceresi ve **araç kutusunun** görüntülendiğinden emin olun.

#### <a name="to-create-a-3-d-terrain-model"></a>3B bir teryağmm modeli oluşturmak için

1. Birlikte çalışmak için 3-b model oluşturun. Projenize bir model ekleme hakkında daha fazla bilgi için, bkz. [Model Düzenleyicisi](../designers/model-editor.md)'ndeki Başlarken bölümü.

2. Sahneye bir düzlem ekleyin. **Araç kutusunda**, **şekiller**altında **düzlem** ' i seçin ve tasarım yüzeyine taşıyın.

   > [!TIP]
   > Düzlem nesnesinin ile çalışmayı kolaylaştırmak için, Tasarım yüzeyinde çerçeveye taşıyabilirsiniz. **Seç** modunda, düzlem nesnesini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çerçeve nesnesi** düğmesini seçin.

3. Yüz seçimi modunu girin. Model Düzenleyicisi araç çubuğunda **yüz seç**' i seçin.

4. Düzlemi alt bölümlere ayır. Yüz seçimi modunda, seçim için etkinleştirmek üzere düzlemi bir kez seçtikten sonra tek yüzeyi seçmek için yeniden seçin. Model Düzenleyicisi araç çubuğunda alt **bölümlere**ayır ' ı seçin. Bu, düzlemi eşit olarak boyutlandırılmış dört bölüme bölünmüş yeni köşeler ekler.

5. Daha fazla alt bölüm oluşturun. Yeni yüzler hala seçili durumdayken alt **bölüyi** iki kez seçin. Bu, Toplam 64 yüz oluşturur. Daha fazla alt bölüm oluşturarak, daha fazla ayrıntı sağlayabilirsiniz.

6. Nokta seçimi modunu girin. Model Düzenleyicisi araç çubuğunda **nokta seç**' i seçin.

7. Bir noktayı bir teryağmi özelliği oluşturacak şekilde değiştirin. Nokta seçimi modunda noktalarından birini seçin ve ardından Model Düzenleyicisi araç çubuğunda **çevir** aracını seçin. Tasarım yüzeyinde, noktayı temsil eden bir kutu görüntülenir. Kutuyu taşımak için yeşil oku kullanın ve bu nedenle noktanın yüksekliğini değiştirin. İlginç teryağmur özellikleri oluşturmak için bu adımı farklı noktalara tekrarlayın.

   > [!TIP]
   > Tek seferde çeşitli noktaları seçerek tek tek seçebilirsiniz.

   Teryağma modeli tamamlanmıştır. İşte Phong gölgeleme uygulanmış son model:

   ![bir teryağmm modeli gösteren 3&#45;D sahneyi](../designers/media/digit-terrain-model.png "Basamak Teryağmur-model")

   [Nasıl yapılır: geometri tabanlı Gradyan Gölgelendirici Oluşturma](../designers/how-to-create-a-geometry-based-gradient-shader.md)bölümünde açıklanan gradyan gölgelendiricisi efektini göstermek için bu teryağmur modelini kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Model Düzenleyicisi](../designers/model-editor.md)
