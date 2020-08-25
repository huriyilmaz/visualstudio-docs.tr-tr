---
title: Visual Studio 'da Python eğitim 5. adım, paket yüklemesi
titleSuffix: ''
description: Visual Studio 'da, Visual Studio 'nun bir Python ortamında paketleri yönetme özelliklerini gösteren, Python özelliklerine yönelik temel bir izlenecek yol 5. adımı.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 32e85f39c4acf9466def24bcfea59bbfd6807a1b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801665"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5. Adım: Python ortamınıza paket yüklemeyi

**Önceki adım: [hata ayıklayıcıda kodu çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python geliştirici topluluğu, kendi projeleriniz ile birleştirebilmeniz için binlerce yararlı paket üretti. Visual Studio, Python ortamlarınızdaki paketleri yönetmek için bir kullanıcı arabirimi sağlar.

## <a name="view-environments"></a>Ortamları görüntüleme

1. **View**  >  **Diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin. **Python ortamları** penceresi **Çözüm Gezgini** için bir eş olarak açılır ve size sunulan farklı ortamları gösterir. Listede, Visual Studio yükleyicisi kullanılarak yüklediğiniz ortamlar ve ayrı olarak yüklediğiniz ortamlar gösterilmektedir. Bu, genel, sanal ve Conda ortamlarını içerir. Kalın olan ortam, yeni projeler için kullanılan varsayılan ortamdır. Ortamlarla çalışma hakkında daha fazla bilgi için bkz. [Visual Studio ortamlarında Python ortamları oluşturma ve yönetme](managing-python-environments-in-visual-studio.md).

   ![Python ortamları penceresi](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Ayrıca, Çözüm Gezgini penceresini seçerek ve **CTRL + K, CTRL + '** klavye kısayolunu kullanarak Python ortamları penceresini açabilirsiniz. Kısayol işe yaramazsa ve menüde Python ortamları penceresini bulamıyorsanız, Python iş yükünü yüklemiş olmanız mümkün değildir. Python 'un nasıl yükleneceğine ilişkin yönergeler için bkz. [Visual Studio 'Da Python desteği nasıl yüklenir](installing-python-support-in-visual-studio.md) .

2. Ortamın **genel bakış** sekmesi, ortamın yükleme klasörü ve yorumlayıcıları ile birlikte bu ortam için **etkileşimli** bir pencereye hızlı erişim sağlar. Örneğin **etkileşimli pencere aç** ' ı seçin ve Visual Studio 'da belirli bir ortam için **etkileşimli** bir pencere görüntülenir.

3. Şimdi, yeni **Dosya**projesi olan yeni bir proje oluşturun  >  **New**  >  **Project**, **Python uygulama** şablonunu seçin. Görüntülenen kod dosyasında, önceki öğretici adımları gibi bir kosinüs dalgası oluşturan aşağıdaki kodu yapıştırın, yalnızca bu kez grafik çizilir. Alternatif olarak, önceden oluşturduğunuz projeyi kullanabilir ve kodu değiştirebilirsiniz.

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
   > Visual Studio 'nun yeni yüklenmiş paket için IntelliSense veritabanını oluşturmakta olduğunu göstermek için, ortamın altında küçük bir ilerleme çubuğu görünür. **IntelliSense** sekmesinde daha ayrıntılı bilgiler de gösterilmektedir. Bu veritabanı tamamlanana kadar, otomatik tamamlama ve söz dizimi denetimi gibi IntelliSense özelliklerinin bu pakete yönelik düzenleyicide etkin olmayacak olduğunu unutmayın.
   >
   > Visual Studio 2017 sürüm 15,6 ve üzeri, IntelliSense ile çalışmaya yönelik farklı ve daha hızlı bir yöntem kullanır ve **IntelliSense** sekmesinden bu etkiye bir ileti görüntüler.

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
