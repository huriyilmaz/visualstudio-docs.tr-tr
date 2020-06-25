---
title: Proje veya çözüm olmadan kod geliştirme
ms.date: 06/22/2020
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
ms.openlocfilehash: 75aeb721ea5625523d29e20193ac406037abedc2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284899"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Visual Studio’da projeler veya çözümler olmadan kod geliştirme

Bir çözüm veya proje dosyası gerekmeden, neredeyse her bir dizin tabanlı proje türünden kodu Visual Studio 'ya açabilirsiniz. Bu, örneğin bir depoyu GitHub üzerinde kopyalayabilir, doğrudan Visual Studio 'da açabilir ve bir çözüm ya da proje oluşturmaya gerek kalmadan geliştirmeye başlayabilirsiniz. Gerekirse, özel derleme görevleri belirtebilir ve basit JSON dosyaları aracılığıyla parametreleri başlatabilirsiniz.

Visual Studio 'da kod dosyalarınızı açtıktan sonra, **Çözüm Gezgini** klasördeki tüm dosyaları görüntüler. Herhangi bir dosyaya tıklayarak dosyayı düzenleyebilirsiniz. Arka planda, Visual Studio IntelliSense, gezinti ve yeniden düzenleme özelliklerini etkinleştirmek için dosyaları dizine oluşturmaya başlar. Dosyaları düzenlerken, oluştururken, taşırken veya silerken, Visual Studio değişiklikleri otomatik olarak izler ve IntelliSense dizinini sürekli olarak güncelleştirir. Kod, söz dizimi renklendirmesi ile görünür ve çoğu durumda temel IntelliSense ifadesinin tamamlanmasını dahil eder.

## <a name="open-any-code"></a>Herhangi bir kodu açın

Aşağıdaki yollarla kodu Visual Studio 'da açabilirsiniz:

- Visual Studio menü çubuğunda **Dosya**  >  **Open**  >  **klasörü**aç ' ı seçin ve ardından kod konumuna gidin.

- Kod içeren bir klasörün bağlam (sağ tıklama) menüsünde, **Visual Studio 'Da aç** komutunu seçin.

::: moniker range="vs-2017"
- Visual Studio **Başlangıç sayfasında** **klasörü aç** bağlantısını seçin.

    > [!IMPORTANT]
    > Tüm kodlar, Visual Studio **başlangıç sayfasından** **Klasör aç** bağlantısı kullanılarak açılamaz. Örneğin, kod dosyanız başka bir deyişle bir çözümün parçası olarak kaydedilmişse &mdash; , bir. sln dosyasında, &mdash; kodunuzu açmak için burada listelenen diğer seçeneklerden birini kullanmanız gerekir.

::: moniker-end

::: moniker range=">=vs-2019"
- Başlangıç penceresinde **klasörü aç** bağlantısını seçin.

    > [!IMPORTANT]
    > Visual Studio başlangıç penceresinden **Klasör aç** bağlantısı kullanılarak kodların hepsi açılamaz. Örneğin, kod dosyanız başka bir deyişle bir çözümün parçası olarak kaydedilmişse &mdash; , bir. sln dosyasında, &mdash; kodunuzu açmak için burada listelenen diğer seçeneklerden birini kullanmanız gerekir.

::: moniker-end

- Klavye kullanıcısı kullanıyorsanız, **Ctrl** + **Shift** + **Alt** + Visual Studio 'da CTRL SHIFT alt**O** tuşlarına basın.

- Kopyalanmış bir GitHub deposundan kodu açın.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Kopyalanmış bir GitHub deposundan kodu açmak için

Aşağıdaki örnekte, bir GitHub deposunun nasıl klonaçılacağı ve sonra kodu Visual Studio 'da nasıl açılacağı gösterilmektedir. Bu yordamı izlemek için, sisteminizde yüklü Windows için bir GitHub hesabı ve git olması gerekir. Daha fazla bilgi için bkz. [Yeni bir GitHub hesabına](https://help.github.com/articles/signing-up-for-a-new-github-account/) kaydolma ve [Windows için git](https://git-for-windows.github.io/) .

1. GitHub 'da kopyalamak istediğiniz depoya gidin.

1. **Kopyala veya indir** düğmesini seçin ve ardından açılan menüdeki **Panoya Kopyala** düğmesini seçerek GITHUB deposu için güvenli URL 'yi kopyalayın.

   ![GitHub kopyalama düğmesi](./media/VSIDE_Code_Clone.png)

1. Visual Studio 'da **Takım Gezgini**açmak için **Takım Gezgini** sekmesini seçin. Sekmeyi görmüyorsanız, Takım Gezgini **Görünüm**' den açın  >  **Team Explorer**.

1. Takım Gezgini, **yerel Git depoları** bölümünde, **Kopyala** komutunu seçin ve ardından GitHub sayfasının URL 'sini metin kutusuna yapıştırın.

   ![Projeyi Kopyala](./media/VSIDE_Code_Clone2.png)

