---
title: 'Nasıl Kullanılır: Eşzamanlılık Görselleştiricisi SDK| Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d97ea90963f70d3a06c669f08473bab27fa08bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68870339"
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Nasıl Kullanılır: Eşzamanlı Lık Görselleştiricisi SDK'yı kullanın
Bu konu, eşpara birimi görselleştiricisi SDK'nın nasıl kullanılacağını, açıklıklar oluşturmak ve bayraklar, mesajlar ve uyarılar yazmak için gösterir.

### <a name="to-use-c"></a>C++ kullanmak için

1. Uygulamanıza Eşzamanlı Görselleştirici SDK desteği ekleyin. Daha fazla bilgi için [Concurrency Visualizer SDK'ya](../profiling/concurrency-visualizer-sdk.md)bakın.

2. SDK `include` için `using` bir ekstre ve bir ekstre ekleyin.

    ```cpp
    #include <cvmarkersobj.h>
    using namespace Concurrency::diagnostic;
    ```

3. Varsayılan işaretçi serisinde üç açıklık oluşturmak için kod ekleyin ve her yayılma ya da bir tane olan bir bayrak, ileti ve bir uyarı yazın. Bayrak, mesaj ve uyarı yazma yöntemleri [marker_series](../profiling/marker-series-class.md) sınıfının üyeleridir. [Yayılma](../profiling/span-class.md) sınıfının oluşturucusu `marker_series` bir nesne gerektirir, böylece her açıklık belirli bir işaretçi serisiyle ilişkilendirilir. A `span` silindiğinde sona erer.

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

4. Menü çubuğunda, uygulamayı çalıştırmak ve Eşzamanlılık Görselleştiricisini görüntülemek için **Çözümle**, **Eşzamanlılık Görselleştiricisi**, **Geçerli Proje ile Başlat'ı** seçin. Aşağıdaki resimde Eşzamanlılık Görselleştiricisi'ndeki üç açıklık ve üç işaretçi gösterilmektedir.

     ![3 işaretleyici ve uyarı içeren Eşzamanlı Lık Görselleştiricisi](../profiling/media/cvmarkersnative.png "CvMarkersNative")

5. Marker serisi için `marker_series` bir dize adı alır için oluşturucu çağırarak ek, özel işaretçi serisi oluşturmak için kod ekleyin.

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

6. Eşzamanlı Lık Görselleştiricisini görüntülemek için geçerli projeyi başlatın. İki işaretçi serisi Threads View'da kendi şeritlerinde görünür. Aşağıdaki resimde iki yeni açıklık gösterilmektedir.

     ![3 özel marker serisi ile Eşzamanlılık Görselleştirici](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")

### <a name="to-use-visual-basic-or-c"></a>Visual Basic veya C kullanmak için\#

1. Uygulamanıza Eşzamanlı Görselleştirici SDK desteği ekleyin. Daha fazla bilgi için [Concurrency Visualizer SDK'ya](../profiling/concurrency-visualizer-sdk.md)bakın.

2. SDK `using` `Imports` için bir veya ekstre ekleyin.

    ```vb
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

3. Varsayılan işaretçi serisinde üç açıklık oluşturmak için kod ekleyin ve her yayılma ya da bir tane olan bir bayrak, ileti ve bir uyarı yazın. Statik `EnterSpan` yöntemi çağırarak bir [Span](/previous-versions/hh694189(v=vs.140)) nesnesi oluşturursunuz. Varsayılan seriye yazmak için [İşaretçiler](/previous-versions/hh694099(v=vs.140)) sınıfının statik yazma yöntemlerini kullanırsınız.

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

4. Menü çubuğunda, uygulamayı çalıştırmak ve Eşzamanlılık Görselleştiricisini görüntülemek için **Çözümle**, **Eşzamanlılık Görselleştiricisi**, **Geçerli Proje ile Başlat'ı** seçin. Aşağıdaki resimde, Eşzamanlılık Görselleştiricisinin İş Parçacıkları Görünümü'nde üç açıklık ve üç işaretçi gösterilmektedir.

     ![İşaretçiler ve uyarılarla Eşzamanlı Görselleştirici](../profiling/media/cvmarkersmanaged.png "CvMarkersYönetilen")

5. Statik [CreateMarkerSeries](/previous-versions/hh694171(v=vs.140)) yöntemini kullanarak müşteri işaretçisi serisi oluşturmak için kod ekleyin. [MarkerSeries](/previous-versions/hh694127(v=vs.140)) sınıfı, yayılma alanları oluşturmak ve bayraklar, iletiler ve uyarılar yazmak için yöntemler içerir.

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

6. Eşzamanlı Lık Görselleştiricisini görüntülemek için geçerli projeyi başlatın. Üç işaretçi serisi, İş Parçacıkları Görünümü'nde kendi şeritlerinde görünür. Aşağıdaki resimde üç yeni açıklık gösterilmektedir.

     ![3 özel marker serisi ile Eşzamanlılık Görselleştirici](../profiling/media/cvmarkerseriesmanaged.png "CvmarkerSeriesManaged")

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)
