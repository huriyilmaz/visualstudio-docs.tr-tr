---
title: 'Nasıl Yapılır: Temel Doku Gölgelendiricisi Oluşturma'
description: Son rengi dokudan RGB ve alfa Graph olarak ayaran tek doku gölgelendiricisi oluşturmak için Gölgelendirici Tasarımcısı ve Yönlendirilen Gölgelendirici Dili kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: e094e8bd318fce3fdb755ea482a696b25af1cdd4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127772"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Nasıl yapılır: Temel doku gölgelendiricisi oluşturma

Bu makalede Gölgelendirici Tasarımcısı'nın ve Yönlendirilen Graph Gölgelendirici Dili'nin (DGSL) tek doku gölgelendiricisi oluşturmak için nasıl kullanılası açıklanmıştır. Bu gölgelendirici, son rengi dokudan örnek alınan RGB ve alfa değerlerine doğrudan ayarlar.

## <a name="create-a-basic-texture-shader"></a>Temel doku gölgelendiricisi oluşturma

Doku örneğinin renk ve alfa değerlerini doğrudan son çıkış rengine yazarak temel, tek doku gölgelendiricisi kullanabilirsiniz.

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize DGSL gölgelendiricisi ekleme hakkında bilgi için Gölgelendirici Tasarımcısı'Başlarken bölümüne [bakın.](../designers/shader-designer.md)

2. Nokta Rengi **düğümünü** silin. Seçim **modunda** Nokta Rengi **düğümünü seçin** ve ardından menü çubuğunda Sil'i **düzenle'yi**  >  **seçin.** Bu, sonraki adımda eklenen düğüme yer sağlar.

3. **Grafiye doku** örneği düğümü ekleyin. Araç **Kutusunda, Doku** altında **Doku** **Örneği'yi seçin** ve tasarım yüzeyine taşıma.

4. **Grafiye bir Doku** Koordinatı düğümü ekleyin. Araç **Kutusunda, Doku** altında **Doku** **Koordinatı'nı** seçin ve tasarım yüzeyine taşıma.

5. Uygulanacak dokuyu seçin. Seç **modunda** Doku Örneği **düğümünü** seçin ve özellikler **penceresinde** Dosya adı özelliğini kullanarak kullanmak istediğiniz **dokuyu** belirtin.

6. Dokuyu genel erişime açık hale. Doku Örneği **düğümünü** seçin ve Özellikler **penceresinde** **Access** özelliğini Genel olarak **ayarlayın.** Artık dokuyu Model Düzenleyicisi gibi başka bir araçtan **ayarlayabilirsiniz.**

7. Bağlan doku örneğine eşgüdüm sağlar. Seç **modunda** Doku **Koordinatı düğümünün** Çıkış **terminali'ni** Doku Örneği **düğümünün TERMINAL** **terminaline** hareket ettirin. Bu bağlantı, dokuyu belirtilen koordinatlarda örnekler.

8. Bağlan örneğini son renge doğru seçin. Doku Örneği **düğümünün RGB** terminali, **Son** Renk düğümünün **RGB** terminaline ve  ardından Doku Örneği düğümünün **Alfa** terminali ile Son Renk düğümünün **Alfa**  **terminaline** hareket ettirin.

Aşağıdaki çizimde tamamlanmış gölgelendirici grafı ve bir kübüne uygulanan gölgelendiricinin önizlemesi gösterilir.

> [!NOTE]
> Bu çizimde, önizleme şekli olarak bir düzlem kullanılır ve gölgelendiricinin etkisini daha iyi göstermek için bir doku belirtilmiştir.

![Gölgelendirici grafiği ve etkisinin önizlemesi](../designers/media/digit-texture-effect.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Görüntü Düzenleyicisi](../designers/image-editor.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
