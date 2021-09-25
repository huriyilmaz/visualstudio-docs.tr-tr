---
title: Python in Visual Studio öğreticisi 1. adım, proje oluşturma
titleSuffix: ''
description: Önkoşullar ve yeni bir Python projesi oluşturma dahil olmak üzere Visual Studio Python özelliklerine ilişkin temel kılavuza genel bakış ve 1. adım.
ms.date: 09/14/2021
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: vs-acquisition
ms.workload:
- python
- data-science
ms.openlocfilehash: 50894927535010efcee70a079f935176590ba653
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429318"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Python ile Visual Studio

Python güvenilir, esnek, öğrenmesi kolay ve tüm işletim sistemlerinde kullanımı ücretsiz olan popüler bir programlama dilidir. Python hem güçlü bir geliştirici topluluğu hem de çok sayıda ücretsiz kitaplık tarafından de destekler. Dil; web uygulamaları, web hizmetleri, masaüstü uygulamaları, betik ve bilimsel bilgi işlem dahil olmak üzere her türlü geliştirmeyi destekler. Birçok üniversite, bilim insanı, gündelik geliştirici ve profesyonel geliştirici Python kullanır.

Visual Studio Python için birinci sınıf dil desteği sağlar. Bu öğretici, aşağıdaki adımlarda size yol gösteren bir kılavuz içerir:

