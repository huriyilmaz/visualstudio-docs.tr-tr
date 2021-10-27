---
title: Kapsayıcılar penceresini Visual Studio
description: Ortam değişkenlerini, dosyaları, günlükleri, bağlantı noktalarını ve daha fazla kapsayıcıyı ve yerel olarak kullanılabilir Docker görüntülerini görmek için Kapsayıcılar araç penceresini kullanarak Visual Studio'de kapsayıcı tabanlı uygulamalarınızı ayıklama ve tanılama becerinizi geliştirmeyi açıklar.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-container-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: f33f0e86fff98d670d964766fcbedfca319b1780
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350800"
---
# <a name="use-the-containers-window"></a>Kapsayıcılar penceresini kullanma

Kapsayıcılar penceresini kullanarak, uygulamanızı barındıran kapsayıcıların içinde neler olduğunu **görüntüebilirsiniz.** Kapsayıcılarınızı görüntülemek ve tanılamak için Docker komutlarını çalıştırmak için komut istemini kullanmaya alışırsanız bu pencere, kapsayıcılarınızı IDE'den ayrılmadan izlemenin daha kolay bir Visual Studio sağlar.

Kapsayıcılar penceresini kullanarak kapsayıcı görüntüleriyle ilgili bilgileri de **görüntüebilirsiniz.**

