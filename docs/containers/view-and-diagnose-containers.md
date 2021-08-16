---
title: Docker kapsayıcılarını ve görüntülerini görüntüleme ve tanılama
description: Uygulamalarınızı barındıran kapsayıcıların içinde neler olduğunu görmek için bir araç penceresi kullanarak Visual Studio tabanlı uygulamalarınızı hata ayıklama ve tanılama becerinizi geliştirmeyi açıklar.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-container-tools
monikerRange: vs-2019
ms.openlocfilehash: 1895f67ae9ecb6bbad992ebbd891f326ec92aa52ae74a7d933f2d7a3127f9b9b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363611"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Visual Studio'da kapsayıcıları ve görüntüleri görüntüleme ve tanılama

Kapsayıcılar penceresini kullanarak, uygulamanızı barındıran kapsayıcıların içinde neler olduğunu **görüntüebilirsiniz.** Kapsayıcılarınızı görüntülemek ve tanılamak için Docker komutlarını çalıştırmak için komut istemini kullanmaya alışırsanız bu pencere, kapsayıcılarınızı IDE'den ayrılmadan izlemenin daha kolay bir Visual Studio sağlar.

## <a name="prerequisites"></a>Önkoşullar

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 sürüm 16.4 Preview 2](https://visualstudio.microsoft.com/downloads) veya sonraki bir sürümü kullanıyorsanız veya Visual Studio 2019'un önceki bir sürümünü kullanıyorsanız Kapsayıcılar pencere [uzantısını yükleyin.](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions)

## <a name="view-information-about-your-containers"></a>Kapsayıcılar hakkında bilgileri görüntüleme

**Kapsayıcılı** bir .NET projesi başlatarak Kapsayıcılar penceresi otomatik olarak açılır. Kapsayıcılarınızı istediğiniz zaman Visual Studio görüntülemek için **Ctrl** Q tuşlarını kullanarak Visual Studio Arama kutusunu etkinleştirin ve ilk öğeyi yazın +  `Containers` ve seçin. Ana menüden **Kapsayıcılar** penceresini de açabilirsiniz. Diğer Kapsayıcıları Görüntüle **menü**  >  **yolunu Windows**  >  **kullanın.**  

![Sol bölmede bir kapsayıcının Visual Studio ve sağ bölmede Ortam sekmesinin seçili olduğu Kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/container-window.png)

Sol tarafta yerel makinenizin kapsayıcı listesini görüyorsunuz. Çözümünüzle ilişkili kapsayıcılar Çözüm Kapsayıcıları **altında gösterilir.** Sağ bölmede Ortam, Bağlantı **Noktaları,** Günlükler ve **Dosyalar** **sekmeleri** **bulunur.**

> [!TIP]
> Kapsayıcılar araç **penceresinin, Kapsayıcılar** araç penceresinin bulunduğu yeri kolayca Visual Studio. Bkz. [Visual Studio'de pencere düzenlerini özelleştirme.](../ide/customizing-window-layouts-in-visual-studio.md) Varsayılan olarak, **hata ayıklayıcı** çalıştırıldıklarında **Kapsayıcılar** penceresi İzleme penceresiyle birlikte yerleştirildi.

## <a name="view-environment-variables"></a>Ortam değişkenlerini görüntüleme

Ortam **sekmesi** kapsayıcıda ortam değişkenlerini gösterir. Uygulama kapsayıcısı için bu değişkenleri dockerfile içinde, bir .env dosyasında veya docker komutu kullanarak bir kapsayıcıyı başlatmanız için -e seçeneğini kullanarak birçok şekilde ayarlayın.

![WebApplication11 kapsayıcı Visual Studio sı için Ortam değişkenlerini gösteren kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Ortam değişkenlerinin herhangi bir değişikliği gerçek zamanlı olarak yansıt yansıtıcı değildir. Ayrıca, bu sekmede yer alan ortam değişkenleri kapsayıcının sistem ortamı değişkenleridir ve uygulamaya yerel kullanıcı ortam değişkenlerini yansıtmaz.

## <a name="view-port-mappings"></a>Bağlantı noktası eşlemelerini görüntüleme

Bağlantı **Noktaları** sekmesinde, kapsayıcınız için geçerli olan bağlantı noktası eşlemelerini kontrol edin.

![Kapsayıcılar penceresindeki Bağlantı Noktaları sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-ports.png)

İyi bilinen bağlantı noktaları birbirine bağlıdır, bu nedenle bağlantı noktası üzerinde kullanılabilir içerik varsa bağlantıya tıklayarak tarayıcıyı açabilirsiniz.

## <a name="view-logs"></a>Günlükleri görüntüleme

**Günlükler** sekmesi komutun sonuçlarını `docker logs` gösterir. Varsayılan olarak, sekme kapsayıcıda stdout ve stderr akışlarını gösterir, ancak çıkışı yapılandırabilirsiniz. Ayrıntılar için bkz. [Docker günlüğü.](https://docs.docker.com/config/containers/logging/)  Varsayılan olarak, **Günlükler** sekmesi günlüklerin akışını sağlar, ancak sekmede Durdur düğmesini seçerek **bunu** devre dışı abilirsiniz.

![Kapsayıcılar penceresindeki Günlükler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-logs.png)

Günlükleri temizlemek için Günlükler **sekmesindeki** Temizle **düğmesini** kullanın.  Tüm günlükleri almak için Yenile **düğmesini** kullanın.

> [!NOTE]
> Visual Studio, Windows kapsayıcılarında hata ayıklama yapmadan çalıştırarak stdout ve stderr'i otomatik olarak Çıkış penceresine yeniden yönlendiriyor. Bu **nedenle, Visual Studio'den Ctrl**  + **F5** kullanarak başlayan Windows kapsayıcıları bu sekmede günlükleri görüntülemez; bunun yerine Çıkış penceresini kullanın. 

## <a name="view-the-filesystem"></a>Dosya sistemi görüntüleme

Dosyalar **sekmesinde,** projenizi içeren uygulama klasörü de dahil olmak üzere kapsayıcının dosya sistemi görüntüleyebilirsiniz.

![Kapsayıcılar penceresindeki Dosyalar sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/container-filesystem.png)

Dosyaları dosya Visual Studio, dosyaya göz atarak çift tıklayın veya sağ tıklar ve Aç'ı **seçin.** Visual Studio salt okunur modda açılır.

![Dosyanın açık olduğu dosyanın ekran görüntüsü Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Dosyalar **sekmesini** kullanarak, kapsayıcının dosya sisteminde IIS günlükleri, yapılandırma dosyaları ve diğer içerik dosyaları gibi uygulama günlüklerini görüntüleyebilirsiniz.

## <a name="start-stop-and-remove-containers"></a>Kapsayıcıları başlatma, durdurma ve kaldırma

Varsayılan olarak, **Kapsayıcılar penceresi** Docker'ın yönettir olduğu makinede tüm kapsayıcıları gösterir. Araç çubuğu düğmelerini kullanarak artık istediğiniz kapsayıcıyı başlatabilir, durdurabilir veya kaldırabilirsiniz (silebilirsiniz).  Kapsayıcılar oluşturuldukça veya kaldırıldıkça bu liste dinamik olarak güncelleştirilir.

## <a name="open-a-terminal-window-in-a-running-container"></a>Çalışan kapsayıcıda terminal penceresi açma

Kapsayıcı penceresindeki Terminal Penceresini Aç düğmesini kullanarak kapsayıcıda bir **terminal** penceresi (komut istemi veya etkileşimli kabuk) **açabilirsiniz.**

![Kapsayıcılar penceresinde Terminal Penceresini Açma ekran görüntüsü](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Kapsayıcıları Windows için Windows istemi açılır. Linux kapsayıcıları için bash kabuğunu kullanarak bir pencere açar.

![Bash penceresinin ekran görüntüsü](media/view-and-diagnose-containers/container-bash-window.png)

Normalde terminal penceresi, ayrı bir Visual Studio dışında açılır. Visual Studio IDE'ye yerleştirilebilir bir araç penceresi olarak tümleştirilmiş bir komut satırı ortamına sahip olmak için, [Terminal Terminali'ni yükleyebilirsiniz.](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)

## <a name="attach-the-debugger-to-a-process"></a>Hata ayıklayıcıyı bir işleme ekleme

Kapsayıcılar penceresi araç çubuğundaki İşleme Ekle düğmesini kullanarak hata ayıklayıcıyı kapsayıcıda **çalışan** bir işleme ekleyebilirsiniz. Bu düğmeyi kullanırken İşleme **Ekle** iletişim kutusu görünür ve kapsayıcıda çalışan kullanılabilir işlemleri gösterir.  

![İşleme Ekle iletişim kutusunun ekran görüntüsü](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Kapsayıcıda yönetilen işlemlere iliştirin. Başka bir kapsayıcıda işlem bulmak için Bul düğmesini **kullanın** ve **Docker** Kapsayıcısı Seç iletişim kutusunda başka bir kapsayıcı seçin.

## <a name="viewing-images"></a>Görüntüleri görüntüleme

Kapsayıcılar penceresindeki Görüntüler sekmesini kullanarak da **görüntüleri** yerel makinede **görüntüleyebilirsiniz.** Dış depolardan çekilen görüntüler ağaç görünümü içinde birlikte gruplandı. Görüntünün ayrıntılarını incelemek için bir görüntü seçin.

Bir görüntüyü kaldırmak için ağaç görünümde görüntüye sağ tıklayın ve Kaldır'ı seçin veya görüntüyü seçin ve araç **çubuğundaki Kaldır** düğmesini kullanın.

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcı Araçlarına Genel Bakış'Visual Studio'da bulunan Kapsayıcı Araçları hakkında [daha fazla bilgi edinebilirsiniz.](overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'de Kapsayıcı Geliştirme](./index.yml)

[Visual Studio için Uzantılar Marketi](https://marketplace.visualstudio.com/)