---
title: Python Visual Studio öğretici adım 5, paket yüklemesi
titleSuffix: ''
description: 5. adım, bir python ortamındaki paketleri yönetmek için Visual Studio ve Visual Studio özellikleri içindeki python yeteneklerini göstermek için temel bir adım adım değildir.
ms.date: 03/09/2020
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e651320fe10def51a58a479aec413bca0b37945
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134714348"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5. Adım: Python ortamınıza paket yüklemeyi

**Önceki adım: [hata ayıklayıcıda kodu çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python geliştirici topluluğu, kendi projeleriniz ile birleştirebilmeniz için binlerce yararlı paket üretti. Visual Studio, Python ortamlarınızdaki paketleri yönetmek için bir kullanıcı arabirimi sağlar.

## <a name="view-environments"></a>Ortamları görüntüleme

1.   >  **diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin. **Python ortamları** penceresi **Çözüm Gezgini** için bir eş olarak açılır.

   Python ortamları penceresinde kullanabileceğiniz farklı ortamlar gösterilir. liste, Visual Studio yükleyicisini kullanarak yüklediğiniz ortamları ve ayrı olarak yüklediğiniz ortamları gösterir. Bu ortamlar genel, sanal ve Conda ortamlarını içerir. Kalın olan ortam, yeni projeler için kullanılan varsayılan ortamdır. ortamlarla çalışma hakkında daha fazla bilgi için bkz. [Visual Studio ortamlarında Python ortamları oluşturma ve yönetme](managing-python-environments-in-visual-studio.md).

   :::moniker range=">=vs-2022"
   ![Python ortamları penceresi-2022](media/environments/environments-default-view-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Python ortamları penceresi-2019](media/environments/environments-default-view-2019.png)
   :::moniker-end

   > [!NOTE]
   > Ayrıca, Çözüm Gezgini penceresinden **Python ortamları** penceresini açmak için **CTRL + K, CTRL + '** klavye kısayolunu da kullanabilirsiniz. Kısayol işe yaramazsa ve menüde Python ortamları penceresini bulamıyorsanız, Python iş yükünü yüklememiş olabilirsiniz. python 'un nasıl yükleneceğine ilişkin yönergeler için bkz. [Visual Studio python desteğini nasıl yükleyeceğiniz Windows](installing-python-support-in-visual-studio.md#how-to-install-python-support-in-visual-studio-on-windows) .

   Bir Python projesi açıkken, **Çözüm Gezgini** **Python ortamları** penceresini açabilirsiniz. **Python ortamları** ' na sağ tıklayın ve **Tüm Python ortamlarını görüntüle**' yi seçin.

   :::moniker range="vs-2022"
   ![Python ortamları-2022](media/environments/environments-view-all-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Python ortamları-2019](media/environments/environments-view-all-2019.png)
   :::moniker-end

1. şimdi, yeni Project **dosya** içeren yeni bir proje oluşturun  >    >  , **Python uygulama** şablonu ' nu seçin.

1. Görüntülenen kod dosyasında, önceki öğretici adımları gibi bir kosinüs dalgası oluşturan aşağıdaki kodu yapıştırın, yalnızca bu kez grafik çizilir. Daha önce oluşturduğunuz projeyi de kullanabilir ve kodu değiştirebilirsiniz.

    ```python
    from math import radians
    import numpy as np # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Düzenleyici penceresinde, `numpy` ve `matplotlib` içeri aktarma deyimlerinin üzerine gelin. Çözümlenmediğini fark edeceksiniz. İçeri aktarma deyimlerini çözümlemek için paketleri varsayılan genel ortama yüklersiniz.
   :::moniker range=">=vs-2022"
   ![Çözümlenmemiş paket içeri aktarması-2022](media/packages-unresolved-import-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
    ![Çözümlenmemiş paket içeri aktarma](media/packages-unresolved-import.png)
   :::moniker-end

1. Python ortamları penceresindeki **genel bakış** sekmesi, bu ortam için **etkileşimli** bir pencereye ve ortamın yükleme klasörüne ve yorumlayıcılara hızlı erişim sağlar. **Paketler** sekmesi genel bakış sekmesinin altında bulunabilir.

    Örneğin **etkileşimli pencere aç** ' ı seçin ve bu ortam için **etkileşimli bir pencere** Visual Studio görüntülenir.

1. Python ortamları penceresindeki **paketler** sekmesi, ortamda yüklü olan tüm paketleri listeler.

## <a name="install-packages-using-the-python-environments-window"></a>Python ortamları penceresini kullanarak paket yükler

Python **ortamı** penceresinde Python paketlerini yüklemek için aşağıdaki adımlara bakın.

   :::moniker range=">=vs-2022"
   [Paketleri bir ortama yükler](media/environments/install-python-packages-2022.gif)
   :::moniker-end

1. **Python ortamları** penceresinde, yeni Python projeleri için varsayılan ortamı seçin.

1. **Paketler** sekmesini seçin.

   :::moniker range="vs-2022"
   ![Bir ortama yüklenen paketler-2022](media/environments/environments-installed-packages-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Bir ortama yüklenen paketler-2019](media/environments/environments-installed-packages-2019.png)
   :::moniker-end

1. `matplotlib`Yüklemek için arama alanına girin `matplotlib` .

1. **Çalıştır komutunu seçin: PIP install Matplotlib** seçeneği.
      Bu seçenek `matplotlib` , ve bağımlı olduğu tüm paketleri (Bu durumda, içerir `numpy` ) yüklenir.

   :::moniker range="vs-2022"
    ![Matplotlib 'yi, paketler sekmesinde ortam-2022 yükleme](media/environments/environments-add-matplotlib-2022.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Matplotlib 'yi, paketler sekmesinde ortam-2019 yükleme](media/environments/environments-add-matplotlib-2019.png)
   :::moniker-end

1. İstenirse yükseltme onayı.

1. Paket yüklendikten sonra, **Python ortamları** penceresinde görünür. Paketin sağ tarafındaki **X** onu kaldırır.

   :::moniker range="vs-2022"
   ![Ortama Matplotlib yükleme-2022](media/environments/environments-add-matplotlib2-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Ortama Matplotlib yükleme-2019](media/environments/environments-add-matplotlib2-2019.png)
   :::moniker-end

    > [!NOTE]
   > Visual Studio, yeni yüklenen paket için ıntellisense veritabanını oluşturmakta olduğunu göstermek için ortamın altında küçük bir ilerleme çubuğu görünür. **IntelliSense** sekmesinde daha ayrıntılı bilgiler de gösterilmektedir. Bu veritabanı tamamlanana kadar, otomatik tamamlama ve söz dizimi denetimi gibi IntelliSense özelliklerinin bu pakete yönelik düzenleyicide etkin olmayacak olduğunu unutmayın.

   > Visual Studio 2017 sürüm 15,6 ve üzeri, ıntellisense ile çalışmaya yönelik farklı ve daha hızlı bir yöntem kullanır ve **ıntellisense** sekmesinden bu etkiye bir ileti görüntüler.

## <a name="run-the-program"></a>Programı çalıştırma

`matplotlib` [Matplotlib](https://matplotlib.org/)yükledikten sonra, çıktıyı görmek için programı (**F5**) veya hata ayıklayıcı olmadan çalıştırın (**CTRL** + **F5**):

   ![Matplotlib örneği çıkışı](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Daha derin git

- [Python ortamları](managing-python-environments-in-visual-studio.md)
- [Visual Studio’da Django Öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Visual Studio’da Flask Öğrenme](learn-flask-visual-studio-step-01-project-solution.md)
