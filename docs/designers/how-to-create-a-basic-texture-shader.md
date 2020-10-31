---
title: 'Nasıl Yapılır: Temel Doku Gölgelendiricisi Oluşturma'
description: Dokusundaki son rengi RGB ve Alfa değerlerini ayarlayan tek dokuda bir gölgelendirici oluşturmak için gölgelendirici tasarımcısını ve yönlendirilmiş Graf gölgelendirici dilini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93696dfe9fbf3b8db1d4be137ced6798b3a60aae
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134504"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Nasıl yapılır: Temel doku gölgelendiricisi oluşturma

Bu makalede, tek bir doku gölgelendirici oluşturmak için Gölgelendirici Tasarımcısının ve yönlendirilmiş grafik gölgelendirici dilinin (DGSL) nasıl kullanılacağı gösterilmektedir. Bu gölgelendirici, son rengi doğrudan dokusunun örneklendiği RGB ve Alfa değerlerine ayarlar.

## <a name="create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma

Bir doku örneğinin Color ve Alpha değerlerini doğrudan nihai çıkış rengine yazarak temel, tek doku gölgelendiriciyi uygulayabilirsiniz.

Başlamadan önce, **Özellikler** penceresinin ve **araç kutusunun** görüntülendiğinden emin olun.

1. Birlikte çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize bir DGSL gölgelendiricisi ekleme hakkında daha fazla bilgi için bkz. [gölgelendirici tasarımcısında](../designers/shader-designer.md)Başlarken bölümü.

2. **Nokta rengi** düğümünü silin. **Seç** modunda, **nokta rengi** düğümünü seçin ve ardından menü çubuğunda Sil **Düzenle** ' yi seçin  >  **Delete** . Bu, bir sonraki adımda eklenen düğüm için yer açar.

3. Grafiğe bir **doku örnek** düğümü ekleyin. **Araç kutusunda** **doku** altında **doku örneği** ' ni seçin ve tasarım yüzeyine taşıyın.

4. Grafiğe bir **doku koordinatı** düğümü ekleyin. **Araç kutusunda** **doku** ' ın altında **doku koordinatı** ' nı seçin ve tasarım yüzeyine taşıyın.

5. Uygulanacak dokuyu seçin. **Seç** modunda, **doku örnek** düğümünü seçin ve ardından **Özellikler** penceresinde, **dosya adı** özelliğini kullanarak kullanmak istediğiniz dokuyu belirtin.

6. Dokuyu herkese açık bir şekilde erişilebilir hale getirin. **Doku örnek** düğümünü seçin ve ardından **Özellikler** penceresinde, **erişim** özelliğini **Public** olarak ayarlayın. Artık dokuyu **Model Düzenleyicisi** gibi başka bir araçtan ayarlayabilirsiniz.

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
