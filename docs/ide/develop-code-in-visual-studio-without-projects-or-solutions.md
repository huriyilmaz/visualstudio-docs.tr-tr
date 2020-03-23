---
title: Proje veya çözüm olmadan kod geliştirme
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596300"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Visual Studio’da projeler veya çözümler olmadan kod geliştirme

Bir çözüm veya proje dosyasına gerek kalmadan, hemen hemen her tür dizin tabanlı projeden Visual Studio'ya kod açabilirsiniz. Bu, örneğin, GitHub'da bir repo klonlayabileceğiniz, doğrudan Visual Studio'ya açabileceğiniz ve bir çözüm veya proje oluşturmak zorunda kalmadan geliştirmeye başlayabileceğiniz anlamına gelir. Gerekirse, basit JSON dosyaları aracılığıyla özel yapı görevlerini belirtebilir ve parametreleri başlatabilirsiniz.

Visual Studio'da kod dosyalarınızı açtıktan sonra **Solution Explorer** klasördeki tüm dosyaları görüntüler. Düzenlemeye başlamak için herhangi bir dosyayı tıklatabilirsiniz. Arka planda Visual Studio, IntelliSense, gezinme ve yeniden düzenleme özelliklerini etkinleştirmek için dosyaları dizine eklemeye başlar. Dosyaları düzenlediğinizde, oluşturdukça, taşırken veya silerken, Visual Studio değişiklikleri otomatik olarak izler ve IntelliSense dizinini sürekli olarak günceller. Kod sözdizimi renklendirme ile görünür ve birçok durumda, temel IntelliSense deyimi tamamlama içerir.

## <a name="open-any-code"></a>Herhangi bir kodu açma

Kodu Visual Studio'ya aşağıdaki yollardan herhangi birinde açabilirsiniz:

- Visual Studio menü çubuğunda **Dosya** > **Aç** > **Klasörünü**seçin ve ardından kod konumuna göz atın.

- Kod içeren bir klasörün bağlam (sağ tıklatma) **menüsünde Visual Studio'da Aç** komutunu seçin.

::: moniker range="vs-2017"
- Visual Studio **Başlangıç Sayfasındaki** **Klasörü Aç** bağlantısını seçin.
::: moniker-end

::: moniker range=">=vs-2019"
- Başlangıç penceresindeki **Klasörü Aç** bağlantısını seçin.
::: moniker-end

- Klavye kullanıcısıysanız Visual Studio'da **Ctrl**+**Shift**+**Alt**+**O** tuşuna basın.

- Klonlanmış GitHub repo'sundan kodu açın.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Klonlanmış GitHub repo'sundan kodu açmak için

