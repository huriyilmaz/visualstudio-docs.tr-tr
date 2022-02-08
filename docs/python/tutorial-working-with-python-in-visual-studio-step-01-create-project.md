---
title: 'Python Visual Studio öğretici 1. adım, proje oluşturma'
titleSuffix: ''
description: önkoşullar ve yeni bir python projesi oluşturma gibi Visual Studio Python özelliklerine ilişkin temel bir anlatımın genel bakış ve 1. adımı.
ms.date: 02/02/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.custom: 'vs-acquisition, devdivchpfy22'
ms.workload:
  - python
  - data-science
---

# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Visual Studio 'de Python ile çalışma

Python, güvenilir, esnek, kolayca öğrenilmesi kolay olan ve tüm işletim sistemlerinde kullanılabilen popüler bir programlama dilidir. Python hem güçlü bir geliştirici topluluğu hem de birçok, ücretsiz kitaplık tarafından desteklenir. Dil, Web uygulamaları, Web Hizmetleri, masaüstü uygulamaları, betik oluşturma ve bilimsel bilgi işlem gibi tüm geliştirme türlerini destekler. Birçok Üniversiteler, bilimciler, gündelik geliştiriciler ve profesyonel geliştiriciler Python kullanır.

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

bir *proje* , tek bir uygulama oluşturmak için birlikte gelen tüm dosyaları Visual Studio yönetir. Uygulama dosyaları, kaynak kodunu, kaynakları ve konfigürasyonları içerir. Proje, tüm proje dosyaları arasındaki ilişkileri biçimlendirir ve yönetir. Proje ayrıca birden çok proje arasında paylaşılan dış kaynakları yönetir. Bir proje, uygulamanızın kolay bir şekilde genişlemesini ve büyümesini sağlar. Proje kullanımı, planlanmamış klasörlerde, betiklerinizde, metin dosyalarında ve bellekte bulunan ilişkilerin el ile yönetilmesine kıyasla çok daha kolaydır.

Bu öğretici, tek bir boş kod dosyası içeren basit bir proje ile başlar.

::: moniker range="<=vs-2019"
1. Visual Studio ' de, **yeni Project** iletişim kutusunu gösteren **dosya**  >  **yeni**  >  **Project** (**Ctrl** + **shıft** + **N**) öğesini seçin. burada, farklı dillerdeki şablonlara gözatıp projeniz için bir tane seçip Visual Studio dosyaları nereye yerleştirmektir.

1. Python şablonlarını görüntülemek için sol tarafta **yüklü**  >  **Python** ' ı seçin veya "Python" ifadesini arayın. Arama kullanmak, dil ağacındaki konumunu anımsayamıyorsanız bir şablonu bulmanın harika bir yoludur.

    ![Python proje şablonlarıyla yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü.](media/vs-getting-started-python-01-new-project.png)

    Visual Studio 'de Python desteği, şişe, flask ve docgo çerçevelerini kullanan web uygulamaları dahil olmak üzere çeşitli proje şablonları içerir. Ancak bu izlenecek yolun amaçları doğrultusunda boş bir proje ile başlayalım.

1. **Python uygulama** şablonu ' nu seçin, proje için bir ad belirtin ve **Tamam**' ı seçin.

1. birkaç dakika sonra, Visual Studio **Çözüm Gezgini** penceresindeki (1) proje yapısını gösterir. Varsayılan kod dosyası düzenleyicide açıktır (2). **Özellikler** penceresi (3) ayrıca, **Çözüm Gezgini**' de seçilen herhangi bir öğe için, diskteki tam konumu da dahil olmak üzere ek bilgileri göstermek için de görünür.

    ![Visual Studio yeni projenin açık olduğunu gösteren ekran görüntüsü.](media/vs-getting-started-python-02-windows.png)

1. Projenizdeki dosyalara ve klasörlere gözatabileceğiniz **Çözüm Gezgini** hakkında bilgi edinmek için birkaç dakikanızı ayırın.

    ![Özellikleri göstermek için genişletilen Çözüm Gezgini ekran görüntüsü.](media/vs-getting-started-python-03-solution-explorer.png)

    (1), **yeni Project** iletişim kutusunda verdiğiniz adı kullanarak projenizde kalın olarak vurgulanır. Disk üzerinde bu proje, proje klasörünüzdeki bir *. pyproj* dosyası tarafından temsil edilir.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir *çözümdür*. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözümde olabilir. Bu çözüm, özel test programları için projelerle birlikte bir Web hizmeti projesi de içerebilir.

    (3) projenizin altında, kaynak dosyaları, bu durumda yalnızca tek bir *. Kopyala* dosyası görürsünüz. Bir dosya seçilmesi **Özellikler** penceresinde özelliklerini görüntüler. Bir dosyaya çift tıklamak söz konusu dosya için uygun olan her türlü şekilde açılır.

    (4) Ayrıca, **Python ortamları** düğümüdür. Genişletilmişse, sizin için kullanılabilen Python yorumlayıcılarını görürsünüz. Bu ortama yüklenen kitaplıkları (5) görmek için bir yorumlayıcı düğümünü genişletin.

    İlgili komutların menüsüne erişmek için **Çözüm Gezgini** bir düğüme veya öğeye sağ tıklayın. Örneğin, **Rename** komutu, proje ve çözüm dahil olmak üzere herhangi bir düğüm veya öğenin adını değiştirmenize izin verir.

