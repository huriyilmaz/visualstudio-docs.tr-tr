---
title: Visual Studio içindeki kapsayıcılar penceresini kullanın
description: ortam değişkenlerini, dosyaları, günlükleri, bağlantı noktalarını ve uygulamanızı barındıran kapsayıcıları ve yerel olarak kullanılabilir docker görüntülerini görmek için kapsayıcılar araç penceresini kullanarak Visual Studio kapsayıcı tabanlı uygulamalarınızı hata ayıklama ve tanılama olanağından nasıl iyileştirebileceğinizi açıklar.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-container-tools
monikerRange: vs-2019
ms.openlocfilehash: d6e4ce1e92afea971d02242c03595020d27c23e3
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096855"
---
# <a name="use-the-containers-window"></a>Kapsayıcılar penceresini kullanma

**Kapsayıcılar** penceresini kullanarak uygulamanızı barındıran kapsayıcılar içinde neler olduğunu görüntüleyebilirsiniz. kapsayıcılarınız ile neler olduğunu görüntülemek ve tanılamak için docker komutlarını çalıştırmak üzere komut istemi 'ni kullanmak üzere kullandıysanız, bu pencere, Visual Studio ıde 'den çıkmadan kapsayıcıları izlemek için daha uygun bir yol sağlar.

