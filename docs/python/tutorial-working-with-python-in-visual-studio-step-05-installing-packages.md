---
title: Python Visual Studio öğretici adım 5, paketleri yüklemek
titleSuffix: ''
description: Visual Studio'daki Python yeteneklerinin temel bir walkthrough'unun 5 adımını, Visual Studio'nun Python ortamında paketleri yönetmeye yönelik özelliklerini gösteren.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372951"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Adım 5: Python ortamınıza paketleri yükleyin

**Önceki adım: [Hata ayıklayıcıda kodu çalıştır](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python geliştirici topluluğu, kendi projelerinize dahil edebilirsiniz yararlı paketler binlerce üretti. Visual Studio, Python ortamlarınızdaki paketleri yönetmek için bir kullanıcı altı bir kullanıcı yontması sağlar.

## <a name="view-environments"></a>Ortamları görüntüleme

1. **Diğer Windows** > **Python Ortamlarını** **Görüntüle** > menüsü komutunu seçin. **Python Ortamları** penceresi Çözüm **Gezgini'ne** eş olarak açılır ve kullanabileceğiniz farklı ortamları gösterir. Liste, Visual Studio yükleyicisini kullanarak yüklediğiniz ortamları ve ayrı olarak yüklediğiniz ortamları gösterir. Bu, küresel, sanal ve conda ortamlarını içerir. Kalın ortam, yeni projeler için kullanılan varsayılan ortamdır. Ortamlarla çalışma hakkında daha fazla bilgi için [Visual Studio ortamlarında Python ortamlarını nasıl oluşturup yönetebilirsiniz'e](managing-python-environments-in-visual-studio.md)bakın.

   ![Python Ortamları penceresi](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Ayrıca Çözüm Gezgini penceresine tıklayarak ve Ctrl+K, Ctrl+' klavye kısayolu kullanarak Python Ortamları penceresini açabilirsiniz. Kısayol çalışmıyorsa ve menüde Python Ortamları penceresini bulamıyorsanız, Python iş yükünü yüklememiş olabilirsiniz. Python'un nasıl yüklenirhakkında rehberlik etmek için [Visual Studio'da Python desteğini nasıl yükleyebilirsiniz'](installing-python-support-in-visual-studio.md) e bakın.

2. Çevrenin **Genel Bakış** sekmesi, ortamın yükleme klasörü ve yorumlayıcılarıyla birlikte o ortam için **Etkileşimli** pencereye hızlı erişim sağlar. Örneğin, **Etkileşimli Aç pencereyi** seçin ve visual studio'da belirli bir ortam için **Etkileşimli** pencere görünür.

3. Şimdi, **Python Uygulama** şablonunu seçerek **Dosya** > **Yeni** > **Projesi**ile yeni bir proje oluşturun. Görünen kod dosyasında, önceki öğretici adımlar gibi bir kosinüs dalgası oluşturan aşağıdaki kodu yapıştırın, yalnızca bu kez grafik olarak çizilmiştir. Alternatif olarak, daha önce oluşturduğunuz projeyi kullanabilir ve kodu değiştirebilirsiniz. 

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

4. Python projesi açıkken, Python Ortamları'na sağ tıklayarak ve **Tüm Python Ortamlarını Görüntüle'yi** seçerek Solution Explorer'dan Python Ortamları penceresini de açabilirsiniz

   ![Ortam](media/environments/environments-view-all-2019.png)

5. Düzenleyici penceresine baktığınızda, ifadelerin üzerinde `numpy` gezinirseniz ve `matplotlib` bunların çözülmediğini fark edeyim. Bunun nedeni, paketlerin varsayılan genel ortama yüklenmemiş olmasıdır.

   ![Çözülmemiş paket alma](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Python Ortamları penceresini kullanarak paketleri yükleme

1. Python Ortamları penceresinden, yeni Python projeleri için varsayılan ortamı tıklatın ve **Paketler** sekmesini seçin. Daha sonra, şu anda ortamda yüklü olan paketlerin bir listesini görürsünüz.

   ![Bir ortama yüklenen paketler](media/environments/environments-installed-packages-2019.png)

2. Adını `matplotlib` arama alanına girerek ve sonra Çalıştır komutunu seçerek yükleyin: **pip install matplotlib** seçeneği. Bu, `matplotlib`(bu durumda içerir) `numpy`bağlı olduğu herhangi bir paket yanı sıra, yüklenir.

   ![Çevreye matplotlib kurulumu](media/environments/environments-add-matplotlib-2019.png)

5. İstenirse yükselmeyi onaylar.

6. Paket yüklendikten sonra **Python Ortamları** penceresinde görünür. Paketin sağındaki **X** onu yükler.

   ![Çevreye matplotlib kurulumunun tamamlanması](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Visual Studio'nun yeni yüklenen paket için IntelliSense veritabanını oluşturmakta olduğunu belirtmek için ortamın altında küçük bir ilerleme çubuğu görünebilir. **IntelliSense** sekmesi de daha ayrıntılı bilgi gösterir. Bu veritabanı tamamlanana kadar, intelliSense özelliklerinin otomatik tamamlama ve sözdizimi denetimi gibi özelliklerin bu paketin düzenleyicisinde etkin olmayacağını unutmayın.
   > 
   > Visual Studio 2017 sürüm 15.6 ve daha sonra IntelliSense ile çalışmak için farklı ve daha hızlı bir yöntem kullanır ve **IntelliSense** sekmesinde bu etkiye yönelik bir ileti görüntüler.

## <a name="run-the-program"></a>Programı çalıştırma

1. Şimdi [matplotlib](https://matplotlib.org/) yüklü,**(F5**) veya hata ayıklayıcı olmadan programı çalıştırın (**Ctrl**+**F5**) çıkışı görmek için:

   ![Matplotlib örneğinin çıktısı](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Daha derine inin

- [Python ortamları](managing-python-environments-in-visual-studio.md)
- [Visual Studio’da Django Öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Visual Studio’da Flask Öğrenme](learn-flask-visual-studio-step-01-project-solution.md)
