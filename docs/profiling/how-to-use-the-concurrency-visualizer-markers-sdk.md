---
title: Eşzamanlılık Görselleştiricisi İşaretçileri SDK'sı | Microsoft Docs
description: Yayma ve yazma bayrakları, iletiler ve uyarılar oluşturmak Visual Studio eşzamanlılık Görselleştiricisi işaretçileri SDK'sı kullanmayı öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 203200b2b5326faa9c140f4a1bb414c0b8edbd1ae27eec5dfdb5247f205075db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368350"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Nasıl: Eşzamanlılık Görselleştiricisi işaretçileri SDK'sı kullanma
Bu konu başlığında, eşzamanlılık GörselleştiriciSI SDK'sı kullanarak yayma ve bayrak, ileti ve uyarı oluşturma hakkında bilgi ve bilgiler ve bilgiler yer almaktadır.

### <a name="to-use-c"></a>C++ kullanmak için

1. Uygulamanıza Eşzamanlılık GörselleştiriciSI SDK'sı desteği ekleyin. Daha fazla bilgi için [bkz. Eşzamanlılık Görselleştirici SDK'sı.](../profiling/concurrency-visualizer-sdk.md)

2. SDK için `include` bir deyimi ve deyimi `using` ekleyin.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Varsayılan işaretçi serisinde üç yayma alanı oluşturmak ve her bir yayılmaya bir bayrak, ileti ve uyarı yazmak için kod ekleyin. Bayrak, ileti ve uyarı yazma yöntemleri, marker_series [üyesidir.](../profiling/marker-series-class.md) Span sınıfının [oluşturucusu,](../profiling/span-class.md) her bir `marker_series` aralığın belirli bir işaretçi serisiyle ilişkilendirilen bir nesnesi gerektirir. Silindiğinde `span` sona erer.

    ```cpp
    marker_series series;
    span *flagSpan = new span(series, 1, _T("flag span"));
    series.write_flag(_T("Here is the flag."));
    delete flagSpan;

    span *messageSpan = new span(series, 2, _T("message span"));
    series.write_flag(_T("Here is the message."));
    delete messageSpan;

    span *alertSpan = new span(series, 3, _T("alert span"));
    series.write_flag(_T("Here is the alert."));
    delete alertSpan;
    ```

