---
title: 'Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 162632f0043d23fb111a9e455c1100f9506924a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589519"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl yapılır: Temel renk shader oluşturma

Bu makalede, düz renk shader oluşturmak için Shader Designer ve Directed Graph Shader Language (DGSL) nasıl kullanılacağını göstermektedir. Bu gölgelendirme son rengi sabit bir RGB renk değerine ayarlar.

## <a name="create-a-flat-color-shader"></a>Düz renk shader oluşturma

Bir RGB renk sabitinin renk değerini son çıktı rengine yazarak düz renk shader uygulayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgeleyici oluşturun. Projenize DGSL shader nasıl ekleyeceğiniz hakkında bilgi [için, Shader Designer'daki](../designers/shader-designer.md)Başlarken bölümüne bakın.

2. Nokta **Rengi** düğümünü silin. **Nokta Rengi** düğümünü seçmek için **Seç** aracını kullanın ve ardından menü çubuğunda**Sil'i** **Düzenle'yi** > seçin.

3. Grafiğe **Renk Sabiti** düğümü ekleyin. Araç **Kutusunda**, **Sabitler**altında Renk **Sabiti'ni** seçin ve tasarım yüzeyine taşıyın.

4. **Renk Sabitdüğümü** için renk değeri belirtin. **Renk Sabiti** düğümünü seçmek için **Seç** aracını kullanın ve ardından **Özellikler** **penceresinde, Çıktı** özelliğinde bir renk değeri belirtin. Turuncu için bir değer belirtin (1.0, 0.5, 0.2, 1.0).

5. Renk sabitini son renge bağlayın. Bağlantıları oluşturmak için, **Renk Sabitdüğümün** **RGB** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın ve ardından **Renk Sabitdüğümün** **Alfa** terminalini **Son Renk** düğümünün **Alfa** terminaline taşıyın. Bu bağlantılar son rengi önceki adımda tanımlanan renk sabitine ayarlar.

Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir küp uygulanan gölgeli bir önizleme gösterir.

> [!NOTE]
> Resimde, gölgeleyicinin etkisini daha iyi göstermek için turuncu bir renk belirtilmiştir.

![Shader grafiği ve sonucu 3&#45;D modelinde](../designers/media/digit-flat-color-effect.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgelilerin nasıl önizaltı izlentisi hakkında daha fazla bilgi için [Bkz.](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl yapılır: Gölgeli dışa aktarma](../designers/how-to-export-a-shader.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
