---
title: Python geliştiricileri için Visual Studio 'ya genel bakış
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: b97655efac3fc42f5e5790e32c97de169e61a6b5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520594"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Visual Studio IDE 'ye hoş geldiniz | Python

Visual Studio *Tümleşik geliştirme ortamı* , Python (ve diğer diller) için kod düzenlemek, hatalarını ayıklamak ve test etmek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma tablası. Tümleşik geliştirme ortamı (IDE), yazılım geliştirmenin birçok yönü için kullanılabilen özellik açısından zengin bir programdır. En çok kullanılan standart düzenleyici ve hata ayıklayıcı üzerinde ve üzerinde, Visual Studio, yazılım geliştirme sürecini kolaylaştırmak için kod tamamlama araçları, etkileşimli REPL ortamları ve diğer özellikleri içerir.

[![Python projesiyle Visual Studio](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

Bu görüntüde, açık bir Python projesiyle Visual Studio ve büyük olasılıkla kullanabileceksiniz birçok anahtar araç penceresi gösterilmektedir:

- [**Çözüm Gezgini**](../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](../get-started/tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.
  - **Çözüm Gezgini** yanı sıra, bilgisayarınızda yüklü farklı Python yorumlayıcıları yönettiğiniz [**Python ortamlardır**](managing-python-environments-in-visual-studio.md).

  ::: moniker range=">=vs-2019"
  - Ayrıca, Visual Studio proje ve çözüm dosyaları oluşturmadan bir klasörde Python kodu açabilir ve çalıştırabilirsiniz. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md).
  ::: moniker-end

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Bu, [Python kodunu düzenlediğiniz](editing-python-code-in-visual-studio.md), kod yapınız içinde gezinmeniz ve hata ayıklama oturumları sırasında kesme noktaları ayarlamanız yerdir. Python ile kod seçip CTRL + ENTER tuşlarına basarak bu kodu [etkileşimli BIR REPL penceresinde](python-interactive-repl-in-visual-studio.md)çalıştırabilirsiniz.

- [Çıkış penceresi](../ide/reference/output-window.md) (alt orta), Visual Studio 'nun hata ayıklama ve hata iletileri, uyarılar, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.
  - Bir [Python ETKILEŞIMLI REPL penceresi](python-interactive-repl-in-visual-studio.md) , çıkış penceresiyle aynı alanda görüntülenir.

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

Visual Studio, Windows ve Mac için kullanılabilir; Ancak, Python desteği yalnızca Windows için Visual Studio 'da kullanılabilir.

Windows üzerinde Visual Studio 'nun üç sürümü vardır: Community, Professional ve Enterprise. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio Ides 'ı karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio 'da, yazılım geliştirirken daha üretken olmanıza yardımcı olan popüler özelliklerden bazıları şunlardır:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntüleyen özellikler kümesi için bir terimdir ve bazı durumlarda, sizin için küçük bit kod yazın. Temel belgeleri düzenleyicide satır içine almak gibidir, bu da tür bilgilerini başka bir yerde aramak zorunda kalmanızı sağlar. IntelliSense özellikleri dile göre farklılık gösterir ve [Python kodunu Düzenle](editing-python-code-in-visual-studio.md#intellisense) makalesinde Python için ayrıntılar bulunur. Aşağıdaki çizimde, IntelliSense 'in bir tür için üye listesini nasıl görüntüleyeceği gösterilmektedir:

   ![Visual Studio IntelliSense ile üye Tamamlama](media/code-editing-completions-simple.png)

- [Yeniden Düzenle](refactoring-python-code.md)

   Kod parçasına sağ tıklayıp **Hızlı Eylemler ve yeniden düzenlemeler**' i seçerek Visual Studio size değişkenlerin akıllı yeniden adlandırılması, bir veya daha fazla kod satırını yeni bir yönteme ayıklama, yöntem parametrelerinin sırasını değiştirme ve daha fazlası gibi işlemler sağlar.

   ![Visual Studio'da yeniden düzenleme](media/tour-ide-refactor-extract-method.png)

- [Lint uygulama](refactoring-python-code.md)

   Python kodunuzda hata ve yaygın sorunlar olup olmadığını denetler, size iyi Python kodlama desenleri teşvik.

   ![Python projeleri için bağlam menüsünde Pylınt komutu](media/code-pylint-command.png)

- Arama kutusu

   Visual Studio çok sayıda menü, seçenek ve özellik ile zaman içinde yoğun görünebilir. Arama kutusu, Visual Studio 'da gerekenleri hızlı bir şekilde bulmanın harika bir yoludur. Aradığınız bir şeyin adını yazmaya başladığınızda, Visual Studio size tam olarak gitmeniz gereken yere sahip olan sonuçları listeler. Visual Studio 'ya işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek istiyorsanız, arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   ![Visual Studio 'da arama kutusu](media/tour-ide-quick-launch.png)

- Dalgalı çizgiler ve [hızlı eylemler](../ide/quick-actions.md)

   Dalgalı çizgiler, siz yazarken kodunuzda hataları veya olası sorunları uyaran dalgalı alt çizgiler. Bu görsel ipuçları, hata oluşturma sırasında veya programı çalıştırdığınızda hatanın bulunmasını beklemeden sorunları anında çözmenizi sağlar. Dalgalı bir çizgi üzerine geldiğinizde, hatayla ilgili ek bilgileri görürsünüz. Ayrıca, bir ampulü, hızlı eylemler olarak bilinen eylemlerle birlikte, hatayı düzelrebilir.

   ![Visual Studio 'da dalgalı çizgiler](media/tour-ide-squiggles.png)

- [Git ve açıklama Özeti](../ide/go-to-and-peek-definition.md)

   **Tanıma Git** özelliği sizi doğrudan bir işlevin veya türün tanımlandığı konuma götürür. **Tanımları göz atma** komutu, tanımı ayrı bir dosya açmadan bir pencerede görüntüler. **Tüm başvuruları bul** komutu ayrıca, verilen ve kullanılan her bir tanımlayıcının nerede tanımlanmakta olduğunu bulmanın yararlı bir yolunu sağlar.

   ![Kod Gezinti komutları](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Python için güçlü özellikler

::: moniker range=">=vs-2019"
- [Kodu proje olmadan çalıştırma](quickstart-05-python-visual-studio-open-folder.md)

    Visual Studio 2019 ' den başlayarak, kod için bir Visual Studio projesi oluşturmak zorunda kalmadan IntelliSense ve hata ayıklama gibi özelliklerden yararlanabilmek için Python kodu içeren bir klasörü açabilirsiniz.
::: moniker-end

- [Visual Studio’yu kullanarak işbirliği yapma](/visualstudio/liveshare/)
  
    Visual Studio Live Share, kullandığınız programlama diline veya oluşturmakta olduğunuz uygulama türlerine bakılmaksızın diğer kişilerle gerçek zamanlı olarak birlikte düzenleme ve hata ayıklama yapmanızı sağlar. 

- [Python etkileşimli REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio, Python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar. Bu, komut satırında *python.exe* Ile aldığınız REPL üzerinde iyileşir. **Etkileşimli** pencerede, rastgele Python kodu girebilir ve anında sonuçlara bakabilirsiniz.

    ![Python etkileşimli penceresi](media/interactive-window.png)

- [Hata Ayıklama](debugging-python-in-visual-studio.md)

    Visual Studio, çalışan işlemlere ekleme, **izleme** ve **anında** Windows 'da ifadeleri değerlendirme, yerel değişkenler, kesme noktaları, Step in/out/Over deyimlerini **belirleme, sonraki deyimi ayarlama**ve daha fazlası dahil olmak üzere Python için kapsamlı bir hata ayıklama deneyimi sağlar. Ayrıca, Linux bilgisayarlarda çalışan uzaktan Python kodunda hata ayıklayabilirsiniz.

    ![Visual Studio 'da Python 'da hata ayıklama](media/remote-debugging-breakpoint-hit.png)

- [C++ ile etkileşim kurma](working-with-c-cpp-python-in-visual-studio.md)

    Python için oluşturulan birçok kitaplık, en iyi performans için C++ dilinde yazılmıştır. Visual Studio, [karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)da dahil olmak üzere C++ uzantıları geliştirmeye yönelik zengin olanaklar sunar.

    ![Python ve C++ ile birlikte karışık modda hata ayıklama](media/mixed-mode-debugging.png)

- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)

    Bir Cpithon tabanlı yorumlayıcı kullanırken, Visual Studio içinde Python kodunuzun performansını değerlendirebilirsiniz.

    ![Profil oluşturma performans raporu](media/profiling-results.png)

- [Birim testi](unit-testing-python-in-visual-studio.md)

    Visual Studio, IDE bağlamında birim testlerini bulmak, çalıştırmak ve hata ayıklamak için tümleşik destek sağlar.

    ![Başarısız test durumunu gösteren birim testi](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki hızlı başlangıçlardan veya öğreticilerden birini izleyerek Visual Studio 'da Python 'u daha fazla inceleyin:

> [!div class="nextstepaction"]
> [Hızlı başlangıç: Flask ile Web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Visual Studio 'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Visual Studio 'da Docgo Web çerçevesini kullanmaya başlama](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Visual Studio 'da Flask Web çerçevesi ile çalışmaya başlama](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Daha fazla Visual Studio özelliği](../ide/advanced-feature-overview.md) bulun
- [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/) ziyaret edin
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/) okuyun
