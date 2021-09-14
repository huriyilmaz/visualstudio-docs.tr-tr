---
title: IPython REPL (etkileşimli pencere)
description: etkileşimli paralel bilgi işlem özellikleriyle kullanıcı dostu etkileşimli bir geliştirme ortamı için ıpython modunda Visual Studio etkileşimli penceresini kullanın.
ms.date: 07/28/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a03216c2fbbc83af1f4a995b43ed4576716e1eb9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726798"
---
# <a name="use-ipython-in-the-interactive-window"></a>Etkileşimli pencerede IPython kullanın

ıpython modunda Visual Studio **etkileşimli** pencere, etkileşimli paralel bilgi işlem özelliklerine sahip, gelişmiş, ancak kullanıcı dostu bir etkileşimli geliştirme ortamıdır. bu makalede, tüm normal [etkileşimli pencere](python-interactive-repl-in-visual-studio.md) özelliklerinin de kullanılabildiği Visual Studio **etkileşimli** penceresinde ıpython kullanımı gösterilmektedir.

Bu kılavuzda, IPython, sayısal tuş a y ve Matplotlib yüklü olmalıdır. Anaconda kullanıyorsanız bu kitaplıklar zaten yüklüdür. İzlenecek yolun geri kalanı, Anaconda kullandığınızı varsayar.

> [!Note]
> IronPython, bunu **Etkileşimli Seçenekler** formunda seçebileceğiniz Için IPython 'u desteklemez. Daha fazla bilgi için bkz. [özellik isteği](https://github.com/Microsoft/PTVS/issues/84).

1. Visual Studio açın, **python ortamları** penceresine geçin (  >  **diğer Windows**  >  **Python ortamlarını** görüntüleyin) ve bir anaconda ortamı seçin.

2. Ve ' nin listelendiğinden emin olmak için, bu ortam için **paketler (Conda)** sekmesini ( **PIP** veya paket olarak görünebilir) inceleyin `ipython` `matplotlib` . Aksi takdirde, bunları buraya yüklersiniz. (Bkz. [Python ortamları Windows-paketler sekmesi](python-environments-window-tab-reference.md).)

3. **Genel bakış** sekmesini seçin ve **IPython etkileşimli modunu kullan**' ı seçin. (Visual Studio 2015 ' de, **seçenekler** iletişim kutusunu açmak için **etkileşimli seçenekleri yapılandır** ' ı seçin, sonra **etkileşimli modu** **ipython** olarak ayarlayın ve **tamam**' ı seçin.

4. **Etkileşimli pencereyi** IPython modunda görüntülemek için **etkileşimli pencereyi aç** ' ı seçin. Etkileşimli modu az önce değiştirdiyseniz pencereyi sıfırlamanız gerekebilir; Ayrıca, **[2] içinde** bir istem almanızı sağlamak üzere yalnızca bir >>> Istemi görünürse **ENTER** tuşuna basmanız gerekebilir.

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

7. REPL ' ı yazmak yerine düzenleyicide kod yazabilir, seçin, sağ tıklayın ve **etkileşimli olarak gönder** komutuna tıklayabilir (veya **CTRL** + **ENTER** tuşuna basın). Aşağıdaki kodu düzenleyicide yeni bir dosyaya yapıştırmayı, **CTRL** + **a** ile seçip **etkileşimli** pencereye göndermeyi deneyin. (Visual Studio, kodu, ara veya kısmi grafikler vermekten kaçınmak için tek bir birim olarak gönderir. farklı bir ortam seçiliyken açık bir python projeniz yoksa Visual Studio, **python ortamları** penceresinde varsayılan olarak hangi ortamın seçildiği için **etkileşimli** bir pencere açar.)

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

8. **Etkileşimli** pencerenin dışındaki grafikleri görmek için, hata ayıklama başlangıcı komutuyla **Hata Ayıkla** komutunu kullanarak kodu çalıştırın  >   .

IPython, sistem kabuğu, değişken değiştirme, çıkış yakalama vb. gibi diğer birçok yararlı özelliğe sahiptir. Daha fazla bilgi için [IPython belgelerine](https://ipython.org/documentation.html) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Azure veri bilimi sanal makinesi](/azure/machine-learning/data-science-virtual-machine/overview) , Jupyıter not defterlerini çok çeşitli veri bilimi araçlarıyla birlikte çalıştırmak için önceden yapılandırılmıştır.