- [0. Adım: Yükleme](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1. Adım: Python projesi oluşturma (bu makale)](#step-1-create-a-new-python-project)
- [2. Adım: İş yerinde IntelliSense'Visual Studio görmek için kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3. Adım: Etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4. Adım: Tamamlanan programı Visual Studio çalıştırın](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5. Adım: Paketleri yükleme ve Python ortamlarını yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6. Adım: Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1. Adım: Yeni bir Python projesi oluşturma

*Proje,* Visual Studio tek bir uygulama üretmek için bir araya gelen tüm dosyaları nasıl yönetecekleridir. Uygulama dosyaları kaynak kodunu, kaynakları ve yapılandırmaları içerir. Proje, projenin tüm dosyaları arasındaki ilişkileri resmileştirin ve sürdürür. Proje ayrıca birden çok proje arasında paylaşılan dış kaynakları da yönetir. Proje, uygulamanın zahmetsizce genişlemesini ve büyümesine olanak sağlar. Projeleri kullanmak geçici klasörlerde, betiklerde, metin dosyalarında ve bellekte ilişkileri el ile yönetmekten çok daha kolaydır.

Bu öğretici, tek ve boş bir kod dosyası içeren basit bir projeyle başlar.

::: moniker range="<=vs-2019"
1. Bu Visual Studio Yeni **Dosya** iletişim kutusunu  >    >  **Project** (**Ctrl** + **Shift** + **N**) **seçeneğini Project** seçin. Burada farklı dillerdeki şablonlara göz atacak, ardından projeniz için bir şablon seçerek dosyaları nereye Visual Studio belirtebilirsiniz.

1. Python şablonlarını görüntülemek için sol **tarafta Yüklü**  >  **Python'ı** seçin veya "Python" araması yazın. Arama kullanmak, dil ağacının konumunu hatırlayasanız bile şablon bulmanın harika bir yoludur.

    ![Python proje şablonlarıyla yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü.](media/vs-getting-started-python-01-new-project.png)

    Visual Studio'da Python desteği Bottle, Flask ve Django çerçevelerini kullanan web uygulamaları dahil olmak üzere çeşitli proje şablonları içerir. Ancak bu izlenecek yol için boş bir projeyle başlayalım.

1. Python Uygulama **şablonunu seçin,** proje için bir ad belirtin ve Tamam'ı **seçin.**

1. Birkaç dakika sonra Visual Studio penceresinde proje yapısını **(1) Çözüm Gezgini** gösterir. Varsayılan kod dosyası düzenleyicide (2) açıktır. Özellikler **penceresi** (3) ayrıca, diskte tam konumu dahil olmak üzere Çözüm Gezgini öğe için ek bilgileri gösterir.

    ![Yeni projenin Visual Studio.'de açılmasını gösteren ekran görüntüsü.](media/vs-getting-started-python-02-windows.png)

1. Projenizin dosya ve klasörlerine **göz atarak Çözüm Gezgini** hakkında bilgi sahibi olmak için birkaç dakikanızı kullanın.

    ![Özellikleri göstermek Çözüm Gezgini genişletilmiş dosyanın ekran görüntüsü.](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Yeni Çalışma Alanı iletişim kutusunda verdiği ad kullanılarak projeniz kalın **Project** vurgulanır. Diskte, bu proje proje klasörünüzdeki *bir .pyproj* dosyasıyla temsil edildi.

    (2) En üst düzeyde, varsayılan *olarak* projenizin adıyla aynı adı olan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözümde olabilir. Çözüm ayrıca bir web hizmetine yönelik bir proje ve ayrılmış test programlarına yönelik projeler içerebilir.

    (3) Projenizin altında kaynak dosyaları (bu durumda yalnızca tek bir *.py dosyası)* görüyorsunuz. Bir dosyayı seçmek, özelliklerini Özellikler **penceresinde** görüntüler. Bir dosyaya çift tıklarsanız dosya, dosya için uygun olan her şekilde açılır.

    (4) Ayrıca projenin altında Python Ortamları **düğümü** vardır. Genişletilirken, sizin için kullanılabilen Python yorumlayıcılarını göreceksiniz. Bu ortama yüklenmiş kitaplıkları görmek için bir yorumlayıcı düğümünü genişletin (5).

    Geçerli komutların menüsüne erişmek için **Çözüm Gezgini** veya öğeye sağ tıklayın. Örneğin Yeniden Adlandır **komutu** proje ve çözüm dahil olmak üzere herhangi bir düğümün veya öğenin adını değiştirmenizi sağlar.

::: moniker-end

::: moniker range=">=vs-2022"
1. Bu Visual Studio Yeni **Dosya'Project**  >    >  **seçin veya** **Ctrl Shift** N + **tuşlarına** + **basın.** Farklı **dillerdeki şablonları** arayabilir ve göz atabilirsiniz. Yeni proje oluştur ekranı görüntülenir.
   
1. Python şablonlarını görüntülemek için python araması *yazın.* Arama, dil ağacının konumunu hatırlayasanız bile şablon bulmanın harika bir yoludur.
   
   ![Python proje şablonlarıyla yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/getting-started-python-new-project.png)
   
   Visual Studio Python desteği Bottle, Flask ve Django çerçeveleri içinde web uygulamaları gibi çeşitli proje şablonları içerir. Bu öğretici için boş bir projeyle başlama.
   
1. **PythonConsoleApp şablonunu ve** ardından Sonraki'yi **seçin.**
   
1. Yeni **projenizi yapılandır ekranında** proje için bir ad ve dosya konumu belirtin ve ardından Oluştur'a **tıklayın.**
   
   Yeni proje yeni Visual Studio.
   
   - Visual Studio **Çözüm Gezgini** penceresinde proje yapısı **(1) gösterilir.**
   - Varsayılan kod dosyası düzenleyicide **(2) açılır.**
   - Özellikler **penceresi,** diskte tam konumu **(3)** **dahil olmak Çözüm Gezgini** öğesi için daha fazla bilgi gösterir.
   
   ![Yeni projenin Visual Studio.'de açılmasını gösteren ekran görüntüsü.](media/vs-2022/getting-started-python-windows.png)
   
1. Projenizin dosya **Çözüm Gezgini** klasörlere göz atabilirsiniz.
   
   ![Özellikleri göstermek Çözüm Gezgini genişletilmiş dosyanın ekran görüntüsü.](media/vs-2022/getting-started-python-solution-explorer.png)
   
   - En üst düzeyde, varsayılan *olarak* projenizin **adı (1)** ile aynı olan çözümüdür.
     
     Diskte *.sln* dosyası olarak görünen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözümde olabilir. Çözüm ayrıca bir web hizmeti için bir proje ve ayrılmış test programları için projeler içerebilir.
   
   - Yeni proje oluştur iletişim kutusunda  verdiği adla projeniz kalın **(2) olarak görünür.** Diskte proje, proje *klasörünüzdeki bir .pyproj* dosyasıdır.
   
   - Projenizin altında kaynak dosyalar vardır, bu durumda yalnızca tek bir *.py* dosyası **(3) vardır.** Bir dosyayı seçmek, özelliklerini Özellikler **penceresinde** görüntüler. Bir dosyaya çift tıklarsanız dosya, dosya için uygun olan her şekilde açılır.
   
   - Projenin altında da **Python** Ortamları düğümü **(4) yer amaktadır.** Kullanılabilir Python yorumlayıcılarını göstermek için düğümü genişletin.
   
   - Bu ortamda yüklü kitaplıkları görmek için bir yorumlayıcı düğümünü genişletin **(5)**.
   
   Geçerli komutların bağlam menüsünü göstermek için **Çözüm Gezgini** herhangi bir düğüme veya öğeye sağ tıklayın. Örneğin Yeniden **Adlandır,** proje ve çözüm dahil olmak üzere bir düğümün veya öğenin adını değiştirmenizi sağlar.
::: moniker-end

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Visual Studio'da Python projeleri.](managing-python-projects-in-visual-studio.md)
- [Python.org'de Python dili hakkında bilgi python.org](https://www.python.org)
- [Yeni Başlayanlar için Python](https://www.python.org/about/gettingstarted/) (python.org)