**Kapsayıcılar** penceresini kullanarak kapsayıcı görüntüleri hakkındaki bilgileri de görüntüleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 sürüm 16,4](https://visualstudio.microsoft.com/downloads) veya üzeri.

## <a name="view-information-about-your-containers"></a>Kapsayıcılarınız hakkındaki bilgileri görüntüleyin

Kapsayıcılı bir .NET projesi başlattığınızda **kapsayıcılar** penceresi otomatik olarak açılır. kapsayıcılarınızı dilediğiniz zaman Visual Studio görüntülemek için **Ctrl** + **Q** ' ı kullanarak Visual Studio arama kutusunu etkinleştirin ve `Containers` ilk öğeyi yazın ve seçin. Ayrıca, ana menüden **kapsayıcılar** penceresini açabilirsiniz. menü yolunu   >  **diğer Windows**  >  **kapsayıcılarını** göster ' i kullanın.  

![sol bölmede seçili bir kapsayıcıya ve sağ bölmede seçili ortam sekmesine sahip Visual Studio kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/container-window.png)

Sol tarafta, yerel makinenizde kapsayıcı listesini görürsünüz. Çözümünüz ile ilişkili kapsayıcılar **çözüm kapsayıcıları** altında gösterilir. Sağ tarafta, **ortam**, **Etiketler**, **bağlantı noktaları**, **birimler**, **Günlükler** ve **dosyalar** için sekmeler içeren bir bölme görürsünüz.

> [!TIP]
> **Kapsayıcılar** araç penceresinin Visual Studio nereye yerleştirildiğini kolayca özelleştirebilirsiniz. Bkz. [Visual Studio pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md). Varsayılan olarak, **kapsayıcı** penceresi, hata ayıklayıcı çalışırken **izleme** penceresiyle birlikte yerleştirilir.

## <a name="view-environment-variables"></a>Ortam değişkenlerini görüntüle

**Ortam** sekmesi, kapsayıcıdaki ortam değişkenlerini gösterir. Uygulamanızın kapsayıcısı için, bu değişkenleri birçok şekilde ayarlayabilirsiniz. Örneğin, Dockerfile, bir. env dosyası veya bir Docker komutu kullanarak bir kapsayıcı başlattığınızda-e seçeneğini kullanabilirsiniz.

![kapsayıcının ortam değişkenlerini gösteren Visual Studio kapsayıcılar penceresinin ekran görüntüsü.](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Ortam değişkenlerinde yapılan değişiklikler gerçek zamanlı olarak yansıtılmaz. Ayrıca, bu sekmedeki ortam değişkenleri, kapsayıcıdaki sistem ortam değişkenleridir ve yerel olarak, uygulamanın kullanıcı ortam değişkenlerini yansıtmaz.

## <a name="view-labels"></a>Etiketleri görüntüle

**Etiketler** sekmesi kapsayıcının etiketlerini gösterir. Etiketler, Docker nesnelerinde özel meta verileri ayarlamanın bir yoludur. Bazı Etiketler Visual Studio tarafından otomatik olarak ayarlanır.

![etiketler sekmesini gösteren Visual Studio kapsayıcılar penceresinin ekran görüntüsü](media/view-and-diagnose-containers/containers-labels.png)

## <a name="view-port-mappings"></a>Bağlantı noktası eşlemelerini görüntüle

**Bağlantı noktaları** sekmesinde, Kapsayıcınız için geçerli olan bağlantı noktası eşlemelerini kontrol edebilirsiniz.

![Kapsayıcılar penceresindeki bağlantı noktaları sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-ports.png)

İyi bilinen bağlantı noktaları bağlanır, bu nedenle bir bağlantı noktasında kullanılabilir içerik varsa, tarayıcıyı açmak için bağlantıya tıklayabilirsiniz.

## <a name="view-volumes"></a>Birimleri görüntüle

**Birimler** sekmesi, kapsayıcıdaki birimleri (bağlı dosya sistemi düğümleri) gösterir.

![Kapsayıcılar penceresindeki birimler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-volumes.png)

## <a name="view-logs"></a>Günlükleri görüntüleme

**Günlükler** sekmesi, komutun sonuçlarını gösterir `docker logs` . Varsayılan olarak, sekmesi bir kapsayıcıda stdout ve stderr akışlarını gösterir, ancak çıktıyı yapılandırabilirsiniz. Ayrıntılar için bkz. [Docker günlüğü](https://docs.docker.com/config/containers/logging/).  Varsayılan olarak, **Günlükler** sekmesi günlükleri akışlar, ancak sekmedeki **Durdur** düğmesini seçerek bunu devre dışı bırakabilirsiniz.

![Kapsayıcılar penceresindeki Günlükler sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/containers-logs.png)

Günlükleri temizlemek için **Günlükler** sekmesindeki **Temizle** düğmesini kullanın.  Tüm günlükleri almak için **Yenile** düğmesini kullanın.

> [!NOTE]
> Visual Studio, Windows kapsayıcılarıyla hata ayıklamadan çalıştırdığınızda stdout ve stderr 'yi **çıkış** penceresine otomatik olarak yönlendirir. bu nedenle, Visual Studio **Ctrl** F5 kullanılarak başlatılan Windows kapsayıcılar +  bu sekmede günlükleri göstermez; bunun yerine **çıkış** penceresini kullanın.

## <a name="view-the-filesystem"></a>Dosya sistemini görüntüleme

**Dosyalar** sekmesinde, projenizin bulunduğu uygulama klasörü de dahil olmak üzere kapsayıcının dosya sistemini görüntüleyebilirsiniz.

![Kapsayıcılar penceresindeki dosyalar sekmesinin ekran görüntüsü](media/view-and-diagnose-containers/container-filesystem.png)

Visual Studio dosyaları açmak için dosyaya gidin ve çift tıklayın ya da sağ tıklayıp **aç**' ı seçin. Visual Studio dosyaları salt okuma modunda açar.

![Visual Studio 'de görüntülenmek üzere açık dosyanın ekran görüntüsü](media/view-and-diagnose-containers/container-file-open.png)

**Dosyalar** sekmesini kullanarak, IIS günlükleri, yapılandırma dosyaları ve kapsayıcının dosya sisteminde bulunan diğer içerik dosyaları gibi uygulama günlüklerini görüntüleyebilirsiniz.

## <a name="start-stop-and-remove-containers"></a>Kapsayıcıları başlatma, durdurma ve kaldırma

**Kapsayıcılar** penceresinde, varsayılan olarak Docker 'ın yönettiği makinedeki tüm kapsayıcılar gösterilir. Artık istemediğiniz bir kapsayıcıyı başlatmak, durdurmak veya kaldırmak (silmek) için araç çubuğu düğmelerini kullanabilirsiniz.  Kapsayıcılar oluşturulduğu veya kaldırıldığı için bu liste dinamik olarak güncelleştirilir.

Birden çok kapsayıcıyı seçmek için örneğin, bir seferde birden fazla tane kaldırmak için **CTRL + tıklama** kullanın. 10 ' dan fazla kapsayıcıyı başlatmaya çalışırsanız, bunu onaylamanız istenir. İsterseniz onay istemi 'ni devre dışı bırakabilirsiniz.

## <a name="open-a-terminal-window-in-a-running-container"></a>Çalışan kapsayıcıda bir Terminal penceresi açın

**Kapsayıcı** penceresinde **Terminal penceresi aç** düğmesini kullanarak kapsayıcıda bir Terminal penceresi (komut istemi veya etkileşimli kabuk) açabilirsiniz.

![Kapsayıcılar penceresinde açık terminal penceresinin ekran görüntüsü](media/view-and-diagnose-containers/containers-open-terminal-window.png)

Windows kapsayıcılar için Windows komut istemi açılır. Linux kapsayıcıları için bash kabuğu kullanılarak bir pencere açılır.

![Bash penceresinin ekran görüntüsü](media/view-and-diagnose-containers/container-bash-window.png)

normalde, terminal penceresi Visual Studio dışında ayrı bir pencere olarak açılır. bir komut satırı ortamının Visual Studio ıde ile tümleşik bir araç penceresi olmasını istiyorsanız, [whack whack Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)' yi yükleyebilirsiniz.

## <a name="attach-the-debugger-to-a-process"></a>Hata ayıklayıcıyı bir işleme iliştir

Kapsayıcı penceresi araç çubuğundaki **Işleme İliştir** düğmesini kullanarak, hata ayıklayıcıyı kapsayıcıda çalışan bir işleme ekleyebilirsiniz. Bu düğmeyi kullandığınızda, **Işleme İliştir** iletişim kutusu görünür ve kapsayıcıda çalışan kullanılabilir işlemleri gösterir.  

![Işleme Iliştir iletişim kutusunun ekran görüntüsü](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Kapsayıcıda yönetilen işlemlere iliştirebilirsiniz. Başka bir kapsayıcıdaki bir işlemi aramak için **bul** düğmesini kullanın ve **Docker kapsayıcısını Seç** iletişim kutusunda başka bir kapsayıcı seçin.

## <a name="viewing-images"></a>Görüntüleri görüntüleme

Ayrıca, **kapsayıcılar** penceresindeki **görüntüler** sekmesini kullanarak yerel makinedeki görüntüleri görüntüleyebilirsiniz. Dış depolardan çekilen görüntüler bir TreeView içinde birlikte gruplandırılır.

![Kapsayıcı görüntülerini gösteren kapsayıcılar penceresini gösteren ekran görüntüsü](media/view-and-diagnose-containers/containers-images.png)

Pencerede yalnızca görüntüler için geçerli olan sekmeler vardır: **Etiketler** ve **Ayrıntılar**. **Ayrıntılar** SEKMESI, JSON biçimindeki görüntünün yapılandırma ayrıntılarını gösterir.

![Kapsayıcılar penceresinin görüntüler > Ayrıntılar sekmesini gösteren ekran görüntüsü](media/view-and-diagnose-containers/containers-images-details.png)

Bir görüntüyü kaldırmak için TreeView 'daki görüntüye sağ tıklayın ve **Kaldır**' ı seçin veya görüntüyü seçin ve araç çubuğundaki **Kaldır** düğmesini kullanın.

## <a name="prune-containers-and-images"></a>Kapsayıcıları ve görüntüleri Ayıkla

**Kapsayıcılar** penceresi araç çubuğunda **Ayıkla** düğmesini kullanarak, artık kullanmadığınız kapsayıcıları ve görüntüleri kolayca kaldırabilirsiniz.

![Ayıkla düğmesini gösteren ekran görüntüsü](media/view-and-diagnose-containers/container-window-prune.png)

Kullanılmayan kapsayıcılarınızın tümünü kaldırmak istediğinizi onaylamanız istenir.

**Görüntüler** sekmesi **seçildiğinde, tüm** salgze görüntülerini kaldırmak isteyip istemediğinizi sorar. Salgze görüntüleri, artık etiketli bir görüntüyle ilişkili olmayan katmanların görüntüleridir. Bunların kaldırılması, disk alanının korunmasına yardımcı olur.

## <a name="configuration-options"></a>Yapılandırma seçenekleri

Kapsayıcıları ve görüntüleri kaldırma veya aynı anda 10 ' dan fazla kapsayıcı başlatma gibi çeşitli görevler için onay iletişim kutuları yapılandırılabilir. İletişim kutusunda onay kutusunu kullanarak her bir istemi devre dışı bırakabilirsiniz. Ayrıca, **Araçlar**  >  **Seçenekler**  >  **kapsayıcı araç**  >  **kapsayıcıları araç penceresinde** ayarlar ' da bu seçenekleri etkinleştirebilir veya devre dışı bırakabilirsiniz. Bkz. [kapsayıcı araçlarını yapılandırma](container-tools-configure.md).

## <a name="next-steps"></a>Sonraki adımlar

[kapsayıcı araçlarına genel bakış ' ı](overview.md)okuyarak Visual Studio bulunan kapsayıcı araçları hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio 'da kapsayıcı geliştirme](./index.yml)
