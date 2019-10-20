---
title: Kod eşlemeleri yavaş
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b3f889661cf0d1c775cd80dad61a92c3f5b60a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654171"
---
# <a name="improve-performance-for-code-maps"></a>Kod haritaları için performansı iyileştirme

İlk kez bir eşleme oluşturduğunuzda, Visual Studio bulduğu tüm bağımlılıkların dizinini oluşturur. Bu işlem, özellikle büyük çözümler için biraz zaman alabilir, ancak daha sonraki performansı geliştirir. Kodunuz değişirse, Visual Studio yalnızca güncelleştirilmiş kodun dizinini oluşturur. Haritanın işlemeyi tamamlaması için geçen süreyi en aza indirmek için aşağıdaki önerileri göz önünde bulundurun:

- Yalnızca ilgilendiğiniz bağımlılıkları eşleyin.

- Tüm çözüm için Haritayı oluşturmadan önce çözüm kapsamını azaltın.

- Kod Haritası araç çubuğunda **derlemeyi atla** ' yı seçerek çözüm için otomatik derlemeyi devre dışı bırakın.

- Kod Haritası araç çubuğunda üst öğeleri **dahil et** ' i seçerek üst öğelerin otomatik eklenmesini devre dışı bırakın.

   ![Derleme ve ekleme üst öğeleri düğmelerini atla](../modeling/media/codemapsfilterskipbuildicons.png)

- İhtiyacınız olmayan düğümleri ve bağlantıları kaldırmak için doğrudan kod eşleme dosyasını düzenleyin. Haritanın değiştirilmesi temeldeki kodu etkilemez. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Bir proje öğesinin **Çıkış Dizinine Kopyala** özelliği **her zaman Kopyala**olarak ayarlandığında, haritalar oluşturmak veya **Çözüm Gezgini** haritaya öğe eklemek daha fazla zaman alabilir. Performansı artırmak için bu özelliği, **daha yeniyse** veya `PreserveNewest` kopyalamak üzere değiştirin. Bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md).

Tamamlanan eşleme yalnızca başarıyla oluşturulmuş kod için bağımlılıkları gösterir. Belirli bileşenler için yapı hataları oluşursa, bu hatalar haritada görüntülenir. Harita üzerinde mimari kararlar vermeden önce bir bileşenin gerçekten oluşturup bu bağımlılıkları kullandığından emin olun.