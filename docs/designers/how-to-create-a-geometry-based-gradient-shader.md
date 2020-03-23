---
title: 'Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96326910a04294e30c410cc96bf9c600bfb3f17c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589466"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl yapılır: Geometri tabanlı gradyan gölgelendirici oluşturma

Bu makalede, geometri tabanlı degrade shader oluşturmak için Shader Designer ve Directed Graph Shader Dili nasıl kullanılacağını göstermektedir. Bu gölgeli, sabit bir RGB renk değerini dünya uzayında bir nesnenin her noktasının yüksekliğine göre ölçeklendiriyor.

## <a name="create-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma

Pikselin konumunu gölgenize ekleyerek geometri tabanlı bir gölgeuygulayabilirsiniz. Gölgelendirme dillerinde, bir piksel 2B ekranda yalnızca renginden ve konumundan daha fazla bilgi içerir. Bazı sistemlerde *parça* olarak bilinen piksel, bir piksele karşılık gelen yüzeyi açıklayan değerler topluluğudur. Bu belgede açıklanan gölgeleyici, parçanın son çıkış rengini etkilemek için dünya uzayında bir 3B nesnenin her pikselinin yüksekliğini kullanır.

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgeleyici oluşturun. Projenize DGSL shader nasıl ekleyeceğiniz hakkında bilgi [için, Shader Designer'daki](../designers/shader-designer.md)Başlarken bölümüne bakın.

2. Nokta **Rengi** düğümünden **Son Renk** düğümünden bağlantı nı kesin. **Nokta Rengi** düğümünün **RGB** terminalini seçin ve ardından **Bağlantıları Kır'ı**seçin. Bu, bir sonraki adımda eklenen düğüm için yer sağlar.

3. Grafiğe bir **Çarpma** düğümü ekleyin. Araç **Kutusunda**, **Matematik**altında, **Çarpın'ı** seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe Maske **Vektör** düğümü ekleyin. Araç **Kutusunda**, **Utility**altında Maske **Vektör'ü** seçin ve tasarım yüzeyine taşıyın.

5. **Maske Vektör** düğümü için maske değerlerini belirtin. **Select** modunda Maske **Vektör** düğümünü seçin ve **ardından Özellikler** penceresinde Yeşil **/ Y** özelliğini **True**olarak ayarlayın ve ardından Kırmızı **/ X,** **Mavi / Z** ve Alfa / **W** özelliklerini **False**olarak ayarlayın. Bu örnekte, **Kırmızı / X**, Yeşil / **Y**ve Mavi **/ Z** özellikleri **Dünya Konum** düğümünün x, y ve z bileşenlerine karşılık gelir ve Alfa / **W** kullanılmaz. Yalnızca **Yeşil / Y** **True**olarak ayarlandığından, giriş vektörünün yalnızca y bileşeni maskelen edildikten sonra kalır.

6. Grafiğe bir **Dünya Konumu** düğümü ekleyin. Araç **Kutusunda**, **Sabitler**altında, **Dünya Konumu'nu** seçin ve tasarım yüzeyine taşıyın.

7. Parçanın dünya uzay konumunu maskeleyin. **Select** modunda, **Dünya Pozisyon** düğümünün **Çıkış** terminalini Maske **Vektör** düğümünün **Vektör** terminaline taşıyın. Bu bağlantı, x ve z bileşenlerini yoksaymak için parçanın konumunu maskeler.

8. RGB renk sabitini maskeli dünya uzay konumuyla çarpın. **Nokta Rengi** düğümünün **RGB** terminalini **Çarpım** düğümünün **Y** terminaline taşıyın ve ardından **Maske Vektör** düğümünün **Çıkış** terminalini **Çarpım** düğümünün **X** terminaline taşıyın. Bu bağlantı, renk değerini dünya uzayında pikselin yüksekliğine göre ölçekler.

9. Ölçeklenmiş renk değerini son renge bağlayın. **Çarpma** düğümünün **Çıkış** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın.

Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir küreye uygulanan gölgeli bir önizleme gösterilmektedir.

> [!NOTE]
> Bu resimde, gölgeleyicinin etkisini daha iyi göstermek için turuncu bir renk belirtilir, ancak önizleme şekli dünya alanında bir konuma sahip olmadığından, gölgeleyici Shader Designer'da tam olarak önizleme yapılamaz. Tam etkiyi göstermek için gölgelendirici gerçek bir sahnede önizlemeli olmalıdır.

![Shader grafiği ve etkisinin önizlemesi](../designers/media/digit-gradient-effect-graph.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgelilerin önizlemesi hakkında bilgi için Bkz. [Shader Designer'da](../designers/shader-designer.md) **Gölgeli'yi Önizleme.**

Aşağıdaki resimde, bu belgede açıklanan gölgeleyici nasıl gösterilir 3B sahneye [uygulanır: Model 3D arazi.](../designers/how-to-model-3-d-terrain.md) Renk yoğunluğu dünyada nokta yüksekliği ile artar.

![3&#45;D arazi modeline uygulanan degrade efekti](../designers/media/digit-gradient-effect-result.png)

Bir 3B modele gölgeli nasıl uygulanacağı hakkında daha fazla bilgi için [bkz.](../designers/how-to-apply-a-shader-to-a-3-d-model.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılsın: Model 3D arazi](../designers/how-to-model-3-d-terrain.md)
- [Nasıl yapılsın: Gri tonlama doku shader oluşturma](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
