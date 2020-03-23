---
title: 'Nasıl Yapılır: Temel Doku Gölgelendiricisi Oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac74155b8de4669d959d9b14e9be20ada2ec51d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589480"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Nasıl yapılır: Temel doku gölgelendiricisi oluşturma

Bu makalede, tek doku gölgeli oluşturmak için Shader Designer ve Directed Graph Shader Language (DGSL) nasıl kullanılacağını göstermektedir. Bu gölgelendirme son rengi doğrudan dokudan alınan RGB ve alfa değerlerine ayarlar.

## <a name="create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma

Bir doku örneğinin renk ve alfa değerlerini doğrudan son çıktı rengine yazarak temel, tek doku gölgeleyici uygulayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin ve **Araç Kutusunun** görüntülendiğinden emin olun.

1. Çalışmak için bir DGSL gölgeleyici oluşturun. Projenize DGSL shader nasıl ekleyeceğiniz hakkında bilgi [için, Shader Designer'daki](../designers/shader-designer.md)Başlarken bölümüne bakın.

2. Nokta **Rengi** düğümünü silin. **Select** modunda, **Nokta Rengi** düğümünü seçin ve ardından menü çubuğunda**Sil'i** **Düzenle'yi** > seçin. Bu, bir sonraki adımda eklenen düğüm için yer sağlar.

3. Grafiğe **Doku Örneği** düğümü ekleyin. Araç **Kutusunda**, **Doku**altında, **Doku Örneği'ni** seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe bir **Doku Koordinat** düğümü ekleyin. Araç **Kutusunda**, **Doku**altında, **Doku Koordinatı'nı** seçin ve tasarım yüzeyine taşıyın.

5. Uygulamak için bir doku seçin. **Select** modunda Doku **Örneği** düğümünü seçin ve ardından **Özellikler** penceresinde **Dosya Adı** özelliğini kullanarak kullanmak istediğiniz dokuyu belirtin.

6. Dokuyu herkese açık hale getirin. Doku **Örneği** düğümünü seçin ve ardından **Özellikler** penceresinde **Access** özelliğini **Ortak**olarak ayarlayın. Artık dokuyu **Model Düzenleyicisi**gibi başka bir araçtan ayarlayabilirsiniz.

7. Doku koordinatlarını doku örneğine bağlayın. **Select** modunda, **Doku Koordinat** düğümünün **Çıkış** terminalini **Doku Örneği** düğümünün **UV** terminaline taşıyın. Bu bağlantı, belirtilen koordinatlarda doku örnekleri.

8. Doku örneğini son renge bağlayın. **Doku Örneği** düğümünün **RGB** terminalini **Son Renk** düğümünün **RGB** terminaline taşıyın ve ardından **Doku Örneği** düğümünün **Alfa** terminalini **Son Renk** düğümünün **Alfa** terminaline taşıyın.

Aşağıdaki resimde tamamlanmış gölgeli grafik ve bir küp uygulanan gölgeli bir önizleme gösterir.

> [!NOTE]
> Bu resimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelinin etkisini daha iyi göstermek için bir doku belirtilmiştir.

![Shader grafiği ve etkisinin önizlemesi](../designers/media/digit-texture-effect.png)

Bazı şekiller bazı gölgeliler için daha iyi önizlemeler sağlayabilir. Shader Designer'da gölgelilerin nasıl önizaltı izlenmehakkında daha fazla bilgi [için](../designers/shader-designer.md) Bkz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Görüntü Düzenleyici](../designers/image-editor.md)
- [Shader Tasarımcısı](../designers/shader-designer.md)
- [Gölgeli Tasarımcı düğümleri](../designers/shader-designer-nodes.md)
