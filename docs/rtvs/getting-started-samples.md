---
title: Örnek R projeleri
description: R ve Visual Studio ile başlamak için bir örnek koleksiyonunun dizini.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: ef3316d929b00203815918a656568f75571e954e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75843817"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio örnek projeler için R Araçları

Bu örnek koleksiyonu R, R Tools for Visual Studio (RTVS) ve Microsoft Machine Learning Server'da başlar:

1. Örnekleri [zip dosyasını](https://github.com/Microsoft/RTVS-docs/archive/master.zip) indirin ve seçtiğiniz bir klasöre ayıklayın.
1. Projede iki klasörü görmek için açın: `examples/Examples.sln`

    - *A First Look at R,* R'ye yeni başlayanlar için nazik bir giriş sunar.
    - *MRS ve Machine Learning,* makine öğrenimi için R ve Microsoft Machine Learning Server'ın nasıl kullanılacağına örnek verir.

## <a name="a-first-look-at-r"></a>R'ye İlk Bakış

Bu örnek, iki kaynak dosyadaki kapsamlı yorumlar aracılığıyla R'ye derinlemesine bir giriş sağlar. En iyi deneyim için imleci dosyanın en üstüne yerleştirin ve kodu satır satır yat pencereye **R Interactive** göndermek için Ctrl+Enter tuşuna basın. (Paketleri yükleyen satırların tamamlanması bir veya iki dakika sürebilir.)

- `1-Getting Started with R.R`paketleri kullanma, veri yükleme ve analiz etme ve çizim dahil olmak üzere birçok R temelini kapsar.

    ![1-R.R örneğinden örnek çıktı](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R`görsel olarak çekici çizimleri ve basit sözdizimi ile bilinen ggplot2 grafik paketini sunar. Bu örnek, Fiji'den gelen deprem verilerini görselleştirir.

    ![2-Giriş ten ggplot2'ye örnek çıktı. R örneği](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server ve Machine Learning

Bu örnek koleksiyonu, makine öğrenme modelleri oluşturmak ve Microsoft [Machine Learning Server'dan](/machine-learning-server/what-is-machine-learning-server)yararlanmak için R'nin nasıl kullanılacağını göstermektedir.

Tüm örneklerde olduğu gibi, dosyayı açın, imleci en üste yerleştirin ve ardından **Ctrl**+**Enter**ile kod satırına satır adım atın. Her klasördeki işaretleme dosyaları da ek ayrıntılar içerir.

- `Benchmarks`Microsoft R Open ve Intel Math Kernel Library (MKL) kullanımı yla mümkün olan performans kazanımlarını göstermek için bir dizi yoğun, paralel doğrusal cebir hesaplaması çalıştırır. Benzetimli verilerle, kıyaslamalar özellikle bir iş parçacığı üzerindeki matris hesaplamalarını ikiye karşı karşı laştırır.

    ![Örnek kıyaslama konusu](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`Microsoft ML Server'ı kullanarak geçmiş bir veri kümesini temel alan bisiklet kiralamaları için bir talep tahmin modeli oluşturur.

- `Data_Exploration`üç komut dosyası içerir:

  - `Import Data from URL.R`URL'de tanımlanan bir veri dosyasının R'ye nasıl yüklenirolduğunu gösterir.
  - `Import Data from URL to xdf.R`URL'de tanımlanan bir veri dosyasının microsoft ML Server'a xdf olarak nasıl yüklenirken yüklenirken gösterir.
  - `Using ggplot2.R``A First Look at R/2-Introduction to ggplot2.R` etkileşimli 3B çizim de dahil olmak üzere ggplot2 işlevselliği daha kapsamlı bir tur vererek, örnek bir uzantısıdır.

      ![Ggplot2 kullanma çıktısı. R örneği](media/samples-3d-interactive.png)

- `Datasets`diğer örnekler tarafından kullanılan üç *.csv* dosyaları içerir
- `Flight_Delays_Prediction_with_R`r, `Flight_Delays_Prediction_with_MRS` makine öğrenimi ve tarihsel zamanında performans ve hava durumu verilerini kullanarak uçuş gecikmelerinin nasıl tahmin edilebildiğini gösterir.
- `Machine learning`uçuş gecikmeleri, konut fiyatları ve bisiklet kiralama tahmin öğrenmek için üç örnek içerir. Bu örnekler birlikte R ve Microsoft ML Server'ın gerçek dünyadaki sorunlara uygulanmasını göstermektedir. Ayrıca, azure machine learning çalışma alanını kullanarak birkaç popüler makine öğrenimi modelini nasıl kullanacağınızı ve bunları Azure [Web](https://azure.microsoft.com/services/machine-learning/) Hizmeti olarak nasıl dağıtabileceğinizi de gösterirler.

- `R_MRO_MRS_Comparison`Komutları, sözdizimi, yapılar ve performans ile R, Microsoft R Open ve Microsoft ML Server benzerliklerve farklılıklarını gösteren altı bölümlü bir karşılaştırmadır.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Microsoft R Open ve Microsoft ML Server'ın özelliği nedir?

[Microsoft R Open](https://mran.revolutionanalytics.com/download/), R Microsoft'un dağılımı, iki önemli şekilde [CRAN R](https://cran.r-project.org/) farklıdır:

1. [Intel Math Kernel Kitaplıkları](https://software.intel.com/intel-mkl)ile kullanıldığında [daha iyi hesaplama performansı.](https://mran.revolutionanalytics.com/rro/#intelmkl1) Kitaplıklar, Microsoft R Open ile birlikte kullanılmak üzere Microsoft'tan ücretsiz olarak indirilebilir.

1. [Tekrarlanabilir R Toolkit,](https://mran.revolutionanalytics.com/rro/#reproducibility) R programınızı oluşturmak için kullandığınız kitaplıkların çalışmanızı yeniden oluşturmak isteyen diğer kişiler tarafından her zaman kullanılabilir olmasını sağlar.

[Microsoft ML Server (MLS),](/machine-learning-server/what-is-machine-learning-server) daha fazla veriyi işlemenizi ve daha hızlı işlemenizi sağlayan R'nin bir uzantısıdır. R'ye iki güçlü yetenek verir:

1. RAM sınırlaması olmadan daha büyük veri kümeleri. ML Server, Hadoop kümeleri, veritabanları ve veri ambarları gibi çeşitli kaynaklardan gelen bellek dışı verileri işleyebilir.

1. Paralel, çok çekirdekli işleme. MLS, kullanılabilir olduğu tüm hesaplama kaynaklarına hesaplamayı verimli bir şekilde dağıtabilir. Kişisel iş istasyonunuzda veya uzak bir kümede MLS daha hızlı bir yanıt alır.

Aşağıdaki karşılaştırma MLS ve MRO MKL ile bazı matris hesaplama ile ilgili önemli ölçüde daha iyi hesaplama performansı Olduğunu göstermektedir R ve MRO MKL olmadan. Bu hesaplamada simüle edilmiş veriler kullanılır:

![MLS ve MRO ile MKL'nin MKL'siz R ve MRO ile karşılaştırılması](media/samples-speed-comparison.png)

MRO ve MLS ile R teknik bir karşılaştırma için, konu yla ilgili [Lixun Zhang ayrıntılı tartışma](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) göz atın.

Aşağıdaki şekil daha sonra 15 dakikadan daha büyük uçuş gecikmeleri tahmin etmek için Lojistik Regresyon modelleri binada kullanılan saniye içinde geçen süreyi karşılaştırır.  CRAN R'de kullanılan geçen süre, az sayıda satır artarken, MLS yalnızca yaklaşık iki kat artar. Bu kıyaslama hakkında ayrıntılı bilgi için *Benchmarks/rxGlm_benchmark'ye göz atın. R* örneği.

![rxGlm kıyaslama](media/samples-rxGLM-benchmark.png)