::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio ' de **dosya**  >  **yeni**  >  **Project** ' i seçin veya **Ctrl** + **shıft** + **N** tuşuna basın. **Yeni proje oluştur** ekranı, farklı dillerdeki şablonlara arayabileceğiniz ve gözatabileceğiniz bir ekran görüntülenir.
   
1. Python şablonlarını görüntülemek için *Python* araması yapın. Arama, dil ağacındaki konumunu anımsayamıyorsanız bir şablon bulmanın harika bir yoludur.
   
   ![Python proje şablonlarıyla yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2022/getting-started-python-new-project.png)
   
   Visual Studio 'de Python desteği, şişe, flask ve docgo çerçeveleri içindeki web uygulamaları gibi çeşitli proje şablonları içerir. Bu öğreticide boş bir proje ile başlayın.
   
1. **PythonConsoleApp** şablonunu seçin ve **İleri**' yi seçin.
   
1. **Yeni projenizi yapılandırın** ekranında, proje için bir ad ve dosya konumu belirtin ve ardından **Oluştur**' u seçin.
   
   Yeni proje Visual Studio açılır.
   
   - Visual Studio **Çözüm Gezgini** pencere, proje yapısını **(1)** gösterir.
   - Varsayılan kod dosyası düzenleyicide açılır **(2)**.
   - **Özellikler** penceresinde, **Çözüm Gezgini**' de seçili öğe için daha fazla bilgi görüntülenir **(3)**.
   
   ![Visual Studio yeni projenin açık olduğunu gösteren ekran görüntüsü.](media/vs-2022/getting-started-python-windows.png)
   
1. Projenizdeki dosyalara ve klasörlere gözatabileceğiniz **Çözüm Gezgini** hakkında bilgi edinin.
   
   ![Özellikleri göstermek için genişletilen Çözüm Gezgini ekran görüntüsü.](media/vs-2022/getting-started-python-solution-explorer.png)
   
   - En üst düzey, varsayılan olarak projenizle aynı ada **(1)** sahip olan *çözümdür*.
     
     Disk üzerinde *. sln* dosyası olarak gösterilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözümde olabilir. Çözüm Ayrıca bir Web hizmeti projesi ve adanmış test programları için projeler içerebilir.
   
   - Projeniz, **Yeni proje oluştur** iletişim kutusunda verdiğiniz adla birlikte kalın **(2)** olarak görüntülenir. Disk üzerinde proje, proje klasörünüzdeki bir *. pyproj* dosyasıdır.
   
   - Projenizin altında kaynak dosyaları, bu durumda yalnızca tek bir *. Kopyala* dosyası **(3)**. Bir dosya seçilmesi **Özellikler** penceresinde özelliklerini görüntüler. Bir dosyaya çift tıklamak söz konusu dosya için uygun olan her türlü şekilde açılır.
   
   - Proje altında ayrıca **Python ortamları** düğümüdür **(4)**. Kullanılabilir Python yorumlayıcılarını göstermek için düğümü genişletin.
   
   - Bu ortamda yüklü olan kitaplıkları **(5)** görmek için bir yorumlayıcı düğümünü genişletin.
   
   İlgili komutların bağlam menüsünü göstermek için **Çözüm Gezgini** bir düğüme veya öğeye sağ tıklayın. Örneğin, **yeniden adlandırma** , proje ve çözüm dahil olmak üzere bir düğüm veya öğenin adını değiştirmenize izin verir.
::: moniker-end

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kodu yaz ve Çalıştır](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derin git

- [Visual Studio 'de Python projeleri](managing-python-projects-in-visual-studio.md).
- [Python.org üzerinde Python dili hakkında bilgi edinin](https://www.python.org)
- [Yeni başlayanlar Için Python](https://www.python.org/about/gettingstarted/) (Python.org)
