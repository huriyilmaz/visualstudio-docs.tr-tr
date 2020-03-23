---
title: Projelere ve çözümlere giriş
ms.date: 02/24/2020
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da2fc196f687e2335933794a578f507dafbc6de3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579979"
---
# <a name="learn-about-projects-and-solutions"></a>Projeler ve çözümler hakkında bilgi edinin

Bu giriş makalesinde Visual Studio'da bir *çözüm* ve *proje* oluşturmanın ne demek olduğunu inceleyeceğiz. Çözüm, sınıf kitaplığı projesi ve karşılık gelen test projesi gibi bir veya daha fazla ilgili kod projesini düzenlemek için kullanılan bir kapsayıcıdır. Bir projenin özelliklerine ve içerebileceği bazı dosyalara bakacağız. Ayrıca bir projeden diğerine bir referans oluşturacağız.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

Bir proje kavramını anlamak için bir eğitim egzersizi olarak sıfırdan bir çözüm ve proje oluşturacağız. Visual Studio'yu genel kullanımınızda, yeni bir proje oluştururken Visual Studio'nun sunduğu çeşitli proje *şablonlarından* bazılarını büyük olasılıkla kullanırsınız.

> [!NOTE]
> Visual Studio'da uygulama geliştirmek için çözümler ve projeler gerekmez. Ayrıca kod içeren bir klasörü açabilir ve kodlamaya, oluşturmaya ve hata ayıklamaya başlayabilirsiniz. Örneğin, bir [GitHub](https://github.com/) repo'sunu klonlarsanız, Visual Studio projeleri ve çözümleri içermeyebilir. Daha fazla bilgi için visual [studio'da proje veya çözüm olmadan kod geliştir'e](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)bakın.

## <a name="solutions-and-projects"></a>Çözümler ve projeler

İsmini rağmen, bir çözüm bir "cevap" değildir. Çözüm, Visual Studio tarafından bir veya daha fazla ilgili projeyi düzenlemek için kullanılan bir kapsayıcıdır. Visual Studio'da bir çözüm açtığınızda, çözümün içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm üreterek araştırmamıza başlayacağız. Visual Studio'u tanımanın ardından, büyük olasılıkla kendinizi çok sık boş çözümler oluştururken bulamazsınız. Yeni bir proje oluşturduğunuzda, Visual Studio zaten açık olan bir çözüm yoksa projeyi barındıracak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Üst menü çubuğunda **Yeni** > **Proje** **yi seçin.** >

   **Yeni Proje** iletişim kutusu açılır.

