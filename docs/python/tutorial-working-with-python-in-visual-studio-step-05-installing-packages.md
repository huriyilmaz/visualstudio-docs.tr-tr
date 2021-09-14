---
title: Python Visual Studio öğretici adım 5, paket yüklemesi
titleSuffix: ''
description: bir python ortamında paketlerin yönetilmesi için Visual Studio özelliklerini gösteren, Visual Studio python özelliklerine yönelik temel bir izlenecek yolun 5. adımı.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: be201d5d9897dd803f9eac3c012d3124c141c26e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726776"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5. Adım: Python ortamınıza paket yüklemeyi

**Önceki adım: [hata ayıklayıcıda kodu çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python geliştirici topluluğu, kendi projeleriniz ile birleştirebilmeniz için binlerce yararlı paket üretti. Visual Studio, Python ortamlarınızdaki paketleri yönetmek için bir kullanıcı arabirimi sağlar.

## <a name="view-environments"></a>Ortamları görüntüleme

1.   >  **diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin. **Python ortamları** penceresi **Çözüm Gezgini** için bir eş olarak açılır ve size sunulan farklı ortamları gösterir. liste, Visual Studio yükleyicisini ve ayrı olarak yüklediğiniz ortamları gösterir. Bu, genel, sanal ve Conda ortamlarını içerir. Kalın olan ortam, yeni projeler için kullanılan varsayılan ortamdır. ortamlarla çalışma hakkında daha fazla bilgi için bkz. [Visual Studio ortamlarında Python ortamları oluşturma ve yönetme](managing-python-environments-in-visual-studio.md).

   ![Python ortamları penceresi](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Ayrıca, Çözüm Gezgini penceresini seçerek ve **CTRL + K, CTRL + '** klavye kısayolunu kullanarak Python ortamları penceresini açabilirsiniz. Kısayol işe yaramazsa ve menüde Python ortamları penceresini bulamıyorsanız, Python iş yükünü yüklemiş olmanız mümkün değildir. python 'un nasıl yükleneceğine ilişkin yönergeler için bkz. [Visual Studio python desteğini yüklemeyi](installing-python-support-in-visual-studio.md) öğrenin.

2. Ortamın **genel bakış** sekmesi, ortamın yükleme klasörü ve yorumlayıcıları ile birlikte bu ortam için **etkileşimli** bir pencereye hızlı erişim sağlar. Örneğin **etkileşimli pencere aç** ' ı seçin ve bu ortam için **etkileşimli** bir pencere Visual Studio görüntülenir.

3. şimdi, yeni Project **dosya** içeren yeni bir proje oluşturun  >    >  , **Python uygulama** şablonu ' nu seçin. Görüntülenen kod dosyasında, önceki öğretici adımları gibi bir kosinüs dalgası oluşturan aşağıdaki kodu yapıştırın, yalnızca bu kez grafik çizilir. Alternatif olarak, önceden oluşturduğunuz projeyi kullanabilir ve kodu değiştirebilirsiniz.

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Bir Python projesi açıkken, **Python** ortamları penceresini sağ tıklayıp Çözüm Gezgini **Tüm Python ortamlarını görüntüle** ' yi seçerek de açabilirsiniz.

   ![Ortam](media/environments/environments-view-all-2019.png)

5. Düzenleyici penceresine baktığınızda, `numpy` ve `matplotlib` Not alma deyimlerinin üzerine geldiğinizde çözümlenmediğini fark edersiniz. Bunun nedeni, paketlerin varsayılan genel ortama yüklenmediği bir ortamdır.

   ![Çözümlenmemiş paket içeri aktarma](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Python ortamları penceresini kullanarak paket yükler

1. Python ortamları penceresinde, yeni Python projeleri için varsayılan ortamı seçin ve **paketler** sekmesini seçin. Ardından, ortamda yüklü olan paketlerin bir listesini görürsünüz.

   ![Bir ortama yüklenen paketler](media/environments/environments-installed-packages-2019.png)

2. `matplotlib`Öğesini arama alanına girerek ve sonra **komutu Çalıştır: PIP install Matplotlib** seçeneğini belirleyerek yüklemeyi seçin. Bunun `matplotlib` yanı sıra bağımlı olduğu paketleri (Bu durumda `numpy` ) yükler.

   ![Ortama Matplotlib yükleme](media/environments/environments-add-matplotlib-2019.png)

5. İstenirse yükseltme onayı.

6. Paket yüklendikten sonra, **Python ortamları** penceresinde görünür. Paketin sağ tarafındaki **X** onu kaldırır.

   ![Ortamda Matplotlib yükleme işleminin tamamlanması](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Visual Studio, yeni yüklenen paket için ıntellisense veritabanını oluşturmakta olduğunu göstermek için ortamın altında küçük bir ilerleme çubuğu görünür. **IntelliSense** sekmesinde daha ayrıntılı bilgiler de gösterilmektedir. Bu veritabanı tamamlanana kadar, otomatik tamamlama ve söz dizimi denetimi gibi IntelliSense özelliklerinin bu pakete yönelik düzenleyicide etkin olmayacak olduğunu unutmayın.
   >
   > Visual Studio 2017 sürüm 15,6 ve üzeri, ıntellisense ile çalışmaya yönelik farklı ve daha hızlı bir yöntem kullanır ve **ıntellisense** sekmesinden bu etkiye bir ileti görüntüler.

## <a name="run-the-program"></a>Programı çalıştırma

1. Artık [Matplotlib](https://matplotlib.org/) yüklendiğinden, çıktıyı görmek için programı (**F5**) veya hata ayıklayıcı olmadan (**CTRL** + **F5**) çalıştırın:

   ![Matplotlib örneği çıkışı](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Daha derin git

- [Python ortamları](managing-python-environments-in-visual-studio.md)
- [Visual Studio’da Django Öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Visual Studio’da Flask Öğrenme](learn-flask-visual-studio-step-01-project-solution.md)
