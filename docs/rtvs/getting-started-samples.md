---
title: Örnek R projeleri
description: R ve Visual Studio ile çalışmaya başlamaya başlamaya Visual Studio.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: b52d548f250df47c120d656f763f75e56d3ee742
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628227"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio için R Araçları projelerini uygulama

Bu örnek koleksiyonu R, Visual Studio için R Araçları (RTVS) ve Microsoft Machine Learning Server:

1. Örnekler [zip dosyasını indirin](https://github.com/Microsoft/RTVS-docs/archive/master.zip) ve istediğiniz bir klasöre ayıklayın.
1. Projede `examples/Examples.sln` iki klasör görmek için açın:

    - *R'ye İlk Bakış, R'ye* yeni gelenler için bir tanıtım verir.
    - *MRS ve Machine Learning* makine öğrenmesi için R ve Microsoft Machine Learning Server kullanımına örnekler verir.

## <a name="a-first-look-at-r"></a>R'ye İlk Bakış

Bu örnek, iki kaynak dosyada yer alan kapsamlı açıklamalar aracılığıyla R'ye kapsamlı bir giriş sağlar. En iyi deneyim için imleci dosyanın en üstüne yerleştirerek Ctrl+Enter tuşlarına basarak kodu tek tek **R Etkileşim.** (Paketleri yüklayan satırların tamamlanması bir veya iki dakika sürebilir.)

- `1-Getting Started with R.R` paketleri kullanma, verileri yükleme ve analiz etme ve çizim gibi birçok R temelini kapsar.

    ![R.R örneğiyle 1-Başlarken örnek çıktı](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` görsel olarak çekici çizimleri ve basit söz dizimi ile bilinen ggplot2 grafik paketini sunar. Bu örnekte Fiji'den deprem verileri görselleştirildi.

    ![2-ggplot2'ye giriş'in örnek çıktısı. R örneği](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server ve Machine Learning

Bu örnek koleksiyonu, makine öğrenmesi modelleri oluşturmak ve bu modellerden yararlanmak için R'nin nasıl [Microsoft Machine Learning Server.](/machine-learning-server/what-is-machine-learning-server)

Tüm örneklerde olduğu gibi dosyayı açın, imleci en üstüne yerleştirin ve **Ctrl** Enter tuşuna basarak kod satırı boyunca adım + **adım inin.** Her klasördeki markdown dosyaları da ek ayrıntılar içerir.

- `Benchmarks` , Microsoft R Open ve Intel Math Kernel Library (MKL) kullanarak mümkün olan performans kazançlarını göstermek için bir dizi yoğun, paralel doğrusal cebir hesaplaması çalıştırır. Simülasyon verileriyle karşılaştırmalar, matris hesaplamalarını bir iş parçacığında iki iş parçacığıyla karşılaştırıldığında gösterir.

    ![Örnek karşılaştırma çizimi](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`, Microsoft ML Server kullanarak geçmiş veri kümelerini temel alan bisiklet kiralamaları için bir talep tahmin modeli ML Server.

- `Data_Exploration` üç betik içerir:

  - `Import Data from URL.R` , URL ile tanımlanan bir veri dosyasının R'ye nasıl yük olduğunu gösterir.
  - `Import Data from URL to xdf.R`, MICROSOFT ML Server'ye URL ile tanımlanan veri ML Server bir xdf olarak nasıl yüklneği gösterir.
  - `Using ggplot2.R` , etkileşimli 3D çizim de dahil olmak üzere ggplot2'nin işlevselliğine daha kapsamlı bir tur atarak örneğin `A First Look at R/2-Introduction to ggplot2.R` bir uzantısıdır.

      ![ggplot2 Kullanma çıkışı. R örneği](media/samples-3d-interactive.png)

- `Datasets` , diğer *.csv* kullanılan üç dosya dosyası içerir
- `Flight_Delays_Prediction_with_R` R, makine öğrenmesi ve geçmiş zamanında performans ile hava durumu verilerini kullanarak uçuş `Flight_Delays_Prediction_with_MRS` gecikmelerini tahmin etmek için nasıl tahminde bulunduracaklarını gösterir.
- `Machine learning` uçuş gecikmelerini, konut fiyatlarını ve bisiklet kiralamalarını tahmin etmek için üç örnek içerir. Bu örnekler birlikte R ve Microsoft ML Server gerçek dünya sorunlarına uygulamayı gösteriyor. Ayrıca, çeşitli popüler makine öğrenmesi modellerini nasıl kullanabileceğiniz ve bunları azure web hizmeti olarak dağıtarak Azure Machine Learning [gösterir.](https://azure.microsoft.com/services/machine-learning/)

- `R_MRO_MRS_Comparison`, komutlar, söz dizimi, yapılar ve performans ile R, Microsoft R Open ve Microsoft ML Server benzerliklerini ve farklarını gösteren altı bölümden bir karşılaştırmadır.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Microsoft R Open ve Microsoft ML Server hakkında özel ML Server?

[Microsoft'un](https://mran.revolutionanalytics.com/download/)R dağıtımı olan Microsoft R Open, [CRAN R'den iki](https://cran.r-project.org/) önemli şekilde farklıdır:

1. [Intel Matematik Çekirdek Kitaplıkları](https://mran.revolutionanalytics.com/rro/#intelmkl1) ile birlikte [kullanılırken daha iyi hesaplama performansı.](https://software.intel.com/intel-mkl) Kitaplıklar, Microsoft R Open ile kullanım için Microsoft'tan ücretsiz olarak indirilebilir.

1. [Yeniden üretebilir R Araç](https://mran.revolutionanalytics.com/rro/#reproducibility) Seti, R programınızı oluşturmak için kullanılan kitaplıkların çalışmanızı yeniden oluşturmak isteyen diğerlerinde her zaman kullanılabilir hale geldi.

[Microsoft ML Server (MLS),](/machine-learning-server/what-is-machine-learning-server) daha fazla veri işlemenizi ve daha hızlı işlemenizi sağlayan bir R uzantısıdır. R'ye iki güçlü özellik sağlar:

1. RAM sınırlamaları olmayan daha büyük veri kümeleri. ML Server Hadoop kümeleri, veritabanları ve veri ambarları gibi çeşitli kaynaklardan yetersiz bellek verilerini işebilirsiniz.

1. Paralel, çok çekirdekli işleme. MLS, hesaplamayı sahip olduğu tüm hesaplama kaynakları arasında verimli bir şekilde dağıtabilirsiniz. Kişisel iş istasyonunda veya uzak kümede MLS daha hızlı bir yanıt alır.

Aşağıdaki karşılaştırma, MKL ile MLS ve MRO'nun belirli matris hesaplaması ile ilgili olarak MKL olmadan R ve MRO'ya kıyasla önemli ölçüde daha iyi hesaplama performansına sahip olduğunu gösterir. Simülasyon verileri bu hesaplamada kullanılır:

![MLS ile MRO'yu MKL ile R ve MRO ile MKL olmadan karşılaştırma](media/samples-speed-comparison.png)

R ile MRO ve MLS'nin teknik karşılaştırması için [Lixun Zhang'ın konuyla ilgili ayrıntılı tartışmalarını](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) göz atabilirsiniz.

Aşağıdaki şekilde, 15 dakikadan uzun uçuş gecikmelerini tahmin etmek için Lojistik Regresyon modellerini inşa etmek için kullanılan saniyeler içinde geçen süre karşılaştırıldı.  CRAN R'de kullanılan geçen süre, az sayıda satır arttıkça önemli ölçüde artarken MLS yalnızca yaklaşık iki kat artar. Bu karşılaştırmanın ayrıntıları için *Benchmarks/rxGlm_benchmark. R* örneği.

![rxGlm karşılaştırması](media/samples-rxGLM-benchmark.png)
