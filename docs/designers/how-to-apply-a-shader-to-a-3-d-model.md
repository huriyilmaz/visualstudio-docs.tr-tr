---
title: 'Nasıl yapılır: 3B modele gölgelendirici uygulama'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 445829c3171eeae3b483055688dcf5f77be67330
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637179"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Nasıl yapılır: 3B modele gölgelendirici uygulama

Bu makalede, bir 3B modele yönlendirilmiş grafik gölgelendirici dili (DGSL) gölgelendiricisi uygulamak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilmektedir.

## <a name="apply-a-shader-to-a-3d-model"></a>3B modele gölgelendirici uygulama

Bir 3B modeline bir gölgelendirici efekti uygulayıp buna ilginç bir görünüm sağlayabilirsiniz.

Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun.

1. Bir veya daha fazla model içeren bir 3B sahneye başlayın. Uygun bir 3B sahneye sahip değilseniz, [nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)bölümünde açıklandığı gibi bir tane oluşturun. Ayrıca, modele uygulayabileceğiniz bir DGSL gölgelendiricisine sahip olmanız gerekir. Uygun bir gölgelendirici yoksa, [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md) bölümünde açıklandığı gibi bir tane oluşturun ve devam etmeden önce dosyayı bir dosyaya kaydettiğinizden emin olun.

2. **Seç** modunda, gölgelendirici uygulamak istediğiniz modeli seçin ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **filename** özelliğinde, modele uygulamak istediğiniz dgsl gölgelendiriciyi belirtin.

Temel renk efektinin uygulandığı bir model aşağıda verilmiştir:

![temel&#45;renk efektini gösteren 3 D sahne](../designers/media/digit-3d-model-effect.png)

Bir modele gölgelendirici uyguladıktan sonra modeli seçerek gölgelendirici tasarımcısında açabilir ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **(Gelişmiş)** özelliğindeki üç nokta ( **...** ) düğmesini seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Nasıl yapılır: Temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)