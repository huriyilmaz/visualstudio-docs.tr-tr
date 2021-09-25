---
title: Projeleri ve Çözümleri Oluşturma ve Temizleme
description: Bir çözümdeki proje veya proje öğelerinden tümünü veya bir kısmını nasıl oluşturabileceğiniz, yeniden oluşturabileceğiniz veya temizleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/14/2021
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 81bf65489fe97dab1a331b8b7d22f8ac05520312
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427752"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Visual Studio projeler ve çözümler oluşturma ve Temizleme

Bu konudaki yordamları kullanarak bir çözümde proje veya proje öğelerinden tümünü veya bir kısmını oluşturabilir, yeniden oluşturabilir veya temizleyebilirsiniz. Adım adım bir öğretici için bkz. [Izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio içindeki proje ve çözümleri oluşturma ve temizleme](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Visual Studio sürümünüzde kullanıcı arabirimi, etkin ayarlarınıza bağlı olarak bu konunun açıklanana kadar farklılık gösterebilir. ayarlarınızı değiştirmek (örneğin, **genel** veya **Visual C++** ayarları) için **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin ve ardından **tüm ayarları sıfırla**' yı seçin.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Tüm çözümü derlemek, yeniden derlemek veya temizlemek için

1. **Çözüm Gezgini**, çözümü seçin veya açın.

2. Menü çubuğunda, **Oluştur**' u seçin ve ardından aşağıdaki komutlardan birini seçin:

    -    +  + Yalnızca en son derlemeden bu yana değiştirilen proje dosyalarını ve bileşenleri derlemek için Build veya Build Solution ' ı seçin ya da CTRL SHIFT **B**' ye basın.

        > [!NOTE]
        > Bir çözüm birden fazla proje içerdiğinde **Build** komutu **derleme çözümü** haline gelir.

    - Çözümü "temizlemek" için **çözümü yeniden oluştur** ' u seçin ve ardından tüm proje dosyaları ve bileşenleri oluşturun.

    - Tüm ara ve çıkış dosyalarını silmek için **Çözümü Temizle** ' yi seçin. Yalnızca proje ve bileşen dosyaları solda, ara ve çıkış dosyalarının yeni örnekleri derlenebilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Tek bir projeyi derlemek veya yeniden derlemek için

1. **Çözüm Gezgini**, projeyi seçin veya açın.

2. Menü çubuğunda **Oluştur**' u seçin ve sonra *ProjectName* **Derle** veya *ProjectName* öğesini **yeniden oluştur** ' u seçin.

    - Yalnızca en son derlemeden bu yana değiştirilen proje bileşenlerini derlemek için **Build** *ProjectName* öğesini seçin.

    - Projeyi "temizlemek" için *ProjectName* **yeniden derle** öğesini seçin ve proje dosyalarını ve tüm proje bileşenlerini derleyin.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Yalnızca başlangıç projesini ve bağımlılıklarını oluşturmak için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler** düğümünü genişletin ve ardından **Oluştur ve Çalıştır** sayfasını seçin.

     Projeleri ve çözümleri **oluşturma ve çalıştırma**  >    >  **seçenekleri** iletişim kutusu açılır.

3. **Yalnızca oluşturma başlangıç projelerini ve çalıştırılan bağımlılıkları Çalıştır** onay kutusunu seçin.

     Bu onay kutusu seçildiğinde, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıkları oluşturulur:

    - Menü çubuğunda **Hata Ayıkla**  >  **Başlat** (**F5**) öğesini seçin.

    - Menü **çubuğunda Build**  >  **Build Solution** (**CTRL** + **Shift** + **B**) öğesini seçin.

    Bu onay kutusu Temizlenmişken, önceki komutlardan birini çalıştırdığınızda tüm projeler, bağımlılıkları ve çözüm dosyaları oluşturulur.

## <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçili Visual C++ projesi oluşturmak için

bir C++ projesi seçin ve ardından menü çubuğunda yalnızca **yapı**  >  **Project** oluştur ' u ve aşağıdaki komutlardan birini seçin:

- **Yalnızca** *ProjectName* oluştur

- **Yalnızca** *ProjectName* öğesini yeniden derle

- **Yalnızca** *ProjectName* 'i temizle

- **Salt bağlantı yalnızca** *ProjectName*

Bu komutlar, herhangi bir proje bağımlılığı veya çözüm dosyası oluşturmadan, yeniden oluşturmaya, temizlemeye veya bağlamaya gerek kalmadan yalnızca seçtiğiniz C++ projesi için geçerlidir. Visual Studio sürümünüze bağlı olarak, **yalnızca Project** alt menüsünde daha fazla komut bulunabilir.

## <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğesi derlemek için

**Çözüm Gezgini**, derlenebilecek eylemler olabilecek birden çok dosya seçin, bu dosyalardan biri için kısayol menüsünü açın ve **Derle**' yi seçin veya **CTRL**+ + **F7** tuşuna basın.

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
- [projeleri ve çözümleri oluşturma ve temizleme (Mac için Visual Studio)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
