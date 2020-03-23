---
title: 'Nasıl yapılır: 3B Modele Shader Uygulama'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ae04f4cc0afb1c24f391d140081040efe9db50e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112762"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Nasıl yapılır. 3B modele gölgelendirici uygulama

Bu makalede, Bir 3B modele Yönlendirilmiş Grafik Shader Dili (DGSL) shader uygulamak için Model Düzenleyicisi nasıl kullanılacağını göstermektedir.

## <a name="apply-a-shader-to-a-3d-model"></a>3B modele gölgelendirici uygulama

Ilginç bir görünüm vermek için bir 3B modele gölgeli efekti uygulayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun.

1. Bir veya daha fazla model içeren bir 3B sahne yle başlayın. Uygun bir 3B sahneniz yoksa, nasıl tanımlanır: [Temel bir 3B Model oluşturun.](../designers/how-to-create-a-basic-3-d-model.md) Ayrıca modele uygulayabileceğiniz bir DGSL gölgeliniz de olmalıdır. Uygun bir gölgelendirmeniz yoksa, Nasıl Yapılır'da açıklandığı gibi bir tane [oluşturun: Temel bir renk gölgeleyicisi oluşturun](../designers/how-to-create-a-basic-color-shader.md) ve devam etmeden önce dosyaya kaydettiğinizden emin olun.

2. **Select** modunda, gölgeleyiciyi uygulamak istediğiniz modeli seçin ve ardından **Özellikler** penceresinde, **Efekt** özelliği grubunun **Dosya Adı** özelliğinde, modele uygulamak istediğiniz DGSL gölgeleyicisini belirtin.

Burada temel renk efekti uygulanan bir model:

![Temel renk efektini gösteren 3&#45;D sahnesi](../designers/media/digit-3d-model-effect.png)

Bir modele gölgeli uyguladıktan sonra, modeli seçerek Shader Designer'da ve ardından **Özellikler** penceresinde, **Effect** özellik grubunun **(Advanced)** özelliğinde elipsis (**...**) düğmesini seçerek açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Nasıl yapılır: Temel renk shader oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Model düzenleyici](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
