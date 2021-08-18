---
title: Projelere ve çözümlere giriş
description: Projeler ve çözümler arasındaki fark ve Visual Studio ' de nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7680930d6617a72db77fb6b5f3d30595faa7ec9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109766"
---
# <a name="introduction-to-projects-and-solutions"></a>Projelere ve çözümlere giriş

Bu giriş makalesinde, Visual Studio bir *çözüm* ve *Proje* oluşturmanın ne anlama geldiğini keşfedeceğiz. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Projenin özelliklerine ve içerdikleri bazı dosyalara bakacağız. Ayrıca bir projeden diğerine bir başvuru oluşturacağız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

Bir proje kavramını anlamak için eğitim alıştırması olarak sıfırdan bir çözüm ve proje oluşturacağız. Visual Studio genel kullanım ortamınızda, yeni bir proje oluşturduğunuzda Visual Studio sunduğu çeşitli proje *şablonlarından* bazılarını kullanacaksınız.

> [!NOTE]
> Visual Studio içinde uygulama geliştirmek için çözümler ve projeler gerekli değildir. Ayrıca yalnızca kod içeren ve kodlamaya, oluşturmaya ve hata ayıklamaya başlayan bir klasörü açabilirsiniz. örneğin, bir [GitHub](https://github.com/) depoyu klonladığınızda, Visual Studio projeleri ve çözümleri içermeyebilir. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. bir çözümü Visual Studio açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmayla başlayacağız. Visual Studio öğrendikten sonra, büyük olasılıkla çok sık boş çözümler oluşturmayacağız. yeni bir proje oluşturduğunuzda, zaten açık bir çözüm yoksa, Visual Studio projeyi barındırmak için otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. üstteki menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   **yeni Project** iletişim kutusu açılır.

1. sol bölmede **diğer Project türler**' i genişletin ve **Visual Studio çözümler**' i seçin. Orta bölmede **boş çözüm** şablonunu seçin. Çözümünüzü **hızlı çözümünüz** olarak adlandırın, sonra **Tamam** düğmesini seçin.

   ![Visual Studio 2017 ' de boş çözüm şablonu](media/tutorial-projects-new-solution.png "Visual Studio 2017 ' deki boş çözüm şablonu.")

   **başlangıç sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 ' de boş çözüm şablonu](media/vs-2019/tutorial-projects-blank-solution-template.png "Visual Studio 2019 ' deki boş çözüm şablonu.")

    > [!TIP]
    > Birden çok iş yükünden biri yüklüyse, **boş çözüm** şablonu arama sonuçları listenizin en üstünde görünmeyebilir. Listenin **Arama bölümüne göre diğer sonuçlara** kaydırma yapmayı deneyin. Burada görünmelidir.

4. Çözüm **hızlı çözümünü** adlandırın ve ardından **Oluştur**' u seçin.

   bir çözüm, Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ekleyelim. Boş bir proje ile başlayacağız ve proje için ihtiyacımız olan öğeleri ekleyeceğiz.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **yeni Project ekle** iletişim kutusu açılır.

1. sol bölmede, **Visual C#** ' ı genişletin ve **masaüstü Windows**' ni seçin. ardından ortadaki bölmede **boş Project (.NET Framework)** şablonunu seçin. Proje **Quickdate** olarak adlandırın ve ardından **Tamam**' ı seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > iletişim kutusunun sol bölmesinde **Visual C#** görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemelisiniz. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. yeni bir iş yükünü yüklemenin kolay bir yolu, **yeni Project ekle** iletişim kutusunun sol alt köşesindeki **aç Visual Studio Yükleyicisi** bağlantısını seçeklemektir. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyicisi bağlantısını aç](media/tutorial-projects-open-installer.png "Visual Studio 2017 ' deki yeni Project ekle iletişim kutusunda aç Visual Studio Yükleyicisi bağlantısı.")

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **Yeni bir proje ekleyen** bir iletişim kutusu açılır.

1. Üstteki arama kutusuna **boş** metin girin ve ardından **dil** altında **C#** ' ı seçin.

1. **boş Project (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

1. Proje **Quickdate** olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > **boş Project (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemelisiniz. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır.
   >
   >Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını** belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyicisi bağlantısını aç](media/vs-2019/tutorial-projects-open-installer.png "Visual Studio yeni Project oluştur iletişim kutusunda aç Visual Studio Yükleyicisi bağlantısı.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projem var. Bir kod dosyası ekleyelim.

1. **Çözüm Gezgini** içindeki **quickdate** projesinin sağ tıklama veya kısayol menüsünden   >  **Yeni öğe** Ekle ' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. **Visual C# öğelerini** genişletin ve **kod** öğesini seçin. Orta bölmede **sınıf** öğesi şablonunu seçin. Sınıf **takvimini** adlandırın ve ardından **Ekle** düğmesini seçin.

   Projeye *Calendar. cs* adlı bir dosya eklenir. Uçtaki *. cs* , C# kod dosyalarına verilen dosya uzantısıdır. Dosya **Çözüm Gezgini**' deki görsel proje hiyerarşisinde görüntülenir ve içeriği düzenleyicide açılır.

1. *Calendar. cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Kodun ne yaptığını anlamanız gerekmez, ancak isterseniz, **CTRL** + **F5** tuşuna basarak ve bugünün tarihini konsola (veya standart çıkış) penceresine yazdırdığınızı görmeniz için programı çalıştırabilirsiniz.

## <a name="add-a-second-project"></a>İkinci bir proje ekleyin

Çözümlerin birden fazla proje içermesi ve genellikle bu projelerin birbirlerine başvurması yaygındır. Bir çözümdeki bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim testi projeleri veya Web siteleri olabilir.

Çözümünüze bir birim testi projesi ekleyelim. Bu kez bir proje şablonundan başlayacağız, böylece projeye ek bir kod dosyası eklememiz gerekmez.

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden   >  **yeni Project** ekle ' yi seçin.

::: moniker range="vs-2017"

2. Sol bölmede, **Visual C#** ' yi genişletin ve **Test** kategorisini seçin. orta bölmede, **MSTest Test Project (.net Core)** proje şablonunu seçin. Projeyi **hızlı test** olarak adlandırın ve ardından **Tamam**' ı seçin.

   **Çözüm Gezgini** ikinci bir proje eklenir ve düzenleyicide *UnitTest1. cs* adlı bir dosya açılır.

   ![Visual Studio İki projeyle Çözüm Gezgini](media/tutorial-projects-solution-explorer.png "Visual Studio 2017 ' de iki projeyle Çözüm Gezgini.")

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni Proje Ekle** iletişim kutusunda, üstteki arama kutusuna metin **birimi testini** girin ve ardından **dil** altında **C#** ' ı seçin.

3. .net Core için **birim testi Project** projesi şablonunu seçin ve ardından **ileri**' yi seçin.

   > [!NOTE]
   > Visual Studio 2019 sürüm 16,9 ' den başlayarak, mstest proje şablonu adı **mstest birim testi Project (.net Core)** iken **birim testi Project** olarak değiştirildi. Bu güncelleştirmede proje oluşturma içindeki birkaç adım değişti.

4. Projeyi **hızlı teste** adlandırın ve ardından **İleri**' yi seçin.

5. Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.

   **Çözüm Gezgini** ikinci bir proje eklenir ve düzenleyicide *UnitTest1. cs* adlı bir dosya açılır.

   ![Visual Studio İki projeyle Çözüm Gezgini](media/vs-2019/tutorial-projects-solution-explorer.png "Visual Studio iki projeyle Çözüm Gezgini.")

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

**Hızlı Tarih** projesindeki yöntemizi test etmek için yeni birim testi projesini kullanacağız, bu nedenle bu projeye bir başvuru eklememiz gerekiyor. Bu, iki proje arasında bir *derleme bağımlılığı* oluşturur. Bu, çözümü oluşturduğunuzda hızlı **Test** öncesinde hızlı bir **Tarih** oluşturulur.

::: moniker range="vs-2017"

1. **Hızlı test** projesinde **Bağımlılıklar** düğümünü seçin ve sağ tıklama ya da bağlam menüsünden **Başvuru Ekle**' yi seçin.

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede, **Projeler** ' i genişletin ve **çözüm**' ü seçin. Orta bölmede, **Quickdate** seçeneğinin yanındaki onay kutusunu işaretleyin ve ardından **Tamam**' ı seçin.

   **Quickdate** projesine bir başvuru eklenir.

   ![Visual Studio içinde proje başvurusunu gösteren Çözüm Gezgini ekran görüntüsü](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Visual Studio bir proje başvurusunu gösteren Çözüm Gezgini ekran görüntüsü.")

::: moniker-end

::: moniker range=">=vs-2019"

1. **hızlı test** projesinde **bağımlılıklar** düğümünü seçin ve sağ tıklama ya da bağlam menüsünden **Project başvuru ekle...** seçeneğini belirleyin.

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede **Projeler**' i genişletin ve **çözüm**' ü seçin. Orta bölmede, **Quickdate** seçeneğinin yanındaki onay kutusunu işaretleyin ve ardından **Tamam**' ı seçin.

   **Quickdate** projesine bir başvuru eklenir.

   ![Visual Studio 2019 ' de proje başvurusunu gösteren Çözüm Gezgini ekran görüntüsü](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

## <a name="add-test-code"></a>Test kodu ekle

1. Şimdi C# test kodu dosyasına test kodu ekleyeceğiz. *UnitTest1. cs* içeriğini şu kodla değiştirin:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Bazı kodlar altında kırmızı renkli bir çizgi görürsünüz. Test projesini **Quickdate** projesine bir [Friend derlemesi](/dotnet/standard/assembly/friend-assemblies) yaparak bu hatayı düzeltireceğiz.

1. **Quickdate** projesine geri döndüğünüzde, zaten açık değilse *Takvim. cs* dosyasını açın. Test projesindeki hatayı çözümlemek için aşağıdaki [using ifadesini](/dotnet/csharp/language-reference/keywords/using-statement) ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini dosyanın en üstüne ekleyin.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Kod dosyası şuna benzemelidir:

   ![CSharp kodu](media/tutorial-projects-cs-code.png "Bu makaledeki test kodu Ekle bölümünde kod parçacığı.")

## <a name="project-properties"></a>Proje özellikleri

Özniteliği içeren *Calendar. cs* dosyasındaki satır, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> **hızlı test** projesinin derleme adına (dosya adı) başvurur. Derleme adı, proje adı ile her zaman aynı olamaz. Projenin derleme adını bulmak için, proje özelliklerini açın.

1. **Çözüm Gezgini**' de **hızlı test** projesini seçin. Sağ tıklama veya bağlam menüsünde **Özellikler**' i seçin veya yalnızca **alt** + **ENTER** tuşuna basın.

   Projenin *Özellik sayfaları* **uygulama** sekmesinde açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **Hızlı test** projesinin derleme adının gerçekten "QuickTest" olduğuna dikkat edin. Bunu değiştirmek isterseniz bunu yapmanız gerekir. Ardından, test projesi oluşturduğunuzda, sonuçta elde edilen ikili dosyanın adı *QuickTest.dll* ' den seçtiğiniz şeyle değişir.

   ![Project özellikleri](media/tutorial-projects-netcore-properties.png "Project Visual Studio Özellikler iletişim kutusu.")

1. Projenin özellik sayfalarındaki **derleme** ve **hata ayıklama** gibi diğer sekmelerin bazılarını keşfedelim. Bu sekmeler farklı proje türleri için farklıdır.

## <a name="next-steps"></a>Sonraki adımlar

::: moniker range="vs-2017"

Birim testinizin çalıştığını denetlemek isterseniz,   >    >  menü çubuğundan **tüm testleri** Çalıştır test ' i seçin. **Test Gezgini** adlı bir pencere açılır ve **TestGetCurrentDate** testin başarılı olduğunu görmeniz gerekir.

::: moniker-end

::: moniker range=">=vs-2019"

Birim testinizin çalıştığını denetlemek isterseniz,   >  menü çubuğundan **Tüm Testleri Çalıştır** test ' i seçin. **Test Gezgini** adlı bir pencere açılır ve **TestGetCurrentDate** testin başarılı olduğunu görmeniz gerekir.

::: moniker-end

![geçilen testi gösteren Visual Studio test gezgini](media/tutorial-projects-test-explorer.png "geçilen bir testi gösteren Visual Studio test gezgini.")

::: moniker range="vs-2017"

> [!TIP]
> **test gezgini** otomatik olarak açılmazsa,   >  menü çubuğundan test **Windows** test  >  **gezgini** ' ni seçerek açın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> **Test Gezgini** otomatik olarak açılmazsa, menü çubuğundan **Test**  >  **Test Gezgini** ' ni seçerek açın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Projelerle ve çözümlerle çalışma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
