---
title: 'Nasıl yapılır: 3B modele gölgelendirici uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15d88f52b3af3a3e4502c618280107a882761259
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664608"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Nasıl Yapılır. 3B Modele Gölgelendirici Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belgede, 3B modeline yönlendirilmiş grafik gölgelendirici dili (DGSL) gölgelendirici uygulamak için Model Düzenleyicisi 'nin nasıl kullanılacağı gösterilir.

 Bu belgede bu etkinlik gösterilmektedir:

- 3B modele gölgelendirici uygulama

## <a name="applying-a-shader-to-a-3-d-model"></a>3B modele gölgelendirici uygulama
 İlgi çekici bir görünüm sağlamak için 3-b modeline bir gölgelendirici efekti uygulayabilirsiniz.

 Başlamadan önce **Özellikler** penceresinin görüntülendiğinden emin olun.

#### <a name="to-apply-a-shader-to-a-3-d-model"></a>3-b modele gölgelendirici uygulamak için

1. Bir veya daha fazla model içeren 3-b sahile başlayın. Uygun bir 3-b sahneye sahip değilseniz, [nasıl yapılır: temel 3B model oluşturma](../designers/how-to-create-a-basic-3-d-model.md)bölümünde açıklandığı gibi bir tane oluşturun. Ayrıca, modele uygulayabileceğiniz bir DGSL gölgelendiricisine sahip olmanız gerekir. Uygun bir gölgelendirici yoksa, [nasıl yapılır: temel renk gölgelendiricisi oluşturma](../designers/how-to-create-a-basic-color-shader.md) bölümünde açıklandığı gibi bir tane oluşturun ve devam etmeden önce dosyayı bir dosyaya kaydettiğinizden emin olun.

2. **Seç** modunda, gölgelendirici uygulamak istediğiniz modeli seçin ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **filename** özelliğinde, modele uygulamak istediğiniz dgsl gölgelendiriciyi belirtin.

   Temel renk efektinin uygulandığı bir model aşağıda verilmiştir:

   ![temel&#45;renk efektini gösteren 3 D sahne](../designers/media/digit-3d-model-effect.png "Basamak-3B-model-efekt")

   Bir modele gölgelendirici uyguladıktan sonra modeli seçerek gölgelendirici tasarımcısında açabilir ve ardından **Özellikler** penceresinde, **efekt** Özellik grubunun **(Gelişmiş)** özelliğindeki üç nokta ( **...** ) düğmesini seçebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: temel bir 3-b modeli oluşturma](../designers/how-to-create-a-basic-3-d-model.md) [nasıl yapılır: temel renk gölgelendirici](../designers/how-to-create-a-basic-color-shader.md) [modeli Düzenleyicisi](../designers/model-editor.md) [Gölgelendirici Tasarımcısı](../designers/shader-designer.md) oluşturma
