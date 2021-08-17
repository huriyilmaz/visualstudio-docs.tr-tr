---
title: 'Nasıl Yapılır: Temel Renk Gölgelendiricisi Oluşturma'
description: Gölgelendirici Tasarımcısı ve Yönlendirilen Gölgelendirici Dili'Graph kullanarak son rengi sabit bir RGB renk değerine ayaran düz bir renk gölgelendiricisi oluşturma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: ecb8cbec45632ea01f5334ce4e6d0a2edbb9a1a3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030483"
---
# <a name="how-to-create-a-basic-color-shader"></a>Nasıl: Temel renk gölgelendiricisi oluşturma

Bu makalede gölgelendirici Tasarımcısı'nın ve Directed Graph Gölgelendirici Dili'nin (DGSL) düz renk gölgelendiricisi oluşturması açıklanmıştır. Bu gölgelendirici, son rengi sabit bir RGB renk değerine ayarlar.

## <a name="create-a-flat-color-shader"></a>Düz renk gölgelendiricisi oluşturma

Rgb renk sabiti renk değerini son çıkış rengine yazarak düz renk gölgelendiricisi gerçekleştirin.

Başlamadan önce Özellikler penceresinin ve **Araç** Kutusunun **görüntülendiğinden emin** olun.

1. Çalışmak için bir DGSL gölgelendiricisi oluşturun. Projenize DGSL gölgelendiricisi ekleme hakkında bilgi için Gölgelendirici Tasarımcısı'Başlarken bölümüne [bakın.](../designers/shader-designer.md)

2. Nokta Rengi **düğümünü** silin. Nokta **Rengi düğümünü** seçmek için **Seçim aracını** kullanın ve ardından menü çubuğunda Sil'i **düzenle'yi**  >  **seçin.**

3. **Grafiye bir Renk** Sabiti düğümü ekleyin. Araç **Kutusunda,** **Sabitler'in altında** Renk **Sabiti'yi seçin** ve tasarım yüzeyine taşıyın.

4. Renk Sabiti düğümü için **bir renk değeri** belirtin. Renk **Sabiti** düğümünü **seçmek için** Seç aracını kullanın ve ardından Özellikler penceresindeki Çıkış  **özelliğinde** bir renk değeri belirtin. Turuncu için değerini (1.0, 0.5, 0.2, 1.0) belirtin.

5. Bağlan sabiti son renge göre değiştirir. Bağlantıları oluşturmak için Renk Sabiti  düğümünün **RGB** terminali'ni **Son** Renk düğümünün **RGB** terminaline  ve ardından Renk Sabiti düğümünün **Alfa** terminali ile Son Renk düğümünün **Alfa** **terminaline** hareket ettirin. Bu bağlantılar, son rengi önceki adımda tanımlanan renk sabiti olarak ayarlayın.

Aşağıdaki çizimde tamamlanmış gölgelendirici grafı ve bir kübüne uygulanan gölgelendiricinin önizlemesi gösterilir.

> [!NOTE]
> Çizimde gölgelendiricinin etkisini daha iyi göstermek için turuncu renk belirtilmiştir.

![Gölgelendirici grafiği ve sonucu 3&#45;D modeli](../designers/media/digit-flat-color-effect.png)

Bazı şekiller bazı gölgelendiriciler için daha iyi önizlemeler sağlar. Gölgelendirici Tasarımcısı'nda gölgelendiricileri önizleme hakkında daha fazla bilgi için bkz. [Gölgelendirici Tasarımcısı.](../designers/shader-designer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır. 3B modele gölgelendirici uygulama](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Nasıl: Gölgelendiriciyi dışarı aktarma](../designers/how-to-export-a-shader.md)
- [Gölgelendirici Tasarımcısı](../designers/shader-designer.md)
- [Gölgelendirici Tasarımcısı düğümleri](../designers/shader-designer-nodes.md)
