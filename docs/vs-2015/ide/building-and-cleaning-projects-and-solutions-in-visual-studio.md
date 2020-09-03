---
title: Temiz proje çözümleri oluşturun
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 15f2817b6fd0aee312ff41af218d01ad80bc785e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620564"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Visual Studio'da Projeler ve Çözümler Oluşturma ve Temizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konudaki yordamları kullanarak bir çözümde proje veya proje öğelerinden tümünü veya bir kısmını oluşturabilir, yeniden oluşturabilir veya temizleyebilirsiniz. Adım adım bir öğretici için bkz. [Izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Visual Studio sürümünüzde Kullanıcı arabirimi, etkin ayarlarınıza bağlı olarak bu konunun açıklanana kadar farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünü açın ve ardından **ayarları Içeri ve dışarı aktar**' ı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

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

2. Menü çubuğunda **Oluştur**' u seçin ve sonra _ProjectName_ **Derle** veya _ProjectName_öğesini **yeniden oluştur** ' u seçin.

    - Yalnızca en son derlemeden bu yana değiştirilen proje bileşenlerini derlemek için **Build** _ProjectName_ öğesini seçin.

    - Projeyi "temizlemek" için _ProjectName_ **yeniden derle** öğesini seçin ve proje dosyalarını ve tüm proje bileşenlerini derleyin.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Yalnızca başlangıç projesini ve bağımlılıklarını oluşturmak için

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler** düğümünü genişletin ve ardından **Oluştur ve Çalıştır** sayfasını seçin.

    **Oluşturma ve çalıştırma, projeler ve çözümler, Seçenekler** iletişim kutusu açılır.

3. **Yalnızca oluşturma başlangıç projelerini ve çalıştırılan bağımlılıkları Çalıştır** onay kutusunu seçin.

    Bu onay kutusu seçildiğinde, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıkları oluşturulur:

   - Menü çubuğunda **hata**  >  **ayıklamayı Başlat hata** Ayıkla (F5) öğesini seçin.

   - Menü **çubuğunda Build**  >  **Build Solution** (CTRL + SHIFT + B) öğesini seçin.

     Bu onay kutusu Temizlenmişken, önceki komutlardan birini çalıştırdığınızda tüm projeler, bağımlılıkları ve çözüm dosyaları oluşturulur. Varsayılan olarak bu onay kutusu işaretli değildir.

## <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçili Visual C++ projesi oluşturmak için

1. Bir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] proje seçin ve ardından menü çubuğunda **Yapı**, **yalnızca proje**ve aşağıdaki komutlardan birini seçin:

   - **Yalnızca** *ProjectName* oluştur

   - **Yalnızca** *ProjectName* öğesini yeniden derle

   - **Yalnızca** *ProjectName* 'i temizle

   - **Salt bağlantı yalnızca** *ProjectName*

     Bu komutlar [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , herhangi bir proje bağımlılığı veya çözüm dosyası oluşturmadan, yeniden oluşturmaya, temizlemeye veya bağlamaya gerek kalmadan yalnızca seçtiğiniz proje için geçerlidir. Sürümünüze bağlı olarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **yalnızca proje** alt menüsünde daha fazla komut bulunabilir.

## <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğesi derlemek için

1. **Çözüm Gezgini**, derlenebilecek eylemler olabilecek birden çok dosya seçin, bu dosyalardan biri için kısayol menüsünü açın ve **Derle**' yi seçin.

     Dosyaların bağımlılıkları varsa, dosyalar bağımlılık sırasıyla derlenir. Dosyalar derlerken kullanılamayan bir ön derlenmiş üstbilgi gerektiriyorsa, derleme işlemi başarısız olur. Derleme işlemi geçerli etkin çözüm yapılandırmasını kullanır.

## <a name="to-stop-a-build"></a>Bir derlemeyi durdurmak için

1. Aşağıdaki adımlardan birini gerçekleştirin:

    - Menü çubuğunda **Oluştur**, **iptal**' i seçin.

    - Ctrl + Break tuşlarını seçin.

## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: derleme günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md) yapı [günlüklerini](../msbuild/obtaining-build-logs-with-msbuild.md) derleme [ve oluşturma derleme](../ide/compiling-and-building-in-visual-studio.md) [yapılandırmalarının](../ide/understanding-build-configurations.md) [hata ayıklama ve yayınlama proje yapılandırmalarının](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [C/C++ derleme başvurusu](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md) [çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)