1. Sol bölmede, **Diğer Proje Türlerini**genişletin, ardından **Visual Studio Solutions'ı**seçin. Orta bölmede **Boş Çözüm** şablonu'nu seçin. Çözümünüzü **QuickSolution**olarak adlandırın, ardından **Tamam** düğmesini seçin.

   ![Visual Studio 2017'de boş çözüm şablonu](media/tutorial-projects-new-solution.png)

   **Başlangıç Sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini'nde** bir çözüm görünür. Projelerinizin içeriğine göz atmak için büyük olasılıkla **Solution Explorer'ı** sık sık kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

3. Yeni **bir proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **Boş Çözüm** şablonunu seçin ve sonra **İleri'yi**seçin.

   ![Visual Studio 2019'da Boş Çözüm şablonu](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. **ÇözümquickSolution**adını ve sonra **Oluştur'u**seçin.

   Visual Studio penceresinin sağ tarafında **ki Solution Explorer'da** bir çözüm görünür. Projelerinizin içeriğine göz atmak için büyük olasılıkla **Solution Explorer'ı** sık sık kullanırsınız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ekleyelim. Boş bir projeyle başlayacağız ve ihtiyacımız olan öğeleri projeye ekleyeceğiz.

::: moniker range="vs-2017"

1. **Çözüm Gezgini'ndeki**Solution **'QuickSolution'** sağ tıkla veya bağlam menüsünden **Yeni Proje** **Ekle'yi** > seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

1. Sol bölmede Visual **C#** seçeneğini genişletin ve **Windows Desktop'ı**seçin. Ardından, orta bölmede Boş **Proje (.NET Framework)** şablonu'nu seçin. Proje **QuickDate**adı, sonra **Tamam**seçin.

   **Solution Explorer'da**QuickDate adlı bir proje çözümün altında görünür. Şu anda *App.config*adlı tek bir dosya içerir.

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **Visual C#** görmüyorsanız,.NET **masaüstü geliştirme** Visual Studio iş yükünü yüklemeniz gerekir. Visual Studio, yalnızca yaptığınız geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni bir iş yükü yüklemenin kolay bir yolu, **Yeni Proje Ekle** iletişim kutusunun sol alt köşesindeki Open Visual Studio **Installer** bağlantısını seçmektir. Visual Studio Installer başlattıktan sonra **.NET masaüstü geliştirme** iş yükünü ve ardından **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyici bağlantısını aç](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini'ndeki**Solution **'QuickSolution'** sağ tıkla veya bağlam menüsünden **Yeni Proje** **Ekle'yi** > seçin.

   **Yeni bir proje ekle**yazan bir iletişim kutusu açılır.

1. **Metni boştaki** arama kutusuna girin ve **ardından Dil'in**altında **C#'yi** seçin.

1. Boş **Proje (.NET Framework)** şablonunu seçin ve sonra **İleri'yi**seçin.

1. **ProjequickDate**adı, sonra **oluştur'u**seçin.

   **Solution Explorer'da**QuickDate adlı bir proje çözümün altında görünür. Şu anda *App.config*adlı tek bir dosya içerir.

   > [!NOTE]
   > **Boş Proje (.NET Framework)** şablonunu görmüyorsanız, **.NET masaüstü geliştirme** Visual Studio iş yükünü yüklemeniz gerekir. Visual Studio, yalnızca yaptığınız geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **aradığınızı bulamadığınızı**belirten metnin altındaki daha fazla araç ve özellik bağlantısı **yükle'yi** seçmektir. Visual Studio Installer başlattıktan sonra **.NET masaüstü geliştirme** iş yükünü ve ardından **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyici bağlantısını aç](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projemiz var. Bir kod dosyası ekleyelim.

1. **Solution Explorer'daki** **QuickDate** projesinin sağ tıklama veya bağlam menüsünden**Yeni Öğe** **Ekle'yi** > seçin.

   **Yeni Öğe Ekle** iletişim kutusu açılır.

1. **Görsel C# Öğelerini**Genişletin, ardından **Kod'u**seçin. Orta bölmede **Sınıf** öğesi şablonu'nu seçin. Sınıf **Takvimi'ni**adlandırın ve sonra **Ekle** düğmesini seçin.

   Projeye *Calendar.cs* adlı bir dosya eklenir. Sonundaki *.cs,* C# kod dosyalarına verilen dosya uzantısıdır. Dosya, **Çözüm Gezgini'ndeki**görsel proje hiyerarşisinde görünür ve içeriği düzenleyicide açılır.

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

   Kodun ne işe yyaptığını anlamanız gerekmez, ancak isterseniz **Ctrl**+**F5** tuşuna basarak programı çalıştırabilir ve bugünkü tarihi konsol (veya standart çıktı) penceresine yazdırdığını görebilirsiniz.

## <a name="add-a-second-project"></a>İkinci bir proje ekleme

Çözümlerin birden fazla proje içermesi yaygındır ve genellikle bu projeler birbirini referans altına almaktadır. Çözümdeki bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim test projeleri veya web siteleri olabilir.

Çözümümüze bir birim test projesi ekleyelim. Bu sefer bir proje şablonundan başlayacağız, böylece projeye ek bir kod dosyası eklemek zorunda kalmayız.

1. **Çözüm Gezgini'ndeki**Solution **'QuickSolution'** sağ tıkla veya bağlam menüsünden**Yeni Proje** **Ekle'yi** > seçin.

::: moniker range="vs-2017"

2. Sol bölmede Visual **C#** seçeneğini genişletin ve **Test** kategorisini seçin. Orta bölmede, **MSTest Test Project (.NET Core)** proje şablonu'nu seçin. **ProjequickTest**adını ve sonra **Tamam**seçin.

   **Çözüm Gezgini'ne**ikinci bir proje eklenir ve UnitTest1.cs *adlı* bir dosya düzenleyicide açılır.

   ![İki proje ile Visual Studio Solution Explorer](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **bir proje** iletişim kutusu ekle kutusunda, metin **birimi testini** üstteki arama kutusuna girin ve **ardından Dil'in**altında **C#'yi** seçin.

3. **MSTest Test Project (.NET Core)** proje şablonu'nu seçin ve ardından **İleri'yi**seçin.

4. Projeye **QuickTest**adını ver ve sonra **Oluştur'u**seçin.

   **Çözüm Gezgini'ne**ikinci bir proje eklenir ve UnitTest1.cs *adlı* bir dosya düzenleyicide açılır.

   ![İki proje ile Visual Studio Solution Explorer](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

**QuickDate** projesinde yöntemimizi test etmek için yeni birim test projesini kullanacağız, bu yüzden bu projeye bir referans eklememiz gerekiyor. Bu, iki proje arasında bir *yapı bağımlılığı* oluşturur, yani çözümü oluşturduğunuzda **QuickDate** **QuickTest'ten**önce oluşturulur.

1. **QuickTest** projesinde **Bağımlılıklar** düğüm'ünden ve sağ tıklatma veya bağlam menüsünden **Başvuru Ekle'yi**seçin.

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede, **Projeleri** genişletin ve **Çözüm'u**seçin. Orta bölmede, **QuickDate'in**yanındaki onay kutusunu seçin ve ardından **Tamam'ı**seçin.

   **QuickDate** projesine bir başvuru eklenir.

   ![Visual Studio 2019 Çözüm Explorer proje referansgösteren](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Test kodu ekleme

1. Şimdi C# test kodu dosyasına test kodu ekleyeceğiz. *UnitTest1.cs* içeriğini aşağıdaki kodla değiştirin:

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

   Bazı kodun altında kırmızı bir dalgalı lık göreceksiniz. Bu hatayı, test projesini **QuickDate** projesine [arkadaş derlemesi](/dotnet/standard/assembly/friend-assemblies) yaparak düzeltiriz.

1. **QuickDate** projesinde, zaten açık değilse *Calendar.cs* dosyasını açın. Test projesindeki hatayı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> gidermek için aşağıdaki deyimi [ve](/dotnet/csharp/language-reference/keywords/using-statement) dosyanın üst bölümüne atfetmeyi ekleyin.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Kod dosyası aşağıdaki gibi görünmelidir:

   ![CSharp kodu](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Proje özellikleri

Öznitelik içeren *Calendar.cs* dosyasındaki <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> **satır, QuickTest** projesinin derleme adı (dosya adı) referansları. Derleme adı her zaman proje adı ile aynı olmayabilir. Projenin montaj adını bulmak için proje özelliklerini açın.

1. **Solution Explorer'da** **QuickTest** projesini seçin. Sağ tıklatma veya bağlam menüsünden **Özellikler'i**seçin veya **Alt**+**Enter**tuşuna basın.

   Projenin *özellik sayfaları* **Uygulama** sekmesinde açılır. Özellik sayfaları proje için çeşitli ayarlar içerir. QuickTest projesinin montaj adının gerçekten **"QuickTest"** olduğuna dikkat edin. Eğer değiştirmek isteseydin, bunu burada yapardın. Daha sonra, test projesini oluşturduğunuzda, elde edilen ikili dosyanın adı *QuickTest.dll'den* seçtiğiniz her şeye değişir.

   ![Proje özellikleri](media/tutorial-projects-netcore-properties.png)

1. **Yapı** ve **Hata Ayıklama**gibi projenin özellik sayfalarının diğer sekmelerinden bazılarını keşfedin. Bu sekmeler farklı proje türleri için farklıdır.

## <a name="next-steps"></a>Sonraki adımlar

Birim testinizin çalışıp çalışmadığını kontrol etmek istiyorsanız, menü çubuğundan**Tüm Testleri** **Test** > **Et'i** > seçin. **Test Gezgini** adlı bir pencere açılır ve **TestGetCurrentDate** testinin geçtiğini görmeniz gerekir.

![Visual Studio'da Test Explorer geçti testi gösteriyor](media/tutorial-projects-test-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> **Test Gezgini** otomatik olarak açılmıyorsa, menü çubuğundan **Test** > **Windows** > **Test Gezgini'ni** seçerek açın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> **Test Gezgini** otomatik olarak açılmıyorsa, menü çubuğundan **Test** > **Gezgini'ni** seçerek açın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturun](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
