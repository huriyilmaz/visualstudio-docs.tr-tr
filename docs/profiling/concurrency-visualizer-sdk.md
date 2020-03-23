---
title: Eşzamanlı Görüntüleyici SDK | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb48733f84dcf484d2c2d7ffb18e838faae07ab0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911191"
---
# <a name="concurrency-visualizer-sdk"></a>Eşzamanlılık Görselleştiricisi SDK
Eşzamanlılık Görselleştiricisi'nde ek bilgi görüntülemek için Eşzamanlılık Görselleştiricisi SDK'yı kullanarak kaynak kodunuzu kullanarak kaynak kodunuzu alet edebilirsiniz. Ek verileri, kodunuzdaki aşamalar ve olaylarla ilişkilendirebilirsiniz. Bu ek görselleştirmeler *işaretçiler*olarak bilinir.  Giriş için, [Eşzamanlılık Görselleştirici SDK tanıtımı](https://blogs.msdn.microsoft.com/visualizeparallel/2011/10/17/introducing-the-concurrency-visualizer-sdk/)bakın.

## <a name="properties"></a>Özellikler
 Bayrakların, yayılma ların ve iletilerin her birinin iki özelliği vardır: kategori ve önem. Gelişmiş [Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, görüntülenen işaretçiler kümesine filtre açmak için bu özellikleri kullanabilirsiniz. Buna ek olarak, bu özellikler işaretçilerin görsel temsilini etkiler. Örneğin, bayrakların boyutu önemli temsil etmek için kullanılır. Buna ek olarak, renk kategoriyi belirtmek için kullanılır.

## <a name="basic-usage"></a>Temel kullanım
 EşzamanlıLık Görselleştiricisi, işaretçiler oluşturmak için kullanabileceğiniz varsayılan bir sağlayıcı ortaya çıkarır. Sağlayıcı zaten Eşzamanlılık Görselleştiricisi ile birlikte kayıtlıdır ve işaretçilerin Kullanıcı Bir A.B.D.'de görünmesi için başka bir şey yapmanız adada yoktur.

### <a name="c-and-visual-basic"></a>C# ve Visual Basic
 C#, Visual basic ve diğer yönetilen kodlarda, [Işaretçiler](/previous-versions/hh694099(v=vs.140)) sınıfında yöntemleri çağırarak varsayılan sağlayıcıkullanın. Bu işaretleri oluşturmak için dört yöntem ortaya çıkarır: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan](/previous-versions/hh694205(v=vs.140)), [WriteMessage](/previous-versions/hh694161(v=vs.140)), ve [WriteAlert](/previous-versions/hh694180(v=vs.140)). Bu işlevler için, özellikler için varsayılanları kullanmak isteyip istemediğinize bağlı olarak birden çok aşırı yükleme vardır.  En basit aşırı yükleme, yalnızca olayın açıklamasını belirten bir dize parametresi alır. Açıklama EşzamanlıLık Görselleştirici raporlarında görüntülenir.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>C# veya Visual Basic projesine SDK desteği eklemek için

1. Menü çubuğunda, **Analiz**et, **Eşzamanlı Görüntüleyici**, **Projeye SDK ekle'yi**seçin.

2. SDK'ya erişmek istediğiniz projeyi seçin ve ardından **Seçili Projeye SDK Ekle** düğmesini seçin.

3. Koduna bir içeri alma veya ekstre kullanma ekleyin.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 C++'da [marker_series Sınıf](../profiling/marker-series-class.md) nesnesi oluşturun ve işlevleri çağırmak için kullanın.  Sınıf `marker_series` belirteçleri oluşturmak için üç işlevleri ortaya çıkarır, [marker_series::write_flag Yöntemi,](../profiling/marker-series-write-flag-method.md) [marker_series::write_message Yöntemi](../profiling/marker-series-write-message-method.md), ve [marker_series::write_alert Yöntemi](../profiling/marker-series-write-alert-method.md).

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>C++ veya C projesine SDK desteği eklemek için

1. Menü çubuğunda, **Analiz**et, **Eşzamanlı Görüntüleyici**, **Projeye SDK ekle'yi**seçin.

2. SDK'ya erişmek istediğiniz projeyi seçin ve ardından **Seçili Projeye SDK Ekle** düğmesini seçin.

3. C++için. `cvmarkersobj.h` C için, `cvmarkers.h`ekle.

4. Kodunuza bir kullanma deyimi ekleyin.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Bir `marker_series` nesne oluşturun ve `span` oluşturucuya geçirin.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Özel kullanım
 Gelişmiş senaryolar için Eşzamanlı Görselleştirici SDK daha fazla denetim ortaya çıkarır.  İki ana kavram daha gelişmiş senaryolarla ilişkilidir: işaretsağlayıcılar ve işaretleyici serisi. İşaretleyici sağlayıcıları farklı ETW sağlayıcılarıdır (her birinin farklı bir GUID'si vardır). İşaretleyici serisi, tek bir sağlayıcı tarafından oluşturulan olayların seri kanallarıdır. Bunları bir işaret sağlayıcı tarafından oluşturulan olayları düzenlemek için kullanabilirsiniz.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>C# veya Visual Basic projesinde yeni bir işaret sağlayıcı kullanmak için

1. Bir [MarkerWriter nesnesi](/previous-versions/hh694138(v=vs.140)) oluşturun.  Oluşturucu bir GUID alır.

2. Sağlayıcıyı kaydetmek için Eşzamanlı Görselleştirici [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu açın.  **İşaretçiler** sekmesini seçin ve ardından **Yeni Sağlayıcı Ekle** düğmesini seçin. Gelişmiş [Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusuna, sağlayıcıyı ve sağlayıcının açıklamasını oluşturmak için kullanılan GUID'yi girin.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>C++ veya C projesinde yeni bir işaretsağlayıcı kullanmak için

1. `CvInitProvider` bir PCV_PROVIDER başlatma işlevini kullanın.  Yapıcı bir GUID* alır\*ve PCV_PROVIDER.

2. Sağlayıcıyı kaydetmek için [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu açın.  **İşaretçiler** sekmesini seçin ve ardından **Yeni Sağlayıcı Ekle** düğmesini seçin. Bu iletişim kutusuna, sağlayıcıyı ve sağlayıcının açıklamasını oluşturmak için kullanılan GUID'yi girin.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>C# veya Visual Basic projesinde işaretleyici serisi kullanmak için

1. Yeni bir [MarkerSeries](/previous-versions/hh694127(v=vs.140))kullanmak için, önce bir [MarkerWriter](/previous-versions/hh694138(v=vs.140)) nesnesi kullanarak oluşturun ve ardından doğrudan yeni seriden işaretolayları oluşturun.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C++ projesinde işaretleyici serisi kullanmak için

1. Bir `marker_series` nesne oluşturun.  Bu yeni seriden olaylar oluşturabilirsiniz.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C projesinde işaretleyici serisi kullanmak için

1. Bir `CvCreateMarkerSeries` PCV_MARKERSERIES oluşturmak için işlevi kullanın.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Ayrıca bkz.

|Başlık|Açıklama|
|-----------|-----------------|
|[C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)|C++için Eşzamanlı Görselleştirici API'yi açıklar.|
|[C kitaplık başvurusu](../profiling/c-library-reference.md)|C için Eşzamanlı Görselleştirici API açıklar.|
|[Araçları](/previous-versions/hh694104(v=vs.140))|Yönetilen kod için Eşzamanlı Görselleştirici API'yi açıklar.|
|[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)|Eşzamanlılık yöntemi kullanılarak oluşturulan ve iş parçacığı yürütme verilerini içeren profil oluşturma veri dosyalarının görünümleri ve raporları için başvuru bilgileri.|