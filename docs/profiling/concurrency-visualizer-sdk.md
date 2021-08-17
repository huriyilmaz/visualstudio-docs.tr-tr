---
title: Eşzamanlılık Görselleştirici SDK'sı | Microsoft Docs
description: Kodunuzu işaretleyicileri görüntülemek üzere görüntülemek için Eşzamanlılık Görselleştirici SDK'sı kullanmayı öğrenin. İşaretçiler, eşzamanlılık Görselleştiricisi'nde olayları işaretlemek için görünen simgelerdir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 648d9375dc71d611e3d5162a7bf39b6af26c2439914f399a01d11da815023d3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355587"
---
# <a name="concurrency-visualizer-sdk"></a>Eşzamanlılık Görselleştiricisi SDK
Eşzamanlılık Görselleştiricisi'nde ek bilgileri görüntülemek için Eşzamanlılık Görselleştiricisi SDK'sı kullanarak kaynak kodunuzu takip edebilirsiniz. Ek verileri kodundaki aşamalar ve olaylarla ilişkilendirilebilirsiniz. Bu ek görselleştirmeler işaretçi *olarak bilinir.*  Giriş niteliğinde bir kılavuz için [bkz. Eşzamanlılık GörselleştiriciSI SDK'sı ile giriş.](/archive/blogs/visualizeparallel/introducing-the-concurrency-visualizer-sdk)

## <a name="properties"></a>Özellikler
 Bayraklar, span'lar ve iletilerin her biri iki özele sahiptir: kategori ve önem. Gelişmiş [Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, görüntülenen işaretçileri filtrelemek için bu özellikleri kullanabilirsiniz. Ayrıca, bu özellikler işaretçilerin görsel gösterimini etkiler. Örneğin, bayrakların boyutu önemi temsil etmek için kullanılır. Ayrıca kategoriyi belirtmek için renk kullanılır.

## <a name="basic-usage"></a>Temel kullanım
 Eşzamanlılık Görselleştiricisi, işaretçi oluşturmak için kullanabileceğiniz varsayılan bir sağlayıcıyı gösterir. Sağlayıcı zaten Eşzamanlılık Görselleştiricisi ile birlikte kaydedilmiştir ve işaretleyicilerin kullanıcı arabiriminde görünmesi için başka bir şey yapmak zorunda değildir.

### <a name="c-and-visual-basic"></a>C# ve Visual Basic
 C#, Visual basic ve diğer yönetilen kodlarda Markers sınıfındaki yöntemleri çağırarak varsayılan [sağlayıcıyı](/previous-versions/hh694099(v=vs.140)) kullanın. İşaretleyici oluşturmak için dört yöntemi ortaya çıkarır: [WriteFlag](/previous-versions/hh694185%28v%3dvs.140%29), [EnterSpan,](/previous-versions/hh694205(v=vs.140)) [WriteMessage](/previous-versions/hh694161(v=vs.140))ve [WriteAlert.](/previous-versions/hh694180(v=vs.140)) Özellikler için varsayılan değerleri kullanmak isteyip istemenize bağlı olarak, bu işlevler için birden çok aşırı yükleme vardır.  En basit aşırı yükleme yalnızca olayın açıklamasını belirten bir dize parametresi alır. Açıklama Eşzamanlılık Görselleştiricisi raporlarında görüntülenir.

##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesine SDK desteği eklemek için

1. Menü çubuğunda Analiz, **Eşzamanlılık** **Görselleştiricisi,** Projeye **SDK ekle'yi seçin.**

2. SDK'ya erişmek istediğiniz projeyi seçin ve ardından Sdk'yı Seçili **Sdk'ya ekle Project** seçin.

3. Kodunuza bir içeri aktarma veya using deyimi ekleyin.

    ```csharp
    using Microsoft.ConcurrencyVisualizer.Instrumentation;
    ```

    ```VB
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation
    ```

### <a name="c"></a>C++
 C++ içinde bir marker_series [Class nesnesi](../profiling/marker-series-class.md) oluşturun ve işlevleri çağırarak kullanın.  sınıfı işaretçi oluşturmak için üç işlev `marker_series` sunar: [marker_series::write_flag Metodu,](../profiling/marker-series-write-flag-method.md) [marker_series::write_message](../profiling/marker-series-write-message-method.md)Yöntemi ve [marker_series::write_alert Yöntemi.](../profiling/marker-series-write-alert-method.md)

##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>C++ veya C projesine SDK desteği eklemek için

1. Menü çubuğunda Analiz, **Eşzamanlılık** **Görselleştiricisi,** Projeye **SDK ekle'yi seçin.**

2. SDK'ya erişmek istediğiniz projeyi seçin ve ardından Sdk'yı Seçili **Sdk'ya ekle Project** seçin.

3. C++ için dahil `cvmarkersobj.h` edin. C için `cvmarkers.h` dahil.

4. Kodunuz için bir using deyimi ekleyin.

    ```cpp
    using namespace Concurrency::diagnostic;
    ```

5. Bir nesnesi `marker_series` oluşturun ve bunu oluşturucuya `span` iletir.

    ```C++

    marker_series mySeries;
    span s(mySeries, _T("Span description"));

    ```

## <a name="custom-usage"></a>Özel kullanım
 Gelişmiş senaryolar için Eşzamanlılık Görselleştirici SDK'sı daha fazla denetim sağlar.  İki temel kavram daha gelişmiş senaryolarla ilişkilendirilmektedir: işaretçi sağlayıcıları ve işaretçi serisi. İşaretçi sağlayıcıları farklı ETW sağlayıcılarıdır (her biri farklı bir GUID'ye sahip). İşaretçi serisi, bir sağlayıcı tarafından oluşturulan olayların seri kanallarıdır. Bunları bir işaretçi sağlayıcısı tarafından oluşturulan olayları düzenlemek için kullanabilirsiniz.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>C# veya Visual Basic projesinde yeni bir işaretçi sağlayıcısı kullanmak için

