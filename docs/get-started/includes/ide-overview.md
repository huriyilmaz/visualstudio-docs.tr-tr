---
ms.date: 03/19/2019
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jillfra
ms.topic: include
ms.openlocfilehash: 69b1bccf20c242965462b807b2a1b64d3c60d671
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77590830"
---
Visual Studio *Tümleşik geliştirme ortamı* , kod düzenlemek, hatalarını ayıklamak ve derlemek ve ardından bir uygulama yayımlamak için kullanabileceğiniz bir yaratıcı başlatma paneliyle bulunur. Bir tümleşik geliştirme ortamı (IDE) birçok yönüyle yazılım geliştirme için kullanılabilen zengin bir programdır. Standart Düzenleyici ve hata ayıklayıcı sağladığımız çoğu IDE'ler sağlamanızı, Visual Studio yazılım geliştirme işlemini kolaylaştırmak için derleyiciler, kod tamamlama araçları, grafik tasarımcıları ve daha birçok özellik içerir.

::: moniker range="vs-2017"

![Visual Studio 2017 IDE](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[Visual Studio 2019 IDE ![](../media/vs-2019/ide-overview.png)](../media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Bu görüntü, büyük olasılıkla kullanacağınız birkaç anahtar araç pencereleri ve bir Proje Aç ile Visual Studio gösterir:

- [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md) (sağ üst) kod dosyalarınızı görüntülemenize, gezinmenize ve yönetmenize olanak sağlar. **Çözüm Gezgini** , dosyaları [çözümler ve projelerle](../tutorial-projects-solutions.md)gruplayarak kodunuzun düzenlenmesine yardımcı olabilir.

- Büyük olasılıkla zaman harcamanız gereken [Düzenleyici penceresi](../../ide/writing-code-in-the-code-and-text-editor.md) (Center), dosya içeriklerini görüntüler. Burada kodunu düzenleyin veya düğme ve metin kutusu içeren bir pencere gibi bir kullanıcı arabirimi tasarım budur.

::: moniker range="vs-2017"

- [Çıkış penceresi](../../ide/reference/output-window.md) (alt orta), Visual Studio 'nun hata ayıklama ve hata iletileri, derleyici uyarıları, yayımlama durumu iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağı kendi sekmesi vardır.

::: moniker-end

- [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts) (sağ alt) [Git](https://git-scm.com/) ve [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts)gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini izlemenize ve kodu başkalarıyla paylaşmanıza olanak sağlar.

## <a name="editions"></a>Sürümler

::: moniker range="vs-2017"

Windows ve Mac için Visual Studio kullanılabilir [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2017 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede Visual Studio 2017'in Windows sürümünde odaklanır.

Visual Studio 2017'in üç sürüm bulunur: Community, Professional ve Enterprise. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio 2017 IDEs 'ı karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

::: moniker range="vs-2019"

Windows ve Mac için Visual Studio kullanılabilir [Mac için Visual Studio](/visualstudio/mac/) , Visual Studio 2019 ile aynı özelliklerin çoğuna sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede, Visual Studio 2019 ' nin Windows sürümü ele alınmaktadır.

Visual Studio 2019: Community, Professional ve Enterprise 'ın üç sürümü vardır. Her sürümde hangi özelliklerin desteklendiği hakkında bilgi edinmek için bkz. [Visual Studio Ides 'ı karşılaştırın](https://visualstudio.microsoft.com/vs/compare/) .

::: moniker-end

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Visual Studio yazılım geliştirme sırasında daha üretken olmanıza yardımcı olan popüler özelliklerinden bazıları şunlardır:

- Dalgalı çizgiler ve [hızlı eylemler](../../ide/quick-actions.md)

   Siz yazarken, hatalar veya kodunuzdaki olası sorunlar için uyarı dalgalı alt çizgiler dalgalı çizgiler var. Bu görsel ipuçları hata derleme sırasında veya programı çalıştırdığınızda bulunmak beklenmeden hemen sorunları düzeltmek etkinleştirin. Bir dalgalı çizgi gelin, hatayla ilgili ek bilgileri görürsünüz. Hatayı düzeltmek için hızlı Eylemler bilinen eylemlerle sol kenar boşluğunda bir ampul de görünebilir.

   ![Visual Studio'da dalgalı çizgiler](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Kod temizleme

   Bir düğmeye tıklayarak kodunuzu biçimlendirin ve [kod stili ayarlarınız](../../ide/reference/options-text-editor-csharp-formatting.md), [. Editorconfig kuralları](../../ide/create-portable-custom-editor-options.md)ve [Roslyn çözümleyiciler](../../code-quality/roslyn-analyzers-overview.md)tarafından önerilen tüm kod düzeltmelerini uygulayın. Kod **Temizleme** , kod incelemeye geçmeden önce kodunuzda sorunları çözmenize yardımcı olur. (Şu anda yalnızca C# kod için kullanılabilir.)

   ![Visual Studio 'da kod temizleme düğmesi](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Yeniden Düzenleme](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, bir veya daha fazla kod satırlarını yöntem parametreleri ve daha fazlasını sırasını değiştirerek yeni bir yönteme ayıklama değişkenlerin akıllı yeniden adlandırma gibi işlemleri içerir.

   ![Visual Studio'da yeniden düzenleme](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense, doğrudan düzenleyicide kod hakkında bilgi görüntüler ve bazı durumlarda, küçük kod parçalarını sizin için yazma özellikleri kümesi için kullanılan bir terimdir. Bu temel belgeleri satır içi başka bir yerde türü bilgi aramak zorunda kalmaktan kurtarır düzenleyicisinde gibidir. IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için bkz [ C# . IntelliSense](../../ide/visual-csharp-intellisense.md), [ C++ Visual IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md)ve [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). Aşağıdaki çizimde, IntelliSense üye listesi bir türü için nasıl görüntülediğini gösterir:

   ![Visual Studio üye listesi](../media/intellisense-list-members.png)

- Arama kutusu

   Visual Studio zamanlarda sürü menüleri, seçenekleri ve özellikleri ile zor görünebilir. Arama kutusu, Visual Studio 'da gerekenleri hızlı bir şekilde bulmanın harika bir yoludur. Aradığınız bir şey adını yazmaya başladığınızda, Visual Studio tam olarak gitmek gerek duyduğunuz aldığınız sonuçları listeler. Visual Studio 'ya işlevsellik eklemeniz gerekiyorsa, örneğin ek bir programlama dili için destek eklemek istiyorsanız, arama kutusu, bir iş yükünü veya tek bir bileşeni yüklemek için Visual Studio Yükleyicisi açan sonuçlar sağlar.

   > [!TIP]
   > Arama kutusunun bir kısayolu olarak **Ctrl**+**Q** tuşuna basın.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 'de Hızlı Başlat arama kutusu](../media/quick-launch-nuget.png)

   Daha fazla bilgi için bkz. [Hızlı başlatma](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 'de arama kutusu](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türü veya programlama diliniz ne olursa olsun, başkalarıyla birlikte düzenleme ve hata ayıklama işlemlerini gerçek zamanlı olarak yapın. Projenizi anında ve güvenli bir şekilde paylaşabilir, gerekirse hata ayıklama oturumları, Terminal örnekleri, localhost Web Apps, sesli çağrılar ve daha fazlasını yapabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   **Çağrı hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu, değiştirme veya kaldırma yöntemi düşündüğünüzü yararlı bilgiler olması veya bir hatayı izlemek çalışırken oluşturabilirsiniz.

   ![Çağrı hiyerarşisi penceresi](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, kodunuz için başvurular bulmanıza yardımcı olur, düzenleyiciden çıkmadan, kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testleri değiştirir.

   ![CodeLens](../media/codelens-overview.png)

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma özelliği, doğrudan bir işlev veya tür tanımlandığı konumuna götürür.

   ![Tanıma Git](../media/go-to-definition-menu.png)

- [Açıklama Özeti](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Özet **tanım** penceresi, aslında ayrı bir dosya açmadan bir yöntemin veya türün tanımını gösterir.

   ![Tanıma göz at](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE yükleyin

Bu bölümde, Visual Studio ile yapabileceğiniz bazı şeyleri denemek için basit bir proje oluşturacaksınız. [IntelliSense](../../ide/using-intellisense.md) 'i kodlama Yardımcısı olarak kullanacaksınız, programın yürütülmesi sırasında bir değişkenin değerini görmek için bir uygulamanın hatalarını ayıkladığınızda ve renk temasını değiştireceksiniz.

::: moniker range="vs-2017"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini*seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

::: moniker range=">=vs-2019"

Başlamak için [Visual Studio 'yu indirin](https://visualstudio.microsoft.com/downloads) ve sisteminize yükleyin. Modüler yükleyici, tercih ettiğiniz programlama dili veya platformu için gereken özellik grupları olan *iş yüklerini*seçmenizi ve yüklemenizi sağlar. [Program oluşturma](#create-a-program)adımlarını izlemek için, yükleme sırasında **.NET Core platformlar arası geliştirme** iş yükünü seçtiğinizden emin olun.

::: moniker-end

![.NET core çoklu platform geliştirme iş yükünü Visual Studio yükleyicisi](../media/dotnet-core-cross-platform-workload.png)

Visual Studio 'Yu ilk kez açtığınızda, isteğe bağlı olarak Microsoft hesabı veya iş veya okul hesabınızı kullanarak [oturum](../../ide/signing-in-to-visual-studio.md) açabilirsiniz.

## <a name="create-a-program"></a>Bir program oluşturma

Şimdi kolları sıvayın ve basit bir program oluşturun.

::: moniker range="vs-2017"

1. Visual Studio’yu açın.

1. Menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

   ![Dosya > Yeni Proje menü çubuğunda](../media/file-new-project-menu.png)

   **Yeni proje** iletişim kutusunda çeşitli proje *şablonları*gösterilmektedir. Şablon, belirtilen proje türü için gereken ayarları ve temel dosyaları içerir.

1. **Görsel C#** altında **.NET Core** şablon kategorisini seçin ve **konsol uygulaması (.NET Core)** şablonunu seçin. **Ad** metin kutusuna **HelloWorld**yazın ve **Tamam** düğmesini seçin.

   ![.NET core uygulaması şablonu](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > **.NET Core** kategorisini görmüyorsanız **.NET Core platformlar arası geliştirme** iş yükünü yüklemeniz gerekir. Bunu yapmak için, **Yeni proje** iletişim kutusunun sol alt kısmındaki **Aç Visual Studio yükleyicisi** bağlantısını seçin. Visual Studio Yükleyicisi açıldıktan sonra, aşağı kaydırarak **.NET Core platformlar arası geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

   Visual Studio projesi oluşturur. "Merhaba Dünya!" değişmez dizesini göstermek için <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemini çağıran basit bir "Merhaba Dünya" uygulaması (program çıktısı) konsol penceresinde.

   Kısa bir süre sonra aşağıdaki gibi görmeniz gerekir:

   ![Visual Studio IDE](../media/overview-ide-console-app.png)

   Alanı çoğu alan Düzenleyicisi penceresinde, uygulamanız için C# kodunu gösterir. Farklı anahtar sözcükleri ve türleri gibi bir kod bölümlerini göstermek için metni otomatik olarak renklendirilmiş dikkat edin. Ayrıca, hangi küme ayraçları başka bir eşleşen küçük, dikey kesikli satır kodda belirtmek ve satır numaralarını Yardım kodu daha sonra bulun. Daraltma veya genişletme kod blokları için küçük, kutulanmış eksi işaretleri seçebilirsiniz. Anahat oluşturma özelliği bu kod, ekranda dağınıklığı aza indirilmesine yardımcı ihtiyacınız olmayan kodu Gizle olanak tanır. Proje dosyaları, **Çözüm Gezgini**adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutuları ile Visual Studio IDE](../media/overview-ide-console-app-red-boxes.png)

   Kullanılabilir diğer menüleri ve araç pencerelerini, ancak geçelim şimdilik.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. Ayrıca, **Ctrl**+**F5**tuşuna da basabilirsiniz.

   ![Hata ayıklama > menü hata ayıklama olmadan Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanın var!

   ![Konsol penceresi](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulama için bazı ek kod ekleyelim. Aşağıdaki C# kodu `Console.WriteLine("Hello World!");`satırı önüne ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. `Console.WriteLine("Hello World!");` belirten satırı aşağıdaki kodla değiştirin:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **Hata ayıkla** > **başla** ' yı seçerek veya **CTRL**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulaması oluşturur ve bir konsol penceresi açar ve sizden adınız için ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Konsol penceresi girdisi](../media/overview-console-input.png)

1. Konsol penceresini kapatın ve çalışan programa durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio’yu açın.

   Başlangıç penceresi, bir depoyu kopyalamaya, yeni bir projeyi açmaya veya yepyeni bir proje oluşturmaya yönelik çeşitli seçeneklerle birlikte görüntülenir.

1. **Yeni proje oluştur**öğesini seçin.

   ![Visual Studio başlangıç penceresi yeni bir proje oluştur](../media/vs-2019/start-window-create-new-project.png)

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu*gösterir. Şablon, belirtilen proje türü için gereken ayarları ve temel dosyaları içerir.

1. İstediğimiz şablonu bulmak için arama kutusuna **.NET Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Ayrıca, **C#** **dil** açılan listesinden seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz. **Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.

    ![Visual Studio 'da yeni proje oluşturma](../media/vs-2019/create-new-project.png)

1. **Yeni projenizi yapılandırın** penceresinde, **Proje adı** kutusuna **HelloWorld** girin, isteğe bağlı olarak proje dosyalarınızın dizin konumunu değiştirin ve ardından **Oluştur**' u seçin.

   ![Visual Studio 'da yeni proje yapılandırma](../media/vs-2019/configure-new-project.png)

   Visual Studio projesi oluşturur. "Merhaba Dünya!" değişmez dizesini göstermek için <xref:System.Console.WriteLine?displayProperty=nameWithType> yöntemini çağıran basit bir "Merhaba Dünya" uygulaması (program çıktısı) konsol penceresinde.

   Kısa bir süre sonra aşağıdaki gibi görmeniz gerekir:

   ![Visual Studio IDE](../media/vs-2019/overview-ide-console-app.png)

   Alanı çoğu alan Düzenleyicisi penceresinde, uygulamanız için C# kodunu gösterir. Farklı anahtar sözcükleri ve türleri gibi bir kod bölümlerini göstermek için metni otomatik olarak renklendirilmiş dikkat edin. Ayrıca, hangi küme ayraçları başka bir eşleşen küçük, dikey kesikli satır kodda belirtmek ve satır numaralarını Yardım kodu daha sonra bulun. Daraltma veya genişletme kod blokları için küçük, kutulanmış eksi işaretleri seçebilirsiniz. Anahat oluşturma özelliği bu kod, ekranda dağınıklığı aza indirilmesine yardımcı ihtiyacınız olmayan kodu Gizle olanak tanır. Proje dosyaları, **Çözüm Gezgini**adlı bir pencerenin sağ tarafında listelenir.

   ![Kırmızı kutuları ile Visual Studio IDE](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Kullanılabilir diğer menüleri ve araç pencerelerini, ancak geçelim şimdilik.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. Ayrıca, **Ctrl**+**F5**tuşuna da basabilirsiniz.

   ![Hata ayıklama > menü hata ayıklama olmadan Başlat](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanın var!

   ![Konsol penceresi](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulama için bazı ek kod ekleyelim. Aşağıdaki C# kodu `Console.WriteLine("Hello World!");`satırı önüne ekleyin:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. `Console.WriteLine("Hello World!");` belirten satırı aşağıdaki kodla değiştirin:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **Hata ayıkla** > **başla** ' yı seçerek veya **CTRL**+**F5**tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulaması oluşturur ve bir konsol penceresi açar ve sizden adınız için ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Konsol penceresi](../media/vs-2019/overview-console-input.png)

1. Konsol penceresini kapatın ve çalışan programa durdurmak için herhangi bir tuşa basın.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) 'in daha verimli bir şekilde kodlamasına yardımcı olması için birkaç yol göz atalım.

İlk olarak `name` değişkenini yeniden adlandıralım:

1. `name` değişkenine çift tıklayarak seçin.

2. Değişken için yeni adı yazın, **Kullanıcı**adı.

   Değişkeni ve bir ampul gri kutu göründüğüne dikkat edin, kenar boşluğunda görünür.

::: moniker range="vs-2017"

3. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ![Visual Studio'da eylemini yeniden adlandır](../media/rename-quick-action.png)

   Değişkeni, bu örnekte yalnızca iki basamağı olan proje boyunca yeniden adlandırılır.

   ![Visual Studio'da yeniden adlandırma düzenlemesi gösteren animasyonlu gif](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ![Visual Studio'da eylemini yeniden adlandır](../media/vs-2019/rename-quick-action.png)

   Değişkeni, bu örnekte yalnızca iki basamağı olan proje boyunca yeniden adlandırılır.

::: moniker-end

4. Artık IntelliSense bir göz atalım. `Console.WriteLine($"\nHello {username}!");`belirten satırın altında `DateTime now = DateTime.`yazın.

   Bir kutu <xref:System.DateTime> sınıfının üyelerini görüntüler. Ayrıca, ayrı bir kutuda şu anda seçilen üyenin açıklamasını görüntüler.

   ![Visual Studio IntelliSense üyeleri Listele](../media/intellisense-list-members.png)

5. Sınıfın bir özelliği olan, bu adı çift tıklayarak veya **sekme**tuşuna basarak **Şimdi**adlı üyeyi seçin. Uca noktalı virgül ekleyerek kod satırını doldurun.

6. Bunun yerine, aşağıdaki kod satırlarını yazın veya yapıştırın:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType>, yazdırıldıktan sonra satır Sonlandırıcı eklememesi için <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> biraz farklıdır. Bu sonraki çıkışa gönderilir metin parçası aynı satırda yazdırılır anlamına gelir. Bu yöntemlerin her biri kendi açıklamasını görmek için kodunuzda gelebilirsiniz.

7. Ardından, yeniden yeniden düzenleme kod biraz daha kısa olmak için kullanacağız. Satır `DateTime now = DateTime.Now;``now` değişkenine tıklayın.

   Kenar boşluğunda bu satırdaki bir tornavida ikonu görüntülendiğine dikkat edin.

8. Önerileri görmek için tornavida simgesine tıklayarak Visual Studio kullanılabilir sahiptir. Bu durumda, kodun genel davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösteriliyor:

   ![Satır içi geçici değişken Visual Studio'da yeniden düzenleme](../media/inline-temporary-variable-refactoring.png)

9. Kodu yeniden düzenleme için **satır içi geçici değişken** ' e tıklayın.

::: moniker range="vs-2017"

10. **Ctrl**+**F5**tuşuna basarak programı yeniden çalıştırın. Çıktı aşağıdakine benzer olacaktır:

    ![Konsol penceresi ile program çıktısı](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. **Ctrl**+**F5**tuşuna basarak programı yeniden çalıştırın. Çıktı aşağıdakine benzer olacaktır:

    ![Konsol penceresi ile program çıktısı](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code"></a>Kodda hata ayıklama

Kod yazmak, çalıştırmak ve hatalar için test gerekir. Visual Studio'nun hata ayıklama sistem aynı anda bir deyim kod adım adım ve kullandıkça, değişkenleri inceleyebilir olanak sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* belirleyebilirsiniz. Bir değişken değişiklikleri değeri olarak kodu nasıl çalıştığını ve daha fazlasını gözlemleyebilirsiniz.

Program "uçuş aşamasında" iken `username` değişkeninin değerini görmek için bir kesme noktası ayarlayalım.

1. `Console.WriteLine($"\nHello {username}!");`belirten kod satırını bulun. Bu kod satırı, programın bu satırı yürütmeyi Duraklat yapmak için diğer bir deyişle, bir kesme noktası ayarlamak için düzenleyicisinin en sol kenar boşluğunda tıklayın. Ayrıca kod satırında herhangi bir yere tıklayabilir ve ardından **F9**' e basabilirsiniz.

   Kırmızı bir daire en sol kenar boşluğunda görünür ve kodu vurgulanır.

   ![Visual Studio'da kod satırında kesme noktası](../media/breakpoint.png)

1. Hata ayıklamayı Başlat > **hata** **ayıklamayı başlatın** veya **F5**'e basarak hata ayıklamayı başlatın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde, yazın ve **ENTER**tuşuna basın.

   Odak, Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Bu program yürütülen kodun sonraki satıra olduğunu gösterir.

1. Değerini görmek için farenizi `username` değişkenin üzerine getirin. Alternatif olarak, `username` ' a sağ tıklayıp, sonra da bu değişkenin değerini görebileceğiniz **izleme** penceresine eklemek Için **Gözcü Ekle** ' yi seçebilirsiniz.

   ![Visual Studio'da hata ayıklama sırasında değişken değeri](../media/debugging-variable-value.png)

1. Programın tamamlanmasını çalışmasına izin vermek için **F5** tuşuna basın.

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcı Özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Visual Studio'yu özelleştirme

Varsayılan renk temasını değiştirme dahil olmak üzere Visual Studio kullanıcı arabirimi kişiselleştirebilirsiniz. **Koyu** temaya geçiş yapmak için:

1. **Seçenekler** iletişim kutusunu açmak için menü çubuğunda **Araçlar** > **Seçenekler** ' i seçin.

::: moniker range="vs-2017"

2. **Ortam** > **genel** Seçenekler sayfasında, **renk teması** seçimini **koyu**olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu**olarak değişir.

   ![Visual Studio'da koyu tema](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Ortam** > **genel** Seçenekler sayfasında, **renk teması** seçimini **koyu**olarak değiştirin ve ardından **Tamam**' ı seçin.

   IDE 'nin tamamına yönelik renk teması **koyu**olarak değişir.

   ![Visual Studio'da koyu tema](../media/vs-2019/dark-theme.png)

::: moniker-end

IDE 'yi kişiselleştirmek için kullanabileceğiniz diğer yollar hakkında bilgi edinmek için bkz. [Visual Studio 'Yu kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).