---
title: 'Nasıl Yapılır: Geometri Tabanlı Gradyan Gölgelendirici Oluşturma'
description: Sabit rgb renk değerini ölçeklendiren geometri tabanlı bir gradyan gölgelendirici oluşturmak için Gölgelendirici Tasarımcısı ve Graph Yönlendirilen Gölgelendirici Dili kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4b204405-ba95-4c5e-bd51-ec033a3ebfb6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 68d0c5af184fa22a41204f7d1937831b67c80244
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104878"
---
# <a name="how-to-create-a-geometry-based-gradient-shader"></a>Nasıl yapılır: Geometri tabanlı gradyan gölgelendirici oluşturma

Bu makalede, geometri tabanlı bir gradyan gölgelendirici oluşturmak için Gölgelendirici Tasarımcısı ve Graph Gölgelendirici Dili'nin nasıl kullanımı açıklanmıştır. Bu gölgelendirici, dünya alanı içinde bir nesnenin her noktasının yüksekliğine göre sabit bir RGB renk değerini ölçeklendirer.

## <a name="create-a-geometry-based-gradient-shader"></a>Geometri tabanlı gradyan gölgelendirici oluşturma

Pikselin konumunu gölgelendiricinize dahil ederek geometri tabanlı gölgelendiriciler gerçekleştirebilirsiniz. Gölgelendirme dillerinde piksel, 2B ekranda yalnızca rengi ve konumuyla ilgili daha fazla bilgi içerir. Piksel (bazı *sistemlerde parça* olarak bilinir) piksele karşılık gelen yüzeyi tanımlayan değerler koleksiyonudur. Bu belgede açıklanan gölgelendirici, parçanın son çıkış rengini etkilemesi için dünya alanı içinde bir 3D nesnenin her pikselin yüksekliğini kullanır.

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Birlikte çalışacak bir DGSL gölgelendiricisi oluşturun. Projenize DGSL gölgelendiricisi ekleme hakkında bilgi için Gölgelendirici Tasarımcısı'Başlarken bölümüne [bakın.](../designers/shader-designer.md)

2. Nokta Rengi **düğümünün** Bağlantısını Son **Renk düğümünden** kesin. Nokta Rengi **düğümünün RGB** **terminalini ve** ardından Bağlantıları **Kesme'yi seçin.** Bu, sonraki adımda eklenen düğüme yer sağlar.

3. **Grafiye** bir Çarpı düğümü ekleyin. Araç **Kutusunda, Matematik'in** **altında** **Çarp'ı** seçin ve tasarım yüzeyine taşıyın.

4. **Grafiye bir** Maske Vektörü düğümü ekleyin. Araç **Kutusunda, Yardımcı** **Program'ın altında** **Vektörü Maskele'yi** seçin ve tasarım yüzeyine taşıma.

5. Maske Vektörü düğümü için **maske değerlerini** belirtin. Seçim **modunda,** Maske  Vektörü düğümünü seçin  ve özellikler penceresinde Yeşil **/ Y** özelliğini **True** olarak ayarlayın ve ardından Kırmızı / X , Mavi **/** **Z** ve Alfa **/ W** özelliklerini False olarak **ayarlayın.** Bu örnekte, Dünya Konumu düğümünün x, y ve z bileşenlerine karşılık gelen Kırmızı  **/ X**, Yeşil / **Y** ve Mavi **/ Z** özellikleri kullanılır ve Alfa **/ W** kullanılmaz. Yalnızca Yeşil **/Y** Değeri True olarak ayar **olduğundan,** giriş vektörü maskeledikten sonra yalnızca y bileşeni kalır.

6. **Grafiye bir** Dünya Konumu düğümü ekleyin. Araç **Kutusunda,** **Sabitler'in altında** Dünya **Konumu'nı** seçin ve tasarım yüzeyine getirin.

7. Parçanın dünya alanı konumunu maskeleme. Seç **modunda,** Dünya Konumu **düğümünün** Çıkış **terminali'ni** Vektör Düğümünü **Maskele** düğümünün **Vektör terminaline** getirin. Bu bağlantı, x ve z bileşenlerini yoksaymak için parçanın konumunu maskeler.

8. RGB renk sabiti ile maskelenmiş dünya alanı konumuyla çarpın. Nokta Rengi düğümünün  **RGB** terminalini Çarpma düğümünün **Y** terminaline ve ardından  Maske Vektörü düğümünün Çıkış **terminalini** Çarpı düğümünün  **X** **terminaline** taşıma. Bu bağlantı renk değerini dünya boşluğunda pikselin yüksekliğine göre ölçeklendirer.

9. Bağlan renk değerini son renge göre değiştirir. Çarpma **düğümünün** Çıkış **terminali'ni** Son Renk **düğümünün RGB** **terminaline** taşıma.

Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küreye uygulanan gölgelendiricinin önizlemesi gösterilir.

> [!NOTE]
> Bu çizimde gölgelendiricinin etkisini daha iyi göstermek için turuncu renk belirtilmiştir, ancak önizleme şekli dünya boşluğunda bir konuma sahip olduğundan gölgelendirici Gölgelendirici Tasarımcısı'nda tam olarak önizlemesi olamaz. Tam etkiyi göstermek için gölgelendiricinin gerçek bir sahnede önizlemesi gerekir.

![Gölgelendirici grafiği ve etkisinin önizlemesi](../designers/media/digit-gradient-effect-graph.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında bilgi için bkz. Gölgelendirici **Tasarımcısı'nda** [gölgelendiricileri önizleme.](../designers/shader-designer.md)

Aşağıdaki çizimde, Nasıl yapılır: 3D arazi modelleme konusunda gösterildiği gibi, bu belgede açıklanan [gölgelendirici 3D sahneye uygulanmıştır.](../designers/how-to-model-3-d-terrain.md) Rengin yoğunluğu, dünyanın her yanında noktanın yüksekliğiyle birlikte artar.

![3 D arazi modeline&#45;gradyan etkisi](../designers/media/digit-gradient-effect-result.png)

Bir 3D modele gölgelendirici uygulama hakkında daha fazla bilgi için bkz. Nasıl [yapılır: 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)modele gölgelendirici uygulama.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Nasıl yapılıyor: 3D arazi modelleme](../designers/how-to-model-3-d-terrain.md)
- [Nasıl edilir: Gri tonlamalı doku gölgelendiricisi oluşturma](../designers/how-to-create-a-grayscale-texture-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
