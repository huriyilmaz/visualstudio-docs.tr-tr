---
title: Örnek R projeleri
description: R ve Visual Studio ile çalışmaya başlamak için bir örnek koleksiyonunun dizini.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 3686a472c6a3d83158b42b253944fbdec87e22a4f4ba8771947da45d78572b44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229240"
---
# <a name="r-tools-for-visual-studio-sample-projects"></a>Visual Studio için R Araçları örnek projeleri

bu örnek koleksiyonu, R, Visual Studio için R Araçları (rtvs) ve Microsoft Machine Learning Server ile çalışmaya başlamanızı ister:

1. [Örnek ZIP dosyasını](https://github.com/Microsoft/RTVS-docs/archive/master.zip) indirin ve seçtiğiniz bir klasöre ayıklayın.
1. `examples/Examples.sln`Projedeki iki klasörü görmek için açın:

    - *R 'ye Ilk bakış* , Newcomers için r 'ye bir Gentle giriş sağlar.
    - *MRS ve Machine Learning* , Machine Learning için R ve Microsoft Machine Learning Server 'in nasıl kullanılacağına ilişkin örnekler sağlar.

## <a name="a-first-look-at-r"></a>R 'ye Ilk bakış

Bu örnek, iki kaynak dosyada kapsamlı açıklamalarla R 'ye ayrıntılı bir giriş sağlar. En iyi deneyim için imleci dosyanın en üstüne yerleştirin ve kod satırını **R etkileşim** penceresine göndermek için CTRL + ENTER tuşlarına basın. (Paketlerin yüklenmesi için bir dakika veya iki işlem gerekebilir.)

- `1-Getting Started with R.R` , paketleri kullanma, verileri yükleme ve çözümleme ve çizme gibi birçok R temelini içerir.

    ![1-R.R örneği ile çalışmaya başlama örnek çıkışı](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` görsel açıdan çekici çizimler ve basit sözdizimi için bilinen ggplot2 grafik paketini tanıtır. Bu örnek, deprem verilerini Fiji 'dan görselleştirir.

    ![2-ggplot2 'e giriş çıkışı örneği. R örneği](media/samples-ggplot-output.png)

## <a name="microsoft-machine-learning-server-and-machine-learning"></a>Microsoft Machine Learning Server ve Machine Learning

bu örnek koleksiyonu, machine learning modelleri oluşturmak ve [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)avantajlarından yararlanmak için R 'yi nasıl kullanacağınızı gösterir.

Tüm örneklerde olduğu gibi, dosyasını açın, imleci üst kısımdaki yere yerleştirin ve ardından **CTRL** ENTER ile kod satırı satırına ilerleyin + . Her klasördeki markaşağı dosyaları da ek ayrıntılar içerir.

- `Benchmarks` , Microsoft R Open ve Intel Math çekirdek kitaplığı (MKL) kullanımı aracılığıyla olası performans kazançlarını göstermek için çok sayıda yoğun, paralel doğrusal algedeniz hesaplamaları çalıştırır. Benzetimli verilerle, kıyaslamalar, bir iş parçacığında matris hesaplamalarını özellikle karşılaştırın.

    ![Örnek kıyaslama çizimi](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS`Microsoft ML Server kullanarak bir geçmiş veri kümesine göre bisiklet için bir talep tahmini modeli oluşturur.

- `Data_Exploration` Üç komut dosyası içerir:

  - `Import Data from URL.R` URL tarafından tanımlanan bir veri dosyasının R 'ye nasıl yükleneceğini gösterir.
  - `Import Data from URL to xdf.R`URL tanımlı bir veri dosyasının bir xdf olarak Microsoft ML Server 'a nasıl yükleneceğini gösterir.
  - `Using ggplot2.R` , `A First Look at R/2-Introduction to ggplot2.R` Örneğin Etkileşimli 3B çizim dahil olmak üzere ggplot2's işlevselliğinin daha kapsamlı bir turuna sahip bir örnek uzantısıdır.

      ![Ggplot2 kullanarak çıkış. R örneği](media/samples-3d-interactive.png)

- `Datasets` Diğer örnekler tarafından kullanılan üç *.csv* dosyası içerir
- `Flight_Delays_Prediction_with_R``Flight_Delays_Prediction_with_MRS`R, Machine Learning ve geçmiş performans ve hava durumu verilerini kullanarak uçuş gecikmelerinin nasıl tahmin edilmesi gerektiğini gösterir.
- `Machine learning` , uçuş gecikmelerini tahmin etmek, fiyatları dengelemek ve bisiklet süreleri için öğrenerek üç örnek içerir. bu örnekler birlikte, gerçek dünyada sorunlara R ve Microsoft ML Server uygulamasını gösterir. ayrıca, çeşitli popüler makine öğrenimi modellerini nasıl kullanacağınızı ve bir [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/) çalışma alanı kullanarak bunları bir Azure Web hizmeti olarak dağıtmayı da gösterir.

- `R_MRO_MRS_Comparison`, komut, sözdizimi, yapılar ve performans ile R, microsoft r Open ve microsoft ML Server benzerlerini ve farklarını gösteren altı bölümden oluşan bir karşılaştırdır.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-ml-server"></a>Microsoft R Open ve Microsoft ML Server hakkında ne özeldir?

Microsoft r [Open](https://mran.revolutionanalytics.com/download/), Microsoft 'un r 'nin dağıtımı, [Cran R](https://cran.r-project.org/) 'den iki önemli şekilde farklıdır:

1. [Intel Math çekirdek kitaplıklarıyla](https://software.intel.com/intel-mkl)kullanıldığında [daha iyi hesaplama performansı](https://mran.revolutionanalytics.com/rro/#intelmkl1) . Kitaplıklar Microsoft R Open ile kullanılmak üzere Microsoft 'tan ücretsiz bir indirme olarak kullanılabilir.

1. [Tekrarlanabilir r Toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility) , r programınızı oluşturmak için kullandığınız kitaplıkların, işinizi yeniden oluşturmak isteyen diğerleri tarafından her zaman kullanılabilir olmasını sağlar.

[Microsoft ML Server (mls)](/machine-learning-server/what-is-machine-learning-server) , daha fazla veri idare etmenize ve daha hızlı işleyebilmeniz için bir R uzantısıdır. R iki güçlü özellik sunar:

1. RAM sınırlamaları olmayan daha büyük veri kümeleri. ML Server, Hadoop kümeleri, veritabanları ve veri ambarları gibi çeşitli kaynaklardan bellek dışı verileri işleyebilir.

1. Paralel, çok çekirdekli işleme. MLS, kullanılabilir olan tüm hesaplama kaynaklarında hesaplamayı verimli bir şekilde dağıtabilir. Kişisel iş istasyonunuzda veya uzak kümenizde, MLS yanıtı daha hızlı bir şekilde alır.

Aşağıdaki karşılaştırma, MKL ile birlikte MLS ve MRO 'ın, MKL olmadan R ve MRO 'dan belirli matris hesaplamasıyla ilgili önemli ölçüde daha iyi hesaplama performansına sahip olduğunu gösterir. Bu hesaplamada sanal veriler kullanılır:

![MLS ve MRO ile mkl ile R ve MRO karşılaştırması, MKL olmadan karşılaştırılıyor](media/samples-speed-comparison.png)

MRO ve MLS ile R 'nin teknik karşılaştırması için, konusunda [ayrıntılı tartışmayı](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) inceleyin.

Aşağıdaki şekil, 15 dakikadan daha büyük uçuş gecikmelerini tahmin etmek üzere lojistik regresyon modellerini oluştururken kullanılan geçen süreyi saniye cinsinden karşılaştırır.  CRAN R 'de kullanılan geçen süre çok az sayıda satırı artırırken önemli ölçüde artar, ancak MLS yalnızca yaklaşık iki kez artar. Bu kıyaslama hakkında ayrıntılı bilgi edinmek için *kıyaslamalar/rxGlm_benchmark inceleyin. R* örneği.

![rxGlm kıyaslaması](media/samples-rxGLM-benchmark.png)
