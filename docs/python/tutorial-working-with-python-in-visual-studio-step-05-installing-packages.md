---
title: Python in Visual Studio öğreticisi 5. adım, paketleri yükleme
titleSuffix: ''
description: 5. Adım, Python ortamındaki paketleri yönetmeye Visual Studio ve Visual Studio Python özelliklerini göstermeyi gösteren temel bir adım adım adım adımdır.
ms.date: 12/11/2021
ms.custom: devdivchpfy22
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: e858edba137685522ba91149f34f9cc6e46774fd
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121368"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5. Adım: Python ortamınıza paket yükleme

**Önceki adım: [Hata ayıklayıcıda kod çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python geliştirici topluluğu, kendi projelerinize dahil etmek için binlerce yararlı paket üretti. Visual Studio Python ortamlarınızı yönetmek için bir kullanıcı arabirimi sağlar.

## <a name="view-environments"></a>Ortamları görüntüleme

1. Diğer Öğeleri  >  **Görüntüle'Windows**  >  **Python Ortamları menü** komutunu seçin. Python **Ortamları penceresi,** ile eş olarak **Çözüm Gezgini.**

   Python ortamları penceresi, size uygun olan farklı ortamları gösterir. Listede, hem Visual Studio yükleyicisini kullanarak Visual Studio ortamları hem de ayrı olarak yüklemiş olduğunuz ortamlar görüntülenir. Bu ortamlar genel, sanal ve conda ortamlarını içerir. Kalın yazı tipinde ortam, yeni projeler için kullanılan varsayılan ortamdır. Ortamlarla çalışma hakkında daha fazla bilgi için bkz. Python ortamlarını oluşturma [ve yönetme Visual Studio.](managing-python-environments-in-visual-studio.md)

   :::moniker range=">=vs-2022"
   ![Python Ortamları penceresi-2022](media/environments/environments-default-view-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Python Ortamları penceresi-2019](media/environments/environments-default-view-2019.png)
   :::moniker-end

   > [!NOTE]
   > **Ctrl+K, Ctrl+'** klavye kısayolunu kullanarak da Python **Ortamları** penceresini Çözüm Gezgini açabilirsiniz. Kısayol çalışmıyorsa ve menüde Python Ortamları penceresini bulamıyorsanız Python iş yükünü yüklememişsinizdir. [Python'ı yükleme hakkında rehberlik için Visual Studio Windows'da Python](installing-python-support-in-visual-studio.md#how-to-install-python-support-in-visual-studio-on-windows) desteğini yükleme.

   Python projesi açıkken Python Ortamları penceresini **Çözüm Gezgini.**  **Python Ortamları'ne sağ tıklayın ve** Tüm Python **Ortamlarını Görüntüle'yi seçin.**

   :::moniker range="vs-2022"
   ![Python Ortamları-2022](media/environments/environments-view-all-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Python Ortamları-2019](media/environments/environments-view-all-2019.png)
   :::moniker-end

1. Şimdi Python Uygulaması şablonunu seçerek **Dosya**  >    >  **Yeni Project** ile yeni bir **proje** oluşturun.

1. Görüntülenen kod dosyasında, önceki öğretici adımları gibi bir kosinüs dalgası oluşturan, yalnızca bu kez grafiksel olarak çizilen aşağıdaki kodu yapıştırın. Daha önce oluşturduğunuz projeyi de kullanabilir ve kodu değiştirebilirsiniz.

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

1. Düzenleyici penceresinde ve içeri aktarma deyimleri `numpy` `matplotlib` üzerine gelin. Çözümlenemediklerini fark edin. İçeri aktarma deyimlerini çözümlemek için paketleri varsayılan genel ortama yükleyin.
   :::moniker range=">=vs-2022"
   ![Çözümlenmemiş paket içeri aktarma-2022](media/packages-unresolved-import-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
    ![Çözümlenmemiş paket içeri aktarma](media/packages-unresolved-import.png)
   :::moniker-end

1. Python **Ortamları** penceresindeki Genel Bakış sekmesi,  bu ortam için etkileşimli bir pencereye ve ortamın ve yorumlayıcıların yükleme klasörüne hızlı erişim sağlar. Paketler **sekmesine** Genel Bakış sekmesinin altından bakabilirsiniz.

    Örneğin, Etkileşimli **pencereyi aç'ı** **seçin Etkileşimli penceresi** ilgili ortam için bir Visual Studio.

1. Python **Ortamları** penceresindeki Paketler sekmesi, ortamda yüklü olan tüm paketleri listeler.

## <a name="install-packages-using-the-python-environments-window"></a>Python Ortamları penceresini kullanarak paketleri yükleme

Python Ortamı penceresinde Python paketlerini yüklemek için aşağıdaki **adımlara** bakın.

   :::moniker range=">=vs-2022"
   [Paketleri bir ortama yükleme](media/environments/install-python-packages-2022.gif)
   :::moniker-end

1. Python Ortamları **penceresinden** yeni Python projeleri için varsayılan ortamı seçin.

1. Paketler **sekmesini** seçin.

   :::moniker range="vs-2022"
   ![Bir ortamda yüklü paketler-2022](media/environments/environments-installed-packages-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![Bir ortamda yüklü paketler-2019](media/environments/environments-installed-packages-2019.png)
   :::moniker-end

1. yüklemek `matplotlib` için arama alanına `matplotlib` girin.

1. Çalıştır **komutu: pip install matplotlib seçeneğini** belirleyin.
      Bu seçenek `matplotlib` , ve bağlı olduğu tüm paketleri (bu durumda , içerir) `numpy` yüklenir.

   :::moniker range="vs-2022"
    ![Paketler sekmesinde environment-2022'de matplotlib yükleme](media/environments/environments-add-matplotlib-2022.png)
   :::moniker-end
   :::moniker range="<=vs-2019"
   ![Paketler sekmesinde environment-2019'da matplotlib yükleme](media/environments/environments-add-matplotlib-2019.png)
   :::moniker-end

1. İstendiğinde yükseltme onayı.

1. Paket yüklendikten sonra Python Ortamları **penceresinde** görünür. **Paketin** sağ tarafından X, paketi kaldırır.

   :::moniker range="vs-2022"
   ![ortamına matplotlib yükleme-2022](media/environments/environments-add-matplotlib2-2022.png)
   :::moniker-end

   :::moniker range="<=vs-2019"
   ![ortamına matplotlib yükleme-2019](media/environments/environments-add-matplotlib2-2019.png)
   :::moniker-end

    > [!NOTE]
   > Ortamın altında, yeni yüklenen paket için IntelliSense veritabanını Visual Studio küçük bir ilerleme çubuğu görünebilir. **IntelliSense sekmesi** daha ayrıntılı bilgiler de gösterir. Veritabanı tamamlanmadan otomatik tamamlama ve söz dizimi denetimi gibi IntelliSense özelliklerinin söz dizimi denetimi için düzenleyicide etkin olmadığını unutmayın.

   > Visual Studio 2017 sürüm 15.6 ve sonrası, IntelliSense ile çalışmak için farklı ve daha hızlı bir yöntem kullanır ve **IntelliSense** sekmesinde bu etkiye bir ileti görüntüler.

## <a name="run-the-program"></a>Programı çalıştırma

`matplotlib` [matplotlib yükledikten](https://matplotlib.org/)sonra, çıktıyı görmek için programı (**F5**) veya hata ayıklayıcı olmadan (**Ctrl** + **F5**) çalıştırın:

   ![matplotlib örneğinin çıktısı](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Python ortamları](managing-python-environments-in-visual-studio.md)
- [Visual Studio’da Django Öğrenme](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Visual Studio’da Flask Öğrenme](learn-flask-visual-studio-step-01-project-solution.md)
