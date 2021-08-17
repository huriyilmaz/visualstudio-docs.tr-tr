---
title: Kod eşlemeleri yavaş
description: Kod eşleme performansını geliştirmeyi ve işlemeyi tamamlamak için gereken zamanı nasıl en aza indirgeyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 74c600fecf01290bd6d00ae0472b061402ceb4ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055569"
---
# <a name="improve-performance-for-code-maps"></a>Kod eşlemeleri için performansı geliştirme

İlk kez bir harita 7.000.Visual Studio, bulduğu tüm bağımlılıkları dizine alar. Bu işlem özellikle büyük çözümler için biraz zaman alsa da, daha sonra performansı iyiler. Kodunuz değişirse, Visual Studio yalnızca güncelleştirilmiş kodu yeniden Visual Studio yeniden kodlar. Haritanın işlemeyi bitirme süresini en aza indirmek için aşağıdaki önerileri göz önünde bulundurabilirsiniz:

- Yalnızca ilgini alan bağımlılıkları eşler.

- Çözümün tamamı için haritayı oluşturmadan önce çözüm kapsamını azaltarak.

- Kod haritası araç çubuğunda Derlemeyi Atla'ya **seçerek çözüm** için otomatik derlemeyi kapatın.

- Kod haritası araç çubuğunda Üst Öğeleri Ekle'yi **seçerek üst** öğe eklemenin otomatik olarak nasıl devre dışı olduğunu kapatın.

   ![Derleme ve Ekleme Ebeveyn düğmelerini atla](../modeling/media/codemapsfilterskipbuildicons.png)

- Kod eşleme dosyasını doğrudan düzenarak ihtiyacınız olan düğümleri ve bağlantıları kaldırın. Haritanın değiştirilmesi, temel alınan kodu etkilemez. Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

Bir proje öğesinin Çıkış Dizinine Kopyala özelliği Her zaman Kopyala olarak **Çözüm Gezgini** eşleme oluşturmak veya haritaya öğe eklemek daha **uzun zaman alır.**  Performansı artırmak için bu özelliği Daha yeni veya **ise kopyala olarak** değiştirebilirsiniz. `PreserveNewest` Bkz. [Artımlı derlemeler.](../msbuild/incremental-builds.md)

Tamamlanan harita yalnızca başarıyla yapılan kod bağımlılıklarını gösterir. Belirli bileşenler için derleme hataları oluşursa, bu hatalar haritada görünür. Haritayı temel alan mimari kararlar almadan önce bir bileşenin gerçekten derlemesi ve bağımlılıkları olduğundan emin olun.
