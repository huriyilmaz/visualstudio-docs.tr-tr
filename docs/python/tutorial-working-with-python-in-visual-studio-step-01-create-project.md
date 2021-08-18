---
title: Python in Visual Studio öğreticisi 1. adım, proje oluşturma
titleSuffix: ''
description: Önkoşullar ve yeni bir Python projesi oluşturma dahil olmak üzere Visual Studio Python özelliklerine ilişkin temel kılavuza genel bakış ve 1. adım.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060732"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Python ile Visual Studio

Python hem güçlü bir geliştirici topluluğu hem de birçok ücretsiz kitaplık tarafından desteklenen, güvenilir, esnek, öğrenmesi kolay, tüm işletim sistemlerinde ücretsiz olarak kullanabileceğiniz popüler bir programlama dilidir. Dil; web uygulamaları, web hizmetleri, masaüstü uygulamaları, betik ve bilimsel bilgi işlem gibi her türlü geliştirmeyi destekler ve birçok üniversite, bilim insanı, gündelik geliştirici ve profesyonel geliştirici tarafından kullanılır.

Visual Studio Python için birinci sınıf dil desteği sağlar. Bu öğretici, aşağıdaki adımlarda size yol gösteren bir kılavuz içerir:

- [0. Adım: Yükleme](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1. Adım: Python projesi oluşturma (bu makale)](#step-1-create-a-new-python-project)
- [2. Adım: İş yerinde IntelliSense'Visual Studio görmek için kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3. Adım: Etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4. Adım: Tamamlanan programı Visual Studio çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5. Adım: Paketleri yükleme ve Python ortamlarını yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6. Adım: Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1. Adım: Yeni bir Python projesi oluşturma

*Proje,* Visual Studio, kaynaklar, yapılandırmalar gibi tek bir uygulama üretmek için bir araya gelen tüm dosyaları nasıl yönetecekleridir. Proje, tüm proje dosyalarıyla birden çok proje arasında paylaşılan dış kaynaklar arasındaki ilişkiyi resmileştirin ve sürdürür. Bu nedenle, projeler, uygulamanın yalnızca geçici klasörlerde, betiklerde, metin dosyalarında ve hatta kendi zihninizin içinde projenin ilişkilerini yönetmekten çok daha kolay bir şekilde genişleterek ve büyütmeye olanak sağlar.

Bu öğreticide, tek ve boş bir kod dosyası içeren basit bir projeyle başlarsiniz.

1. Bu Visual Studio Yeni **Dosya** iletişim kutusunu  >    >  **Project** (**Ctrl** + **Shift** + **N**) **seçeneğini Project** seçin. Burada farklı dillerdeki şablonlara göz atacak, projeniz için bir şablon seçerek dosyaları nereye Visual Studio belirtebilirsiniz.

1. Python şablonlarını görüntülemek için sol **tarafta Yüklü**  >  **Python'ı** seçin veya "Python" araması yazın. Arama kullanmak, dil ağacının konumunu hatırlayasanız bile şablon bulmanın harika bir yoludur.

    ![Python projelerinin gösterildiği yeni proje iletişim kutusu](media/vs-getting-started-python-01-new-project.png)

    Visual Studio'da Python desteğinin Bottle, Flask ve Django çerçevelerini kullanan web uygulamaları da dahil olmak üzere bir dizi proje şablonuna nasıl dahil olduğunu göreceksiniz. Ancak bu kılavuzda boş bir projeyle başlayalım.

1. Python Uygulama **şablonunu seçin,** proje için bir ad belirtin ve Tamam'ı **seçin.**

1. Birkaç dakika sonra Visual Studio penceresinde proje yapısını **(1) Çözüm Gezgini** gösterir. Varsayılan kod dosyası düzenleyicide açıktır (2). Özellikler **penceresi** (3) ayrıca, diskte tam konumu dahil olmak üzere **Çözüm Gezgini** öğe için ek bilgileri gösterir.

    ![Çözüm Gezgini Python projesiyle çalışma](media/vs-getting-started-python-02-windows.png)

1. Projenizin dosya ve klasörlerine **göz atarak Çözüm Gezgini** hakkında bilgi sahibi olmak için birkaç dakikanızı kullanın.

    ![Çözüm Gezgini özellikleri göstermek için genişletilmiş özellikler](media/vs-getting-started-python-03-solution-explorer.png)

    (1) New Project iletişim kutusunda verdiği ad kullanılarak projeniz **kalın Project** vurgulanır. Diskte, bu proje proje klasörünüzdeki *bir .pyproj* dosyasıyla temsil edildi.

    (2) En üst düzeyde, varsayılan *olarak* projenizin adıyla aynı adı olan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözüm içinde yer alıyor olabilir. Çözüm ayrıca bir web hizmetine yönelik bir proje ve ayrılmış test programlarına yönelik projeler içerebilir.

    (3) Projenizin altında kaynak dosyaları (bu durumda yalnızca tek bir *.py dosyası)* görüyorsunuz. Bir dosyanın seçimi özellikler penceresinde **görüntülenir.** Bir dosyaya çift tıklarsanız dosya, dosya için uygun olan her şekilde açılır.

    (4) Ayrıca projenin altında Python Ortamları **düğümü** vardır. Genişletilirken, sizin için kullanılabilen Python yorumlayıcılarını göreceksiniz. Bu ortama yüklenmiş kitaplıkları görmek için bir yorumlayıcı düğümünü genişletin (5).

    Geçerli komutların menüsüne erişmek için **Çözüm Gezgini** düğüme veya öğeye sağ tıklayın. Örneğin Yeniden Adlandır **komutu,** proje ve çözüm dahil olmak üzere herhangi bir düğümün veya öğenin adını değiştirmenizi sağlar.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Visual Studio.](managing-python-projects-in-visual-studio.md)
- [Python.org'da Python dili hakkında bilgi python.org](https://www.python.org)
- [Yeni Başlayanlar için Python](https://www.python.org/about/gettingstarted/) (python.org)
