---
title: Python Visual Studio öğretici 1. adım, proje oluşturma
titleSuffix: ''
description: önkoşullar ve yeni bir python projesi oluşturma gibi Visual Studio Python özelliklerine ilişkin temel bir anlatımın genel bakış ve 1. adımı.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: ec5fd5494b7b4f5878947f70aaa1675462e0b7ab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628280"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Visual Studio 'de Python ile çalışma

Python, güvenilir, esnek, öğrenilmesi kolay, tüm işletim sistemlerinde kullanılmak üzere ücretsiz olan ve güçlü bir geliştirici topluluğu ve çok sayıda ücretsiz kitaplık tarafından desteklenen popüler bir programlama dilidir. Dil, Web uygulamaları, Web Hizmetleri, masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işlem gibi tüm geliştiriciler destekler ve birçok üniversiteler, bilimçiler, rastgele geliştiriciler ve profesyonel geliştiriciler tarafından kullanılır.

Visual Studio Python için birinci sınıf dil desteği sağlar. Bu öğretici aşağıdaki adımlarda size rehberlik eder:

- [Adım 0: yükleme](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1. Adım: Python projesi oluşturma (Bu makale)](#step-1-create-a-new-python-project)
- [2. adım: Visual Studio ıntellisense 'i iş başında görmek için kodu yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3. Adım: etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4. adım: tamamlanmış programı Visual Studio hata ayıklayıcısında çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5. Adım: paketleri yükleyip Python ortamlarını yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6. Adım: git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1. Adım: yeni bir Python projesi oluşturma

bir *proje* , kaynak kodu, kaynaklar, konfigürasyonlar vb. dahil olmak üzere tek bir uygulama oluşturmak için birlikte gelen tüm dosyaları Visual Studio yönetir. Proje formları, projenin tüm dosyaları ve birden çok proje arasında paylaşılan dış kaynaklar arasındaki ilişkiyi korur. Bu nedenle, projeler, uygulamanızın geçici klasörlerde, betiklere, metin dosyalarında ve hatta kendi aklından daha kolay bir şekilde genişlemesine ve büyümesine imkan sağlar.

Bu öğreticide, tek bir boş kod dosyası içeren basit bir proje ile çalışmaya başlayabilirsiniz.

1. Visual Studio ' de,   >    >    +  + **yeni Project** iletişim kutusunu gösteren dosya yeni Project (Ctrl shıft **N**) öğesini seçin. burada, farklı dillerdeki şablonlara gözatıp projeniz için bir tane seçip Visual Studio dosyaları nereye yerleştirmektir.

1. Python şablonlarını görüntülemek için sol tarafta **yüklü**  >  **Python** ' ı seçin veya "Python" ifadesini arayın. Arama kullanmak, dil ağacındaki konumunu anımsayamıyorsanız bir şablonu bulmanın harika bir yoludur.

    ![Python projeleri gösterilen yeni proje iletişim kutusu](media/vs-getting-started-python-01-new-project.png)

    Visual Studio 'da Python desteğinin, şişe, flask ve docgo çerçevelerini kullanan web uygulamaları dahil olmak üzere birçok proje şablonu nasıl içerdiğini fark edebilirsiniz. Ancak bu izlenecek yolun amaçları doğrultusunda boş bir proje ile başlayalım.

1. **Python uygulama** şablonu ' nu seçin, proje için bir ad belirtin ve **Tamam**' ı seçin.

1. birkaç dakika sonra, Visual Studio **Çözüm Gezgini** penceresindeki (1) proje yapısını gösterir. Varsayılan kod dosyası düzenleyicide açıktır (2). **Özellikler** penceresi (3) ayrıca, **Çözüm Gezgini**' de seçilen herhangi bir öğe için, diskteki tam konumu da dahil olmak üzere ek bilgileri göstermek için de görünür.

    ![Python projesiyle Çözüm Gezgini](media/vs-getting-started-python-02-windows.png)

1. Projenizdeki dosyalara ve klasörlere gözatabileceğiniz **Çözüm Gezgini** hakkında bilgi edinmek için birkaç dakikanızı ayırın.

    ![Çeşitli özellikleri göstermek için genişletilmiş Çözüm Gezgini](media/vs-getting-started-python-03-solution-explorer.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde kalın olarak vurgulanır. Disk üzerinde bu proje, proje klasörünüzdeki bir *. pyproj* dosyası tarafından temsil edilir.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir *çözümdür*. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözüm içinde bulunabilir. Bu çözüm, özel test programları için projelerle birlikte bir Web hizmeti projesi de içerebilir.

    (3) projenizin altında, kaynak dosyaları, bu durumda yalnızca tek bir *. Kopyala* dosyası görürsünüz. Bir dosya seçilmesi **Özellikler** penceresinde özelliklerini görüntüler. Bir dosyaya çift tıklamak söz konusu dosya için uygun olan her türlü şekilde açılır.

    (4) Ayrıca, **Python ortamları** düğümüdür. Genişletilmişse, sizin için kullanılabilen Python yorumlayıcılarını görürsünüz. Bu ortama yüklenen kitaplıkları (5) görmek için bir yorumlayıcı düğümünü genişletin.

    İlgili komutların menüsüne erişmek için **Çözüm Gezgini** bir düğüme veya öğeye sağ tıklayın. Örneğin, **Rename** komutu, proje ve çözüm dahil olmak üzere herhangi bir düğüm veya öğenin adını değiştirmenize izin verir.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kodu yaz ve Çalıştır](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derin git

- [Visual Studio 'de Python projeleri](managing-python-projects-in-visual-studio.md).
- [Python.org üzerinde Python dili hakkında bilgi edinin](https://www.python.org)
- [Yeni başlayanlar Için Python](https://www.python.org/about/gettingstarted/) (Python.org)
