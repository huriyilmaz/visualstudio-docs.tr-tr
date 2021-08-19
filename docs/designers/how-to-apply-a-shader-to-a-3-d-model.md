---
title: 'Nasıl yapılır: 3B modele gölgelendirici uygulama'
description: Model düzenleyicisi 'ni kullanarak, ilginç bir görünüm sağlamak için bir 3b modele yönlendirilmiş Graph gölgelendirici dili gölgelendiricisi uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.workload:
- multiple
ms.openlocfilehash: 08f078d07ad1a3d408c25f5cda2d8d19754ae881
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127824"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Nasıl yapılır. 3B modele gölgelendirici uygulama

bu makalede, bir 3b modele yönlendirilmiş Graph gölgelendirici dili (dgsl) gölgelendiricisi uygulamak için Model düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir.

## <a name="apply-a-shader-to-a-3d-model"></a>3B modele gölgelendirici uygulama

Bir 3B modeline bir gölgelendirici efekti uygulayıp buna ilginç bir görünüm sağlayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun.

1. Bir veya daha fazla model içeren bir 3B sahneye başlayın. Uygun bir 3B sahneye sahip değilseniz, [nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)bölümünde açıklandığı gibi bir tane oluşturun. Ayrıca, modele uygulayabileceğiniz bir DGSL gölgelendiricisine sahip olmanız gerekir. Uygun bir gölgelendirici yoksa, [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md) bölümünde açıklandığı gibi bir tane oluşturun ve devam etmeden önce dosyayı bir dosyaya kaydettiğinizden emin olun.

2. **Seç** modunda, gölgelendirici uygulamak istediğiniz modeli seçin ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **filename** özelliğinde, modele uygulamak istediğiniz dgsl gölgelendiriciyi belirtin.

Temel renk efektinin uygulandığı bir model aşağıda verilmiştir:

![3&#45;D sahneyi temel renk efektini gösterir](../designers/media/digit-3d-model-effect.png)

Bir modele gölgelendirici uyguladıktan sonra modeli seçerek gölgelendirici tasarımcısında açabilir ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **(Gelişmiş)** özelliğindeki üç nokta (**...**) düğmesini seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
