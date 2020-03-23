---
title: Python geliştiricileri için Visual Studio'ya Genel Bakış
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 8b8b656aaefe4440e811378da2b84d1b944d4fb1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73661925"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Visual Studio IDE'ye Hoş Geldiniz | Python

Visual Studio *tümleşik geliştirme ortamı,* Python (ve diğer diller) için kodu düzenlemek, hata ayıklamak ve test etmek ve ardından bir uygulama yayınlamak için kullanabileceğiniz yaratıcı bir başlatma rampasıdır. Entegre geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen zengin özelliklere sahip bir programdır. Çoğu IDA'nın sağladığı standart düzenleyici ve hata ayıklayıcının üzerinde ve üstünde, Visual Studio yazılım geliştirme sürecini kolaylaştırmak için kod tamamlama araçları, etkileşimli REPL ortamları ve diğer özellikler içerir.

[![Python projesi ile Visual Studio](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Bu resim, Visual Studio'da açık bir Python projesi ve büyük olasılıkla kullanacağınız birkaç anahtar araç penceresi ile gösterilmektedir:

- [**Solution Explorer**](../ide/solutions-and-projects-in-visual-studio.md) (sağ üstte), kod dosyalarınızı görüntülemenizi, gezinmenizi ve yönetmenize olanak tanır. **Solution Explorer,** dosyaları [çözüm ve projelere](../get-started/tutorial-projects-solutions.md)gruplandırma yaparak kodunuzu düzenlemenize yardımcı olabilir.
  - Solution **Explorer'ın** yanı sıra, bilgisayarınızda yüklü olan farklı Python yorumlayıcılarını yönettiğiniz [**Python Ortamları**](managing-python-environments-in-visual-studio.md)da vardır.

  ::: moniker range=">=vs-2019"
  - Ayrıca Visual Studio proje ve çözüm dosyaları oluşturmadan bir klasörde Python kodunu açıp çalıştırabilirsiniz. Daha fazla bilgi için [Bkz. Quickstart: Python kodunu bir klasörde açın ve çalıştırın.](quickstart-05-python-visual-studio-open-folder.md)
  ::: moniker-end

- Zamanınızın büyük kısmını harcayacağınız [düzenleyici penceresi](../ide/writing-code-in-the-code-and-text-editor.md) (merkez), dosya içeriğini görüntüler. Python kodunu [düzenlediğiniz,](editing-python-code-in-visual-studio.md)kod yapınızda gezindiğiniz ve hata ayıklama oturumları sırasında kesme noktaları ayarladığınız yerdir. Python ile kodu seçebilir ve bu kodu [etkileşimli REPL penceresinde](python-interactive-repl-in-visual-studio.md)çalıştırmak için Ctrl+Enter tuşuna basabilirsiniz.

- [Çıktı penceresi](../ide/reference/output-window.md) (alt orta) Visual Studio'nun hata ayıklama ve hata iletileri, uyarılar, yayımlama durum iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.
  - Bir [Python Interactive REPL penceresi](python-interactive-repl-in-visual-studio.md) Çıktı penceresi ile aynı alanda görünür.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ altta), [Git](https://git-scm.com/) ve [Team Foundation Sürüm Denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts)gibi sürüm denetim teknolojilerini kullanarak iş öğelerini izlemenizi ve kodu başkalarıyla paylaşmanızı sağlar.

## <a name="editions"></a>Sürümler

Visual Studio, Windows ve Mac için kullanılabilir; ancak Python desteği yalnızca Windows için Visual Studio'da kullanılabilir.

Windows'da Visual Studio'nun üç sürümü vardır: Topluluk, Profesyonel ve Kurumsal. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için [Visual Studio IID'lerini karşılaştırın'](https://visualstudio.microsoft.com/vs/compare/) a bakın.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio'da yazılım geliştirdikçe daha üretken olmanıza yardımcı olan popüler özelliklerden bazıları şunlardır:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense, kodunuz hakkındaki bilgileri doğrudan düzenleyicide görüntüleyen ve bazı durumlarda sizin için küçük kod bitleri yazan bir dizi özellik için bir terimdir. Bu, editörde temel belgelerin sıralı olması gibi bir şey, bu da sizi yazı bilgilerini başka bir yerde aramaktan kurtarır. IntelliSense özellikleri dile göre değişir ve [Python kodu düzenleme](editing-python-code-in-visual-studio.md#intellisense) makalesi Python için ayrıntılara sahiptir. Aşağıdaki resimde, IntelliSense'in bir tür için üye listesini nasıl görüntülenebilmektedir:

   ![Visual Studio IntelliSense ile üye tamamlama](media/code-editing-completions-simple.png)

- [Yeniden Düzenle](refactoring-python-code.md)

   Bir kod parçasına sağ tıklayarak ve **Hızlı eylemleri ve Refactorings'i**seçerek Visual Studio, değişkenlerin akıllı yeniden adlandırması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemler sağlar.

   ![Visual Studio'da yeniden düzenleme](media/tour-ide-refactor-extract-method.png)

- [Lint uygulama](refactoring-python-code.md)

   Python kodunuzdaki hataları ve sık karşılaşılan sorunları kontrol eder ve sizi iyi Python kodlama desenleri ile teşvik eder.

   ![Python projeleri için bağlam menüsünde PyLint komutu](media/code-pylint-command.png)

- Arama kutusu

   Visual Studio bu kadar çok menü, seçenek ve özellikleri ile zaman zaman ezici görünebilir. Arama kutusu hızla Visual Studio ne ihtiyacınız bulmak için harika bir yoldur. Aradığınız bir şeyin adını yazmaya başladığınızda, Visual Studio sizi tam olarak gitmeniz gereken yere götürecek sonuçları listeler. Visual Studio'ya işlevsellik eklemeniz gerekirse, örneğin ek bir programlama dili için destek eklemek için arama kutusu, visual studio yük leyicisini iş yükü veya tek tek bir bileşen yüklemek için açan sonuçlar sağlar.

   ![Visual Studio'da arama kutusu](media/tour-ide-quick-launch.png)

- Squiggles ve [Hızlı Eylemler](../ide/quick-actions.md)

   Dalgalı dalgalı, yazarken kodunuzda ki hatalara veya olası sorunlara karşı sizi uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları hemen çözmenizi sağlar. Bir dalgalı üzerinde gezinirseniz, hata hakkında ek bilgiler görürsünüz. Bir ampul de hataları düzeltmek için, Hızlı Eylemler olarak bilinen eylemleri ile sol kenar boşluğunda görünebilir.

   ![Görsel Stüdyo'da Squiggles](media/tour-ide-squiggles.png)

- [Git ve Peek Tanımı](../ide/go-to-and-peek-definition.md)

   **Tanıma Git** özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür. **Peek Tanımlar** komutu, ayrı bir dosya açmadan tanımı bir pencerede görüntüler. **Tüm Başvuruları Bul** komutu, verilen herhangi bir tanımlayıcının hem tanımlandığını hem de kullanıldığını bulmak için yararlı bir yol da sağlar.

   ![Kod gezinti komutları](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Python için güçlü özellikler

::: moniker range=">=vs-2019"
- [Proje olmadan kod çalıştırma](quickstart-05-python-visual-studio-open-folder.md)

    Visual Studio 2019'dan itibaren, Kod için bir Visual Studio projesi oluşturmak zorunda kalmadan IntelliSense ve hata ayıklama gibi özelliklerin keyfini çıkarmak için Python kodu içeren bir klasör açabilirsiniz.
::: moniker-end

- [Visual Studio’yu kullanarak işbirliği yapma](/visualstudio/liveshare/)
  
    Visual Studio Live Share, kullandığınız programlama dili veya uygulama türleri ne olursa olsun, başkalarıyla gerçek zamanlı olarak işbirliği içinde bir şekilde düzeltme ve hata ayıklama yapmanızı sağlar. 

- [Python İnteraktif REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio, python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar ve komut satırında *python.exe* ile elde ettiğiniz REPL'yi geliştirir. **Etkileşimli** pencerede rasgele Python kodu girebilir ve hemen sonuçları görebilirsiniz.

    ![Python etkileşimli pencere](media/interactive-window.png)

- [Hata ayıklama](debugging-python-in-visual-studio.md)

    Visual Studio, Python için çalışan işlemlere bağlanma, **Watch** ve **Immediate** pencerelerinde ifadeleri değerlendirme, yerel değişkenleri inceleme, kesme noktaları, adım/çıkış/çıktı ifadeleri, **Sonraki Bildirimi Ayarla**ve daha fazlası dahil olmak üzere kapsamlı bir hata ayıklama deneyimi sağlar. Ayrıca Linux bilgisayarlarda çalışan uzak Python kodunu hata ayıklayabilirsiniz.

    ![Visual Studio'da Python'u Hata Ayıklama](media/remote-debugging-breakpoint-hit.png)

- [C++ ile etkileşim kurma](working-with-c-cpp-python-in-visual-studio.md)

    Python için oluşturulan birçok kitaplık, en iyi performans için C++ ile yazılır. Visual [Studio, karışık modlu hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)da dahil olmak üzere C++ uzantıları geliştirmek için zengin olanaklar sağlar.

    ![Python ve C++'ın karışık mod hata ayıklama](media/mixed-mode-debugging.png)

- [Profil oluşturma](profiling-python-code-in-visual-studio.md)

    CPython tabanlı bir yorumlayıcı kullanırken, Python kodunuzu Visual Studio'daki performansını değerlendirebilirsiniz.

    ![Performans raporu profil oluşturma](media/profiling-results.png)

- [Birim Testi](unit-testing-python-in-visual-studio.md)

    Visual Studio, tüm IDE bağlamında birim testleri keşfetmek, çalıştırmak ve hata ayıklama için entegre destek sağlar.

    ![Başarısız test durumunu gösteren birim testi](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Sonraki adımlar

Python'u Visual Studio'da aşağıdaki hızlı başlangıçlardan veya öğreticilerden birini izleyerek daha fazla keşfedin:

> [!div class="nextstepaction"]
> [Quickstart: Flask ile bir web uygulaması oluşturun](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Visual Studio'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Visual Studio'daki Django web çerçevesi ile başlayın](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Visual Studio'daki Flask web çerçevesi ile başlayın](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Diğer Visual Studio özelliklerini](../ide/advanced-feature-overview.md) keşfedin
- [ziyaret visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/) okuyun
