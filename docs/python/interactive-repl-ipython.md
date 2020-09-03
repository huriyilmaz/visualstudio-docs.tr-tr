---
title: IPython REPL (etkileşimli pencere)
description: Etkileşimli paralel bilgi Işlem özellikleriyle kullanıcı dostu etkileşimli bir geliştirme ortamı için, IPython modunda Visual Studio etkileşimli penceresini kullanın.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b1fe36a4ee74ca1b41c1db1d79a6e4683c1f2b1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542434"
---
# <a name="use-ipython-in-the-interactive-window"></a>Etkileşimli pencerede IPython kullanın

IPython modundaki Visual Studio **etkileşimli** penceresi, etkileşimli paralel bilgi işlem özelliklerine sahip, gelişmiş, ancak kullanımı kolay bir etkileşimli geliştirme ortamıdır. Bu makalede, tüm normal [etkileşimli pencere](python-interactive-repl-in-visual-studio.md) özelliklerinin de kullanılabildiği Visual Studio **etkileşimli** penceresinde IPython kullanımı anlatılmaktadır.

Bu izlenecek yol için, IPython ve gerekli kitaplıkları içeren [Anaconda](https://www.continuum.io) ortamının yüklü olması gerekir.

> [!Note]
> IronPython, bunu **Etkileşimli Seçenekler** formunda seçebileceğiniz Için IPython 'u desteklemez. Daha fazla bilgi için bkz. [özellik isteği](https://github.com/Microsoft/PTVS/issues/84).

1. Visual Studio 'yu açın, **Python ortamları** penceresine geçin (**View**  >  **diğer Windows**  >  **Python ortamlarını**görüntüleyin) ve bir Anaconda ortamı seçin.

2. **Packages**Ve ' nin listelendiğinden emin olmak için, bu ortam için **paketler (Conda)** sekmesini ( **PIP** veya paket olarak görünebilir) inceleyin `ipython` `matplotlib` . Aksi takdirde, bunları buraya yüklersiniz. (Bkz. [Python ortamları Windows-paketler sekmesi](python-environments-window-tab-reference.md).)

3. **Genel bakış** sekmesini seçin ve **IPython etkileşimli modunu kullan**' ı seçin. (Visual Studio 2015 ' de, **Seçenekler** iletişim kutusunu açmak için **etkileşimli seçenekleri Yapılandır** ' ı seçin, sonra **etkileşimli modu** **IPython**olarak ayarlayın ve **Tamam**' ı seçin.

4. **Etkileşimli pencereyi** IPython modunda görüntülemek için **etkileşimli pencereyi aç** ' ı seçin. Etkileşimli modu az önce değiştirdiyseniz pencereyi sıfırlamanız gerekebilir; Ayrıca, **[2] içinde**bir istem almanızı sağlamak üzere yalnızca bir >>> Istemi görünürse **ENTER** tuşuna basmanız gerekebilir.

    ![IPython modundaki etkileşimli pencere](media/ipython-repl-03.png)

5. Aşağıdaki kodu girin:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np

   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Son satırı girdikten sonra, satır içi bir grafik görmeniz gerekir (isterseniz sağ alt köşeye sürükleyerek yeniden boyutlandırabilirsiniz).

    ![Etkileşimli pencerede satır içi grafik](media/ipython-repl-04.png)

7. REPL ' ı yazmak yerine düzenleyicide kod yazabilir, seçin, sağ tıklayın ve **etkileşimli olarak gönder** komutuna tıklayabilir (veya **CTRL** + **ENTER**tuşuna basın). Aşağıdaki kodu düzenleyicide yeni bir dosyaya yapıştırmayı, **CTRL** + **a**ile seçip **etkileşimli** pencereye göndermeyi deneyin. (Visual Studio, bu kodu, ara veya kısmi grafikler vermekten kaçınmak için tek bir birim olarak gönderir. Farklı bir ortam seçiliyken açık bir Python projeniz yoksa, Visual Studio, **Python ortamları** penceresinde varsayılan olarak her ortam seçildiğinde **etkileşimli** bir pencere açar.)

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

8. **Etkileşimli** pencerenin dışındaki grafikleri görmek için, hata ayıklama başlangıcı komutuyla **Hata Ayıkla**komutunu kullanarak kodu çalıştırın  >  **Start without Debugging** .

IPython, sistem kabuğu, değişken değiştirme, çıkış yakalama vb. gibi diğer birçok yararlı özelliğe sahiptir. Daha fazla bilgi için [IPython belgelerine](https://ipython.org/documentation.html) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- Jupi 'yi kolayca ve yükleme olmadan kullanmak için, not defterlerinizi diğer kişilerle tutmanıza ve paylaşmanıza olanak tanıyan ücretsiz [Azure Notebooks barındırılan hizmeti](https://notebooks.azure.com/) deneyin.

- [Azure veri bilimi sanal makinesi](/azure/machine-learning/data-science-virtual-machine/overview) , JUPITER not defterlerini çok çeşitli veri bilimi araçlarıyla birlikte çalıştırmak için de önceden yapılandırılmıştır.
