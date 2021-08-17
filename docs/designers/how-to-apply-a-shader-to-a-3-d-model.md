---
title: 'Nasıl yapılır: 3D Modele Gölgelendirici Uygulama'
description: Model Düzenleyicisi'ni kullanarak 3D modele Graph görünümü vermek için Directed Graph Language gölgelendiricisi uygulama hakkında bilgi öğrenin.
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
ms.openlocfilehash: 86b6f467200b136a95afeed5740e6cdbdae991d3223df5ff2f458607d90fa50d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435184"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Nasıl yapılır. 3B modele gölgelendirici uygulama

Bu makalede, 3D modele Yönlendirilen Graph Gölgelendirici Dili (DGSL) gölgelendiricisi uygulamak için Model Düzenleyicisi'ni kullanma açıklanmıştır.

## <a name="apply-a-shader-to-a-3d-model"></a>3B modele gölgelendirici uygulama

3D modele ilginç bir görünüm vermek için gölgelendirici etkisi uygulayabilirsiniz.

Başlamadan önce Özellikler penceresinin **görüntülendiğinden** emin olun.

1. Bir veya daha fazla model içeren 3D bir sahneyle başlar. Uygun bir 3D sahne yoksa, Nasıl 3D Modeli Oluşturma konusunda açıklandığı gibi bir [tane oluşturun.](../designers/how-to-create-a-basic-3-d-model.md) Ayrıca modele uygulayabilecek bir DGSL gölgelendiricisi de olması gerekir. Uygun bir gölgelendiriciye sahip değilsanız, Nasıl [yapacaklar:](../designers/how-to-create-a-basic-color-shader.md) Temel renk gölgelendiricisi oluşturma konusunda açıklandığı gibi bir gölgelendirici oluşturun ve devam etmek için bir dosyaya kaydettiklerinden emin olun.

2. Seç **modunda** gölgelendiriciyi uygulamak istediğiniz modeli seçin ve özellikler penceresindeki **Etki** özellik grubunun **Dosya** adı özelliğinde, modele uygulamak istediğiniz DGSL gölgelendiriciyi belirtin. 

Temel renk etkisi uygulanmış bir model şu şekildedir:

![3&#45;renk etkisini gösteren D sahnesi](../designers/media/digit-3d-model-effect.png)

Bir modele gölgelendiriciyi uygulattıktan sonra modeli seçerek Gölgelendirici Tasarımcısı'nda açabilir  ve ardından Özellikler penceresinde, **Etki** özellik grubunun **(Gelişmiş)** özelliğinde üç nokta (**...**) düğmesini seçerek açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)
- [Nasıl: Temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md)
- [Model düzenleyicisi](../designers/model-editor.md)
- [Gölgelendirici tasarımcısı](../designers/shader-designer.md)
