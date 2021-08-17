---
title: Proje veya çözüm olmadan kod geliştirme
description: Projeler veya çözümlere gerek kalmadan doğrudan Visual Studio kod geliştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/22/2020
ms.topic: how-to
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e23ffa2cef27dc2607e238aa8674e91ff71efbd1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078433"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Visual Studio’da projeler veya çözümler olmadan kod geliştirme

Neredeyse her tür dizin tabanlı projeden, çözüm veya proje Visual Studio gerek kalmadan kodu bir dizine açabilirsiniz. Bu, örneğin, GitHub üzerinde bir Visual Studio veya proje oluşturmak zorunda kalmadan doğrudan Visual Studio açabilirsiniz ve geliştirmeye başlayabilirsiniz. Gerekirse, özel derleme görevleri belirtebilir ve basit JSON dosyaları aracılığıyla parametreleri başlatabilirsiniz.

Kod dosyalarınızı Visual Studio **Çözüm Gezgini** klasördeki tüm dosyaları görüntüler. Herhangi bir dosyaya tıklarsanız düzenlemeye başlayabilirsiniz. Arka planda IntelliSense Visual Studio gezinti ve yeniden düzenleme özelliklerini etkinleştirmek için dosyaların dizinini oluşturmaya başlar. Siz dosyaları düzenlerken, oluşturdukları, taşıyla veya sil Visual Studio değişiklikleri otomatik olarak izler ve IntelliSense dizinini sürekli olarak ler. Kod söz dizimi renklendirme ile görünür ve çoğu durumda temel IntelliSense deyimi tamamlamayı içerir.

## <a name="open-any-code"></a>Herhangi bir kodu açma

Aşağıdaki yollarla Visual Studio açabilirsiniz:

- Dosya Visual Studio çubuğunda Dosya Klasör   >  **Aç'ı**  >  **seçin** ve ardından kod konumunu bulun.

- Kod içeren bir klasörün bağlam (sağ tıklama) menüsünde Open **in Visual Studio** komutunu seçin.

::: moniker range="vs-2017"
- Başlangıç **Sayfasında Klasör** Aç bağlantısını Visual Studio **seçin.**

    > [!IMPORTANT]
    > Tüm kodlar, başlangıç sayfasındaki **Klasör Aç** bağlantısı kullanılarak Visual Studio **açılamaz.** Örneğin, kod dosyanız başka bir deyişle bir çözümün parçası olarak kaydedilmişse, .sln dosyasında kodunuzu açmak için burada listelenen diğer seçeneklerden &mdash; &mdash; birini kullansanız gerekir.

::: moniker-end

::: moniker range=">=vs-2019"
- Başlangıç **penceresinde Klasör** Aç bağlantısını seçin.

    > [!IMPORTANT]
    > Başlangıç penceresindeki Klasör Aç bağlantısı **kullanılarak tüm** kodlar Visual Studio açılmaz. Örneğin, kod dosyanız başka bir deyişle bir çözümün parçası olarak kaydedilmişse, .sln dosyasında kodunuzu açmak için burada listelenen diğer seçeneklerden &mdash; &mdash; birini kullansanız gerekir.

::: moniker-end

- Klavye kullanıcısıysanız, **Ctrl** + **Shift** + **Alt** + **O tuşlarına basarak** Visual Studio.

- Kopyalanan bir GitHub açın.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Kopyalanmış bir GitHub açmak için

