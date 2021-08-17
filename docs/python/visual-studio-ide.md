---
description: Visual Studio tümleşik geliştirme ortamı, Python (ve diğer diller) için kod düzenlemek, hatalarını ayıklamak ve test etmek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma tablası.
title: Python geliştiricileri için Visual Studio genel bakış
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: a81616e50cc4f7a3aab5fc4ccfa52d378eeb34d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027285"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Visual Studio ıde 'ye hoş geldiniz | Python

Visual Studio *tümleşik geliştirme ortamı* , Python (ve diğer diller) için kod düzenlemek, hatalarını ayıklamak ve test etmek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma tablası. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen özellik açısından zengin bir programdır. standart düzenleyicinin ve üzerinde birçok ıdes 'in sağladığı hata ayıklayıcı, Visual Studio kod tamamlama araçları, etkileşimli REPL ortamları ve yazılım geliştirme sürecini kolaylaştırmak için diğer özellikleri içerir.

[![Python projesiyle Visual Studio](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

bu görüntüde, açık bir Python projesi ve büyük olasılıkla kullanabileceksiniz birçok anahtar araç penceresi içeren Visual Studio gösterilmektedir:

- [**Çözüm Gezgini**](../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](../get-started/tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.
  - **Çözüm Gezgini** yanı sıra, bilgisayarınızda yüklü farklı Python yorumlayıcıları yönettiğiniz [**Python ortamlardır**](managing-python-environments-in-visual-studio.md).

  ::: moniker range=">=vs-2019"
  - ayrıca, Visual Studio proje ve çözüm dosyaları oluşturmadan bir klasörde Python kodu açabilir ve çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Bu, [Python kodunu düzenlediğiniz](editing-python-code-in-visual-studio.md), kod yapınız içinde gezinmeniz ve hata ayıklama oturumları sırasında kesme noktaları ayarlamanız yerdir. Python ile kod seçip CTRL + ENTER tuşlarına basarak bu kodu [etkileşimli BIR REPL penceresinde](python-interactive-repl-in-visual-studio.md)çalıştırabilirsiniz.

- [çıkış penceresi](../ide/reference/output-window.md) (alt orta), Visual Studio hata ayıklama ve hata iletileri, uyarılar, yayımlama durumu iletileri ve daha fazlası gibi bildirimleri gönderir. Her ileti kaynağının kendi sekmesi vardır.
  - Bir [Python ETKILEŞIMLI REPL penceresi](python-interactive-repl-in-visual-studio.md) , çıkış penceresiyle aynı alanda görüntülenir.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation Sürüm Denetimi (tfvc)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

Visual Studio Windows ve Mac için kullanılabilir; ancak, Python desteği yalnızca Windows için Visual Studio kullanılabilir.

Windows Visual Studio üç sürümü vardır: Community, Professional ve Enterprise. her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Compare Visual Studio ıdes](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

yazılım geliştirirken daha üretken olmanıza yardımcı olan Visual Studio popüler özelliklerden bazıları şunlardır:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen özellikler kümesi için bir terimdir ve bazı durumlarda, sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu da tür bilgilerini başka bir yerde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir ve [Python kodunu Düzenle](editing-python-code-in-visual-studio.md#intellisense) makalesinde Python için ayrıntılar bulunur. Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ![Visual Studio ıntellisense ile üye tamamlama](media/code-editing-completions-simple.png)

- [Yeniden Düzenle](refactoring-python-code.md)

   bir kod parçasına sağ tıklayıp **hızlı eylemler ve yeniden düzenlemeler**' i seçerek, Visual Studio değişkenlerin akıllı yeniden adlandırma, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemler sağlar.

   ![Visual Studio'da yeniden düzenleme](media/tour-ide-refactor-extract-method.png)

- [Lint uygulama](refactoring-python-code.md)

   Python kodunuzda hata ve yaygın sorunlar olup olmadığını denetler, size iyi Python kodlama desenleri teşvik.

   ![Python projeleri için bağlam menüsünde Pylınt komutu](media/code-pylint-command.png)

- Arama kutusu

   Visual Studio birçok menü, seçenek ve özellik ile zaman içinde çok daha fazla görünebilir. Arama kutusu, Visual Studio ihtiyacınız olanları hızlı bir şekilde bulmanın harika bir yoludur. aradığınız bir şeyin adını yazmaya başladığınızda Visual Studio, sizi tam olarak gitmeniz gereken yere götürür sonuçları listeler. Visual Studio işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek üzere arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   ![Visual Studio arama kutusu](media/tour-ide-quick-launch.png)

- Dalgalı çizgiler ve [hızlı eylemler](../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, hata oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları anında çözmenizi sağlar. Dalgalı bir çizgi üzerine geldiğinizde, hatayla ilgili ek bilgileri görürsünüz. Ayrıca, bir ampulü, hızlı eylemler olarak bilinen eylemlerle birlikte, hatayı düzelrebilir.

   ![Visual Studio dalgalı çizgiler](media/tour-ide-squiggles.png)

- [Git ve açıklama Özeti](../ide/go-to-and-peek-definition.md)

   **Tanıma Git** özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür. **Tanımları göz atma** komutu, tanımı ayrı bir dosya açmadan bir pencerede görüntüler. **Tüm başvuruları bul** komutu ayrıca, verilen ve kullanılan her bir tanımlayıcının nerede tanımlanmakta olduğunu bulmanın yararlı bir yolunu sağlar.

   ![Kod Gezinti komutları](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Python için güçlü özellikler

::: moniker range=">=vs-2019"
- [Kodu proje olmadan çalıştırma](quickstart-05-python-visual-studio-open-folder.md)

    Visual Studio 2019 ' den başlayarak, kod için bir Visual Studio projesi oluşturmaya gerek kalmadan ıntellisense ve hata ayıklama gibi özelliklerden yararlanabilmek için Python kodu içeren bir klasörü açabilirsiniz.
::: moniker-end

- [Visual Studio’yu kullanarak işbirliği yapma](/visualstudio/liveshare/)

    Visual Studio Live Share, kullandığınız programlama diline veya oluşturmakta olduğunuz uygulama türlerine bakılmaksızın diğer kişilerle gerçek zamanlı olarak birlikte düzenleme ve hata ayıklama yapmanızı sağlar.

- [Python etkileşimli REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio, Python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (repl) penceresi sağlar. bu, komut satırında *python.exe* sahip olduğunuz REPL üzerinde geliştirilir. **Etkileşimli** pencerede, rastgele Python kodu girebilir ve anında sonuçlara bakabilirsiniz.

    ![Python etkileşimli penceresi](media/interactive-window.png)

- [Hata Ayıklama](debugging-python-in-visual-studio.md)

    Visual Studio, çalışan işlemlere ekleme, **izleme** ve **anında** windows 'da ifadeleri değerlendirme, yerel değişkenleri belirleme, kesme noktaları, step ın/out/over deyimleri, **sonraki deyimi** ve daha fazlasını belirleme dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar. Ayrıca, Linux bilgisayarlarda çalışan uzaktan Python kodunda hata ayıklayabilirsiniz.

    ![Visual Studio Python 'da hata ayıklama](media/remote-debugging-breakpoint-hit.png)

- [C++ ile etkileşim kurma](working-with-c-cpp-python-in-visual-studio.md)

    Python için oluşturulan birçok kitaplık, en iyi performans için C++ dilinde yazılmıştır. Visual Studio, [karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)da dahil olmak üzere C++ uzantıları geliştirmeye yönelik zengin olanaklar sağlar.

    ![Python ve C++ ile birlikte karışık modda hata ayıklama](media/mixed-mode-debugging.png)

- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)

    Bir cpi tabanlı yorumlayıcı kullanırken, Visual Studio içinde Python kodunuzun performansını değerlendirebilirsiniz.

    ![Profil oluşturma performans raporu](media/profiling-results.png)

- [Birim testi](unit-testing-python-in-visual-studio.md)

    Visual Studio, tüm ıde bağlamındaki birim testlerini bulmak, çalıştırmak ve hata ayıklamak için tümleşik destek sağlar.

    ![Başarısız test durumunu gösteren birim testi](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki hızlı başlangıçlardan veya öğreticilerden birini izleyerek Visual Studio Python 'u daha fazla inceleyin:

> [!div class="nextstepaction"]
> [Hızlı başlangıç: Flask ile Web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Visual Studio 'de Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Visual Studio 'de Docgo Web çerçevesini kullanmaya başlayın](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Visual Studio ' de Flask Web çerçevesini kullanmaya başlayın](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Ayrıca bkz.

- [daha fazla Visual Studio özellik](../ide/advanced-feature-overview.md) bul
- [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/) ziyaret edin
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/) okuyun
