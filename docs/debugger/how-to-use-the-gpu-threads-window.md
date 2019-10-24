---
title: Hata ayıklayıcıda GPU Iş parçacıklarını görüntüleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 972b21c4535df37dd81da6aceaa062b39176469c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732096"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma (C++)
GPU Iş parçacıkları penceresinde, hata ayıklaması yaptığınız uygulamadaki GPU üzerinde çalışan iş parçacıklarını inceleyebilir ve bunlarla çalışabilirsiniz. GPU üzerinde çalışan uygulamalar hakkında daha fazla bilgi için bkz [ C++ . amp genel bakış](/cpp/parallel/amp/cpp-amp-overview).

 GPU Iş parçacıkları penceresi, her bir satırın tüm sütunlarda aynı değerlere sahip olan bir GPU iş parçacığı kümesini temsil ettiği bir tablo içerir. Sütunlardaki öğeleri sıralayabilir, yeniden sıralayabilir, kaldırabilir ve gruplandırabilirsiniz. GPU Iş parçacıkları penceresinden bayrak, unbayrak, dondurma (askıda) ve çözme (devam etme) iş parçacıklarını işaretleyebilirsiniz. Aşağıdaki sütunlar, GPU Iş parçacıkları penceresinde görüntülenir:

- Özel dikkat etmek istediğiniz bir iş parçacığını işaretleyecek bayrak sütunu.

- Geçerli iş parçacığını gösteren sarı bir okun geçerli iş parçacığı sütunu.

- Aynı konumdaki iş parçacığı sayısını görüntüleyen **Iş parçacığı sayısı** sütunu.

- Her iş parçacığı grubunun bulunduğu kod satırını görüntüleyen **satır** sütunu.

- Her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen **Adres** sütunu. Bu sütun varsayılan olarak gizlidir.

- Kaynak kodundaki **konum sütunu.**

- İş parçacığının etkin, engellenen, başlatılmamış veya tamamlanmamış olduğunu gösteren **durum** sütunu.

- Satırdaki iş parçacıkları için kutucuk dizinini gösteren **döşeme** sütunu.

  Tablonun üst bilgisinde, gösterilen kutucuk ve iş parçacığı gösterilmektedir.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>GPU Iş parçacıkları penceresini görüntüleme

1. **Çözüm Gezgini**' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. Projenin **Özellik sayfaları** penceresinde, **yapılandırma özellikleri**altında **hata ayıklama**öğesini seçin.

3. **Başlatmak Için hata ayıklayıcı** listesinde, **yerel Windows hata ayıklayıcısı**' nı seçin. **Hata ayıklayıcı türü** listesinde **yalnızca GPU**' yı seçin. GPU üzerinde çalışan koddaki kesme noktalarına bölmek için bu hata ayıklayıcıyı seçmeniz gerekir.

4. **Tamam** düğmesini seçin.

5. GPU kodunda bir kesme noktası ayarlayın.

6. Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin. Uygulamanın kesme noktasına ulaşmasını bekleyin.

7. Bir menü çubuğu, **Hata Ayıkla**, **Windows**, **GPU iş parçacıkları**' nı seçin.

### <a name="to-switch-to-a-different-thread"></a>Farklı bir iş parçacığına geçiş yapmak için

- Sütuna çift tıklayın. (Klavye: satırı seçin ve ENTER ' u seçin.)

### <a name="to-display-a-particular-tile-and-thread"></a>Belirli bir kutucuğu ve iş parçacığını görüntüleme

1. GPU Iş parçacıkları penceresinde **Iş parçacığı değiştiricisini Genişlet** düğmesini seçin.

2. Metin kutularına kutucuk ve iş parçacığı değerlerini girin.

3. Üzerine okuna sahip düğmeyi seçin.

### <a name="to-display-or-hide-a-column"></a>Bir sütunu göstermek veya gizlemek için

- GPU Iş parçacıkları penceresi için kısayol menüsünü açın, **sütunlar**' ı seçin ve ardından göstermek veya gizlemek istediğiniz sütunu seçin.

### <a name="to-sort-by-a-column"></a>Bir sütuna göre sıralamak için

- Sütun başlığını seçin.

### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için

- GPU Iş parçacıkları penceresi için kısayol menüsünü açın, **Gruplandır**' ı seçin ve ardından görünen sütun adlarından birini seçin. İş parçacıklarının grubunu çözmek için **hiçbiri** ' ni seçin.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>İş parçacığı satırını dondurmak veya çözme

- Satır için kısayol menüsünü açın ve **dondurma** veya **çözme**seçeneğini belirleyin.

### <a name="to-flag-or-unflag-a-row-of-threads"></a>İş parçacıklarının bir satırına bayrak eklemek veya bayrak kaldırmak için

- İş parçacığının Bayrak sütununu seçin veya iş parçacığının kısayol menüsünü açın ve **bayrak** ya da **Unflag**' ı seçin.

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için

- GPU Iş parçacıkları penceresinde bayrak düğmesini seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok İş Parçacıklı Uygulamaların Hatalarını Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl Yapılır: Paralel İzleme Penceresini Kullanma](../debugger/how-to-use-the-parallel-watch-window.md)
- [İzlenecek yol: C++ AMP Uygulamasında Hata Ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)