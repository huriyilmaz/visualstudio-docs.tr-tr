---
title: Projelere ve çözümlere giriş
description: Projeler ve çözümler arasındaki farkları ve bunları projelerde nasıl Visual Studio.
ms.date: 11/12/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7e869d593be04c42151753039a6e9be4981cdd2d
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453509"
---
# <a name="introduction-to-projects-and-solutions"></a>Projelere ve çözümlere giriş

Bu giriş makalesinde, bir çözüm ve bir proje *oluşturmanın* ne anlama geldiğini *Visual Studio.* Çözüm, sınıf kitaplığı projesi ve karşılık gelen bir test projesi gibi bir veya daha fazla ilgili kod projesini düzenlemek için bir kapsayıcıdır.

Bir proje kavramını anlamaya yönelik bir eğitim alıştırması olarak sıfırdan bir çözüm ve proje oluşturun. Normalde yeni projeler oluşturmak için Visual Studio *şablonlarını* kullanırsınız. Ayrıca, bir projenin özelliklerine ve içerenin bazı dosyalarına göz atarak bir projeden diğerine başvuru oluşturabilirsiniz.

> [!NOTE]
> Uygulama geliştirme Visual Studio çözüm ve proje gerektirmez. Kod içeren bir klasör açıp kodlamaya, oluşturmaya ve hata ayıklamaya başlayabilirsiniz. Örneğin, kopyalanan bir [GitHub,](https://github.com/) farklı proje ve Visual Studio içereyem olabilir. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019'Visual Studio indirme sayfasına gidip ücretsiz yükleyin. [](https://visualstudio.microsoft.com/downloads)

::: moniker-end

::: moniker range=">=vs-2022"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Bu Visual Studio çözüm bir "yanıt" değildir. Çözüm yalnızca bir veya daha fazla Visual Studio düzenlemek için kullandığı kapsayıcıdır. Bir çözümü Visual Studio, çözümün içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmanıza başlayabilirsiniz. Bu sorunları Visual Studio, büyük olasılıkla çok sık boş çözümler oluşturmaz. Yeni bir proje oluşturursanız, Visual Studio zaten açık olmadığı sürece proje için otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Üst menü çubuğunda Dosya Yeni **dosya'Project.** >  > 

   Yeni **Project** iletişim kutusu açılır.

1. Sol bölmede Diğer Project **Türleri'ni genişletin** ve ardından **Çözümler'Visual Studio seçin.** Orta bölmede Boş Çözüm **şablonunu** seçin. Çözüme **QuickSolution adını** ve ardından Tamam **düğmesini** seçin.

   ![Visual Studio 2017'de Boş Çözüm şablonunun seçili olduğunu gösteren ekran görüntüsü.](media/tutorial-projects-new-solution.png "Visual Studio 2017'de Boş Çözüm şablonu.")

   Başlangıç **Sayfası** kapanır ve Çözüm Gezgini **penceresinin** sağ tarafında bir Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında** arama kutusuna **boş çözüm** girin, Boş Çözüm şablonunu seçin ve **ardından** Sonraki'yi **seçin.**

   ![Visual Studio 2019'da boş çözüm şablonunun seçili olduğunu gösteren ekran görüntüsü.](media/vs-2019/tutorial-projects-blank-solution-template.png "Visual Studio 2019'daki Boş Çözüm şablonu.")

    > [!TIP]
    > Yüklü birkaç iş yükünüz varsa, **Arama** sonuçları listenizin en üstünde Boş Çözüm şablonu görüne görünebilir. Listenin arama bölümünü **temel alarak Diğer sonuçlara kaydırmayı** deneyin. Burada görünse gerekir.

4. Çözüme **QuickSolution adını ve** ardından Oluştur'ı **seçin.**

   Çözüm, **Çözüm Gezgini** penceresinin sağ tarafındaki Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

::: moniker range=">=vs-2022"

1. Yeni Visual Studio açın ve başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında,** arama kutusuna *boş* çözüm yazın, Boş Çözüm şablonunu **seçin** ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/tutorial-projects-blank-solution-template.png" alt-text="Visual Studio'da Boş Çözüm şablonunun seç Visual Studio." border="false":::

    > [!TIP]
    > Yüklü birkaç iş yükünüz varsa, **Arama** sonuçları listenizin en üstünde Boş Çözüm şablonu görüne görünebilir. Şablonu bulmak için **aramanıza bağlı olarak Diğer sonuçlar'da** kaydırmayı deneyin.

4. Yeni **projenizi yapılandırma sayfasında** çözüme **QuickSolution** adını ve ardından Oluştur'a **tıklayın.**

   Hızlı **Çözüm** çözümü **Çözüm Gezgini** penceresinin sağ tarafındaki Visual Studio görünür. Projenizin **içeriğine Çözüm Gezgini** sık sık bu dosyaları kullanacağız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projenizi ekleyin. Boş bir projeyle çalışmaya başlama ve ihtiyacınız olan öğeleri ekleme.

::: moniker range="vs-2017"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

   Yeni **Veri Project** iletişim kutusu açılır.

1. Sol bölmede **Visual C# öğesini genişletin ve** Masaüstü'Windows **seçin.** Ardından orta bölmede Boş Bölme **(Project (.NET Framework) şablonunu** seçin. Projeye **QuickDate adını ve** ardından Tamam'ı **seçin.**

   Hızlı Date adlı bir proje, çözümün altında **Çözüm Gezgini.** Şu andaApp.configadlı *tek bir dosya içerir.*

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **Visual C#** öğesini görmüyorsanız, **.NET masaüstü** geliştirmeyi iş yüküne Visual Studio gerekir. Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni iş yükü yüklemenin kolay bir yolu, **Yeni** Visual Studio Yükleyicisi Ekle iletişim kutusunun sol alt köşesindeki Aç **bağlantısını Project** etmektir. Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Dosya aç bağlantısını gösteren Visual Studio Yükleyicisi görüntüsü.](media/tutorial-projects-open-installer.png "Visual Studio Yükleyicisi 2017'de Yeni Project Ekle iletişim Visual Studio bağlantısı.")

::: moniker-end

::: moniker range="vs-2019"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

   Yeni proje ekle seçeneğinin **yer alan bir iletişim kutusu açılır.**

1. En üstte **yer alan** arama kutusuna metni boş girin ve Dil'in altında **C#** öğesini **seçin.**

1. Boş Veri **(Project) .NET Framework** ve ardından Sonraki'yi **seçin.**

1. Projeye **QuickDate adını ve ardından** Oluştur'a **seçin.**

   Hızlı Date adlı bir proje, çözümün altında **Çözüm Gezgini.** Şu andaApp.configadlı *tek bir dosya içerir.*

   > [!NOTE]
   > Boş Yükleme **(Project) şablonunu .NET Framework.** **.NET masaüstü** geliştirme ve yükleme Visual Studio yüklemeniz gerekir. Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır.
   >
   >Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay  bir yolu, arayabilirsiniz öğesini bu değil mi? metninin altındaki Daha fazla araç ve özellik yükle **bağlantısını seçmektir.** Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Dosya aç bağlantısını gösteren Visual Studio Yükleyicisi görüntüsü.](media/vs-2019/tutorial-projects-open-installer.png "Yeni Visual Studio Yükleyicisi Oluştur iletişim kutusundaki Aç bağlantısı Project iletişim Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. içinde Çözüm **'QuickSolution' seçeneğine** **sağ Çözüm Gezgini** ve bağlam  > **menüsünden Yeni Project** Ekle'yi seçin.

1. Yeni **proje ekle sayfasında,** en üstte *yer* alan arama kutusuna boş yazın ve Tüm diller'in altında **C#** **öğesini seçin.**

1. C# Boş Veri **Project (.NET Framework) şablonunu** ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Boş Yükleme **(Project) (.NET Framework)** şablonunu görmüyorsanız, **.NET masaüstü** geliştirme ve yükleme Visual Studio yüklemeniz gerekir.
   >
   >Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay  bir yolu, arayabilirsiniz öğesini bu değil mi? metninin altındaki Daha fazla araç ve özellik yükle **bağlantısını seçmektir.** Uygulama Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir'i **seçin.**
   >
   > :::image type="content" source="media/vs-2022/tutorial-projects-open-installer.png" alt-text="Dosya aç bağlantısını gösteren Visual Studio Yükleyicisi görüntüsü." border="false":::

1. Yeni **projenizi yapılandır sayfasında,** projeye **QuickDate** adını ve ardından Oluştur'a **tıklayın.**

   **QuickDate projesi,** çözümün altında **Çözüm Gezgini.** Şu anda proje,App.config **adlı tek bir dosya içerir.**

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş projenize bir kod dosyası ekleyin.

1. Çözüm Gezgini'daki **QuickDate** projesinin sağ tıklama veya bağlam **menüsünden** Yeni Öğe **Ekle'yi**  >  **seçin.**

   Yeni **Öğe Ekle iletişim** kutusu açılır.

1. **Visual C# Öğeleri'ne genişletin** ve Ardından Kod'a **seçin.** Orta bölmede Sınıf öğesi **şablonunu** seçin. **Ad'ın** altında *Takvim yazın* ve Ekle'yi **seçin.**

   Visual Studio *Calendar.cs adlı bir* dosyayı projeye ekler. Sonundaki *.cs,* C# kod dosyaları için dosya uzantısıdır. **Calendar.cs** dosyası, Çözüm Gezgini **proje** hiyerarşisinde görünür ve dosya düzenleyicide açılır.

1. *Calendar.cs* dosyasının içeriğini aşağıdaki kodla değiştirin:

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

   Kodun yaptığı her şeyi henüz anlamaya gerek yok. **Ctrl** F5 tuşlarına basarak uygulamayı çalıştırın ve uygulamanın bugünün tarihini konsola veya standart çıkış penceresine + yazdırıyor olduğunu görebilirsiniz. Ardından konsol penceresini kapatın.

## <a name="add-a-second-project"></a>İkinci proje ekleme

Çözümler genellikle birden fazla proje içerir ve bu projeler genellikle birbirine başvurur. Bir çözümde bulunan bazı projeler sınıf kitaplıkları, bazıları yürütülebilir uygulamalar ve bazıları birim testi projeleri veya web siteleri olabilir.

Çözümünüze birim testi projesi eklemek için projeye başka bir kod dosyası eklemek zorunda olmadığınız bir proje şablonundan başlayabilirsiniz.

::: moniker range="vs-2017"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

2. Sol bölmede **Visual C# öğesini genişletin** ve Test **kategorisini** seçin. Orta bölmede MSTest Test Testi Project **(.NET Core) proje** şablonunu seçin. Projeye **QuickTest adını ve** ardından Tamam'ı **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.cs* adlı bir dosya düzenleyicide açılır.

   ![İki projeyle Çözüm Gezgini ekran görüntüsü.](media/tutorial-projects-solution-explorer.png "Çözüm Gezgini 2017'de iki Visual Studio projeyle birlikte.")

::: moniker-end

::: moniker range="vs-2019"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

2. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna metin birimi **testini** girin ve dil'in altında **C#** öğesini **seçin.**

3. .NET Core **Project** Birim Testi proje şablonunu ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > 2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Birim Testi Project (.NET Core)** olarak Birim **Testi** Project. Bu güncelleştirmede proje oluşturma adımlarının birkaçı değiştirildi.

4. Projeye **QuickTest adını ve** ardından Sonraki'yi **seçin.**

5. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.cs* adlı bir dosya düzenleyicide açılır.

   ![İki projeyle Çözüm Gezgini ekran görüntüsü.](media/vs-2019/tutorial-projects-solution-explorer.png "Çözüm Gezgini iki projeyle Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

1. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna birim *testi* yazın ve Ardından Tüm diller'in altında **C#** **öğesini seçin.**

1. C# Birim **Testi Project (.NET Framework) proje** şablonunu ve ardından Sonraki'yi **seçin.**

1. Yeni **projenizi yapılandır sayfasında,** projeye *QuickTest* adını ve ardından Oluştur'a **tıklayın.**

   Visual Studio **QuickTest** projesini **Çözüm Gezgini** ekler ve **UnitTest1.cs** dosyası düzenleyicide açılır.

   :::image type="content" source="media/vs-2022/tutorial-projects-solution-explorer.png" alt-text="İki projeyle Çözüm Gezgini ekran görüntüsü." border="false":::

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

Yönteminizi **QuickDate** projesinde test etmek için yeni birim testi projesini kullan çünkü Bu nedenle **QuickTest** projesine **QuickDate'e** bir başvuru eklemeniz gerekir. Başvuru eksildi, *iki* proje arasında bir derleme bağımlılığı oluşturur, yani çözümü derlemek için **QuickDate,** QuickTest'den önce **derlemeler oluşturur.**

::: moniker range="vs-2017"

1. QuickTest **projesinde** **Bağımlılıklar düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Başvuru Ekle'yi **seçin.**

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i genişletin **ve** Çözüm'i **seçin.** Orta bölmede **QuickDate** seçeneğinin yanındaki onay kutusunu ve ardından Tamam'ı **seçin.**

   **QuickDate projesine bir** başvuru eklenir.

   ![Proje başvurularını Çözüm Gezgini ekran görüntüsü Visual Studio.](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Veri Çözüm Gezgini proje başvurularını gösteren ekran Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. **QuickTest** **projesinde** Bağımlılıklar düğümünü seçin ve sağ tıklama veya bağlam menüsünden Başvuru **ekle'Project seçin.**

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i **genişletin ve** Çözüm'i **seçin.** Orta bölmede **QuickDate** seçeneğinin yanındaki onay kutusunu ve ardından Tamam'ı **seçin.**

   **QuickDate projesine bir** başvuru eklenir.

   ![2019'Çözüm Gezgini proje başvurularını gösteren Visual Studio ekran görüntüsü.](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Bu **Çözüm Gezgini,** **QuickTest** projesinin  Başvurular düğümüne sağ tıklayın ve bağlam **menüsünden Başvuru** Ekle'yi seçin.

1. Başvuru Yöneticisi **iletişim kutusundaki** Projeler'in **altında** **QuickDate** öğesinin yanındaki onay kutusunu işaretleyin ve ardından Tamam'ı **seçin.**

   içinde **QuickTest projesinin altında QuickDate** **projesine** bir başvuru **Çözüm Gezgini.**

   :::image type="content" source="media/vs-2022/tutorial-projects-solution-explorer-reference.png" alt-text="Proje başvurularını Çözüm Gezgini ekran görüntüsü." border="false":::

::: moniker-end

## <a name="add-test-code"></a>Test kodu ekleme

1. Şimdi C# test kodu dosyasına test kodu ekleyin. *UnitTest1.cs içeriğini* aşağıdaki kodla değiştirin:

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

   Bazı kodun altında kırmızı bir geçiş görünür. Test projesini **QuickDate** projesine arkadaş [derlemesi yaparak](/dotnet/standard/assembly/friend-assemblies) bu hatayı düzeltin.

1. Test projesinde hatayı çözmek için *Calendar.cs* dosyasında aşağıdaki [using](/dotnet/csharp/language-reference/keywords/using-statement) deyimini ve özniteliğini <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> dosyanın en üstüne ekleyin.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   **Calendar.cs kodu** şu ekran görüntüsüne benzer şekilde görüntü gerekir:

   ::: moniker range="<=vs-2019"

   ![C Sharp kodunu gösteren ekran görüntüsü.](media/tutorial-projects-cs-code.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/tutorial-projects-cs-code.png" alt-text="C Sharp kodunu gösteren ekran görüntüsü." border="false":::

   ::: moniker-end

### <a name="run-the-unit-test"></a>Birim testini çalıştırma

::: moniker range="vs-2017"

Birim testinizin çalışa çalışa çalışa bir kontrol etmek için menü **çubuğundan Test**  >    >  **Çalıştırması Tüm Testleri'i** seçin. Test Gezgini adlı **bir pencere** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

::: moniker-end

::: moniker range=">=vs-2019"

Birim testinizin çalışa çalışa çalışa çalışa bir kontrol etmek için menü **çubuğundan Test**  >   Çalıştırması Tüm Testleri'i seçin. **Test Gezgini penceresi** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

::: moniker-end

::: moniker range="<=vs-2019"

![Test Gezgini'ni ve geçildi testini gösteren ekran görüntüsü.](media/tutorial-projects-test-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-projects-test-explorer.png" alt-text="Test Gezgini'ni ve geçildi testini gösteren ekran görüntüsü." border="false":::

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğunda Test Gezgini'ni  >  **Windows** Test  >  **Gezgini'ni** seçerek açın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğundan Test **Gezgini'ni**  >  **seçerek** açın.

::: moniker-end

## <a name="project-properties"></a>Proje özellikleri

Özniteliği içeren *Calendar.cs* dosyasındaki <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> satır, **QuickTest** projesinin derleme adına veya dosya adına başvurur. Derleme adı her zaman proje adıyla aynı olmayacaktır. Projenin derleme adını bulmak için proje özelliklerini kullanın. Özellik sayfaları, proje için çeşitli ayarlar içerir.

1. Bu **Çözüm Gezgini** Hızlı Test projesine  sağ tıklayın ve Özellikler'i **seçin** veya projeyi seçin ve Alt Enter **tuşuna** + **basın.**

   Projenin *özellik* sayfaları Uygulama **sekmesine** açılır. QuickTest **projesinin** derleme adı aslında **QuickTest'tir.**

   2004'e tıklayın. Test projesini derlemek için sonuçta elde edilen  ikili dosyanın adıQuickTest.dllolarak *\<NewName>.dll.*

    ::: moniker range="<=vs-2019"

    ![Proje özelliklerini gösteren ekran görüntüsü.](media/tutorial-projects-netcore-properties.png)

    ::: moniker-end

    ::: moniker range=">=vs-2022"

    :::image type="content" source="media/vs-2022/tutorial-project-properties.png" alt-text="Proje özelliklerini gösteren ekran görüntüsü." lightbox="media/vs-2022/tutorial-project-properties.png":::

    ::: moniker-end

1. Projenin özellik sayfalarının Build ve Debug gibi diğer **sekmelerini** **keşfedin.** Bu sekmeler farklı proje türleri için farklıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümlerle çalışma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
