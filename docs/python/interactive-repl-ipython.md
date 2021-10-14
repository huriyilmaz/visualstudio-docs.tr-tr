---
title: IPython REPL (etkileşimli pencere)
description: Etkileşimli Paralel Visual Studio özelliklerine sahip kullanıcı dostu bir etkileşimli geliştirme ortamı için IPython modundaki yeni etkileşimli pencereyi kullanın.
ms.date: 07/28/2021
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: dd68ee68c17842ee8812a524043251c974a1877f
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968637"
---
# <a name="use-ipython-in-the-interactive-window"></a>IPython'un Etkileşimli penceresi

IPython **modundaki** Visual Studio Etkileşimli penceresi, Etkileşimli Paralel Bilgi İşlem özelliklerine sahip gelişmiş ancak kullanıcı dostu bir etkileşimli geliştirme ortamıdır. Bu makalede, Visual Studio **Interactive** penceresinde IPython'un nasıl Etkileşimli penceresi [açıklanmıştır.](python-interactive-repl-in-visual-studio.md)

Bu kılavuz için IPython, numpy ve matplotlib'i yüklemiş olması gerekir. Anaconda kullanıyorsanız, bu kitaplıklar zaten yüklü. Gözden geçirmenin geri kalanında Anaconda'yı kullanmakta olduğunu varsayabilirsiniz.

> [!Note]
> IronPython, Etkileşimli Seçenekler formunda seçmenize rağmen IPython'ı **desteklemez.** Daha fazla bilgi için özellik [isteğine bakın.](https://github.com/Microsoft/PTVS/issues/84)

1. Yeni Visual Studio açın, Python Ortamları penceresine **(** **Python** Ortamlarını  >  **Windows)** ve bir  >  Anaconda ortamı seçin.

2. ve'nin listelendiğinden emin olmak için bu ortam için Paketler **(Conda)** sekmesini **(pip** veya Paketler olarak **görünebilir)** `ipython` `matplotlib` inceleyebilirsiniz. Yüklü değilse, bunları buraya yükleyin. [(Bkz. Python Ortamları pencereleri - Paketler sekmesi](python-environments-window-tab-reference.md).)

3. Genel Bakış **sekmesini seçin** ve **IPython etkileşimli modunu kullan'ı seçin.** (2015 Visual Studio de, Seçenekler iletişim kutusunu açmak  için Etkileşimli  seçenekleri yapılandır'ı seçin, ardından Etkileşimli Mod'ı **IPython** olarak ayarlayın ve Tamam'ı **seçin).** 

4. Etkileşimli **pencereyi** IPython modunda **açmak** için Etkileşimli pencereyi aç'ı seçin. Etkileşimli modu yeni değiştirdiyebilirsiniz; Yalnızca bir komut istemi görüntülenirse **Enter** tuşuna >>> , böylece [2] içinde gibi bir istem **alasanız da gerekir.**

    ![IPython modunda etkileşimli pencere](media/ipython-repl-03.png)

5. Aşağıdaki kodu girin:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Son satırı girdikten sonra bir satır içi graf (istenirse sağ alt köşede sürükleyerek yeniden boyutlandırabilirsiniz) görüyorsanız.

    ![Etkileşimli pencerede satır içi grafik](media/ipython-repl-04.png)

7. REPL'ye yazmak yerine düzenleyicide kod yazabilir, bunu seçin, sağ tıklayın  ve Etkileşimli Gönder komutunu seçin (veya Ctrl Enter **tuşlarına** + **basın).** Aşağıdaki kodu düzenleyicide yeni bir dosyaya yapıştırmayı, **Ctrl** A ile seçmeyi ve etkileşimli + pencereye **göndermeyi** deneyin. (Visual Studio veya kısmi graflar vermemek için kodu tek bir birim olarak gönderir. Farklı bir ortam seçiliyken açık bir Python projeniz yoksa Visual Studio Python  Ortamları penceresinde varsayılan olarak seçtiğiniz ortamlar için etkileşimli bir **pencere** açar.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Düzenleyiciden etkileşimli pencereye kod gönderme](media/ipython-repl-05.png)

8. Grafikleri Etkileşimli pencerenin dışında  görmek için Hata Ayıklama Olmadan Başlat komutunu kullanarak  >  **kodu** çalıştırın.

IPython'un sistem kabuğuna kaçış, değişken değiştirme, çıkışı yakalama gibi birçok yararlı özelliği vardır. Daha fazla bilgi [için IPython belgelerine](https://ipython.org/documentation.html) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Veri Bilimi Sanal Makinesi,](/azure/machine-learning/data-science-virtual-machine/overview) birçok farklı veri bilimi aracıyla birlikte Jupyter not defterlerini çalıştırmak için önceden yapılandırılmıştır.