1. Projenin dosyalarını yerel bir git deposuna kopyalamak için **Kopyala** düğmesini seçin. Deponun boyutuna bağlı olarak, bu işlem birkaç dakika sürebilir.

1. Depo, sisteminize kopyalandıktan sonra, **Takım Gezgini**' de, yeni kopyalanmış deponun bağlam (sağ tıklama) menüsünde **Aç** komutunu seçin.

   ![Kopyalanmış depo](./media/VSIDE_Code_Clone3.png)

1. **Çözüm Gezgini**dosyaları görüntülemek Için **klasör görünümünü göster** komutunu seçin.

   ![Klasör görünümünü göster](./media/VSIDE_Code_Clone3_show.png)

   Artık kopyalanmış depodaki klasörlere ve dosyalara gözatabilir, Sözdizimi renklendirmesi ve diğer özelliklerle birlikte Visual Studio kod Düzenleyicisi 'nde kodu görüntüleyebilir ve arayabilirsiniz.

## <a name="run-and-debug-your-code"></a>Kodunuzu çalıştırın ve hata ayıklayın

Visual Studio 'da bir proje veya çözüm olmadan kodunuzda hata ayıklaması yapabilirsiniz! Bazı dillerde hata ayıklamak için, kod tabanında, yürütülebilir dosya veya proje gibi geçerli bir *başlangıç dosyası* belirtmeniz gerekebilir. Araç çubuğundaki **Başlat** düğmesinin yanındaki açılan liste kutusu, Visual Studio 'nun algıladığı tüm başlangıç öğelerini ve özellikle belirlediğiniz öğeleri listeler. Kodunuzda hata ayıklarken Visual Studio bu kodu çalıştırır.

Kodunuzu Visual Studio 'da çalışacak şekilde yapılandırmak, ne tür koda ve derleme araçlarının ne olduğuna bağlı olarak farklılık gösterir.

### <a name="codebases-that-use-msbuild"></a>MSBuild kullanan codeesalar

MSBuild tabanlı kod tabanlarında, **Başlangıç** düğmesinin açılan listesinde görünen birden çok derleme yapılandırması olabilir. Başlangıç öğesi olarak kullanmak istediğiniz dosyayı seçin ve ardından hata ayıklamaya başlamak için **Başlat** düğmesini seçin.

> [!NOTE]
> C# ve Visual Basic codeesaları için, **.net masaüstü geliştirme** iş yükünün yüklü olması gerekir. C++ kod tabanları için, C++ iş yükünün yüklü **olduğu masaüstü geliştirmesine** sahip olmanız gerekir.

### <a name="codebases-that-use-custom-build-tools"></a>Özel derleme araçları kullanan kod tabanları

Kod tabanınız özel derleme araçları kullanıyorsa, Visual Studio 'Nun bir *. JSON* dosyasında tanımlanan *derleme görevlerini* kullanarak kodunuzu nasıl derleyeceğinizi bildirmeniz gerekir. Daha fazla bilgi için bkz. [Yapı ve hata ayıklama görevlerini özelleştirme](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Python veya JavaScript kodu içeren codeesalar

Kod tabanınız Python veya JavaScript kodu içeriyorsa, herhangi bir *. JSON* dosyası yapılandırmanız gerekmez, ancak ilgili iş yükünü yüklemelisiniz. Başlangıç betiğini de yapılandırmanız gerekir:

1. **Araçlar** [Node.js development](https://visualstudio.microsoft.com/vs/node-js/) [Python development](https://visualstudio.microsoft.com/vs/python/)  >  **ve Özellikler al**' ı seçerek veya Visual Studio 'yu kapatarak ve Visual Studio yükleyicisi çalıştırarakNode.js geliştirme veya Python geliştirme iş yükünü yüklemelisiniz.

   ![Node.js ve Python geliştirme iş yükleri](media/python_nodejs_workloads.png)

1. **Çözüm Gezgini**, JavaScript veya Python dosyasının sağ tıklama veya bağlam menüsünde **Başlangıç öğesi olarak ayarla** komutunu seçin.

1. Hata ayıklamaya başlamak için **Başlat** düğmesini seçin.

### <a name="codebases-that-contain-c-code"></a>C++ kodu içeren codeesalar

Visual Studio 'da çözüm veya proje olmadan C++ kodu açma hakkında bilgi için bkz. [c++ Için klasör projelerini açma](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Visual Studio projesi içeren codeesalar

Kod klasörünüz bir Visual Studio projesi içeriyorsa, projeyi başlangıç öğesi olarak belirtebilirsiniz.

![Projeyi başlangıç öğesi olarak ayarla](media/customize-set-project-as-startup-item.png)

**Başlat** düğmesinin metni, projenin başlangıç öğesi olduğunu yansıtacak şekilde değişir.

![Başlangıç düğmesinde proje](media/customize-start-button-project.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++ için Klasör projelerini açma](/cpp/build/open-folder-projects-cpp)
- [C++ ' da CMake projeleri](/cpp/build/cmake-projects-in-visual-studio)
- [Kod ve metin düzenleyicisinde kod yazma](../ide/writing-code-in-the-code-and-text-editor.md)
