---
title: Kapsayıcılar penceresini Visual Studio
description: Ortam değişkenlerini, dosyaları, günlükleri, bağlantı noktalarını ve daha fazla kapsayıcıyı ve yerel olarak kullanılabilir Docker görüntülerini görmek için Kapsayıcılar araç penceresini kullanarak Visual Studio'de kapsayıcı tabanlı uygulamalarınızı hata ayıklama ve tanılama becerinizi geliştirmeyi açıklar.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 10/27/2021
ms.technology: vs-container-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: 0170d7e1e84cb5d2a6e37eca271866187f599d58
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002087"
---
# <a name="use-the-containers-window"></a>Kapsayıcılar penceresini kullanma

Kapsayıcılar penceresini kullanarak, uygulamanızı barındıran kapsayıcıların içinde neler olduğunu **görüntüebilirsiniz.** Kapsayıcılarınızı görüntülemek ve tanılamak için Docker komutlarını çalıştırmak için komut istemini kullanmaya alışırsanız bu pencere, kapsayıcılarınızı IDE'den ayrılmadan izlemenin daha kolay bir Visual Studio sağlar.

Kapsayıcılar penceresini kullanarak kapsayıcı görüntüleriyle ilgili bilgileri de **görüntüebilirsiniz.**

## <a name="prerequisites"></a>Önkoşullar

