---
title: Paralel İş Parçacıklarında Değişkenlerde İzleme | Microsoft Docs
description: Veri kümesinde paralel iş parçacıklarında değişkenler üzerinde bir Visual Studio. Bir ifadenin birden çok iş parçacığında yer alan değerleri aynı anda görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 04/25/2017
ms.topic: how-to
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9bbf8abeb1df22588351b74fc6484b4e85210793
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065455"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Visual Studio'da Paralel İş Parçacıklarında Değişkenleri İzleme Ayarlama (C#, Visual Basic, C++)
Paralel izleme penceresi, bir ifadenin birden çok iş parçacığında yer alan değerleri aynı anda görüntüebilirsiniz. Her satır bir uygulamada çalışan bir iş parçacığını temsil eder, ancak bir iş parçacığı birden çok satırda temsil olabilir. Daha belirgin olarak her satır, işlev imzası geçerli yığın çerçevesindeki işlevle eşleşen bir işlev çağrısını temsil eder. Sütunlarda yer alan öğeleri sıralayabilirsiniz, yeniden sıralayabilirsiniz, kaldırabilir ve gruplayabilirsiniz. İş parçacıklarını bayrakla askıya alabilir, unflag, dondurabilir (askıya alabilir) ve çözülme (sürdürme) için kullanılabilir. Paralel İzleme penceresinde aşağıdaki **sütunlar görüntülenir:**

- Özellikle dikkat etmek istediğiniz bir iş parçacığını işaretleyebilirsiniz bayrak sütunu.

- Geçerli iş parçacığı sütunu, sarı bir ok geçerli iş parçacığını gösterir (curly kuyruğu olan yeşil bir ok, geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı bağlamına sahip olduğunu gösterir).

- Makineyi, işlemi, kutucuğu, görevi ve iş parçacığını görüntüley gören yapılandırılabilir bir sütun.

  > [!TIP]
  > Görev bilgilerini Paralel İzleme **penceresinde görüntülemek** için önce Görev penceresini **açabilirsiniz.**

- İzlemek *için ifade* girebilirsiniz boş saat ekleme sütunları.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Paralel Bağlantı Noktası'izleme penceresi

1. Kodda bir kesme noktası ayarlayın.

2. Menü çubuğunda Hata Ayıkla, **Hata Ayıklamayı** **Başlat'ı seçin.** Uygulamanın kesme noktalarına ulaşacak şekilde beklemesi.

3. Menü çubuğunda Hata **Ayıkla'Windows,** **Paralel** İzleme **'yi ve** ardından bir izleme penceresi seçin. En fazla dört pencere açsanız iyi olabilir.

### <a name="to-add-a-watch-expression"></a>İzleme ifadesi eklemek için

- Boş saat ekleme *sütunlarından birini seçin* ve bir izleme ifadesi girin.

### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını bayrakla bayrakla bayraklama veya bayrağını açma

- Satır (ilk sütun) için bayrak sütununu seçin veya iş parçacığının kısayol menüsünü açıp Bayrak **veya** Bayrağı **Kaldır'ı seçin.**

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını görüntülemek için

- Paralel **İzleme penceresinin sol** üst köşesindeki Yalnızca Bayraklı Göster **düğmesini** seçin.

### <a name="to-switch-to-another-thread"></a>Başka bir iş parçacığına geçmek için

- Geçerli iş parçacığı sütununa (ikinci sütun) çift tıklayın. (Klavye: Satırı seçin ve Enter tuşuna basın.)

### <a name="to-sort-a-column"></a>Bir sütunu sıralamak için

- Sütun başlığını seçin.

### <a name="to-group-threads"></a>İş parçacıklarını grupla

- Parallel izleme penceresi kısayol menüsünü açın, **Grupla'yı seçin** ve ardından uygun alt menü öğesini seçin.

### <a name="to-freeze-or-thaw-threads"></a>İş parçacıklarını dondurma veya çözme

- Satırın kısayol menüsünü açın  ve Dondurma veya **Çözme'yi seçin.**

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Paralel veri kaynağında verileri dışarı izleme penceresi

- Dosyada **aç düğmesini Excel** sonra Csv'de aç Excel **CSV'ye** **aktar'ı seçin.**

### <a name="to-filter-by-a-boolean-expression"></a>Boole ifadesine göre filtrelemek için

- Boole İfadesine Göre Filtrele **kutusuna bir Boole ifadesi** girin. Hata ayıklayıcısı her iş parçacığı bağlamı için ifadeyi değerlendirir. Yalnızca değerin görüntüleniyor `true` olduğu satırlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl: GPU İş Parçacıkları Penceresini Kullanma](../debugger/how-to-use-the-gpu-threads-window.md)
- [Adım adım kılavuz: C++ AMP Uygulamanın Hata Ayıklaması](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)