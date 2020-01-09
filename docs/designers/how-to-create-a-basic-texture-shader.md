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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589480"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Nasıl yapılır: temel doku gölgelendiricisi oluşturma

Bu makalede, tek bir doku gölgelendirici oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir. Bu gölgelendirici, son rengi doğrudan dokusunun örneklendiği RGB ve Alfa değerlerine ayarlar.

## <a name="create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma

Bir doku örneğinin Color ve Alpha değerlerini doğrudan nihai çıkış rengine yazarak temel, tek doku gölgelendiriciyi uygulayabilirsiniz.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Nokta rengi** düğümünü silin. **Seç** modunda, **nokta rengi** düğümünü seçin ve ardından menü çubuğunda **Düzenle** > **Sil**' i seçin. Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe bir **doku örnek** düğümü ekleyin. **Araç kutusunda** **doku**altında **doku örneği** ' ni seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe bir **doku koordinatı** düğümü ekleyin. **Araç kutusunda** **doku**' ın altında **doku koordinatı** ' nı seçin ve tasarım yüzeyine taşıyın.

5. Uygulanacak dokuyu seçin. **Seç** modunda, **doku örnek** düğümünü seçin ve ardından **Özellikler** penceresinde, **dosya adı** özelliğini kullanarak kullanmak istediğiniz dokuyu belirtin.

6. Dokuyu herkese açık bir şekilde erişilebilir hale getirin. **Doku örnek** düğümünü seçin ve ardından **Özellikler** penceresinde, **erişim** özelliğini **Public**olarak ayarlayın. Artık dokuyu **Model Düzenleyicisi**gibi başka bir araçtan ayarlayabilirsiniz.

7. Doku koordinatlarını doku örneğine bağlayın. **Seç** modunda, **doku koordinat** düğümünün **Çıkış** terminali ' ni **doku örnek** düğümünün **UV** terminaline taşıyın. Bu bağlantı, belirtilen koordinatlarda dokuyu örnekler.

8. Doku örneğini son renge bağlayın. **Doku örneği** düğümünün **RGB** terminalini **son renk** düğümünün **RGB** terminaline taşıyın ve ardından **doku örnek** düğümünün **Alfa** terminalini **son renk** düğümünün **Alfa** terminaline taşıyın.

Aşağıdaki çizimde, tamamlanmış gölgelendirici grafiği ve bir küpe uygulanan gölgelendirici önizlemesi gösterilmektedir.

> [!NOTE]
> Bu çizimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelendirici efektini daha iyi göstermek için bir doku belirtilmiştir.

![Gölgelendirici Grafiği ve efektinin önizlemesi](../designers/media/digit-texture-effect.png)

Bazı biçimler bazı gölgelendiriciler için daha iyi önizleme sağlayabilir. Gölgelendirici tasarımcısında gölgelendiricilerin önizlemesi hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