4. Uygulamayı çalıştırmak ve Eşzamanlılık Görselleştirici'yi görüntülemek için menü **çubuğunda** Analiz **,** Eşzamanlılık Görselleştiricisi, Geçerli Project Ile Başla'ya tıklayın. Aşağıdaki çizimde Eşzamanlılık Görselleştiricisi'nde üç yayma ve üç işaretçi gösterilmiştir.

     ![3 işaretçi ve uyarı ile Eşzamanlılık Görselleştiricisi](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. için işaretçi serisi için bir dize adı alan oluşturucu çağırarak ek, özel işaretçi `marker_series` serisi oluşturmak için kod ekleyin.

    ```cpp
    marker_series flagSeries(_T("flag series"));
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));
    flagSeries.write_flag(1, _T("flag"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete flagSeriesSpan;

    marker_series messageSeries(_T("message series"));
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));
    messageSeries.write_message(1, _T("message"));
    // Sleep to even out the display in the Concurrency Visualizer.
    Sleep(50);
    delete messageSeriesSpan;
    ```

6. Eşzamanlılık Görselleştiricisini görüntülemek için geçerli projeyi başlatma. İki işaretçi serisi, İş Parçacıkları Görünümünde kendi kulvarlarında görünür. Aşağıdaki çizimde iki yeni aralık gösterilmiştir.

     ![Eşzamanlılık Görselleştiricisi'nde bayrak aralığı ve ileti aralığı ile bir işaretçi, bayrak ve ileti serisi gösteren İş Parçacıkları görünümünün ekran görüntüsü.](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Visual Basic veya C kullanmak için\#

1. Uygulamanıza Eşzamanlılık GörselleştiriciSI SDK'sı desteği ekleyin. Daha fazla bilgi için [bkz. Eşzamanlılık Görselleştirici SDK'sı.](../profiling/concurrency-visualizer-sdk.md)

2. SDK için `using` bir `Imports` veya deyimi ekleyin.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Varsayılan işaretçi serisinde üç yayma alanı oluşturmak için kod ekleyin ve her bir yayılmaya bir bayrak, ileti ve uyarı yazın. Statik yöntemi [çağırarak bir Span](/previous-versions/hh694189(v=vs.140)) nesnesi `EnterSpan` oluştururuz. Varsayılan seriye yazmak için [Markers](/previous-versions/hh694099(v=vs.140)) sınıfının statik yazma yöntemlerini kullanırsiniz.

    ```vb
    Dim flagSpan As Span = Markers.EnterSpan("flag span")
    Markers.WriteFlag("Here is the flag.")
    flagSpan.Leave()

    Dim messageSpan As Span = Markers.EnterSpan("message span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteMessage("Here is a message")
    messageSpan.Leave()

    Dim alertSpan As Span = Markers.EnterSpan("alert span")
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1)
    Markers.WriteAlert("Here is an alert")
    alertSpan.Leave()
    ```

    ```csharp
    Span flagSpan = Markers.EnterSpan("flag span");
    Markers.WriteFlag("Here is the flag.");
    flagSpan.Leave();

    Span messageSpan = Markers.EnterSpan("message span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteMessage("Here is a message");
    messageSpan.Leave();

    Span alertSpan = Markers.EnterSpan("alert span");
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.
    System.Threading.Thread.Sleep(1);
    Markers.WriteAlert("Here is an alert");
    alertSpan.Leave();
    ```

4. Uygulamayı çalıştırmak ve Eşzamanlılık Görselleştirici'yi görüntülemek için menü **çubuğunda** Analiz **,** Eşzamanlılık Görselleştiricisi, Geçerli Project Ile Başla'ya tıklayın. Aşağıdaki çizimde Eşzamanlılık Görselleştiricisi'nin İş Parçacıkları Görünümü'nde üç yayma ve üç işaretçi gösterilir.

     ![İşaretçiler ve uyarılar ile Eşzamanlılık Görselleştiricisi](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")

5. Statik [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) yöntemini kullanarak müşteri işaretçi serisi oluşturmak için kod ekleyin. [MarkerSeries sınıfı,](/previous-versions/hh694127(v=vs.140)) yayma ve bayrak, ileti ve uyarı oluşturma yöntemlerini içerir.

    ```VB

    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")
    System.Threading.Thread.Sleep(1)
    flagSeries.WriteFlag(1, "flag")
    System.Threading.Thread.Sleep(1)
    flagSeriesSpan.Leave()

    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")
    messageSeries.WriteMessage("message")
    System.Threading.Thread.Sleep(1)
    messageSeriesSpan.Leave()
    ```

    ```csharp

    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");
    System.Threading.Thread.Sleep(1);
    flagSeries.WriteFlag(1, "flag");
    System.Threading.Thread.Sleep(1);
    flagSeriesSpan.Leave();

    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");
    messageSeries.WriteMessage("message");
    System.Threading.Thread.Sleep(1);
    messageSeriesSpan.Leave();
    ```

6. Eşzamanlılık Görselleştiricisini görüntülemek için geçerli projeyi başlatma. Üç işaretçi serisi, İş Parçacıkları Görünümünde kendi kulvarlarında görünür. Aşağıdaki çizimde üç yeni aralık gösterilmiştir.

     ![Eşzamanlılık Görselleştiricisi'nde ileti, uyarı ve bayrak aralığı ile bir işaretçi, bayrak ve ileti serisini gösteren İş Parçacıkları görünümünün ekran görüntüsü.](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
