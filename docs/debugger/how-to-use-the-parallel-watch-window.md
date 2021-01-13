---
title: Paralel Iş parçacıklarında değişkenler için bir Izleme ayarlama | Microsoft Docs
description: Visual Studio 'da paralel iş parçacıklarında değişkenler için bir izleme ayarlayın. Aynı anda birden çok iş parçacığında bir ifadenin tuttuğu değerleri görüntüler.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28aeffb629a44c296fb9a349e165c7ce88f70b0c
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150580"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Visual Studio 'da paralel Iş parçacıklarında değişkenler için bir Izleme ayarlama (C#, Visual Basic, C++)
Paralel izleme penceresi, bir ifadenin birden çok iş parçacığında tuttuğu değerleri aynı anda görüntüleyebilirsiniz. Her satır bir uygulamada çalışan bir iş parçacığını temsil eder, ancak bir iş parçacığı birden çok satırda gösterilebilir. Daha belirgin olarak, her satır, işlev imzası geçerli yığın çerçevesindeki işlevle eşleşen bir işlev çağrısını temsil eder. Sütunlardaki öğeleri sıralayabilir, yeniden sıralayabilir, kaldırabilir ve gruplandırabilirsiniz. İş parçacıklarını bayrak, unbayrak, dondurma (askıya al) ve çözme (devam etme). **Paralel izleme** penceresinde aşağıdaki sütunlar görüntülenir:

- Özel dikkat etmek istediğiniz bir iş parçacığını işaretleyecek bayrak sütunu.

- Sarı bir okun geçerli iş parçacığını gösterdiği geçerli iş parçacığı sütunu (küme ayracı içeren yeşil bir ok, geçerli olmayan bir iş parçacığının geçerli hata ayıklayıcı içeriğine sahip olduğunu gösterir).

- Makine, işlem, kutucuk, görev ve iş parçacığını görüntüleyebilen yapılandırılabilir bir sütun.

  > [!TIP]
  > Görev bilgilerini **paralel izleme** penceresinde göstermek için, önce **görev** penceresini açmanız gerekir.

- Görüntülenecek ifadeleri girebileceğiniz, boş *ekleme izleme* sütunları.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>Paralel izleme penceresi görüntüleme

1. Kodda bir kesme noktası ayarlayın.

2. Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin. Uygulamanın kesme noktasına ulaşmasını bekleyin.

3. Menü çubuğunda **Hata Ayıkla**, **Windows**, **paralel izleme**' yi seçin ve ardından bir Gözcü penceresi seçin. Dört tane pencere açabilirsiniz.

### <a name="to-add-a-watch-expression"></a>Bir Gözcü ifadesi eklemek için

- Boş bir *Gözcü Ekle* sütunlarından birini seçin ve ardından bir Gözcü ifadesi girin.

### <a name="to-flag-or-unflag-a-thread"></a>Bir iş parçacığını işaretlemek veya bayrak kaldırmak için

- Satır için bayrak sütununu seçin (ilk sütun) veya iş parçacığının kısayol menüsünü açın ve **bayrak** ya da **Unflag**' ı seçin.

### <a name="to-display-only-flagged-threads"></a>Yalnızca bayraklı iş parçacıklarını göstermek için

- **Paralel izleme** penceresinin sol üst köşesindeki **yalnızca bayraklı bayrağı göster** düğmesini seçin.

### <a name="to-switch-to-another-thread"></a>Başka bir iş parçacığına geçiş yapmak için

- Geçerli iş parçacığı sütununa (ikinci sütun) çift tıklayın. (Klavye: satırı seçin ve ENTER tuşuna basın.)

### <a name="to-sort-a-column"></a>Bir sütunu sıralamak için

- Sütun başlığını seçin.

### <a name="to-group-threads"></a>İş parçacıklarını gruplandırmak için

- Paralel izleme penceresi için kısayol menüsünü açın, **Gruplandır**' ı seçin ve ardından uygun alt menü öğesini seçin.

### <a name="to-freeze-or-thaw-threads"></a>İş parçacıklarını dondurmak veya çözme

- Satır için kısayol menüsünü açın ve **dondurma** veya **çözme** seçeneğini belirleyin.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>Verileri paralel izleme penceresi dışarı aktarmak için

- **Excel 'de aç** düğmesini seçin ve sonra **Excel 'de aç** veya **CSV 'ye aktar**' ı seçin.

### <a name="to-filter-by-a-boolean-expression"></a>Boole ifadesine göre filtrelemek için

- **Boole ifadesine göre filtrele** kutusuna bir Boole ifadesi girin. Hata ayıklayıcı, her bir iş parçacığı bağlamı için ifadeyi değerlendirir. Yalnızca değerin `true` görüntülendiği satırlar görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Nasıl yapılır: GPU Iş parçacıkları penceresini kullanma](../debugger/how-to-use-the-gpu-threads-window.md)
- [İzlenecek yol: C++ AMP uygulamasında hata ayıklama](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)