Aşağıdaki örnekte, bir GitHub klonlama ve ardından kodunu Visual Studio. Bu yordamı takip etmek için, sisteminize bir GitHub hesabı ve Windows için Git yüklemeniz gerekir. Daha [fazla bilgi için bkz. GitHub hesabı için](https://help.github.com/articles/signing-up-for-a-new-github-account/) kaydolma ve Windows [git.](https://git-for-windows.github.io/)

1. Bu kopyada klonlamak istediğiniz GitHub.

1. Kopyala **veya İndir düğmesini** seçin  ve ardından açılan menüde Panoya Kopyala düğmesini seçerek GitHub için güvenli URL'yi kopyalayın.

   ![GitHub düğmesi](./media/VSIDE_Code_Clone.png)

1. Bu Visual Studio, dosya **Takım Gezgini** açmak için sekmeyi **Takım Gezgini.** Sekmeyi görmüyorsanız Görünüm sekmesinden açın   >  Takım Gezgini.

1. Bu Takım Gezgini Yerel **Git** Depoları bölümünde Kopyala  komutunu seçin ve GitHub sayfasının URL'sini metin kutusuna yapıştırın.

   ![Projeyi kopyalama](./media/VSIDE_Code_Clone2.png)

1. Projenin **dosyalarını** yerel bir Git deposuna klonlamak için Kopyala düğmesini seçin. Bu işlem, repo boyutuna bağlı olarak birkaç dakika sürebilir.

1. Repo sisteminize kopyalandıktan sonra, **Takım Gezgini'da,** yeni  kopyalanan merkezin bağlam (sağ tıklama) menüsünde Aç komutunu seçin.

   ![Kopyalanan repo](./media/VSIDE_Code_Clone3.png)

1. klasördeki **dosyaları görüntülemek için** Klasör Görünümünü Göster komutunu **Çözüm Gezgini.**

   ![Klasör görünümünü göster](./media/VSIDE_Code_Clone3_show.png)

   Artık kopyalanan renge ve dosyalara göz atabilir ve söz dizimi renklendirmesi ve diğer özelliklerle birlikte kodu Visual Studio düzenleyicide görüntüp arayabilirsiniz.

## <a name="run-and-debug-your-code"></a>Kodunuzu çalıştırma ve hata ayıklama

Proje veya çözüm olmadan Visual Studio kodunda hata ayıkabilirsiniz! Bazı dillerde hata ayıklamak için kod temeli  içinde betik, yürütülebilir dosya veya proje gibi geçerli bir başlangıç dosyası belirtmeniz gerekir. Araç çubuğundaki Başlat düğmesinin  yanındaki açılan liste kutusu, algılayan tüm başlangıç öğelerinin Visual Studio olarak sizin özel olarak saptadınız öğeleri listeler. Visual Studio hata ayıklarken önce bu kodu çalıştırır.

Kodunuzun kod içinde Visual Studio, ne tür bir kod olduğu ve derleme araçlarının ne olduğuna bağlı olarak farklılık gösterir.

### <a name="codebases-that-use-msbuild"></a>MSBuild kullanan kod MSBuild

MSBuild tabanlı kod temelleri, Başlat düğmesinin açılan listesinde **görünen** birden çok derleme yapılandırmasına sahip olabilir. Başlangıç öğesi olarak kullanmak istediğiniz dosyayı seçin ve ardından başlat düğmesini **seçerek** hata ayıklamaya başlayabilirsiniz.

> [!NOTE]
> C# ve Visual Basic kod tabanı için .NET masaüstü geliştirme iş **yükünün yüklü** olması gerekir. C++ kod tabanı için C++ ile **Masaüstü geliştirme iş yükünün yüklü** olması gerekir.

### <a name="codebases-that-use-custom-build-tools"></a>Özel derleme araçları kullanan kodbase'ler

Kod tabanınız özel derleme araçları kullanıyorsa, bir .json Visual Studio  tanımlanan derleme görevlerini kullanarak kodunuzun nasıl *derlemesi gerektiğini söylemeniz* gerekir. Daha fazla bilgi için [bkz. Derleme ve hata ayıklama görevlerini özelleştirme.](../ide/customize-build-and-debug-tasks-in-visual-studio.md)

### <a name="codebases-that-contain-python-or-javascript-code"></a>Python veya JavaScript kodu içeren kod tabanı

Kod tabanınız Python veya JavaScript kodu içeriyorsa herhangi bir *.json* dosyası yapılandırmanız zorunlu değil, ancak ilgili iş yükünü yüklemeniz gerekir. Başlangıç betiği de yapılandırmanız gerekir:

1. Araçlar Araç [Node.js Özellikleri Al'i](https://visualstudio.microsoft.com/vs/node-js/) seçerek ya da uygulamanın Visual Studio çalıştırarak uygulama geliştirme veya [Python](https://visualstudio.microsoft.com/vs/python/) geliştirme  >  Visual Studio Yükleyicisi.

   ![Node.js ve Python geliştirme iş yükleri](media/python_nodejs_workloads.png)

1. Bu **Çözüm Gezgini** JavaScript veya Python dosyasının sağ tıklama veya bağlam menüsünde Başlangıç Öğesi Olarak Ayarla **komutunu** seçin.

1. Hata **ayıklamaya** başlamak için Başlat düğmesini seçin.

### <a name="codebases-that-contain-c-code"></a>C++ kodu içeren kodbase'ler

C++ kodunu çözüm veya proje olmadan açma hakkında daha fazla bilgi Visual Studio bkz. [C++ için Klasör Projelerini Açma.](/cpp/build/open-folder-projects-cpp)

### <a name="codebases-that-contain-a-visual-studio-project"></a>Visual Studio projesi içeren kod tabanı

Kod klasörünüz bir Visual Studio proje içeriyorsa, projeyi başlangıç öğesi olarak kullanabilirsiniz.

![Projeyi başlangıç öğesi olarak ayarlama](media/customize-set-project-as-startup-item.png)

Başlat **düğmesinin** metni, projenin başlangıç öğesi olduğunu yansıtacak şekilde değişir.

![Project düğmesine tıklayın](media/customize-start-button-project.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ içinde CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [Kod ve metin düzenleyicisinde kod yazma](../ide/writing-code-in-the-code-and-text-editor.md)