Aşağıdaki örnek, Bir GitHub repo'sunu nasıl klonlayıp visual studio'da kodunu niçin açacağımı gösterir. Bu yordamı izlemek için sisteminizde bir GitHub hesabınız ve Windows için Git yüklü olmalıdır. Daha fazla bilgi [için yeni bir GitHub hesabı için kaydolma](https://help.github.com/articles/signing-up-for-a-new-github-account/) ve [Windows için Git'e](https://git-for-windows.github.io/) bakın.

1. GitHub'da klonlamak istediğiniz repoya gidin.

1. **Clone veya Download** düğmesini seçin ve ardından GitHub repo'su için güvenli URL'yi kopyalamak için açılır menüdeki **Panoya Kopyala** düğmesini seçin.

   ![GitHub klon düğmesi](./media/VSIDE_Code_Clone.png)

1. Visual Studio'da, **Team Explorer'ı**açmak için **Takım Gezgini** sekmesini seçin. Sekmeyi görmüyorsanız, > **Görünüm Ekibi Gezgini'nden** **View**açın.

1. Team Explorer'da, **Yerel Git Depoları** bölümünün altında, **Klon** komutunu seçin ve ardından GitHub sayfasının URL'sini metin kutusuna yapıştırın.

   ![Projeyi klonlama](./media/VSIDE_Code_Clone2.png)

1. Projenin dosyalarını yerel bir Git deposunda klonlamak için **Klon** düğmesini seçin. Repo'nun boyutuna bağlı olarak, bu işlem birkaç dakika sürebilir.

1. Repo sisteminize klonlandıktan sonra, **Team Explorer'da,** yeni klonlanan repo'nun bağlamındaki (sağ tıklatma) menüsündeki **Aç** komutunu seçin.

   ![Klonlanmış repo](./media/VSIDE_Code_Clone3.png)

1. **Solution Explorer'daki**dosyaları görüntülemek için **Klasör Görünümü'nu Göster** komutunu seçin.

   ![Klasör görünümünü göster](./media/VSIDE_Code_Clone3_show.png)

   Artık klonlanmış repo'daki klasörlere ve dosyalara göz atabilir ve sözdizimi renklendirme ve diğer özelliklerle birlikte Visual Studio kod düzenleyicisinde kodu görüntüleyebilir ve arayabilirsiniz.

## <a name="run-and-debug-your-code"></a>Kodunuzu çalıştırın ve hata ayıklama

Visual Studio'da kodunuzu bir proje veya çözüm olmadan hata ayıklayabilirsiniz! Bazı dillerin hata ayıklanması için kod tabanında komut dosyası, çalıştırılabilir veya proje gibi geçerli bir *başlangıç dosyası* belirtmeniz gerekebilir. Araç çubuğundaki **Başlat** düğmesinin yanındaki açılır liste kutusu, Visual Studio'nun algıladığının tüm başlangıç öğelerinin yanı sıra özel olarak belirlediğiniz öğeleri listeler. Visual Studio, kodunuzu hata ayıklama yaptığınızda bu kodu ilk olarak çalıştırın.

Kodunuzu Visual Studio'da çalışacak şekilde yapılandırmak, kodun ne tür bir kod olduğuna ve yapı araçlarının ne olduğuna bağlı olarak değişir.

### <a name="codebases-that-use-msbuild"></a>MSBuild kullanan codebases

MSBuild tabanlı codebases **Başlat** düğmesinin açılır listesinde görünen birden çok yapı yapılandırmaları olabilir. Başlangıç öğesi olarak kullanmak istediğiniz dosyayı seçin ve sonra hata ayıklamaya başlamak için **Başlat** düğmesini seçin.

> [!NOTE]
> C# ve Visual Basic kod tabanları için **.NET masaüstü geliştirme** iş yükünün yüklü olması gerekir. C++ kod tabanları için C++ iş yükü **yüklü Masaüstü geliştirmeniz** gerekir.

### <a name="codebases-that-use-custom-build-tools"></a>Özel yapı araçları kullanan codebases

Kod tabanınız özel yapı araçları kullanıyorsa, Visual Studio'ya *.json* dosyasında tanımlanan *yapı görevlerini* kullanarak kodunuzu nasıl oluştureceğinizi söylemeniz gerekir. Daha fazla bilgi için [yapıyı özelleştir ve görevleri ayıklama bölümüne](../ide/customize-build-and-debug-tasks-in-visual-studio.md)bakın.

### <a name="codebases-that-contain-python-or-javascript-code"></a>Python veya JavaScript kodu içeren codebases

Kod tabanınız Python veya JavaScript kodu içeriyorsa, *.json* dosyalarını yapılandırmanız gerekir, ancak ilgili iş yükünü yüklemeniz gerekir. Ayrıca başlangıç komut dosyasını yapılandırmanız gerekir:

1. **Araçlar** > **Al Araçları ve Özellikleri**seçerek veya Visual Studio'yu kapatıp Visual Studio Yükleyicisini çalıştırarak [Düğüm.js geliştirme](https://visualstudio.microsoft.com/vs/node-js/) veya Python [geliştirme](https://visualstudio.microsoft.com/vs/python/) iş yükünü yükleyin.

   ![Düğüm.js ve Python geliştirme iş yükleri](media/python_nodejs_workloads.png)

1. **Solution**Explorer'da, JavaScript veya Python dosyasının sağ tıklama veya bağlam menüsünde Başlangıç Öğesi komutu **olarak Ayarla'yı** seçin.

1. Hata ayıklamaya başlamak için **Başlat** düğmesini seçin.

### <a name="codebases-that-contain-c-code"></a>C++ kodu içeren kod tabanları

Visual Studio'da çözümsüz veya proje olmadan C++ kodunu açma hakkında bilgi için [C++ için Açık Klasör projelerine](/cpp/build/open-folder-projects-cpp)bakın.

### <a name="codebases-that-contain-a-visual-studio-project"></a>Visual Studio projesi içeren codebases

Kod klasörünüz bir Visual Studio projesi içeriyorsa, projeyi başlangıç öğesi olarak atayabilirsiniz.

![Projeyi başlangıç öğesi olarak ayarlama](media/customize-set-project-as-startup-item.png)

**Başlat** düğmesinin metni, projenin başlangıç öğesi olduğunu yansıtacak şekilde değişir.

![Başlat düğmesinde Proje](media/customize-start-button-project.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++'da CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [Kod ve metin düzenleyicisinde kod yazma](../ide/writing-code-in-the-code-and-text-editor.md)
