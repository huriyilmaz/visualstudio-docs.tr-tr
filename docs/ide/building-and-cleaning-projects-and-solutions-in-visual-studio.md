---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1cf71abb19f6d4a3a459b4e5559e536f18f41c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114561"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Visual Studio'da projeler ve çözümler oluşturun ve temizleyin

Bu konudaki yordamları kullanarak, bir çözümdeki projelerin veya proje öğelerinin tamamını veya bazılarını oluşturabilir, yeniden oluşturabilir veya temizleyebilirsiniz. Adım adım öğretici için [Walkthrough: Building a application](../ide/walkthrough-building-an-application.md)'a bakın.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'da Build ve clean projects ve solutions adresine](/visualstudio/mac/building-and-cleaning-projects-and-solutions)bakın.

> [!NOTE]
> Visual Studio'nun sürümünüzdeki UI, etkin ayarlarınıza bağlı olarak bu konunun açıkladığı ndan farklı olabilir. Ayarlarınızı değiştirmek için, örneğin **Genel** veya **Görsel C++** ayarlarını değiştirmek **için, Araçlar** > **İçe Ve Dışa Aktar Ayarlarını**seçin ve ardından **tüm ayarları sıfırla'yı**seçin.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Tüm çözümü oluşturmak, yeniden oluşturmak veya temizlemek için

1. **Solution**Explorer'da, çözümü seçin veya açın.

2. Menü çubuğunda **Oluştur'u**seçin ve ardından aşağıdaki komutlardan birini seçin:

    - Yalnızca en son yapılana göre değişen proje dosyalarını ve bileşenlerini derlemek için **Çözüm Oluştur** veya **Oluştur'u** seçin.

        > [!NOTE]
        > Bir çözüm birden fazla proje içerdiğinde **Yapı** komutu **Çözüm Oluştur** olur.

    - Çözümü "temizlemek" için **Çözümü Yeniden Oluştur'u** seçin ve ardından tüm proje dosyalarını ve bileşenlerini oluşturun.

    - Ara ve çıktı dosyalarını silmek için **Çözüm'i** Temizle'yi seçin. Yalnızca proje ve bileşen dosyaları bırakıldığında, ara ve çıktı dosyalarının yeni örnekleri oluşturulabilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir proje oluşturmak veya yeniden oluşturmak için

1. **Çözüm Gezgini'nde**projeyi seçin veya açın.

2. Menü çubuğunda, **Oluştur'u**seçin ve ardından ProjectName **Oluştur** veya *ProjectName'i* Yeniden **Oluştur'u** *ProjectName*seçin.

    - Yalnızca en son yapılana göre değişen proje bileşenlerini oluşturmak için *ProjectName* **Oluştur'u** seçin.

    - *Projeyi* "temizlemek" için **ProjectName'i yeniden oluşturun** ve ardından proje dosyalarını ve tüm proje bileşenlerini oluşturun.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Yalnızca başlangıç projesini ve bağımlılıklarını oluşturmak için

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Seçenekler** iletişim kutusunda, Projeler **ve Çözümler** düğümlerini genişletin ve ardından **Yap ve Çalıştır** sayfasını seçin.

     **Projeler** >  **Oluştur ve Çalıştır** > **Seçenekleri** iletişim kutusu açılır.

3. Çalıştır onay kutusunda **Ki Tek başlangıç projeleri ve bağımlılıkları** oluşturun' u seçin.

     Bu onay kutusu seçildiğinde, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıkları oluşturulur:

    - Menü çubuğunda **Hata Ayıklama** > **Başlat** **(F5)** seçeneğini belirleyin.

    - Menü çubuğunda **Yapı** > **Çözüm** **(Ctrl**+**Shift**+**B)** seçeneğini belirleyin.

    Bu onay kutusu temizlendiğinde, önceki komutlardan birini çalıştırdığınızda tüm projeler, bunların bağımlılıkları ve çözüm dosyaları oluşturulur. Varsayılan olarak bu onay kutusu işaretli değildir.

## <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçili Visual C++ projesini oluşturmak için

Bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje seçin ve ardından menü çubuğunda Yalnızca **Project'i Oluştur'u** > **Project Only**ve aşağıdaki komutlardan birini seçin:

- **Yalnızca** *Proje Adı* Oluştur

- **Yalnızca** *Proje Adını* Yeniden Oluştur

- Yalnızca *Proje Adını* **Temizle**

- **Bağlantı Sadece** *Proje Adı*

Bu komutlar yalnızca, [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje bağımlılıklarını veya çözüm dosyalarını oluşturmadan, yeniden oluşturmadan, temizlemeden veya bağlamadan seçtiğiniz proje için geçerlidir. Sürümünüze bağlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]olarak, **Yalnızca Project** alt menüsü daha fazla komut içerebilir.

## <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğesi derlemek için

**Çözüm Gezgini'nde,** derlenebilecek birden çok dosya seçin, bu dosyalardan biri için kısayol menüsünü açın ve ardından **Derle'i**seçin.

Dosyaların bağımlılıkları varsa, dosyalar bağımlılık sırasına göre derlenir. Dosyaları derlediğinizde kullanılamayan önceden derlenmiş bir üstbilgi gerektiriyorsa derleme işlemi başarısız olur. Derleme işlemi geçerli etkin çözüm yapılandırmasını kullanır.

## <a name="to-stop-a-build"></a>Bir yapıyı durdurmak için

Aşağıdaki adımlardan birini gerçekleştirin:

- Menü çubuğunda **İptal Yap'ı** > **Cancel**seçin.

- **Ctrl**+**Break**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılsın: Yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Yapı günlükleri edinme](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Derleme ve bina](../ide/compiling-and-building-in-visual-studio.md)
- [Yapı yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Nasıl yapılır: Hata ayıklama ve dağıtım yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ bina referansı](/cpp/build/reference/c-cpp-building-reference)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Projeler ve çözümler oluşturun ve temizleyin (Mac için Visual Studio)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