## <a name="prerequisites"></a>Önkoşullar

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 sürüm 16.4 veya](https://visualstudio.microsoft.com/downloads) sonraki bir sürümü.

## <a name="view-information-about-your-containers"></a>Kapsayıcılar hakkında bilgileri görüntüleme

**Kapsayıcılı** bir .NET projesi başlatarak Kapsayıcılar penceresi otomatik olarak açılır. Kapsayıcılarınızı istediğiniz zaman Visual Studio görüntülemek için **Ctrl** Q tuşlarını kullanarak Visual Studio Arama kutusunu etkinleştirin ve ilk öğeyi yazın +  `Containers` ve seçin. Ana menüden **Kapsayıcılar** penceresini de açabilirsiniz. Diğer Kapsayıcıları Görüntüle **menü**  >  **yolunu Windows**  >  **kullanın.**  

![Sol bölmede bir kapsayıcının Visual Studio ve sağ bölmede Ortam sekmesinin seçili olduğu Kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/container-window.png)

Sol tarafta yerel makinenizin kapsayıcı listesini görüyorsunuz. Çözümünüzle ilişkili kapsayıcılar Çözüm Kapsayıcıları **altında gösterilir.** Sağ bölmede Ortam, **Etiketler,** Bağlantı **Noktaları,** **Birimler,** Günlükler ve Dosyalar **sekmelerini** **içeren** bir bölme **görüntülenir.**

> [!TIP]
> Kapsayıcılar araç **penceresinin, Kapsayıcılar** araç penceresinin bulunduğu yeri kolayca Visual Studio. Bkz. ['de pencere düzenlerini Visual Studio.](../ide/customizing-window-layouts-in-visual-studio.md) Varsayılan olarak, **hata ayıklayıcı** çalıştırıldıklarında **Kapsayıcılar** penceresi İzleme penceresiyle birlikte yerleştirildi.

## <a name="view-environment-variables"></a>Ortam değişkenlerini görüntüleme

Ortam **sekmesi** kapsayıcıda ortam değişkenlerini gösterir. Uygulama kapsayıcısı için bu değişkenleri dockerfile içinde, bir .env dosyasında veya docker komutu kullanarak bir kapsayıcıyı başlatmanız için -e seçeneğini kullanarak birçok şekilde ayarlayın.

![Kapsayıcılar penceresinin ekran Visual Studio kapsayıcının Ortam değişkenlerini gösteren ekran görüntüsü.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Ortam değişkenlerinin herhangi bir değişikliği gerçek zamanlı olarak yansıt yansıtıcı değildir. Ayrıca, bu sekmede yer alan ortam değişkenleri kapsayıcının sistem ortamı değişkenleridir ve uygulamaya yerel kullanıcı ortam değişkenlerini yansıtmaz.

## <a name="view-labels"></a>Etiketleri görüntüleme

Etiketler **sekmesi** kapsayıcının etiketlerini gösterir. Etiketler, Docker nesnelerinde özel meta verileri ayarlamanın bir yolutur. Bazı etiketler, otomatik olarak Visual Studio.

![Etiketler sekmesini gösteren kapsayıcılar Visual Studio penceresinin ekran görüntüsü](media/view-and-diagnose-containers/containers-labels.png)

## <a name="view-port-mappings"></a>Bağlantı noktası eşlemelerini görüntüleme

Bağlantı **Noktaları** sekmesinde, kapsayıcınız için geçerli olan bağlantı noktası eşlemelerini kontrol edin.

![Kapsayıcılar penceresindeki Bağlantı Noktaları sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-ports.png)

İyi bilinen bağlantı noktaları birbirine bağlıdır, bu nedenle bağlantı noktası üzerinde kullanılabilir içerik varsa bağlantıya tıklayarak tarayıcıyı açabilirsiniz.

## <a name="view-volumes"></a>Birimleri görüntüleme

Birimler **sekmesinde** kapsayıcı üzerindeki birimler (bağlı dosya sistemi düğümleri) görüntülenir.

![Kapsayıcılar penceresinde birimler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-volumes.png)

## <a name="view-logs"></a>Günlükleri görüntüleme

**Günlükler** sekmesi komutun sonuçlarını `docker logs` gösterir. Varsayılan olarak, sekme kapsayıcıda stdout ve stderr akışlarını gösterir, ancak çıkışı yapılandırabilirsiniz. Ayrıntılar için bkz. [Docker günlüğü.](https://docs.docker.com/config/containers/logging/)  Varsayılan olarak, **Günlükler** sekmesi günlüklerin akışını sağlar, ancak sekmede Durdur düğmesini seçerek **bunu** devre dışı abilirsiniz.

![Kapsayıcılar penceresindeki Günlükler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-logs.png)

Günlükleri temizlemek için Günlükler **sekmesindeki** Temizle **düğmesini** kullanın.  Tüm günlükleri almak için Yenile **düğmesini** kullanın.

> [!NOTE]
> Visual Studio, Windows kapsayıcıları ile hata ayıklama olmadan  çalıştırarak stdout ve stderr'i otomatik olarak Çıkış penceresine yeniden yönlendiriyor Windows. Bu nedenle **Visual Studio'den Ctrl** + **F5** ile başlayan kapsayıcılar bu sekmede günlükleri görüntülemez; bunun yerine Çıkış penceresini kullanın. 

## <a name="view-the-filesystem"></a>Dosya sistemi görüntüleme

Dosyalar **sekmesinde,** projenizi içeren uygulama klasörü de dahil olmak üzere kapsayıcının dosya sistemi görüntüleyebilirsiniz.

![Kapsayıcılar penceresindeki Dosyalar sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/container-filesystem.png)

Dosyaları dosya Visual Studio, dosyaya göz atarak çift tıklayın veya sağ tıklar ve Aç'ı **seçin.** Visual Studio dosyaları salt okunur modda açar.

![Dosyanın açık olduğu dosyanın ekran görüntüsü Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Dosyalar **sekmesini** kullanarak, kapsayıcının dosya sisteminde IIS günlükleri, yapılandırma dosyaları ve diğer içerik dosyaları gibi uygulama günlüklerini görüntüleyebilirsiniz.

## <a name="start-stop-and-remove-containers"></a>Kapsayıcıları başlatma, durdurma ve kaldırma

Varsayılan olarak, **Kapsayıcılar penceresi** Docker'ın yönettir olduğu makinede tüm kapsayıcıları gösterir. Araç çubuğu düğmelerini kullanarak artık istediğiniz kapsayıcıyı başlatabilir, durdurabilir veya kaldırabilirsiniz (silebilirsiniz).  Kapsayıcılar oluşturuldukça veya kaldırıldıkça bu liste dinamik olarak güncelleştirilir.

Birden çok kapsayıcı seçmek için örneğin, aynı anda birden fazla kapsayıcıyı kaldırmak için **Ctrl tuşunu basılı tutarak tıklayın.** 10'dan fazla kapsayıcı başlatmayı denersiniz, bunu onaylamanız istenir. İsterseniz onay istemini devre dışı abilirsiniz.

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

Kapsayıcılar penceresindeki Görüntüler sekmesini kullanarak da **görüntüleri** yerel makinede **görüntüleyebilirsiniz.** Dış depolardan çekilen görüntüler ağaç görünümü içinde birlikte gruplandı.

![Kapsayıcı görüntülerini gösteren Kapsayıcılar penceresini gösteren ekran görüntüsü](media/view-and-diagnose-containers/containers-images.png)

Pencerede yalnızca görüntüler için geçerli olan sekmeler vardır: **Etiketler ve** **Ayrıntılar.** Ayrıntılar **sekmesi,** görüntünün yapılandırma ayrıntılarını JSON biçiminde gösterir.

![Kapsayıcılar penceresinin > Ayrıntılar sekmesini gösteren ekran görüntüsü](media/view-and-diagnose-containers/containers-images-details.png)

Bir görüntüyü kaldırmak için ağaç görünümde görüntüye sağ tıklayın ve Kaldır'ı seçin veya görüntüyü seçin ve araç **çubuğundaki Kaldır** düğmesini kullanın.

## <a name="prune-containers-and-images"></a>Kapsayıcıları ve görüntüleri ayıklama

Kapsayıcılar penceresi araç çubuğundaki Ayıklama düğmesini kullanarak artık kullanmamış **olduğunuz** kapsayıcıları ve **görüntüleri kolayca** kaldırabilirsiniz.

![Ayıklama düğmesini gösteren ekran görüntüsü](media/view-and-diagnose-containers/container-window-prune.png)

Kullanılmayan tüm kapsayıcılarınızı kaldırmak istediğinizden emin olmak istemeniz istensin.

Görüntüler **sekmesi** seçildiğinde, **Buda düğmesi** tüm dalgalı görüntüleri kaldırmak isterken sorar. Dalgalı görüntüler artık etiketli görüntüyle ilişkilendirilen katmanlardan oluşan görüntülerdir. Bunları kaldırmak bazen disk alanı tasarrufu sağlar.

## <a name="configuration-options"></a>Yapılandırma seçenekleri

Kapsayıcıları ve görüntüleri kaldırma veya aynı anda 10'dan fazla kapsayıcı başlatma gibi çeşitli görevler için onay iletişim kutuları yalıtabilirsiniz. İletişim kutusundaki onay kutusunu kullanarak her istemi devre dışı abilirsiniz. Araç Seçenekleri Kapsayıcı Araçları Kapsayıcıları Araç Penceresi'nde bulunan ayarları kullanarak da  >  **bu**  >  **seçenekleri etkinleştirebilirsiniz**  >  **veya devre dışı abilirsiniz.** Bkz. [Kapsayıcı Araçlarını Yapılandırma.](container-tools-configure.md)

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio'de bulunan Kapsayıcı Araçları hakkında daha fazla Visual Studio Için [Bkz. Kapsayıcı Araçlarına Genel Bakış.](overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'de Kapsayıcı Geliştirme](./index.yml)