:::moniker range="vs-2019"

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 sürüm 16.4 veya](https://visualstudio.microsoft.com/downloads) sonraki bir sürümü.
:::moniker-end
:::moniker range=">=vs-2022"
- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2022](https://visualstudio.microsoft.com/downloads) veya [Visual Studio 2019 sürüm 16.4](https://visualstudio.microsoft.com/downloads) veya sonrası.

:::moniker-end

## <a name="view-information-about-your-containers"></a>Kapsayıcılar hakkında bilgileri görüntüleme

**Kapsayıcılı** bir .NET projesi başlatarak Kapsayıcılar penceresi otomatik olarak açılır. Kapsayıcılarınızı istediğiniz zaman Visual Studio görüntülemek için **Ctrl** Q tuşlarını kullanarak Visual Studio Arama kutusunu etkinleştirin ve ilk öğeyi yazın +  `Containers` ve seçin. Ana menüden **Kapsayıcılar** penceresini de açabilirsiniz. Diğer Kapsayıcıları Görüntüle **menü**  >  **yolunu Windows**  >  **kullanın.**  

:::moniker range="vs-2019"
![Sol bölmede bir kapsayıcının Visual Studio ve sağ bölmede Ortam sekmesinin seçili olduğu Kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/container-window.png)
:::moniker-end
:::moniker range="vs-2022"
![Sol bölmede bir kapsayıcının Visual Studio ve sağ bölmede Ortam sekmesinin seçili olduğu Kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/container-tools-window.png)
:::moniker-end

Sol tarafta yerel makinenizin kapsayıcı listesini görüyorsunuz. Çözümünüzle ilişkili kapsayıcılar Çözüm Kapsayıcıları **altında gösterilir.** Sağ bölmede Ortam, **Etiketler,** Bağlantı **Noktaları,** **Birimler,** Günlükler ve Dosyalar **sekmelerini** **içeren** bir bölme **görüntülenir.**

> [!TIP]
> Kapsayıcılar araç penceresinin **depolamaya** yerleştirildiklerini kolayca Visual Studio. Bkz. [Visual Studio. .](../ide/customizing-window-layouts-in-visual-studio.md) Varsayılan olarak, **hata ayıklayıcı** çalıştırıldıklarında **Kapsayıcılar** penceresi İzleme penceresiyle birlikte yerleştirildi.

## <a name="view-environment-variables"></a>Ortam değişkenlerini görüntüleme

Ortam **sekmesi** kapsayıcıda ortam değişkenlerini gösterir. Uygulama kapsayıcısı için bu değişkenleri dockerfile içinde, bir .env dosyasında veya docker komutu kullanarak bir kapsayıcıyı başlatmanız için -e seçeneğini kullanarak birçok şekilde ayarlayın.

:::moniker range="vs-2019"
![Kapsayıcılar penceresinin ekran Visual Studio kapsayıcının Ortam değişkenlerini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/containers-environment-vars.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresinin ekran Visual Studio kapsayıcının Ortam değişkenlerini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-environment-variables.png)
:::moniker-end
> [!NOTE]
> Ortam değişkenlerinin herhangi bir değişikliği gerçek zamanlı olarak yansıtılamamaktadır. Ayrıca, bu sekmede ortam değişkenleri kapsayıcının sistem ortam değişkenleridir ve uygulamaya yerel kullanıcı ortam değişkenlerini yansıtmaz.

## <a name="view-labels"></a>Etiketleri görüntüleme

Etiketler **sekmesi** kapsayıcının etiketlerini gösterir. Etiketler, Docker nesnelerinde özel meta verileri ayarlamanın bir yolutur. Bazı etiketler, otomatik olarak Visual Studio.

:::moniker range="vs-2019"
![Etiketler sekmesini gösteren kapsayıcılar Visual Studio ekran görüntüsü.](media/view-and-diagnose-containers/containers-labels.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Etiketler sekmesini gösteren kapsayıcılar Visual Studio ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-labels.png)
:::moniker-end

## <a name="view-port-mappings"></a>Bağlantı noktası eşlemelerini görüntüleme

Bağlantı **Noktaları** sekmesinde, kapsayıcınız için geçerli olan bağlantı noktası eşlemelerini kontrol edin.

:::moniker range="vs-2019"
![Kapsayıcılar penceresindeki Bağlantı Noktaları sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/containers-ports.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresindeki Bağlantı Noktaları sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-ports.png)
:::moniker-end
İyi bilinen bağlantı noktaları birbirine bağlıdır, bu nedenle bağlantı noktası üzerinde kullanılabilir içerik varsa bağlantıya tıklayarak tarayıcıyı açabilirsiniz.

## <a name="view-volumes"></a>Birimleri görüntüleme

Birimler **sekmesi** kapsayıcı üzerindeki birimleri (bağlı dosya sistemi düğümleri) gösterir.

:::moniker range="vs-2019"
![Kapsayıcılar penceresindeki Birimler sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/containers-volumes.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresindeki Birimler sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-volumes.png)
:::moniker-end

## <a name="view-logs"></a>Günlükleri görüntüleme

**Günlükler** sekmesi komutun sonuçlarını `docker logs` gösterir. Varsayılan olarak, sekme kapsayıcıda stdout ve stderr akışlarını gösterir, ancak çıkışı yapılandırabilirsiniz. Ayrıntılar için bkz. [Docker günlüğü.](https://docs.docker.com/config/containers/logging/)  Varsayılan olarak, **Günlükler** sekmesi günlüklerin akışını sağlar, ancak sekmede Durdur düğmesini seçerek **bunu** devre dışı abilirsiniz.

:::moniker range="vs-2019"
![Kapsayıcılar penceresindeki Günlükler sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/containers-logs.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresindeki Günlükler sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-logs.png)
:::moniker-end

Günlükleri temizlemek için Günlükler **sekmesindeki** Temizle **düğmesini** kullanın.  Tüm günlükleri almak için Yenile **düğmesini** kullanın.

> [!NOTE]
> Visual Studio, Windows kapsayıcılarında hata ayıklama yapmadan çalıştırarak  stdout ve stderr'i otomatik olarak Çıkış penceresine yeniden yönlendiriyor. Bu **nedenle, Visual Studio'den Ctrl** + **F5** kullanarak başlayan Windows kapsayıcıları bu sekmede günlükleri görüntülemez; bunun yerine Çıkış penceresini kullanın. 

## <a name="view-the-filesystem"></a>Dosya sistemi görüntüleme

Dosyalar **sekmesinde,** projenizi içeren uygulama klasörü de dahil olmak üzere kapsayıcının dosya sistemi görüntüleyebilirsiniz.

:::moniker range="vs-2019"
![Kapsayıcılar penceresindeki Dosyalar sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/container-filesystem.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresindeki Dosyalar sekmesinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-files.png)
:::moniker-end

Dosyaları dosya Visual Studio, dosyaya göz atarak çift tıklayın veya sağ tıklar ve Aç'ı **seçin.** Visual Studio salt okunur modda açılır.

:::moniker range="vs-2019"
![Dosyanın açık olduğu dosyanın ekran görüntüsü Visual Studio.](media/view-and-diagnose-containers/container-file-open.png)
:::moniker-end
:::moniker range="vs-2022"
![Dosyanın açık olduğu dosyanın ekran görüntüsü Visual Studio.](media/view-and-diagnose-containers/vs-2022/container-file-open.png)
:::moniker-end

Dosyalar **sekmesini** kullanarak, kapsayıcının dosya sisteminde IIS günlükleri, yapılandırma dosyaları ve diğer içerik dosyaları gibi uygulama günlüklerini görüntüleyebilirsiniz.

## <a name="start-stop-and-remove-containers"></a>Kapsayıcıları başlatma, durdurma ve kaldırma

Varsayılan olarak, **Kapsayıcılar penceresi** Docker'ın yönettir olduğu makinede tüm kapsayıcıları gösterir. Araç çubuğu düğmelerini kullanarak artık istediğiniz kapsayıcıyı başlatabilir, durdurabilir veya kaldırabilirsiniz (silebilirsiniz).  Kapsayıcılar oluşturuldukça veya kaldırıldıkça bu liste dinamik olarak güncelleştirilir.

Birden çok kapsayıcı seçmek için örneğin, aynı anda birden fazla kapsayıcıyı kaldırmak için **Ctrl tuşunu basılı tutarak tıklayın.** 10'dan fazla kapsayıcı başlatmayı denersiniz, bunu onaylamanız istenir. İsterseniz onay istemini devre dışı abilirsiniz.

## <a name="open-a-terminal-window-in-a-running-container"></a>Çalışan kapsayıcıda terminal penceresi açma

Kapsayıcı penceresindeki Terminal Penceresini Aç düğmesini kullanarak kapsayıcıda bir **terminal** penceresi (komut istemi veya etkileşimli kabuk) **açabilirsiniz.**

:::moniker range="vs-2019"
![Kapsayıcılar penceresindeKi Terminal Penceresini Aç'ın ekran görüntüsü.](media/view-and-diagnose-containers/containers-open-terminal-window.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresindeKi Terminal Penceresini Aç'ın ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-open-terminal-window.png)
:::moniker-end

Kapsayıcıları Windows için Windows istemi açılır. Linux kapsayıcıları için bash kabuğunu kullanarak bir pencere açar.

:::moniker range="vs-2019"
![Bash penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/container-bash-window.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Bash penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/container-bash-window.png)
:::moniker-end

Normalde terminal penceresi, ayrı bir Visual Studio dışında açılır. Visual Studio IDE'ye yerleştirilebilir bir araç penceresi olarak tümleştirilmiş bir komut satırı ortamına sahip olmak için, [Sıra Terminali'ni yükleyebilirsiniz.](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)

## <a name="attach-the-debugger-to-a-process"></a>Hata ayıklayıcıyı bir işleme ekleme

Kapsayıcılar penceresi araç çubuğundaki İşleme Ekle düğmesini kullanarak  hata ayıklayıcıyı kapsayıcıda çalışan bir işleme ekleyebilirsiniz. Bu düğmeyi kullanırken İşleme **Ekle** iletişim kutusu görünür ve kapsayıcıda çalışan kullanılabilir işlemleri gösterir.  

:::moniker range="vs-2019"
![İşleme Ekle iletişim kutusunun ekran görüntüsü.](media/view-and-diagnose-containers/containers-attach-to-process.jpg)
:::moniker-end
:::moniker range=">=vs-2022"
![İşleme Ekle iletişim kutusunun ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-attach-to-process.png)
:::moniker-end

Kapsayıcıda yönetilen işlemlere iliştirin. Başka bir kapsayıcıda işlem bulmak için Bul düğmesini **kullanın** ve **Docker** Kapsayıcısı Seç iletişim kutusunda başka bir kapsayıcı seçin.

## <a name="viewing-images"></a>Görüntüleri görüntüleme

Kapsayıcılar penceresindeki Görüntüler sekmesini kullanarak da **görüntüleri** yerel makinede **görüntüleyebilirsiniz.** Dış depolardan çekilen görüntüler ağaç görünümü içinde birlikte gruplandı.

:::moniker range="vs-2019"
![Kapsayıcı görüntülerini gösteren Kapsayıcılar penceresini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/containers-images.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcı görüntülerini gösteren Kapsayıcılar penceresini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-images-labels.png)
:::moniker-end

Pencerede yalnızca görüntüler için geçerli olan sekmeler vardır: **Etiketler ve** **Ayrıntılar.** Ayrıntılar **sekmesi,** görüntünün yapılandırma ayrıntılarını JSON biçiminde gösterir.

:::moniker range="vs-2019"
![Kapsayıcılar penceresinin > Görüntüler ve Ayrıntılar sekmesini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/containers-images-details.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Kapsayıcılar penceresinin > Görüntüler ve Ayrıntılar sekmesini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-images-details.png)
:::moniker-end

Bir görüntüyü kaldırmak için ağaç görünümde görüntüye sağ tıklayın ve Kaldır'ı seçin veya görüntüyü seçin ve araç **çubuğundaki Kaldır** düğmesini kullanın.

## <a name="prune-containers-and-images"></a>Kapsayıcıları ve görüntüleri ayıklama

Kapsayıcılar penceresi araç çubuğundaki Ayıklama düğmesini kullanarak artık kullanmamanız **durumdaki** kapsayıcıları ve **görüntüleri kolayca** kaldırabilirsiniz.

:::moniker range="vs-2019"
![Ayıkla düğmesini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/container-window-prune.png)
:::moniker-end
:::moniker range=">=vs-2022"
![Ayıkla düğmesini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/vs-2022/containers-prune.png)
:::moniker-end

Kullanılmayan kapsayıcılarınızın tümünü kaldırmak istediğinizi onaylamanız istenir.

**Görüntüler** sekmesi **seçildiğinde, tüm** salgze görüntülerini kaldırmak isteyip istemediğinizi sorar. Salgze görüntüleri, artık etiketli bir görüntüyle ilişkili olmayan katmanların görüntüleridir. Bunların kaldırılması, disk alanının korunmasına yardımcı olur.

## <a name="configuration-options"></a>Yapılandırma seçenekleri

Kapsayıcıları ve görüntüleri kaldırma veya aynı anda 10 ' dan fazla kapsayıcı başlatma gibi çeşitli görevler için onay iletişim kutuları yapılandırılabilir. İletişim kutusunda onay kutusunu kullanarak her bir istemi devre dışı bırakabilirsiniz. Ayrıca, **Araçlar**  >  **Seçenekler**  >  **kapsayıcı araç**  >  **kapsayıcıları araç penceresinde** ayarlar ' da bu seçenekleri etkinleştirebilir veya devre dışı bırakabilirsiniz. Bkz. [kapsayıcı araçlarını yapılandırma](container-tools-configure.md).

## <a name="next-steps"></a>Sonraki adımlar

[kapsayıcı araçlarına genel bakış ' ı](overview.md)okuyarak Visual Studio bulunan kapsayıcı araçları hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio 'da kapsayıcı geliştirme](./index.yml)
