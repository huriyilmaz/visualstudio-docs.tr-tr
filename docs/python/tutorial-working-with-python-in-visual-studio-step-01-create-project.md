---
title: Visual Studio 'da Python öğreticisi 1. adım, proje oluşturma
titleSuffix: ''
description: Önkoşullar ve yeni bir Python projesi oluşturma gibi Visual Studio 'da Python özelliklerine ilişkin temel bir izlenecek yol ve adım 1 ' e genel bakış.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ed4fdbfe7090a66d955461f2c3a394f6fb661c5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430756"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Visual Studio 'da Python ile çalışma

Python, güvenilir, esnek, öğrenilmesi kolay, tüm işletim sistemlerinde kullanılmak üzere ücretsiz olan ve güçlü bir geliştirici topluluğu ve çok sayıda ücretsiz kitaplık tarafından desteklenen popüler bir programlama dilidir. Dil, Web uygulamaları, Web Hizmetleri, masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işlem gibi tüm geliştiriciler destekler ve birçok üniversiteler, bilimçiler, rastgele geliştiriciler ve profesyonel geliştiriciler tarafından kullanılır.

Visual Studio, Python için birinci sınıf dil desteği sağlar. Bu öğretici aşağıdaki adımlarda size rehberlik eder:

- [Adım 0: yükleme](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1. Adım: Python projesi oluşturma (Bu makale)](#step-1-create-a-new-python-project)
- [2. Adım: Visual Studio IntelliSense 'i iş başında görmek için kodu yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3. Adım: etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4. Adım: tamamlanmış programı Visual Studio hata ayıklayıcısında çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5. Adım: paketleri yükleyip Python ortamlarını yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6. Adım: git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1. Adım: yeni bir Python projesi oluşturma

*Proje* , Visual Studio 'nun, kaynak kodu, kaynaklar, konfigürasyonlar vb. gibi tek bir uygulama oluşturmak için birlikte gelen tüm dosyaları yönetmektedir. Proje formları, projenin tüm dosyaları ve birden çok proje arasında paylaşılan dış kaynaklar arasındaki ilişkiyi korur. Bu nedenle, projeler, uygulamanızın geçici klasörlerde, betiklere, metin dosyalarında ve hatta kendi aklından daha kolay bir şekilde genişlemesine ve büyümesine imkan sağlar.

Bu öğreticide, tek bir boş kod dosyası içeren basit bir proje ile çalışmaya başlayabilirsiniz.

1. Visual Studio 'da **File**  >  **New**  >  **Project** **Ctrl** + **Shift** + **Yeni proje** iletişim kutusunu gösteren dosya yeni proje ' yi (CTRL SHIFT**N**) seçin. Burada, farklı dillerdeki şablonlara gözatıp projeniz için bir tane seçin ve Visual Studio 'Nun dosyaları nereye yerleştirip nerede olduğunu belirtirsiniz.

1. Python şablonlarını görüntülemek için sol tarafta **yüklü**  >  **Python** ' ı seçin veya "Python" ifadesini arayın. Arama kullanmak, dil ağacındaki konumunu anımsayamıyorsanız bir şablonu bulmanın harika bir yoludur.

    ![Python projeleri gösterilen yeni proje iletişim kutusu](media/vs-getting-started-python-01-new-project.png)

    Visual Studio 'da Python desteğinin, şişe, Flask ve Docgo çerçevelerini kullanan Web uygulamaları dahil olmak üzere birçok proje şablonu nasıl içerdiğini fark edebilirsiniz. Ancak bu izlenecek yolun amaçları doğrultusunda boş bir proje ile başlayalım.

1. **Python uygulama** şablonu ' nu seçin, proje için bir ad belirtin ve **Tamam**' ı seçin.

1. Birkaç dakika sonra Visual Studio **Çözüm Gezgini** penceresinde (1) proje yapısını gösterir. Varsayılan kod dosyası düzenleyicide açıktır (2). **Özellikler** penceresi (3) ayrıca, **Çözüm Gezgini**' de seçilen herhangi bir öğe için, diskteki tam konumu da dahil olmak üzere ek bilgileri göstermek için de görünür.

    ![Python projesiyle Çözüm Gezgini](media/vs-getting-started-python-02-windows.png)

1. Projenizdeki dosyalara ve klasörlere gözatabileceğiniz **Çözüm Gezgini**hakkında bilgi edinmek için birkaç dakikanızı ayırın.

    ![Çeşitli özellikleri göstermek için genişletilmiş Çözüm Gezgini](media/vs-getting-started-python-03-solution-explorer.png)

    (1), **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projenizde kalın olarak vurgulanır. Disk üzerinde bu proje, proje klasörünüzdeki bir *. pyproj* dosyası tarafından temsil edilir.

    (2) en üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir *çözümdür*. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözüm içinde bulunabilir. Bu çözüm, özel test programları için projelerle birlikte bir Web hizmeti projesi de içerebilir.

    (3) projenizin altında, kaynak dosyaları, bu durumda yalnızca tek bir *. Kopyala* dosyası görürsünüz. Bir dosya seçilmesi **Özellikler** penceresinde özelliklerini görüntüler. Bir dosyaya çift tıklamak söz konusu dosya için uygun olan her türlü şekilde açılır.

    (4) Ayrıca, **Python ortamları** düğümüdür. Genişletilmişse, sizin için kullanılabilen Python yorumlayıcılarını görürsünüz. Bu ortama yüklenen kitaplıkları (5) görmek için bir yorumlayıcı düğümünü genişletin.

    İlgili komutların menüsüne erişmek için **Çözüm Gezgini** bir düğüme veya öğeye sağ tıklayın. Örneğin, **Rename** komutu, proje ve çözüm dahil olmak üzere herhangi bir düğüm veya öğenin adını değiştirmenize izin verir.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kodu yaz ve Çalıştır](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derin git

- [Visual Studio 'Da Python projeleri](managing-python-projects-in-visual-studio.md).
- [Python.org üzerinde Python dili hakkında bilgi edinin](https://www.python.org)
- [Yeni başlayanlar Için Python](https://www.python.org/about/gettingstarted/) (Python.org)
