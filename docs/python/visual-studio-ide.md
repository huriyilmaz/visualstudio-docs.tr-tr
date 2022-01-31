---
description: Tümleşik Visual Studio ortamı, Kodu düzenlemek, hata ayıklamak ve test etmek ve ardından bir uygulamayı yayımlamak için kullanabileceğiniz Python (ve diğer diller) için yaratıcı bir başlatma panelidir.
title: Python geliştiricileri Visual Studio genel bakış
titleSuffix: ''
ms.date: 01/26/2022
ms.topic: overview
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 99ffbe74bf5026aa3ed7f827ded2b53391fee24d
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887053"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Visual Studio IDE | Python

Tümleşik Visual Studio ortamı, Kodu  düzenlemek, hata ayıklamak ve test etmek ve ardından bir uygulamayı yayımlamak için kullanabileceğiniz Python (ve diğer diller) için yaratıcı bir başlatma panelidir. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılmaktadır ve özellik bakımından zengin bir programdır. IDE'lerin çoğu tarafından kullanılan standart düzenleyici ve hata ayıklayıcının üzerinde ve üzerinde, Visual Studio tamamlama araçları, etkileşimli REPL ortamları ve yazılım geliştirme sürecini kolaylaştıran diğer özellikler yer almaktadır.

[![Visual Studio Python projesiyle çalışma](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Bu görüntüde, Visual Studio Python projesine ve büyük olasılıkla kullanabileceğiniz birkaç anahtar araç pencereye sahip olan görseller yer alelade bir şekilde görüntüdedir:

- [**Çözüm Gezgini**](../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları çözümler ve projeler olarak gruplamanıza yardımcı [olabilir](../get-started/tutorial-projects-solutions.md).
  - Bu **Çözüm Gezgini**[**, bilgisayarınızda**](managing-python-environments-in-visual-studio.md) yüklü olan farklı Python yorumlayıcılarını yönetebilirsiniz.

  ::: moniker range=">=vs-2019"
  - Ayrıca, bir klasördeki Python kodunu proje ve çözüm dosyaları oluşturmadan Visual Studio çalıştırabilirsiniz. Daha fazla bilgi için bkz [. Hızlı Başlangıç: Bir klasörde Python kodunu açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- Büyük [olasılıkla](../ide/writing-code-in-the-code-and-text-editor.md) zaman harcamanız gereken düzenleyici penceresi (orta), dosya içeriğini görüntüler. Burada Python kodunu [düzenleyebilir, kod](editing-python-code-in-visual-studio.md) yapınız içinde gezinebilirsiniz ve hata ayıklama oturumları sırasında kesme noktaları ayarlayabilirsiniz. Python ile kodu seçerek Ctrl+Enter tuşlarına basarak bu kodu etkileşimli bir [REPL penceresinde çalıştırabilirsiniz](python-interactive-repl-in-visual-studio.md).

- Çıkış [penceresi](../ide/reference/output-window.md) (alttaki orta), hata ayıklama Visual Studio hata iletileri, uyarılar, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.
  - Çıkış [penceresiyle aynı alanda bir Python Etkileşimli REPL](python-interactive-repl-in-visual-studio.md) penceresi görüntülenir.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (sağ alt) git ve Team Foundation Sürüm Denetimi (TFVC) gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenizi ve başka [](https://git-scm.com/) [kullanıcılarla kod paylaşmayı sağlar](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true).

## <a name="editions"></a>Sürümler

Visual Studio mac Windows kullanılabilir; ancak Python desteği yalnızca Visual Studio için Windows.

Windows'da Visual Studio sürümü vardır: Windows, Community, Professional ve Enterprise. Her [sürümde Visual Studio özellikler hakkında](https://visualstudio.microsoft.com/vs/compare/) bilgi edinmek için bkz. IDE'leri karşılaştırma.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Yazılım geliştirirken daha üretken Visual Studio yardımcı olacak özelliklerden bazıları şunlardır:

- [Intellisense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük kod parçaları yazan bir özellik kümesi terimidir. Bu, düzenleyicide satır içinde temel belgelere sahip olmak gibi, başka bir yerde tür bilgilerini aramadan tasarruf etmektir. IntelliSense özellikleri dile göre değişiklik gösterir ve [Python kodunu düzenleme makalesinde](editing-python-code-in-visual-studio.md#intellisense) Python'a ilişkin ayrıntılar vardır. Aşağıdaki çizimde, IntelliSense'in bir tür için üye listesini nasıl görüntülesi gösterilmiştir:

   ![Visual Studio IntelliSense ile üye tamamlama](media/code-editing-completions-simple.png)

- [Yeniden Düzenle](refactoring-python-code.md)

   Visual Studio, bir kod parçasına sağ tıklar ve Hızlı eylemler ile Yeniden Düzenleme'yi seçerek değişkenleri akıllı bir şekilde yeniden tanımlama, bir veya daha fazla kod satırı ayıklar ve yöntem parametrelerinin sıralamalarını değiştirme gibi işlemler sağlar.

   ![Visual Studio'da yeniden düzenleme](media/tour-ide-refactor-extract-method.png)

- [Lint uygulama](refactoring-python-code.md)

   Python kodundaki hataları ve yaygın sorunları lint etme denetimleri, iyi Python kodlama desenleriyle sizi teşvik ediyor.

   ![Python projeleri için bağlam menüsünde PyLint komutu](media/code-pylint-command.png)

- Arama kutusu

   Visual Studio menüler, seçenekler ve özelliklerle zaman zaman aşırı yoğun görünebilir. Arama kutusu, ihtiyacınız olan her şeyi hızla bulmanın harika bir Visual Studio. Aramanız gereken bir şeyin adını yazmaya başladığınızda, Visual Studio tam olarak nereye gitmenizi istediğiniz sonuçları listeler. Visual Studio programlama dili desteği ekleme gibi işlevler eklemeniz gerekirse, arama kutusu bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açmanızı sağlayan sonuçlar sağlar.

   ![Visual Studio'da arama kutusu](media/tour-ide-quick-launch.png)

- Geçişler ve [Hızlı Eylemler](../ide/quick-actions.md)

   Dalgalı çizgiler, kod yazma sırasında sizi hatalara veya olası sorunlara karşı uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, derleme sırasında veya programı çalıştırarak hatanın keşfedilmalarını beklemeden sorunları hemen düzeltmeye olanak sağlar. Bir geçişin üzerine gelindiğinde hata hakkında ek bilgiler alırsınız. Hatayı düzeltmek için sol kenar boşluğunda Hızlı Eylemler olarak bilinen eylemlerle birlikte bir ampul de görünebilir.

   ![Visual Studio'da Visual Studio](media/tour-ide-squiggles.png)

- [Tanıma Git ve Tanıma Göz At](../ide/go-to-and-peek-definition.md)

   Tanıma **Git özelliği** sizi doğrudan bir işlev veya türün tanımlandığı konuma alır. **Tanımlara Göz At** komutu, tanımı ayrı bir dosya açılmadan bir pencerede görüntüler. Tüm **Başvuruları Bul komutu,** belirli bir tanımlayıcının tanımlandığı ve kullanılan yeri bulmanın yararlı bir yolunu da sağlar.

   ![Kod gezinti komutları](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Python için güçlü özellikler

::: moniker range=">=vs-2019"
- [Proje olmadan kod çalıştırma](quickstart-05-python-visual-studio-open-folder.md)

    2019'Visual Studio başlayarak, kod için bir Visual Studio projesi oluşturmak zorunda kalmadan IntelliSense ve hata ayıklama gibi özelliklerden keyif almak için Python kodu içeren bir klasör açabilirsiniz.
::: moniker-end

- [Visual Studio’yu kullanarak işbirliği yapma](/visualstudio/liveshare/)

    Visual Studio Live Share, kullanmakta olduğunuz programlama diline veya uygulama türlerine bakılmaksızın başkalarını gerçek zamanlı olarak işbirliğine dayalı olarak düzenlemenizi ve hata ayıklamayı sağlar.

- [Python Etkileşimli REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio Python ortamlarınızı her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar. Bu pencere, komutpython.exerepl ile elde edersiniz.** Etkileşimli **pencerede** rastgele Python kodu girebilirsiniz ve hemen sonuçları görebilirsiniz.

    ![Python etkileşimli penceresi](media/interactive-window.png)

- [Hata Ayıklama](debugging-python-in-visual-studio.md)

    Visual Studio, çalışan işlemlere ekleme, İzleme ve Anında pencerelerde ifadeleri değerlendirme, yerel değişkenleri inceleme, kesme noktaları, adım adım/dışarı/dışarı  deyimleri, Sonraki Deyimi Ayarla ve daha fazlası dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar.  Linux bilgisayarlarda çalışan uzak Python kodunda da hata ayıkabilirsiniz.

    ![Visual Studio'da Python'da hata ayıklama](media/remote-debugging-breakpoint-hit.png)

- [C++ ile etkileşim kurma](working-with-c-cpp-python-in-visual-studio.md)

    Python için oluşturulan birçok kitaplık, en iyi performans için C++ dilinde yazılır. Visual Studio, karma mod hata ayıklama dahil olmak üzere C++ uzantıları geliştirmek [için zengin tesisler sağlar](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Python ve C++ karma mod hata ayıklaması](media/mixed-mode-debugging.png)

- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)

    CPython tabanlı bir yorumlayıcı kullanırken, Python kodunuzun performansını uygulama içinde Visual Studio.

    ![Profil oluşturma performans raporu](media/profiling-results.png)

- [Birim Testi](unit-testing-python-in-visual-studio.md)

    Visual Studio, birim testlerini bulma, çalıştırma ve hata ayıklama için IDE bağlamında tümleşik destek sağlar.

    ![Başarısız test durumunu gösteren birim testi](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki hızlı başlangıç Visual Studio öğreticilerden birini kullanarak Python'da python'i daha fazla keşfedin:

> [!div class="nextstepaction"]
> [Hızlı Başlangıç: Flask ile web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Visual Studio'de Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Kullanmaya başlayın Django web çerçevesiyle Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Kullanmaya başlayın Flask web çerçevesiyle Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Ayrıca bkz.

- Daha [fazla Visual Studio keşfedin](../ide/advanced-feature-overview.md)
- [Visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Visual Studio [blog'larını okuyun](https://devblogs.microsoft.com/visualstudio/)
