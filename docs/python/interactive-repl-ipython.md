---
title: IPython REPL (etkileşimli pencere)
description: Interactive Parallel Computing özelliklerine sahip kullanıcı dostu etkileşimli geliştirme ortamı için IPython modunda Visual Studio etkileşimli penceresini kullanın.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b4510ed738fdd2b33389ab4242dbde86cffff8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957762"
---
# <a name="use-ipython-in-the-interactive-window"></a>Etkileşimli pencerede IPython'u kullanma

IPython modundaki Visual Studio **Interactive** penceresi, İnteraktif Paralel Bilgi İşlem özelliklerine sahip gelişmiş ama kullanıcı dostu bir etkileşimli geliştirme ortamıdır. Bu makale, tüm normal [Etkileşimli pencere](python-interactive-repl-in-visual-studio.md) özelliklerinin de bulunduğu Visual Studio **Interactive** penceresinde IPython'u kullanarak geçer.

Bu geçiş için, IPython ve gerekli kitaplıkları içeren [Anaconda](https://www.continuum.io) ortamıyüklü olmalıdır.

> [!Note]
> IronPython, **Etkileşimli Seçenekler** formunda seçebildiğiniz halde IPython'u desteklemez. Daha fazla bilgi için [özellik isteğine](https://github.com/Microsoft/PTVS/issues/84)bakın.

1. Visual Studio'yu açın, **Python Ortamları** penceresine geçin **(Diğer Windows** > **Python Ortamlarını****Görüntüle** > ) ve bir Anaconda ortamı seçin.

2. Bu ortam için **paketler (Conda)** sekmesini **(pip** veya **Packages**olarak `ipython` `matplotlib` görünebilir) inceleyin ve bu sekmeler listelenmiştir. Değilse, buraya yükleyin. [(Bkz. Python Ortamları pencereleri - Paketler sekmesi](python-environments-window-tab-reference.md).)

3. Genel **Bakış** sekmesini seçin ve **IPython etkileşimli modunu kullan'ı**seçin. (Visual Studio 2015'te, **Seçenekler** iletişim kutusunu açmak için **etkileşimli seçenekleri yapıya** dizme'yi seçin, ardından **Etkileşimli Modu** **IPython**olarak ayarlayın ve **Tamam'ı**seçin).

4. IPython modunda **Etkileşimli** pencereyi açmak için **etkileşimli pencereyi aç'ı** seçin. Etkileşimli modu yeni değiştirdiyseniz pencereyi sıfırlamanız gerekebilir; yalnızca bir >>> istemi görünürse **Enter** tuşuna basmanız da gerekebilir, böylece **Giriş [2]** gibi bir istemi elde elabilirsiniz.

    ![IPython modunda etkileşimli pencere](media/ipython-repl-03.png)

5. Aşağıdaki kodu girin:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Son satırı girdikten sonra, bir satır içi grafik görmeniz gerekir (istenirse sağ alt köşede sürükleyerek yeniden boyutlandırabilirsiniz).

    ![Etkileşimli pencerede satır çizgisi grafiği](media/ipython-repl-04.png)

7. REPL'de yazmak yerine, düzenleyiciye kod yazabilir, seçebilir, sağ tıklatabilir ve **Etkileşimli Gönder** komutunu (veya **Ctrl**+**Enter**tuşuna basın) seçebilirsiniz. Aşağıdaki kodu düzenleyicideki yeni bir dosyaya yapıştırmayı deneyin, **Ctrl**+**A**ile seçin ve **etkileşimli** pencereye göndermeyi deneyin. (Visual Studio size ara veya kısmi grafikler vermekten kaçınmak için kodu tek bir birim olarak gönderir. Ve farklı bir ortam seçili bir Python projeniz yoksa, Visual Studio **Python Ortamları** penceresinde varsayılan olarak seçilen ortam için **etkileşimli** bir pencere açar.)

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

8. **Etkileşimli** pencerenin dışındaki grafikleri görmek için, hata ayıklama komutu olmadan **Hata Ayıklama** > Başlat'ı kullanarak kodu**çalıştırın.**

IPython, sistem kabuğuna kaçmak, değişken ikame, çıktı yakalama, vb. gibi birçok yararlı özelliğe sahiptir. Daha fazla bilgi için [IPython belgelerine](https://ipython.org/documentation.html) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- Jupyter'ı kolayca ve kurulum olmadan kullanmak için, dizüstü bilgisayarlarınızı saklamanızı ve başkalarıyla paylaşmanızı sağlayan ücretsiz [Azure Notebook barındırılan hizmeti](https://notebooks.azure.com/) deneyin.

- [Azure Veri Bilimi Sanal Makinesi,](/azure/machine-learning/data-science-virtual-machine/overview) jupyter dizüstü bilgisayarları diğer veri bilimi araçlarıyla birlikte çalıştırmak için önceden yapılandırılmıştır.
