---
title: Hata Ayıklayıcı hizmetinde GPU İş Parçacıklarını | Microsoft Docs
description: Gpu İş Parçacıkları penceresini kullanarak hata ayıklarken hata ayıklamış olduğu uygulamada GPU üzerinde çalışan iş parçacıklarını Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 971462777b2c2cf8ccf315b2764fc514b4991548542fcfe0b62144a8689e65e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378716"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Nasıl: GPU İş Parçacıkları Penceresini Kullanma (C++)
GPU İş Parçacıkları penceresinde, hata ayıklamakta olan uygulamada GPU üzerinde çalışan iş parçacıklarını inceler ve bu iş parçacıklarıyla çalışabilirsiniz. GPU üzerinde çalıştırilen uygulamalar hakkında daha fazla bilgi için bkz. [C++ AMP Genel Bakış.](/cpp/parallel/amp/cpp-amp-overview)

 GPU İş Parçacıkları penceresi, her satırın tüm sütunlarda aynı değerlere sahip bir dizi GPU iş parçacığını temsil ettiği bir tablo içerir. Sütunlarda yer alan öğeleri sıralayabilirsiniz, yeniden sıralayabilirsiniz, kaldırabilir ve gruplayabilirsiniz. GPU İş Parçacıkları penceresinden iş parçacıklarını bayrakla askıya alabilir, dondurabilir (askıya alabilir) ve çözülebilirsiniz (sürdürebilirsiniz). GPU İş Parçacıkları penceresinde aşağıdaki sütunlar görüntülenir:

- Özellikle dikkat etmek istediğiniz bir iş parçacığını işaretleyebilirsiniz bayrak sütunu.

- Geçerli iş parçacığı sütununu, içinde sarı bir ok geçerli iş parçacığını gösterir.

- Aynı **konumdaki** iş parçacığı sayısını görüntüleyen İş Parçacığı Sayısı sütunu.

- Her **iş** parçacığı grubunun bulunduğu kod satırı görüntüleyen Çizgi sütunu.

- Her **iş** parçacığı grubunun bulunduğu yönerge adresini görüntüleyen Adres sütunu. Bu sütun varsayılan olarak gizlidir.

- Kaynak  kodun konumu olan Konum sütunu.

- İş **parçacığının** etkin, engellenmiş, başlatlanmadı veya tamamlandı olduğunu gösteren Durum sütunu.

- **Satırdaki** iş parçacıklarının kutucuk dizinini gösteren Kutucuk sütunu.

  Tablonun üst bilgisinde görüntülenen kutucuk ve iş parçacığı gösterilir.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>GPU İş Parçacıkları penceresini görüntülemek için

1. Bu **Çözüm Gezgini** proje kısayol menüsünü açın ve Özellikler'i **seçin.**

2. Projenin **Özellik Sayfaları penceresindeki** Yapılandırma Özellikleri'nin **altında Hata Ayıklama'ya** **tıklayın.**

3. Başlat için **Hata Ayıklayıcısı listesinde Yerel** Windows Hata **Ayıklayıcı'ya tıklayın.** Hata **Ayıklayıcı Türü listesinde Yalnızca** **GPU'su seçin.** GPU üzerinde çalışan kodda kesme noktalarında kesme noktalarında kesme noktası seçmek için bu hata ayıklayıcıyı seçmeniz gerekir.

4. Tamam **düğmesini** seçin.

5. GPU kodunda bir kesme noktası ayarlayın.

6. Menü çubuğunda Hata Ayıkla, **Hata Ayıklamayı** **Başlat'ı seçin.** Uygulamanın kesme noktalarına ulaşacak şekilde beklemesi.

7. Menü çubuğunda Hata Ayıkla , Windows **,** GPU İş **Parçacıkları'ı seçin.** 

### <a name="to-switch-to-a-different-thread"></a>Farklı bir iş parçacığına geçmek için

- Sütuna çift tıklayın. (Klavye: Satırı seçin ve Enter tarak seçin.)

### <a name="to-display-a-particular-tile-and-thread"></a>Belirli bir kutucuğu ve iş parçacığını görüntülemek için

1. GPU İş **Parçacıkları penceresinde İş Parçacığı** Anahtarcıyı Genişlet düğmesini seçin.

2. Metin kutularına kutucuk ve iş parçacığı değerlerini girin.

3. Üzerinde ok olan düğmeyi seçin.

### <a name="to-display-or-hide-a-column"></a>Bir sütunu görüntülemek veya gizlemek için

- GPU İş Parçacıkları penceresinin kısayol menüsünü açın, **Sütunlar'ı** ve ardından görüntülemek veya gizlemek istediğiniz sütunu seçin.

### <a name="to-sort-by-a-column"></a>Sütuna göre sıralamak için

- Sütun başlığını seçin.

### <a name="to-group-threads"></a>İş parçacıklarını grupla

- GPU İş Parçacıkları penceresinin kısayol menüsünü açın, **Grupla'yı seçin** ve görüntülenen sütun adlarından birini seçin. İş **parçacıklarının** grubunu çözmek için Hiçbiri'ne tıklayın.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>İş parçacıklarının bir satırı dondurulması veya çözülme

- Satırın kısayol menüsünü açın  ve Dondurma veya **Çözme'yi seçin.**

### <a name="to-flag-or-unflag-a-row-of-threads"></a>bir iş parçacığı satırına bayrak veya bayrak asma

- İş parçacığı için bayrak sütununu seçin veya iş parçacığının kısayol menüsünü açıp Bayrak veya Bayrağı **Kaldır'ı seçin.** 

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için

- GPU İş Parçacıkları penceresinde bayrak düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl: Paralel İzleme Penceresini Kullanma](../debugger/how-to-use-the-parallel-watch-window.md)
- [Adım adım kılavuz: C++ AMP Uygulamanın Hata Ayıklaması](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)