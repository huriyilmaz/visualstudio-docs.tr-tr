---
title: Docker konteyner günlükleri, ortam değişkenleri ve dosya sistemi erişimi
description: Uygulamanızı barındıran kapsayıcıların içinde neler olup bittiğini görmek için bir araç penceresi kullanarak Visual Studio'daki hata ayıklama ve tanılama yeteneğinizi nasıl geliştireceğinizaçık.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027302"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Visual Studio'da kapsayıcılar ve görüntüler nasıl görüntülenebilir ve tanılar

**Kapsayıcılar** penceresini kullanarak uygulamanızı barındıran kapsayıcıların içinde neler olup bittiğini görüntüleyebilirsiniz. Kapsayıcılarınızda neler olup bittiğini görüntülemek ve tanılamak için Docker komutlarını çalıştırmak için komut istemini kullanmaya alışkınsanız, bu pencere Visual Studio IDE'den çıkmadan kapsayıcılarınızı izlemek için daha kullanışlı bir yol sağlar.

## <a name="prerequisites"></a>Önkoşullar

- [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 sürüm 16.4 Önizleme 2](https://visualstudio.microsoft.com/downloads) veya daha sonra, ya da Visual Studio 2019'un önceki bir sürümünü kullanıyorsanız, [Kapsayıcılar pencere uzantısını](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions)yükleyin.

## <a name="view-information-about-your-containers"></a>Kapsayıcılarınız hakkındaki bilgileri görüntüleme

Kapsayıcıbir .NET projesini başlattığınızda **Kapsayıcılar** penceresi otomatik olarak açılır. İstediğiniz zaman Visual Studio'daki konteynırlarınızı görüntülemek için Visual Studio `Containers` Arama kutusunu etkinleştirmek için **Ctrl**+**Q'yu** kullanın ve ilk öğeyi yazın ve seçin. **Kapsayıcılar** penceresini ana menüden de açabilirsiniz. Menü yolunu diğer**Windows** > **Kapsayıcılarını** **Görüntüle'yi** > kullanın.  

![Kapsayıcılar penceresinde Çevre sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/container-window.png)

Sol tarafta, yerel makinenizdeki kapsayıcıların listesini görürsünüz. Çözümünüzle ilişkili kapsayıcılar **Çözüm Kapları**altında gösterilir. Sağda, **Çevre,** **Bağlantı Noktaları,** **Günlükler**ve **Dosyalar**için sekmeler içeren bir bölme görürsünüz.

> [!TIP]
> **Kapsayıcılar** araç penceresinin Visual Studio'ya sabitlendiği yeri kolayca özelleştirebilirsiniz. [Bkz. Visual Studio'da pencere düzenlerini özelleştirme.](../ide/customizing-window-layouts-in-visual-studio.md) Varsayılan olarak, hata ayıklama çalışırken **Kapsayıcılar** penceresi **İzleme** penceresine sabitlenir.

## <a name="view-environment-variables"></a>Ortam değişkenlerini görüntüleme

**Çevre** sekmesi kapsayıcıdaki ortam değişkenlerini gösterir. Uygulamanızın kapsayıcısı için, bu değişkenleri birçok şekilde ayarlayabilirsiniz, örneğin Dockerfile'da, .env dosyasında veya Docker komutunu kullanarak bir kapsayıcıyı başlattığınızda -e seçeneğini kullanarak.

