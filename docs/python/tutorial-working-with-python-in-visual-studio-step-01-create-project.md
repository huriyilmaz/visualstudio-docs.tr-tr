---
title: Python Visual Studio öğretici adım 1, bir proje oluşturmak
titleSuffix: ''
description: Ön koşullar ve yeni bir Python projesi oluşturma dahil olmak üzere Visual Studio'daki Python yeteneklerinin temel bir gözden geçirmesine genel bakış ve adım 1.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430756"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Visual Studio Python ile çalışma

Python güvenilir, esnek, öğrenmesi kolay, tüm işletim sistemlerinde kullanımı ücretsiz ve hem güçlü bir geliştirici topluluğu hem de birçok ücretsiz kütüphane tarafından desteklenen popüler bir programlama dilidir. Dil, web uygulamaları, web hizmetleri, masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işlem de dahil olmak üzere tüm gelişim yöntemlerini destekler ve birçok üniversite, bilim adamı, gündelik geliştiriciler ve profesyonel geliştiriciler tarafından kullanılır.

Visual Studio Python için birinci sınıf dil desteği sağlar. Bu öğretici size aşağıdaki adımlarda rehberlik eder:

- [Adım 0: Kurulum](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Adım 1: Python projesi oluşturma (bu makale)](#step-1-create-a-new-python-project)
- [Adım 2: Visual Studio IntelliSense'i iş yerinde görmek için kod yazın ve çalıştırın](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Adım 3: Etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Adım 4: Visual Studio hata ayıklama tamamlanan programı çalıştırın](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Adım 5: Paketleri yükleyin ve Python ortamlarını yönetin](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Adım 6: Git ile çalışın](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>Adım 1: Yeni bir Python projesi oluşturma

*Proje,* Visual Studio'nun kaynak kodu, kaynaklar, yapılandırmalar ve benzeri gibi tek bir uygulama oluşturmak için bir araya gelen tüm dosyaları nasıl yönettiğidir. Proje, tüm projenin dosyalarının yanı sıra birden çok proje arasında paylaşılan dış kaynaklar arasındaki ilişkiyi resmileştirir ve korur. Bu nedenle, projeler uygulamanızın yalnızca özel klasörlerde, komut dosyalarında, metin dosyalarında ve hatta kendi zihninizde bir projenin ilişkilerini yönetmekten çok daha kolay genişlemesine ve büyümesine olanak sağlar.

Bu öğreticide, tek, boş kod dosyası içeren basit bir proje ile başlar.

1. Visual Studio'da, **Yeni Proje** iletişim kutusunu gündeme getiren **Dosya** > **Yeni** > **Projesi** 'ni **(Ctrl**+**Shift**+**N)** seçin. Burada farklı dillerde şablonlara göz atın, ardından projeniz için bir tane seçin ve Visual Studio'nun dosyaları nereye yerleştirdiğinizi belirtin.

1. Python şablonlarını görüntülemek için solda **Yüklü** > **Python'u** seçin veya "Python"u arayın. Aramayı kullanmak, dil ağacındaki konumunu hatırlayamadığınız da şablonu bulmanın harika bir yoludur.

    ![Python projeleri gösterilen yeni proje iletişim kutusu](media/vs-getting-started-python-01-new-project.png)

    Visual Studio'daki Python desteğinin Şişe, Flask ve Django çerçevelerini kullanan web uygulamaları da dahil olmak üzere bir dizi proje şablonunu nasıl içerdiğine dikkat edin. Ancak bu iznin amaçları için boş bir projeyle başlayalım.

1. Python **Application** şablonunu seçin, proje için bir ad belirtin ve **Tamam'ı**seçin.

1. Birkaç dakika sonra Visual Studio, Çözüm **Gezgini** penceresinde proje yapısını gösterir (1). Varsayılan kod dosyası düzenleyicide açıktır (2). **Özellikler** penceresi (3), **Çözüm Gezgini'nde**seçilen herhangi bir öğe için diskteki tam konumu da dahil olmak üzere ek bilgiler gösterir.

    ![Python projesi ile Çözüm Gezgini](media/vs-getting-started-python-02-windows.png)

1. Projenizdeki dosya ve klasörlere göz attığınız **Solution Explorer'ı**tanımak için birkaç dakikanızı ayırın.

    ![Çözüm Gezgini çeşitli özellikleri göstermek için genişletilmiş](media/vs-getting-started-python-03-solution-explorer.png)

    (1) **Yeni Proje** iletişim kutusunda vermiş olduğunuz adı kullanarak projeniz kalın olarak vurgulanır. Diskte, bu proje proje klasörünüzde bir *.pyproj* dosyası yla temsil edilir.

    (2) En üst düzeyde varsayılan olarak projeile aynı ada sahip bir *çözüm*dür. Diskteki *bir .sln* dosyasıyla temsil edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için bir C++ uzantısı yazarsanız, bu C++ projesi aynı çözüm içinde yer alabilir. Çözüm, özel test programları için projelerle birlikte bir web hizmeti projesi de içerebilir.

    (3) Projenizin altında kaynak dosyaları görürsünüz, bu durumda yalnızca tek bir *.py* dosyası. Bir dosya seçilirken özellikleri **Özellikler** penceresinde görüntülenir. Bir dosyayı çift tıklatma, dosyayı o dosya için uygun olan şekilde açar.

    (4) Ayrıca proje altında **Python Ortamlar** düğüm. Genişletildiğinde, kullanabileceğiniz Python yorumlayıcılarını görürsünüz. Bu ortama yüklenen kitaplıkları görmek için bir yorumlayıcı düğümgenişletin (5).

    Geçerli komutlardan oluşan bir menüye erişmek için **Solution Explorer'daki** herhangi bir düğümü veya öğeyi sağ tıklatın. Örneğin, **Yeniden Adlandırma** komutu, proje ve çözüm de dahil olmak üzere herhangi bir düğümün veya öğenin adını değiştirmenize olanak tanır.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Kod yazma ve çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha derine inin

- [Visual Studio'da Python projeleri](managing-python-projects-in-visual-studio.md).
- [python.org'daki Python dili hakkında bilgi edinin](https://www.python.org)
- [Yeni Başlayanlar için Python](https://www.python.org/about/gettingstarted/) (python.org)
