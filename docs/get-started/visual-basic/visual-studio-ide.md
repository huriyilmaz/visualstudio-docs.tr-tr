---
title: Visual Basic geliştiricilerine genel bakış
description: Kod düzenlemek Visual Studio hata ayıklamak ve derlemek ve ardından bir uygulamayı geliştirici olarak yayımlamak için Visual Basic öğrenin.
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f2868a4a86f1ce70fbaf9f94bf1c5f3971b45c59
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430009"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Visual Studio IDE | Visual Basic

Tümleşik *geliştirme ortamı* (IDE), yazılım geliştirmenin birçok özelliğini destekleyen zengin bir programdır. IDE Visual Studio düzenleme, hata ayıklama ve kod derleme ve ardından uygulama yayımlamak için kullanabileceğiniz yaratıcı bir başlatma panelidir. Çoğu IDE'nin sağlediği standart düzenleyici ve hata ayıklayıcının üzerinde ve üzerinde, Visual Studio, kod tamamlama araçları, grafik tasarımcıları ve yazılım geliştirme sürecini geliştirmek için daha birçok özellik vardır.

::: moniker range="vs-2017"

![2017 IDE Visual Studio kodunun ekran Visual Basic görüntüsü.](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

[![2019 IDE Visual Studio kodunun ekran Visual Basic görüntüsü.](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/ide-overview.png" alt-text="IDE'Visual Studio kodunun ve Visual Basic işlevlerinin ekran görüntüsü." lightbox="media/vs-2022/ide-overview.png" border="false":::

::: moniker-end

Yukarıdaki görüntüde, Visual Studio pencerelerini ve işlevlerini Visual Basic açık bir Visual Basic açık bir proje ile ilgili bilgiler ve bilgiler yer alelade:

- Bu [Çözüm Gezgini](../../ide/solutions-and-projects-in-visual-studio.md)sağ üst köşedeki kod dosyalarınızı abilir, gezinebilirsiniz ve yönetebilirsiniz. **Çözüm Gezgini,** dosyaları çözümler ve projeler olarak gruplamanıza yardımcı [olabilir.](tutorial-projects-solutions.md)

- Büyük [olasılıkla zaman](../../ide/writing-code-in-the-code-and-text-editor.md)harcamanız gereken merkezi düzenleyici penceresi, dosya içeriğini görüntüler. Düzenleyici penceresinde, kodu düzenleyebilir veya düğmeleri ve metin kutuları olan bir pencere gibi bir kullanıcı arabirimi tasarabilirsiniz.

::: moniker range="vs-2017"

- Çıkış [penceresi](../../ide/reference/output-window.md) (alttaki orta), hata ayıklama Visual Studio hata iletileri, derleyici uyarıları, yayımlama durum iletileri ve daha fazlası gibi bildirimler gönderdiği yerdir. Her ileti kaynağının kendi sekmesi vardır.

::: moniker-end

::: moniker range="<=vs-2019"
- Bu [Takım Gezgini](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true)sağ altta iş öğelerini izleyebilir ve [Git](https://git-scm.com/) ve Team Foundation Sürüm Denetimi [(TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)gibi sürüm denetimi teknolojilerini kullanarak kod paylaşabilirsiniz.
::: moniker-end

::: moniker range=">=vs-2022"
- Sağ [altta](/visualstudio/version-control/) yer alan Git Değişiklikleri'nde, Git ve GitHub gibi sürüm denetimi teknolojilerini kullanarak iş öğelerini [izleyebilir](https://git-scm.com/) ve [diğerleriyle kod GitHub.](https://docs.github.com/github)
::: moniker-end

## <a name="editions"></a>Sürümler

Visual Studio mac ve Windows kullanılabilir. [Mac için Visual Studio,](/visualstudio/mac/) Windows için Visual Studio özelliklere sahiptir ve platformlar arası ve mobil uygulamalar geliştirmek için iyileştirilmiştir. Bu makalede, Windows sürümüne Visual Studio.

Üç sürüm vardır: Visual Studio, Community, Professional ve Enterprise. Her [sürümün Visual Studio hakkında](https://visualstudio.microsoft.com/vs/compare/) bilgi edinmek için bkz. Visual Studio sürümleri karşılaştırma.

## <a name="popular-productivity-features"></a>Popüler üretkenlik özellikleri

Yazılım geliştirme Visual Studio üretkenliğinizi geliştiren bazı popüler özellikler şunlardır:

- Geçişler ve [Hızlı Eylemler](../../ide/quick-actions.md)

  Dalgalı çizgiler, siz yazarak kodundaki hatalara veya olası sorunlara karşı sizi uyaran dalgalı alt çizgilerdir. Bu görsel ipuçları, derleme veya çalışma zamanı sırasında hataları keşfetmeyi beklemeden sorunları hemen düzeltmeye yardımcı olur. Bir geçişin üzerine gelindiğinde hata hakkında daha fazla bilgi alırsınız. Hatayı düzeltmek için gerçekleştirebilir hızlı eylemleri gösteren *sol* kenar boşluğunda bir ampul de görünebilir.

   ::: moniker range="vs-2017"

   ![Visual Studio'da iki durumlu alt çizginin ekran görüntüsü.](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio'da iki durumlu alt çizginin ekran görüntüsü.](media/vs-2019/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/squiggles-error.png" alt-text="Visual Studio'da iki durumlu alt çizginin ekran görüntüsü." border="false":::

   ::: moniker-end

- [Yeniden Düzenle](../../ide/refactoring-in-visual-studio.md)

   Yeniden düzenleme, değişkenlerin akıllı yeniden adı oluşturma, bir veya daha fazla kod satırı ayıklanan yeni bir yöntem ve yöntem parametrelerinin sırası değiştirme gibi işlemleri içerir.

   ::: moniker range="vs-2017"

   ![Visual Studio'daki Yeniden düzenleme menüsünün ekran görüntüsü.](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio'daki Yeniden düzenleme menüsünün ekran görüntüsü.](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/refactoring-menu.png" alt-text="Visual Studio'daki Yeniden düzenleme menüsünün ekran görüntüsü." border="false":::

   ::: moniker-end

- [Intellisense](../../ide/using-intellisense.md)

   IntelliSense, kodunuzla ilgili bilgileri doğrudan düzenleyicide görüntülemenizi ve bazı durumlarda sizin için küçük kod bitlerini yazmanızı sağlar. Bu, düzenleyicide satır içinde temel belgelere sahip olmak gibi bir şey, bu nedenle başka bir yerde tür bilgilerini aramana gerek kalmadan.

   Aşağıdaki çizimde, IntelliSense'in bir tür için üye listesini nasıl görüntülesi gösterilmiştir:

   ::: moniker range="vs-2017"

   ![IntelliSense üye listesinin ekran görüntüsü.](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![IntelliSense üye listesinin ekran görüntüsü.](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/intellisense.png" alt-text="IntelliSense üye listesinin ekran görüntüsü." border="false":::

   ::: moniker-end

   IntelliSense özellikleri dile göre değişiklik gösterir. Daha fazla bilgi için bkz. [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense,](../../ide/visual-cpp-intellisense.md) [JavaScript IntelliSense](../../ide/javascript-intellisense.md) [ve IntelliSense Visual Basic.](../../ide/visual-basic-specific-intellisense.md)

- [Visual Studio arama](../../ide/visual-studio-search.md)

   Visual Studio menüler, seçenekler ve özellikler bazen aşırı zor görünebilir. Visual Studio veya **Ctrl** Q, IDE özelliklerini ve kodunu tek bir yerde hızla + bulmanın harika bir yoludur.

   Aramanız gereken bir şeyin adını yazmaya başladığınızda Visual Studio gereken sonuçları listeler. Başka bir programlama dili gibi işlevler eklemeniz gerekirse, iş yükünü veya bileşeni yüklemek Visual Studio Yükleyicisi arama kutusu sonuçlarından işlevi açabilirsiniz.

   ::: moniker range="vs-2017"

   ![2017'Hızlı Başlat arama kutusunu Visual Studio ekran görüntüsü.](../media/quick-launch-nuget.png)

   Daha fazla bilgi için [bkz. Hızlı Başlat.](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Hızlı Başlat 2019'daki Visual Studio gösteren ekran görüntüsü.](../media/vs-2019/quick-launch-nuget.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/quick-launch-nuget.png" alt-text="Visual Studio'da Hızlı Başlat kutusunu gösteren ekran Visual Studio." border="false":::

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Uygulama türünüz veya programlama diliniz ne olursa olsun, diğerleriyle gerçek zamanlı işbirliği yaparak düzenleme ve hata ayıklama. Projenizi anında ve güvenli bir şekilde paylaşabilirsiniz. Hata ayıklama oturumlarını, terminal örneklerini, localhost web uygulamalarını, sesli çağrıları ve daha fazlasını da paylaşabilirsiniz.

- [Çağrı Hiyerarşisi](../../ide/reference/call-hierarchy.md)

   Çağrı **Hiyerarşisi** penceresi, seçilen bir yöntemi çağıran yöntemleri gösterir. Bu bilgiler, yöntemi değiştirmeyi veya kaldırmayı düşünürken veya bir hatayı bulmaya çalışırken yararlı olabilir.

   ::: moniker range="vs-2017"

   ![Visual Studio'da Arama Hiyerarşisi penceresini gösteren ekran Visual Studio.](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio'da Arama Hiyerarşisi penceresini gösteren ekran Visual Studio.](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/call-hierarchy.png" alt-text="Visual Studio'da Arama Hiyerarşisi penceresini gösteren ekran Visual Studio." border="false":::

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens, düzenleyiciden ayrılmadan kod başvurularını, kod değişikliklerini, bağlantılı hataları, iş öğelerini, kod incelemelerini ve birim testlerini bulumanıza yardımcı olur.

   ::: moniker range="vs-2017"

   ![Visual Studio'da CodeLens'i gösteren ekran görüntüsü.](media/codelens.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio'da CodeLens'i gösteren ekran görüntüsü.](media/vs-2019/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/codelens.png" alt-text="Visual Studio'da CodeLens'i gösteren ekran görüntüsü." border="false":::

   ::: moniker-end

- [Tanıma Git](../../ide/go-to-and-peek-definition.md)

   Tanıma **Git özelliği** sizi doğrudan bir işlevin veya tür tanımının bulunduğu konuma alır.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017'de Tanıma Git'i gösteren ekran görüntüsü.](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019'da Tanıma Git'i gösteren ekran görüntüsü.](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/go-to-definition-menu.png" alt-text="Visual Studio'da Tanıma Git'i gösteren ekran Visual Studio." border="false":::

   ::: moniker-end

- [Tanıma Göz At](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Tanıma **Göz At** penceresinde ayrı bir dosya açılmadan bir yöntem veya tür tanımı gösterilir.

   ::: moniker range="vs-2017"

   ![Visual Studio'da Tanıma Göz At'Visual Studio.](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio'da Tanıma Göz At'Visual Studio.](media/vs-2019/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/peek-definition.png" alt-text="Visual Studio'da Tanıma Göz At'Visual Studio." border="false":::

   ::: moniker-end

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

Bu bölümde, yeni bir proje oluşturarak bu projeyle mümkün olan en iyi şekilde Visual Studio. Renk temasını değiştirme, kodlama yardımı olarak [IntelliSense](../../ide/using-intellisense.md) kullanma ve uygulama yürütme sırasında değişken değerini görmek için uygulamada hata ayıklamayı öğrenirsiniz.

::: moniker range="vs-2017"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirin ve sisteminize yükleyin. Modüler yükleyici, tercih ettiği programlama dili veya platform için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için](#create-a-program)yükleme sırasında .NET Core platformlar arası geliştirme iş yükünü **seçin.**

![Ağ geçidinde nokta NET Core platformlar arası geliştirme iş yükünün Visual Studio Yükleyicisi.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range="vs-2019"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirin ve sisteminize yükleyin. Modüler yükleyici, tercih ettiği programlama dili veya platform için gereken özellik grupları olan iş yüklerini seçmenize ve yüklemenize olanak sağlar. Program oluşturma adımlarını [takip etmek için](#create-a-program)yükleme sırasında .NET Core platformlar arası geliştirme iş yükünü **seçin.**

![Ağ geçidinde nokta NET Core platformlar arası geliştirme iş yükünün Visual Studio Yükleyicisi.](../media/dotnet-core-cross-platform-workload.png)

::: moniker-end

::: moniker range=">=vs-2022"

Çalışmaya başlamanız için [Visual Studio](https://visualstudio.microsoft.com/downloads) indirin ve sisteminize yükleyin. Modüler yükleyicide, istediğiniz programlama dilleri *veya platformlar* için ihtiyacınız olan özellik grupları olan iş yüklerini seçer ve yükleyebilirsiniz. Bir program oluşturmak üzere aşağıdaki [adımları kullanmak için,](#create-a-program)yükleme sırasında .NET masaüstü geliştirme **iş yükünü seçmeyi** emin olun.

:::image type="content" source="media/vs-2022/dot-net-development-workload.png" alt-text="Uygulamanın içinde seçilen nokta NET masaüstü geliştirme iş yükünün Visual Studio Yükleyicisi." border="false":::

::: moniker-end

İlk kez Visual Studio kez oturum asanız, [](../../ide/signing-in-to-visual-studio.md) oturum açmak için Microsoft hesabı veya iş veya okul hesabınızla oturum açabilirsiniz.

## <a name="customize-visual-studio"></a>Özelleştirme Visual Studio

Varsayılan renk temasını Visual Studio kullanıcı arabirimini kişiselleştirebilirsiniz.

### <a name="change-the-color-theme"></a>Renk temasını değiştirme

Renk temasını değiştirmek için:

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda, Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** sayfasında Renk teması seçimini Koyu olarak ayarlayın ve >  ardından Tamam'a **tıklayın.**  

   ![Renk temasını renk temasının koyu olarak değiştirilmesini gösteren ekran Visual Studio.](media/change-color-theme.png)

   IDE'nin tamamı için renk teması Koyu olarak **değişir.**

   ![Koyu temada Visual Studio gösteren ekran görüntüsü.](../../ide/media/quickstart-personalize-dark-theme.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde Kod olmadan **devam'ı seçin.**

   :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Visual Studio 2019'daki Başlangıç penceresinin ekran görüntüsü, 'Kod olmadan devam edin' bağlantısı vurgulanmış.":::

   IDE açılır.

1. Menü çubuğunda Visual Studio Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** > **sayfasında** Renk teması seçimini  **Koyu olarak** ve ardından Tamam'ı **seçin.**

   ![Renk temasını renk temasının koyu olarak değiştirilmesini gösteren ekran Visual Studio.](media/change-color-theme.png)

   IDE'nin tamamı için renk teması Koyu olarak **değişir.**

   ![Koyu temada Visual Studio gösteren ekran görüntüsü.](../media/vs-2019/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio'yu açın. Başlangıç penceresinde Kod olmadan **devam'ı seçin.**

   :::image type="content" source="media/vs-2022/continue-without-code.png" alt-text="Kod olmadan devam Visual Studio Başlangıç ekranı vurgulanmış şekilde ekran görüntüsü." border="false":::

1. Menü çubuğunda Visual Studio Seçenekler iletişim **kutusunu** > **açmak için** Araçlar Seçenekler'i seçin. 

1. Ortam Genel **seçenekleri** sayfasında Renk Teması seçimini Mavi veya Açık olarak değiştirerek >  Tamam'ı **seçin.**   

   :::image type="content" source="media/vs-2022//change-color-theme.png" alt-text="Visual Studio'da renk temasını Mavi olarak değiştirmeyi gösteren Visual Studio.":::

   IDE'nin tamamı için renk teması buna göre değişir. Aşağıdaki ekran görüntüsü mavi temayı gösterir:

   :::image type="content" source="media/vs-2022/blue-theme.png" alt-text="Mavi temada Visual Studio gösteren ekran görüntüsü.":::
::: moniker-end

### <a name="select-environment-settings"></a>Ortam ayarlarını seçme

Geliştiricilerin Visual Studio ortam ayarlarını kullanmak için Visual Basic yapılandırabilirsiniz.

1. Menü çubuğunda Araçlar İçeri ve Dışarı  >  **Aktarma'Ayarlar.**

1. **İlkeleri İçeri ve Dışarı Ayarlar Sihirbazı'nda** Tüm ayarları **sıfırla'yı ve** ardından Sonraki'yi **seçin.**

1. Geçerli Ayarları **Kaydet Ayarlar,** sıfırlamadan önce geçerli ayarlarınızı kaydedip kaydetmeyebilirsiniz. Herhangi bir ayarı özelleştirmediyebilirsiniz, hayır, yalnızca **ayarları sıfırla'yı seçin ve geçerli ayarlarım'ın üzerine yazmanız gerekir.** Sonra **İleri**’yi seçin.

1. Varsayılan **Koleksiyon Seçin sayfasında, Ayarlar** seçin Visual Basic **ve** ardından Son'a **tıklayın.**

1. Sıfırlama Tamamlandı **sayfasında Kapat'ı** **seçin.**

IDE'nizi kişiselleştirmenin diğer yolları hakkında bilgi edinmek için [bkz. Visual Studio.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="create-a-program"></a>Program oluşturma

Basit bir program oluşturma ve bu programa dalın.

::: moniker range="vs-2017"

1. Yeni Visual Studio çubuğunda Dosya Yeni **Dosya'Project.** > 

   ![Menü çubuğundaKi Dosya > Yeni Project gösteren ekran görüntüsü.](media/file-new-project-menu.png)

   Yeni **Project** iletişim kutusunda birkaç proje *şablonu görüntülenir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Visual Basic altında **.NET Core** **kategorisini** seçin ve ardından Konsol Uygulaması **(.NET Core) şablonunu** seçin. Ad **metin** kutusuna **HelloWorld yazın ve** tamam **düğmesini** seçin.

   ![.NET Core uygulama şablonunu gösteren ekran görüntüsü.](media/overview-npd.png)

   > [!NOTE]
   > .NET Core kategorisini **görmüyorsanız.NET Core** platformlar arası geliştirme **iş yükünü yüklemeniz** gerekir. Bunu yapmak için, Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol alt kısmında bulunan Dosya aç **Project** seçin. Uygulama Visual Studio Yükleyicisi sonra ekranı aşağı kaydırın ve **.NET Core** platformlar arası geliştirme iş yükünü seçin ve ardından Değiştir'i **seçin.**

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısaca, aşağıdakine benzer bir şey görüyoruz:

   ![IDE'nin Visual Studio ekran görüntüsü.](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu düzenleyici penceresinde görünür ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretlerini seçebilirsiniz. Bu kod açıklama özelliği, ihtiyacınız olan kodu gizleyerek ekrandaki dağınıklığı en aza indirmenizi sağlar. Proje dosyaları, Çözüm Gezgini adlı bir pencerede **sağ tarafta listelenir.**

   ![IDE'nin kırmızı Visual Studio gösteren ekran görüntüsü.](media/overview-ide-console-app-red-boxes.png)

   Başka menüler ve araç pencereleri de vardır, ancak şimdilik devam edin.

1. Şimdi uygulamayı başlatabilirsiniz. Bunu yapmak için menü çubuğundaki **Hata Ayıklama menüsünden** Hata **Ayıklama** Olmadan Başlat'ı seçebilirsiniz. **Ctrl** + **F5 tuşlarına da basarak.**

   ![Hata Ayıklama olmadan başlat'> hata ayıklamasını gösteren ekran görüntüsü.](../media/overview-start-without-debugging.png)

   Visual Studio uygulamayı derler ve şu iletiyle bir konsol penceresi **Merhaba Dünya!**. Artık çalışan bir uygulama var!

   ![Konsol penceresini gösteren ekran görüntüsü.](../media/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Şimdi uygulamaya bazı ek kodlar ekleriz. Aşağıdaki kodu Visual Basic satırın önünde `Console.WriteLine("Hello World!")` ekleyin:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu **kod, konsol penceresinde Adınız nedir?** metnini görüntüler ve ardından kullanıcının bir metin girmesini ve enter tuşuna kadar **beklemesini** sağlar.

1. aşağıdaki kodla `Console.WriteLine("Hello World!")` ifade eden satırı değiştirme:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **Ctrl** F5 tuşlarına basarak + **uygulamayı yeniden çalıştırın.**

   Visual Studio yeniden yapılandırıyorsanız, bir konsol penceresi açılır ve sizden adınız istenir.

1. Konsol penceresine adınız girin ve Enter tuşuna **basın.**

   ![Konsol penceresi girişini gösteren ekran görüntüsü.](../media/overview-console-input.png)

1. Konsol penceresini kapatmak ve çalışan programı durdurmak için herhangi bir tuşa basın.

::: moniker-end

::: moniker range="vs-2019"

1. Yeni Visual Studio çubuğunda Dosya Yeni   >  **dosya'Project.**  >   (Alternatif olarak **Ctrl tuşuna basın** + **Shift ile kaydırma** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Visual Studio 2019 menü çubuğundan > Yeni > Project seçiminin ekran görüntüsü.":::

   Yeni **proje oluştur penceresi** açılır ve birkaç proje şablonu *gösterilir.* Şablon, verilen proje türü için gereken temel dosyaları ve ayarları içerir.

1. Bizim istediğiniz şablonu bulmak için arama kutusuna **.net Core konsolunu** yazın veya girin. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre otomatik olarak filtrelenir. Tüm dil açılan listesinden **Visual Basic'i,** Tüm platformlar listesinden  Windows Konsolu'nu  seçerek şablon  sonuçlarını daha fazla  **filtreleyebilirsiniz.**

   Konsol Uygulaması **şablonunu seçin** ve ardından Sonraki'ye **tıklayın.**

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="2019'da istediğiniz şablonu Visual Studio 'Yeni proje oluştur' penceresinin ekran görüntüsü.":::

1. Yeni **projenizi yapılandır** penceresinde, **Project** adı kutusuna **HelloWorld** yazın, isteğe bağlı olarak proje dosyalarınızın dizin konumunu (varsayılan yerel ayardır) ve ardından `C:\Users\<name>\source\repos` Sonraki 'ye **tıklayın.**

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="2019'da projenin adını Visual Studio 'Yeni projenizi yapılandır' penceresinin ekran görüntüsü.":::

1. Ek **bilgiler penceresinde,** Hedef Çerçeve açılan menüsünde **.NET Core 3.1'in** görüntülendiğinden emin olup Oluştur'a **tıklayın.** 

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="2019'da ,NET Core Framework'Visual Studio istediğiniz sürümü seçerek 'Ek bilgiler' penceresinin ekran görüntüsü.":::

   Visual Studio projeyi oluşturur. Bu, "Merhaba Dünya!" değişmez dizesini görüntülemek için yöntemini çağıran basit bir <xref:System.Console.WriteLine?displayProperty=nameWithType> "Merhaba Dünya" uygulamasıdır konsol (program çıkışı) penceresinde.

   Kısaca, aşağıdakine benzer bir şey görüyoruz:

   ![IDE'nin Visual Studio ekran görüntüsü.](media/overview-ide-console-app.png)

   Uygulamanın Visual Basic kodu düzenleyici penceresinde görünür ve bu da yerlerin çoğunu alır. Metnin, kodun anahtar sözcükler ve türler gibi farklı bölümlerini göstermek için otomatik olarak renklendirmesine dikkat eder. Ayrıca, kodda küçük, dikey kesikli satırlar hangi ayraçların eş olduğunu ve satır numaraları daha sonra kodu bulumanıza yardımcı olur. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi işaretini seçebilirsiniz. Bu kod ana hattı özelliği, ihtiyacınız olmayan kodun gizlenmesini sağlar ve ekran dağınıklığını en aza indirmenize yardımcı olur. Proje dosyaları, **Çözüm Gezgini** adlı bir pencerenin sağ tarafında listelenir.

   ![kırmızı kutulara Visual Studio ıde 'yi gösteren ekran görüntüsü.](media/overview-ide-console-app-red-boxes.png)

   Diğer menüler ve araç pencereleri mevcuttur, ancak şimdilik bu aşamada geçiş yapalım.

1. Şimdi uygulamayı başlatın. Bunu, menü çubuğundaki **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' a tıklayarak yapabilirsiniz. **CTRL** + **F5** tuşuna da basabilirsiniz.

   ![Hata ayıklama > hata ayıklama olmadan başlayan ekran görüntüsü.](media/vs-2019/start-without-debugging.png)

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   ![Merhaba Dünya iletisini gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-window.png)

1. Konsol penceresini kapatmak için klavyenizde herhangi bir tuşa basın.

1. Uygulamaya bazı ek kodlar ekleyelim. aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından **ENTER** tuşuna basarak Kullanıcı bir metin girip girene kadar bekler.

1. Aşağıdaki koda gelen satırı değiştirin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. **CTRL** F5 tuşuna basarak uygulamayı yeniden çalıştırın + .

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı girin ve **ENTER**'a basın.

   ![Ad Sorunuzun ne olduğunu ve uygulamanın yanıtını gösteren konsol penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-input.png)

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

::: moniker range=">=vs-2022&quot;

1. Visual Studio menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin. **CTRL** + **SHIFT** + **N** tuşlarına da basabilirsiniz.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/file-new-project.png&quot; alt-text=&quot;Visual Studio menü çubuğundan > yeni Project > dosyanın ekran görüntüsü.&quot; border=&quot;false&quot;:::

   **Yeni proje oluştur** penceresi açılır ve birçok proje *şablonunu* gösterir. Şablon, belirli bir proje türünün gerektirdiği temel dosyaları ve ayarları içerir.

1. Bir şablonu bulmak için arama kutusuna anahtar sözcükleri yazabilir veya girebilirsiniz. Kullanılabilir şablonların listesi, girdiğiniz anahtar sözcüklere göre filtreler. tüm **diller** açılan listesinden **Visual Basic** seçerek şablon sonuçlarını daha fazla filtreleyebilirsiniz, tüm **platformlar** listesinden ve **tüm proje türleri** listesinden **konsolundan** **Windows** .

   Visual Basic **konsol uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/create-project.png&quot; alt-text=&quot;Visual Basic konsol uygulaması seçiliyken yeni proje oluştur penceresinin ekran görüntüsü.&quot; border=&quot;false&quot;:::

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** kutusuna **HelloWorld** yazın. İsteğe bağlı olarak, proje dizini konumunu *C: \\ Users \\ \<name> \\ kaynak \\ deposunun* varsayılan konumundan değiştirip **İleri**' yi seçin.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/configure.png&quot; alt-text=&quot;Yeni projenizi, HelloWorld adlı proje adı ile yapılandırın penceresinin ekran görüntüsü.&quot; border=&quot;false&quot;:::

1. **Ek bilgi** penceresinde, **.net 6,0** ' in **hedef Framework** açılan menüsünde göründüğünü doğrulayın ve ardından **Oluştur**' u seçin.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/additional-information.png&quot; alt-text=&quot;Dot NET 6,0 seçiliyken ek bilgi penceresinin ekran görüntüsü.&quot; border=&quot;false&quot;:::

   Visual Studio projeyi oluşturur. Program <xref:System.Console.WriteLine?displayProperty=nameWithType> **, Hello, World!** dizesini görüntüleyen yöntemi çağıran basit bir &quot;Merhaba Dünya&quot; uygulamasıdır. bir konsol penceresinde.

   proje dosyaları, **Çözüm Gezgini** adlı bir pencerede Visual Studio ıde 'nin sağ tarafında görünür. **Çözüm Gezgini** penceresinde **program. vb** dosyasını seçin. uygulamanın Visual Basic kodu, alanın çoğunu alan merkezi düzenleyici penceresinde açılır.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/open-program.png&quot; alt-text=&quot;düzenleyicide Program nokta V b kodunu gösteren Visual Studio g/ç ekran görüntüsü.&quot; border=&quot;false&quot;:::

   Kod, anahtar sözcükler ve türler gibi farklı parçaları göstermek için otomatik olarak renklendirilir. Satır numaraları kodu bulmanıza yardımcı olur.

   Koddaki küçük, dikey kesikli çizgiler kod yapısını veya birlikte gelen kod bloklarını gösterir. Kod bloklarını daraltmak veya genişletmek için küçük, kutulu eksi veya artı işaretlerini de seçebilirsiniz. Bu kod ana hattı özelliği, ekran dağınıklığını en aza indirmeye yardımcı olmak için, görmeniz gerekmeyen kodu gizlemenizi sağlar.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/editor-features.png&quot; alt-text=&quot;kırmızı kutulara Visual Studio ı D E r 'yi gösteren ekran görüntüsü.&quot; border=&quot;false&quot;:::

   Diğer birçok menü ve araç penceresi mevcuttur.

1. Visual Studio üst menüden **hata ayıklama**  >  **olmadan başlat** öğesini seçerek uygulamayı başlatın. **CTRL** + **F5** tuşuna da basabilirsiniz.

   :::image type=&quot;content&quot; source=&quot;media/vs-2022/start-without-debugging.png&quot; alt-text=&quot;Hata ayıklama > hata ayıklama menü öğesi olmadan başlangıcını gösteren ekran görüntüsü.&quot; border=&quot;false&quot;:::

   Visual Studio uygulamayı oluşturur ve **Merhaba Dünya!** iletisi ile bir konsol penceresi açılır. Artık çalışan bir uygulamanız var!

   :::image type=&quot;content&quot; source=&quot;../media/vs-2019/overview-console-window.png&quot; alt-text=&quot;Çıktı Merhaba Dünya gösteren hata ayıklama konsolu penceresinin ekran görüntüsü ve bu pencereyi kapatmak için herhangi bir tuşa basın.&quot; border=&quot;false&quot;:::

1. Konsol penceresini kapatmak için herhangi bir tuşa basın.

1. Uygulamaya daha fazla kod ekleyelim. aşağıdaki Visual Basic kodu aşağıdaki satırdan önce ekleyin `Console.WriteLine(&quot;Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Bu kod, konsol penceresinde **adınızın ne olduğunu** görüntüler ve ardından Kullanıcı bazı metinleri girene kadar bekler.

1. Aşağıdaki satıra yazan çizgiyi değiştirin `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Hata **ayıklama** > **olmadan Başlat** öğesini seçerek veya **CTRL** + **F5** tuşuna basarak uygulamayı yeniden çalıştırın.

   Visual Studio uygulamayı yeniden oluşturur ve bir konsol penceresi açılır ve sizden adınızı ister.

1. Konsol penceresine adınızı yazın ve **ENTER** tuşuna basın.

   :::image type="content" source="../media/vs-2022/overview-console-input.png" alt-text="Bir ad, giriş ve Hello Georgette! çıkışı için istem gösteren hata ayıklama konsolu penceresinin ekran görüntüsü." border="false":::

1. Herhangi bir tuşa basarak konsol penceresini kapatın ve çalışan programı durdurun.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Yeniden düzenleme ve IntelliSense kullanma

Yeniden [düzenleme](../../ide/refactoring-in-visual-studio.md) ve [IntelliSense](../../ide/using-intellisense.md) 'in daha verimli bir şekilde kodlamasına yardımcı olması için birkaç yol göz atalım.

İlk olarak, değişkeni yeniden adlandırın `name` :

1. Değişkene çift tıklayın `name` ve değişken için yeni ad, *Kullanıcı* adı yazın.

   Değişken etrafında bir kutu belirir ve kenar boşluğunda ampul görünür.

1. Kullanılabilir [hızlı eylemleri](../../ide/quick-actions.md)göstermek için ampul simgesini seçin. ' **Name ' öğesini ' username ' olarak yeniden adlandır**' ı seçin.

   ::: moniker range="<=vs-2019"
   ![Visual Studio yeniden adlandırma eylemini gösteren ekran görüntüsü.](media/rename-quick-action.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022&quot;
   :::image type=&quot;content&quot; source=&quot;media/vs-2022/rename.png&quot; alt-text=&quot;Visual Studio yeniden adlandırma eylemini gösteren ekran görüntüsü.&quot; border=&quot;false&quot;:::
   ::: moniker-end

   Değişken, proje genelinde yeniden adlandırılır, bu durumda yalnızca iki yer vardır.

Şimdi IntelliSense 'e göz atın.

1. Yazılı satırın altına `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")` aşağıdaki kodu yazın:

   ```vb
   Dim now = Date.
   ```
   
   Bir kutu, sınıfının üyelerini görüntüler <xref:System.DateTime> . Şu anda seçili olan üyenin açıklaması ayrı bir kutu içinde de görüntülenir.

   ::: moniker range="<=vs-2019"
   ![Visual Studio 'teki IntelliSense Liste üyelerini gösteren ekran görüntüsü.](media/intellisense-list-members.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022&quot;
   :::image type=&quot;content&quot; source=&quot;media/vs-2022/intellisense-list-members.png&quot; alt-text=&quot;Visual Studio 'teki IntelliSense Liste üyelerini gösteren ekran görüntüsü.&quot; border=&quot;false&quot;:::
   ::: moniker-end

1. Sınıfın bir özelliği olan **Şimdi** adlı üyeyi seçin. **Şimdi** üzerine çift tıklayın veya seçin ve **Tab** tuşuna basın.

1. Bu satırın altına aşağıdaki kod satırlarını girin:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write(&quot;Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> , <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> yazdırıldıktan sonra bir satır Sonlandırıcı eklemediğinden farklıdır. Diğer bir deyişle, çıktıya gönderilen sonraki metin parçası aynı satıra yazdırılır. Açıklamalarını görmek için kodunuzda bu yöntemlerin her birinin üzerine gelebilmeniz gerekir.

Daha sonra, yeniden düzenleme kullanarak kodu biraz daha kısa hale getirin.

::: moniker range="<=vs-2019"
1. Satırdaki değişkeni seçin `now` `Dim now = Date.Now` . Bu satırdaki kenar boşluğunda bir screwdriver simgesi görüntülenir.

1. Visual Studio sunulan önerileri görmek için screwdriver simgesini seçin. Bu durumda, genel kod davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösterilmektedir.

   ![Visual Studio 'da satır Içi geçici değişken önerisini gösteren ekran görüntüsü.](media/inline-temporary-variable-refactoring.png)

1. Kodu yeniden düzenleme için **satır içi geçici değişken** ' i seçin.

1. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

   ![Bir ad, giriş ve çıkış istemi gösteren hata ayıklama konsolu penceresinin ekran görüntüsü.](../media/vs-2019/overview-console-final.png)
   ::: moniker-end

::: moniker range=">=vs-2022"
1. Satırdaki değişkeni seçin `now` `Dim now = Date.Now` . Bu satırdaki kenar boşluğunda ampul simgesi görünür.

1. Visual Studio sunulan önerileri görmek için ampul simgesini seçin. Bu durumda, genel kod davranışını değiştirmeden bir kod satırını kaldırmak için [satır içi geçici değişken](../../ide/reference/inline-temporary-variable.md) yeniden düzenlemesi gösterilmektedir.

   :::image type="content" source="media/vs-2022/inline-temporary-variable.png" alt-text="Visual Studio 'da satır Içi geçici değişken önerisini gösteren ekran görüntüsü." border="false":::

1. Kodu yeniden düzenleme için **satır içi geçici değişken** ' i seçin.

1. **CTRL** F5 tuşuna basarak programı yeniden çalıştırın + . Çıktı şuna benzer:

   :::image type="content" source="../media/vs-2022/overview-console-final.png" alt-text="Bir ad, giriş ve çıkış istemi gösteren hata ayıklama konsolu penceresinin ekran görüntüsü." border="false":::
::: moniker-end

## <a name="debug-code"></a>Kod hatalarını ayıklama

Kod yazdığınızda çalıştırmanız ve hatalar için test etmeniz gerekir. Visual Studio hata ayıklama sistemi, bir seferde kod tek bir bildirimde ilerlemenizi ve gittiğiniz değişkenleri incelemenizi sağlar. Kodun belirli bir satırda yürütülmesini durduran *kesme noktaları* ayarlayabilir ve kodun çalıştığı şekilde değişken değerinin nasıl değiştiğini gözlemleyebilirsiniz.

Program çalışırken değişkenin değerini görmek için bir kesme noktası ayarlayın `username` .

1. `Console.WriteLine("Hello " + username + "!")`Satırın yanındaki sol kenar boşluğuna veya cilt payına tıklayarak belirten kod satırında bir kesme noktası ayarlayın. Ayrıca kod satırını seçip **F9** tuşuna basabilirsiniz.

   Cilt alanında kırmızı bir daire görünür ve çizgi vurgulanır.

   ::: moniker range="<=vs-2019"
   ![Visual Studio bir kod satırı üzerinde bir kesme noktası gösteren ekran görüntüsü.](media/breakpoint.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/breakpoint.png" alt-text="Visual Studio bir kod satırı üzerinde bir kesme noktası gösteren ekran görüntüsü." border="false":::
   ::: moniker-end

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı başlatın** veya **F5**'e basın.

1. Konsol penceresi göründüğünde ve adınızı istediğinde adınızı girin.

   odak Visual Studio kod düzenleyicisine geri döner ve kesme noktasıyla birlikte kod satırı sarı renkle vurgulanır. Sarı vurgu, bu kod satırının sonraki yürütüleceği anlamına gelir. Kesme noktası, uygulamanın bu satırda yürütmeyi duraklatmasını sağlar.

1. `username`Değerini görmek için farenizi değişkenin üzerine getirin. Ayrıca, ' ı sağ tıklayıp `username` **izleme Ekle** ' yi seçerek değişkeni **izleme** penceresine ekleyebilirsiniz; burada da bu değeri görebilirsiniz.

   ::: moniker range="<=vs-2019"
   ![Visual Studio hata ayıklama sırasında bir değişken değeri gösteren ekran görüntüsü.](media/debugging-variable-value.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/inspect-variable.png" alt-text="Visual Studio hata ayıklama sırasında bir değişken değeri gösteren ekran görüntüsü." border="false":::
   ::: moniker-end

1. Uygulamayı çalıştırmaya son vermek için **F5** tuşuna basın.

Visual Studio hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcı özellik turu](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki tanıtım makaleleriyle birlikte Visual Studio daha fazlasını yapın:

> [!div class="nextstepaction"]
> [Kod düzenleyicisini kullanmayı öğrenin](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Projeler ve çözümler hakkında bilgi edinin](tutorial-projects-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [daha fazla Visual Studio özelliği](../../ide/advanced-feature-overview.md)bulun.
- [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/vs/)adresini ziyaret edin.
- [Visual Studio blogunu](https://devblogs.microsoft.com/visualstudio/)okuyun.