![Kapsayıcılar penceresinde Çevre sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Ortam değişkenlerinde yapılan değişiklikler gerçek zamanlı olarak yansıtılmamaktadır. Ayrıca, bu sekmedeki ortam değişkenleri kapsayıcıdaki sistem ortamı değişkenleridir ve uygulamanın yerel kullanıcı ortamı değişkenlerini yansıtmaz.

## <a name="view-port-mappings"></a>Bağlantı noktası eşlemelerini görüntüleme

Bağlantı **Noktaları** sekmesinde, kapsayıcınız için geçerli olan bağlantı noktası eşlemelerini denetleyebilirsiniz.

![Kapsayıcılar penceresindeki Bağlantı Noktaları sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-ports.png)

Bilinen bağlantı noktaları birbirine bağlıdır, bu nedenle bir bağlantı noktasında içerik varsa, tarayıcıyı açmak için bağlantıyı tıklatabilirsiniz.

## <a name="view-logs"></a>Günlükleri görüntüleme

**Günlükler** sekmesi `docker logs` komutun sonuçlarını gösterir. Varsayılan olarak, sekme bir kapsayıcı üzerinde stdout ve stderr akışları gösterir, ancak çıktıyı yapılandırabilirsiniz. Ayrıntılar için [Docker günlüğe kaydedin.](https://docs.docker.com/config/containers/logging/)  Varsayılan olarak, **Günlükler** sekmesi günlükleri akışı, ancak sekmede **Durdur** düğmesini seçerek devre dışı bırakabilirsiniz.

![Kapsayıcılar penceresinde günlükler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-logs.png)

Günlükleri temizlemek için **Günlükler** sekmesindeki **Temizle** düğmesini kullanın.  Tüm günlükleri almak için **Yenile** düğmesini kullanın.

> [!NOTE]
> Visual Studio, Windows kapsayıcılarıyla hata ayıklama yapmadan çalıştırdığınızda stdout ve stderr'ı otomatik olarak **Çıkış** penceresine yönlendirir, bu nedenle **Ctrl**+**F5** kullanarak Visual Studio'dan başlayan Windows kapsayıcıları bu sekmede günlükleri görüntülemez; bunun yerine **Çıktı** penceresini kullanın.

## <a name="view-the-filesystem"></a>Dosya sistemini görüntüleme

**Dosyalar** sekmesinde, projenizi içeren uygulama klasörü de dahil olmak üzere kapsayıcının dosya sistemini görüntüleyebilirsiniz.

![Kapsayıcılar penceresindeki Dosyalar sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/container-filesystem.png)

Visual Studio'da dosyaları açmak için dosyaya göz atın ve çift tıklayın veya sağ tıklayın ve **Aç'ı**seçin. Visual Studio dosyaları salt okunur modunda açar.

![Visual Studio'da görüntülenmek için açık olan dosyanın ekran görüntüsü](media/view-and-diagnose-containers/container-file-open.png)

**Dosyalar** sekmesini kullanarak, kapsayıcınızın dosya sisteminde IIS günlükleri, yapılandırma dosyaları ve diğer içerik dosyaları gibi uygulama günlüklerini görüntüleyebilirsiniz.

## <a name="start-stop-and-remove-containers"></a>Kapsayıcıları başlatın, durdurun ve kaldırın

Varsayılan olarak, **Kapsayıcılar** penceresi Docker'ın yönettiği makinedeki tüm kapsayıcıları gösterir. Artık istemediğiniz bir kapsayıcıyı başlatmak, durdurmak veya kaldırmak (silmek) için araç çubuğu düğmelerini kullanabilirsiniz.  Kapsayıcılar oluşturuldukça veya kaldırıldıkça bu liste dinamik olarak güncelleştirilir.

## <a name="open-a-terminal-window-in-a-running-container"></a>Çalışan bir kapsayıcıda terminal penceresi açma

**Kapsayıcı** penceresindeki **Terminal Penceresini Aç** düğmesini kullanarak kapsayıcıda bir terminal penceresi (komut istemi veya etkileşimli kabuk) açabilirsiniz.

![Kapsayıcılar penceresindeki Terminal Penceresini Aç ekran görüntüsü](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Windows kapsayıcıları için Windows komut istemi açılır. Linux kapsayıcıları için, bash kabuğunu kullanarak bir pencere açar.

![Bash penceresinin ekran görüntüsü](media/view-and-diagnose-containers/container-bash-window.png)

Normalde terminal penceresi Visual Studio'nun dışında ayrı bir pencere olarak açılır. Visual Studio IDE'ye takılabilir araç penceresi olarak entegre edilmiş bir komut satırı ortamı istiyorsanız, [Whack Whack Terminali'ni](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)yükleyebilirsiniz.

## <a name="attach-the-debugger-to-a-process"></a>Hata ayıklama işlemine ekleme

Kapsayıcılar penceresi araç çubuğundaki **İşleme Ekle** düğmesini kullanarak hata ayıklama işlemini kapsayıcıda çalışan bir işleme ekleyebilirsiniz. Bu düğmeyi kullandığınızda, **İşleme Ekle** iletişim kutusu görüntülenir ve kapsayıcıda çalışan kullanılabilir işlemleri gösterir.  

![İşleme Ekle iletişim kutusunun ekran görüntüsü](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Kapsayıcıda yönetilen işlemlere ekleyebilirsiniz. Başka bir kapsayıcıda işlem aramak için **Bul** düğmesini kullanın ve **Docker Kapsayıcıseç** iletişim kutusunda başka bir kapsayıcı seçin.

## <a name="viewing-images"></a>Görüntüleri görüntüleme

**Kapsayıcılar** penceresindeki **Görüntüler** sekmesini kullanarak görüntüleri yerel makinede de görüntüleyebilirsiniz. Dış depolardan çekilen görüntüler bir ağaç görünümünde gruplandırılır. Görüntünün ayrıntılarını incelemek için bir resim seçin.

Görüntüyü kaldırmak için, ağaç görünümündeki resme sağ tıklayın ve **Kaldır'ı**seçin veya resmi seçin ve araç çubuğundaki **Kaldır** düğmesini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

[Konteyner Araçlarına Genel Bakış'ı](overview.md)okuyarak Visual Studio'da bulunan Konteyner Araçları hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'da Konteyner Geliştirme](/visualstudio/containers)

[Visual Studio için Uzantıları Marketplace](https://marketplace.visualstudio.com/)
