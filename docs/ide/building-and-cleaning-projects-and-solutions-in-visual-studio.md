---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
description: Bir çözümdeki proje veya proje öğelerinden tümünü veya bir kısmını nasıl oluşturabileceğiniz, yeniden oluşturabileceğiniz veya temizleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d2ab8a723b69f4c5930c91a10719a2107ad83003
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136803"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme

Bu konudaki yordamları kullanarak bir çözümde proje veya proje öğelerinden tümünü veya bir kısmını oluşturabilir, yeniden oluşturabilir veya temizleyebilirsiniz. Adım adım bir öğretici için bkz. [Izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio içindeki proje ve çözümleri oluşturma ve Temizleme](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Visual Studio sürümünüzde Kullanıcı arabirimi, etkin ayarlarınıza bağlı olarak bu konunun açıklanana kadar farklılık gösterebilir. Ayarlarınızı değiştirmek (örneğin, **genel** veya **Visual C++** ayarları) için **Araçlar**  >  **içeri ve dışarı aktarma ayarları**' nı seçin ve ardından **tüm ayarları Sıfırla**' yı seçin.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Tüm çözümü derlemek, yeniden derlemek veya temizlemek için

1. **Çözüm Gezgini**, çözümü seçin veya açın.

2. Menü çubuğunda, **Oluştur**' u seçin ve ardından aşağıdaki komutlardan birini seçin:

    - Yalnızca en son derlemeden bu yana değiştirilen proje dosyalarını ve bileşenlerini derlemek için **Build** veya **Build Solution** öğesini seçin.

        > [!NOTE]
        > Bir çözüm birden fazla proje içerdiğinde **Build** komutu **derleme çözümü** haline gelir.

    - Çözümü "temizlemek" için **çözümü yeniden oluştur** ' u seçin ve ardından tüm proje dosyaları ve bileşenleri oluşturun.

    - Tüm ara ve çıkış dosyalarını silmek için **Çözümü Temizle** ' yi seçin. Yalnızca proje ve bileşen dosyaları solda, ara ve çıkış dosyalarının yeni örnekleri derlenebilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir projeyi derlemek veya yeniden derlemek için

1. **Çözüm Gezgini**, projeyi seçin veya açın.

2. Menü çubuğunda **Oluştur**' u seçin ve sonra *ProjectName* **Derle** veya *ProjectName*öğesini **yeniden oluştur** ' u seçin.

    - Yalnızca en son derlemeden bu yana değiştirilen proje bileşenlerini derlemek için **Build** *ProjectName* öğesini seçin.

    - Projeyi "temizlemek" için *ProjectName* **yeniden derle** öğesini seçin ve proje dosyalarını ve tüm proje bileşenlerini derleyin.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Yalnızca başlangıç projesini ve bağımlılıklarını oluşturmak için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler** düğümünü genişletin ve ardından **Oluştur ve Çalıştır** sayfasını seçin.

     Projeleri ve çözümleri **oluşturma ve çalıştırma**  >  **Projects and Solutions**  >  **seçenekleri** iletişim kutusu açılır.

3. **Yalnızca oluşturma başlangıç projelerini ve çalıştırılan bağımlılıkları Çalıştır** onay kutusunu seçin.

     Bu onay kutusu seçildiğinde, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıkları oluşturulur:

    - Menü çubuğunda **Hata Ayıkla**  >  **Başlat** (**F5**) öğesini seçin.

    - Menü **çubuğunda Build**  >  **Build Solution** (**CTRL** + **Shift** + **B**) öğesini seçin.

    Bu onay kutusu Temizlenmişken, önceki komutlardan birini çalıştırdığınızda tüm projeler, bağımlılıkları ve çözüm dosyaları oluşturulur. Varsayılan olarak bu onay kutusu işaretli değildir.

## <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçili Visual C++ projesi oluşturmak için

Bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje seçin ve ardından menü çubuğunda **Build**  >  **yalnızca proje**oluştur ' u ve aşağıdaki komutlardan birini seçin:

- **Yalnızca** *ProjectName* oluştur

- **Yalnızca** *ProjectName* öğesini yeniden derle

- **Yalnızca** *ProjectName* 'i temizle

- **Salt bağlantı yalnızca** *ProjectName*

Bu komutlar [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , herhangi bir proje bağımlılığı veya çözüm dosyası oluşturmadan, yeniden oluşturmaya, temizlemeye veya bağlamaya gerek kalmadan yalnızca seçtiğiniz proje için geçerlidir. Sürümünüze bağlı olarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , **yalnızca proje** alt menüsünde daha fazla komut bulunabilir.

## <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğesi derlemek için

**Çözüm Gezgini**, derlenebilecek eylemler olabilecek birden çok dosya seçin, bu dosyalardan biri için kısayol menüsünü açın ve **Derle**' yi seçin.

Dosyaların bağımlılıkları varsa, dosyalar bağımlılık sırasıyla derlenir. Dosyalar derlerken kullanılamayan bir ön derlenmiş üstbilgi gerektiriyorsa, derleme işlemi başarısız olur. Derleme işlemi geçerli etkin çözüm yapılandırmasını kullanır.

## <a name="to-stop-a-build"></a>Bir derlemeyi durdurmak için

Aşağıdaki adımlardan birini gerçekleştirin:

- Menü çubuğunda, **derleme**  >  **iptali**' ni seçin.

- **CTRL** + **Kes**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Yapı yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Nasıl yapılır: Hata ayıklama ve dağıtım yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ oluşturma başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [Çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
- [Projeleri ve çözümleri oluşturma ve Temizleme (Mac için Visual Studio)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