1. [MarkerWriter nesnesi](/previous-versions/hh694138(v=vs.140)) oluşturun.  Oluşturucu bir GUID alır.

2. Sağlayıcıyı kaydetmek için Eşzamanlılık Görselleştiricisi Gelişmiş Ayarlar [kutusunu](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) açın.  **İşaretçiler sekmesini** ve ardından Yeni Sağlayıcı **Ekle düğmesini** seçin. Gelişmiş [Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda, sağlayıcıyı oluşturmak için kullanılan GUID'yi ve sağlayıcının açıklamasını girin.

#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>C++ veya C projesinde yeni bir işaretçi sağlayıcısı kullanmak için

1. İşlevi `CvInitProvider` kullanarak bir PCV_PROVIDER.  Oluşturucu bir GUID* alır ve \* PCV_PROVIDER.

2. Sağlayıcıyı kaydetmek için Gelişmiş Ağ [İletişim Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) açın.  **İşaretçiler sekmesini** ve ardından Yeni Sağlayıcı **Ekle düğmesini** seçin. Bu iletişim kutusunda, sağlayıcıyı oluşturmak için kullanılan GUID'yi ve sağlayıcının açıklamasını girin.

#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>C# veya Visual Basic projesinde işaretçi Visual Basic kullanma

1. Yeni bir [MarkerSeries kullanmak](/previous-versions/hh694127(v=vs.140))için, önce bir [MarkerWriter](/previous-versions/hh694138(v=vs.140)) nesnesi kullanarak oluşturun ve ardından doğrudan yeni seriden işaretçi olayları oluşturun.

    ```csharp
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries("Series 1");
    series1.WriteFlag("My flag");
    ```

    ```VB
    Dim series1 As New myMarkerWriter.CreateMarkerSeries("Series 1")
    series1.WriteFlag("My flag")
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C++ projesinde işaretçi serisi kullanmak için

1. Bir nesnesi `marker_series` oluşturun.  Bu yeni seriden olaylar üretesiniz.

    ```scr
    marker_series series;
    series.write_flag(_T("Hello world!"));
    ```

#### <a name="to-use-a-marker-series-in-a-c-project"></a>C projesinde işaretçi serisi kullanmak için

1. İşlevi `CvCreateMarkerSeries` kullanarak bir PCV_MARKERSERIES.

    ```C++
    PCV_MARKERSERIES series;
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);
    CvWriteFlag(series, _T("Writing a flag"));
    ```

## <a name="see-also"></a>Ayrıca bkz.

|Başlık|Açıklama|
|-----------|-----------------|
|[C++ kitaplık başvurusu](../profiling/cpp-library-reference.md)|C++ için Eşzamanlılık GörselleştiriciSI API'sini açıklar.|
|[C kitaplığı başvurusu](../profiling/c-library-reference.md)|C için Eşzamanlılık GörselleştiriciSI API'sini açıklar.|
|[Araçları](/previous-versions/hh694104(v=vs.140))|Yönetilen kod için Eşzamanlılık GörselleştiriciSI API'sini açıklar.|
|[Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)|Eşzamanlılık yöntemi kullanılarak oluşturulan ve iş parçacığı yürütme verilerini içeren profil oluşturma veri dosyalarının görünümleri ve raporları için başvuru bilgileri.|