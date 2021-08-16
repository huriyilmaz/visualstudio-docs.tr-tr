---
title: Projelere ve çözümlere giriş
description: Projeler ve çözümler arasındaki farkları ve bunları projelerde nasıl Visual Studio.
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
ms.openlocfilehash: a3d99cd3cb3920a083c592e233947839d6d1f7d05c7dd67bc66e096e5d5bf9ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273584"
---
# <a name="introduction-to-projects-and-solutions"></a>Projelere ve çözümlere giriş

Bu giriş makalesinde, bir çözüm ve bir  proje oluşturmanın ne anlama geldiğini incele Visual Studio.  Çözüm, bir veya daha fazla ilgili kod projesini (örneğin, sınıf kitaplığı projesini ve karşılık gelen bir test projesini) düzenlemek için kullanılan bir kapsayıcıdır. Bir projenin özelliklerine ve içerenin bazı dosyalarına göz atabilirsiniz. Ayrıca bir projeden diğerine başvuru da oluşturuz.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

Bir proje kavramını anlamak için eğitim amaçlı bir alıştırma olarak sıfırdan bir çözüm ve proje oluşturmamız gerekir. Genel olarak Visual Studio Visual Studio, yeni bir proje 200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000 

> [!NOTE]
> Bu hizmetlerde uygulama geliştirmek için çözümler ve Visual Studio. Ayrıca kod içeren bir klasör açıp kodlamaya, oluşturmaya ve hata ayıklamaya başlayabilirsiniz. Örneğin, bir GitHub [](https://github.com/) klonlarsanız, bu bir Visual Studio ve çözüm içereyem olabilir. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Çözüm, bir veya daha fazla ilgili Visual Studio düzenlemek için tek bir kapsayıcı tarafından kullanılan kapsayıcıdır. Bir çözümü Visual Studio, çözümün içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmamıza başlayacağız. Uygulama hakkında bilgi Visual Studio, büyük olasılıkla kendinizi çok sık boş çözümler oluştururken bulamazsınız. Yeni bir proje oluşturursanız, Visual Studio açık bir çözüm yoksa projeyi otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Üst menü çubuğunda Dosya Yeni **Dosya'Project.** >  > 

   Yeni **Project** iletişim kutusu açılır.

1. Sol bölmede Diğer Project **Türleri'ni genişletin** ve ardından **Çözümler'Visual Studio seçin.** Orta bölmede Boş Çözüm **şablonunu** seçin. Çözüme **QuickSolution adını** ve ardından Tamam **düğmesini** seçin.

   ![Visual Studio 2017'de Boş Çözüm şablonu](media/tutorial-projects-new-solution.png "Visual Studio 2017 ' deki boş çözüm şablonu.")

   Başlangıç **Sayfası** kapanır ve Çözüm Gezgini **penceresinin** sağ tarafında bir Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında** arama kutusuna **boş çözüm** girin, Boş Çözüm şablonunu seçin ve **ardından** Sonraki'yi **seçin.**

   ![Visual Studio 2019'da Boş Çözüm şablonu](media/vs-2019/tutorial-projects-blank-solution-template.png "Visual Studio 2019 ' deki boş çözüm şablonu.")

    > [!TIP]
    > Yüklü birkaç iş yükünüz varsa, **Arama** sonuçları listenizin en üstünde Boş Çözüm şablonu görüne görünebilir. Listenin arama bölümünü **temel alarak Diğer sonuçlara kaydırmayı** deneyin. Burada görünse gerekir.

4. Çözüme **QuickSolution adını ve** ardından Oluştur'a **seçin.**

   Çözüm, **Çözüm Gezgini** penceresinin sağ tarafındaki Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ek o zaman. Boş bir projeyle başlayacağız ve ihtiyacımız olan öğeleri projeye ekleyebilirsiniz.

::: moniker range="vs-2017"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi  > **Project.**

   Yeni **Veri Project** iletişim kutusu açılır.

1. Sol bölmede **Visual C# öğesini genişletin ve** Masaüstü'Windows **seçin.** Ardından orta bölmede Boş Bölme **(Project) .NET Framework** seçin. Projeye **QuickDate adını ve** ardından Tamam'ı **seçin.**

   Çözüm altında QuickDate adlı bir proje görüntülenir **ve** Çözüm Gezgini. Şu andaApp.configadlı *tek bir dosya içerir.*

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **Visual C#** öğesini görmüyorsanız, **.NET** masaüstü geliştirmeyi iş yüküne Visual Studio gerekir. Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni iş yükü yüklemenin kolay bir  yolu, Yeni Visual Studio Yükleyicisi Ekle iletişim kutusunun sol alt köşesindeki Aç **bağlantısını Project** etmektir. Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Bağlantı Visual Studio Yükleyicisi açma](media/tutorial-projects-open-installer.png "Visual Studio 2017 ' deki yeni Project ekle iletişim kutusunda aç Visual Studio Yükleyicisi bağlantısı.")

::: moniker-end

::: moniker range=">=vs-2019"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi  > **Project.**

   Yeni proje ekle'yi **söyleyen bir iletişim kutusu açılır.**

1. En üstte **yer alan** arama kutusuna metni boş girin ve Dil'in altında **C#** öğesini **seçin.**

1. Boş veri **Project (.NET Framework) şablonunu** ve ardından Sonraki'yi **seçin.**

1. Projeye **QuickDate adını ve ardından** Oluştur'a **seçin.**

   Çözüm altında QuickDate adlı bir proje görüntülenir **ve** Çözüm Gezgini. Şu andaApp.configadlı *tek bir dosya içerir.*

   > [!NOTE]
   > Boş Yükleme **(Project) (.NET Framework)** şablonunu görmüyorsanız. **.NET masaüstü** geliştirme şablonunu Visual Studio yüklemeniz gerekir. Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır.
   >
   >Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay  bir yolu, arayabilirsiniz öğesini bu değil mi? metninin altındaki Daha fazla araç ve özellik yükle **bağlantısını seçmektir.** Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Bağlantı Visual Studio Yükleyicisi açma](media/vs-2019/tutorial-projects-open-installer.png "Visual Studio yeni Project oluştur iletişim kutusunda aç Visual Studio Yükleyicisi bağlantısı.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projemiz var. Şimdi bir kod dosyası ekleriz.

1. Çözüm Gezgini'daki **QuickDate** projesinin sağ tıklama veya bağlam **menüsünden** Yeni Öğe **Ekle'yi**  >  **seçin.**

   Yeni **Öğe Ekle iletişim** kutusu açılır.

1. **Visual C# Öğeleri'ne genişletin** ve Ardından Kod'a **seçin.** Orta bölmede Sınıf öğesi **şablonunu** seçin. Sınıfa **Takvim adını** ve ardından Ekle **düğmesini** seçin.

   Projeye *Calendar.cs* adlı bir dosya eklenir. Sonundaki *.cs,* C# kod dosyalarına verilen dosya uzantısıdır. Dosya, içindeki görsel proje hiyerarşisinde **Çözüm Gezgini** ve içeriği düzenleyicide açılır.

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

   Kodun ne yaptığını anlamanız gerek değildir, ancak **Ctrl** + **F5** tuşlarına basarak programı çalıştırabilir ve konsol (veya standart çıkış) penceresine bugünün tarihini yazdırıyor olduğunu görebilirsiniz.

## <a name="add-a-second-project"></a>İkinci proje ekleme

Çözümlerin birden fazla proje içermesi yaygındır ve bu projeler genellikle birbirine başvurur. Bir çözümde bulunan bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim testi projeleri veya web siteleri olabilir.

Şimdi çözüme bir birim testi projesi ekleriz. Bu kez projeye ek bir kod dosyası eklememiz gerekmay için bir proje şablonundan başlayacağız.

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi   >  **Project.**

::: moniker range="vs-2017"

2. Sol bölmede **Visual C# öğesini genişletin** ve Test **kategorisini** seçin. Orta bölmede MSTest Test Project **(.NET Core) proje** şablonunu seçin. Projeye **QuickTest adını ve** ardından Tamam'ı **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.cs* adlı bir dosya düzenleyicide açılır.

   ![Visual Studio Çözüm Gezgini projeyle çalışma](media/tutorial-projects-solution-explorer.png "Visual Studio 2017 ' de iki projeyle Çözüm Gezgini.")

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna metin birimi **testini** girin ve dil'in altında **C#** öğesini **seçin.**

3. .NET Core **Project** Birim Testi proje şablonunu ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > 2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Birim Testi Project (.NET Core)** olarak Birim **Testi** Project. Bu güncelleştirmede proje oluşturma adımlarının birkaçı değiştirildi.

4. Projeye **QuickTest adını ve** ardından Sonraki'yi **seçin.**

5. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

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
