---
title: Projelere ve çözümlere giriş
description: Projeler ve çözümler arasındaki fark ve Visual Studio ' de nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 09/14/2021
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
ms.openlocfilehash: db3eea7017645d51065ed62e038c3323125e7b71
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128432013"
---
# <a name="introduction-to-projects-and-solutions"></a>Projelere ve çözümlere giriş

Bu tanıtım makalesinde, Visual Studio bir *çözüm* ve *Proje* oluşturmanın ne anlama geldiğini incelenir. Bir çözüm, bir veya daha fazla ilgili kod projesini bir sınıf kitaplığı projesi ve buna karşılık gelen bir test projesi gibi düzenlemek için bir kapsayıcıdır.

Bir proje kavramını anlamak için eğitim alıştırması yaparken, sıfırdan bir çözüm ve proje oluşturacaksınız. genellikle, yeni projeler oluşturmak için Visual Studio proje *şablonlarını* kullanırsınız. Ayrıca, bir projenin özelliklerine ve içerebileceği bazı dosyalara bakacaksınız ve bir projeden diğerine başvuru oluşturacaksınız.

> [!NOTE]
> Visual Studio uygulamalarında uygulama geliştirme, çözüm ve proje gerektirmez. Yalnızca kod içeren ve kodlamaya, oluşturmaya ve hata ayıklamaya başlayan bir klasörü açabilirsiniz. örneğin, klonlanmış bir [GitHub](https://github.com/) deposu Visual Studio projeleri ve çözümleri içermeyebilir. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).
::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Visual Studio, bir çözüm "yanıt" değildir. bir çözüm, bir veya daha fazla ilgili projeyi düzenlemek için kullanılan bir kapsayıcı Visual Studio. bir çözümü açtığınızda, Visual Studio çözümün içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmayı başlatın. Visual Studio öğrendikten sonra muhtemelen çok sık boş çözümler oluşturmayacağız. yeni bir proje oluşturduğunuzda, bir çözüm zaten açık değilse Visual Studio otomatik olarak proje için bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. üstteki menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   **yeni Project** iletişim kutusu açılır.

1. sol bölmede **diğer Project türler**' i genişletin ve **Visual Studio çözümler**' i seçin. Orta bölmede **boş çözüm** şablonunu seçin. Çözümünüzü **hızlı çözümünüz** olarak adlandırın, sonra **Tamam** düğmesini seçin.

   ![Visual Studio 2017 ' de seçili boş bir çözüm şablonunu gösteren ekran görüntüsü.](media/tutorial-projects-new-solution.png "Visual Studio 2017'de Boş Çözüm şablonu.")

   **başlangıç sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 ' de seçili boş bir çözüm şablonunu gösteren ekran görüntüsü.](media/vs-2019/tutorial-projects-blank-solution-template.png "Visual Studio 2019'daki Boş Çözüm şablonu.")

    > [!TIP]
    > Birden çok iş yükünden biri yüklüyse, **boş çözüm** şablonu arama sonuçları listenizin en üstünde görünmeyebilir. Listenin **Arama bölümüne göre diğer sonuçlara** kaydırma yapmayı deneyin. Burada görünmelidir.

4. Çözüm **hızlı çözümünü** adlandırın ve ardından **Oluştur**' u seçin.

   bir çözüm, Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio açın ve başlangıç penceresinde **yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna *boş çözüm* yazın, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/tutorial-projects-blank-solution-template.png" alt-text="Visual Studio ' de seçili boş bir çözüm şablonunu gösteren ekran görüntüsü." border="false":::

    > [!TIP]
    > Birden çok iş yükünden biri yüklüyse, **boş çözüm** şablonu arama sonuçları listenizin en üstünde görünmeyebilir. Şablonu bulmak için **aramanıza göre diğer sonuçlar** arasında gezinmeyi deneyin.

4. **Yeni projenizi yapılandırın** sayfasında çözüm **hızlı çözüm**' ü adlandırın ve ardından **Oluştur**' u seçin.

   **hızlı çözüm** çözümü, Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** görünür. Projelerinizin içeriğine gitmek için **Çözüm Gezgini** sık kullanılır.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi ilk projenizi çözüme ekleyin. Boş bir proje ile başlayın ve ihtiyacınız olan öğeleri ekleyin.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **yeni Project ekle** iletişim kutusu açılır.

1. sol bölmede, **Visual C#** ' ı genişletin ve **masaüstü Windows**' ni seçin. ardından ortadaki bölmede **boş Project (.NET Framework)** şablonunu seçin. Proje **Quickdate** olarak adlandırın ve ardından **Tamam**' ı seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > iletişim kutusunun sol bölmesinde **Visual C#** görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemelisiniz. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. yeni bir iş yükünü yüklemenin kolay bir yolu, **yeni Project ekle** iletişim kutusunun sol alt köşesindeki **aç Visual Studio Yükleyicisi** bağlantısını seçeklemektir. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > ![açık Visual Studio Yükleyicisi bağlantısını gösteren ekran görüntüsü.](media/tutorial-projects-open-installer.png "Visual Studio 2017'de Project yeni Visual Studio Yükleyicisi Ekle iletişim kutusundaki Visual Studio bağlantısı.")

::: moniker-end

::: moniker range="vs-2019"

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
   > ![açık Visual Studio Yükleyicisi bağlantısını gösteren ekran görüntüsü.](media/vs-2019/tutorial-projects-open-installer.png "Yeni Visual Studio Yükleyicisi Oluştur iletişim kutusundaki Açık kaynak Project bağlantısı Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümüne** sağ tıklayın ve  > bağlam menüsünden **yeni Project** ekle ' yi seçin.

1. **Yeni Proje Ekle** sayfasında, üstteki arama kutusuna *boş* yazın ve **tüm diller** altında **C#** ' ı seçin.

1. C# **boş Project (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   > [!NOTE]
   > Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. **boş Project (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemeniz gerekir.
   >
   >Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını** belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
   >
   > :::image type="content" source="media/vs-2022/tutorial-projects-open-installer.png" alt-text="açık Visual Studio Yükleyicisi bağlantısını gösteren ekran görüntüsü." border="false":::

1. **Yeni projenizi yapılandırın** sayfasında, proje **quickdate** adını adlandırın ve ardından **Oluştur**' u seçin.

   **Quickdate** projesi **Çözüm Gezgini** çözüm altında görünür. Şu anda proje **App.config** adlı tek bir dosya içeriyor.

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş projenize bir kod dosyası ekleyin.

1. **Çözüm Gezgini** içindeki **quickdate** projesinin sağ tıklama veya kısayol menüsünden   >  **Yeni öğe** Ekle ' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. **Visual C# öğelerini** genişletin ve **kod** öğesini seçin. Orta bölmede **sınıf** öğesi şablonunu seçin. **Ad**' ın altında, *Takvim* yazın ve ardından **Ekle**' yi seçin.

   Visual Studio projeye *Calendar. cs* adlı bir dosya ekler. Uçtaki *. cs* , C# kod dosyaları için dosya uzantısıdır. **Takvim. cs** dosyası **Çözüm Gezgini** görsel proje hiyerarşisinde görüntülenir ve dosya düzenleyicide açılır.

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

   Kodun henüz yaptığı her şeyi anlamanız gerekmez. **Ctrl** F5 tuşlarına basarak uygulamayı çalıştırın ve uygulamanın bugünün tarihini konsola veya standart çıkış penceresine + yazdırıyor olduğunu görebilirsiniz.

## <a name="add-a-second-project"></a>İkinci proje ekleme

Çözümler genellikle birden fazla proje içerir ve bu projeler genellikle birbirine başvurur. Bir çözümde bulunan bazı projeler sınıf kitaplıkları, bazıları yürütülebilir uygulamalar ve bazıları birim testi projeleri veya web siteleri olabilir.

Çözümünüze birim testi projesi eklemek için projeye başka bir kod dosyası eklemek zorunda olmadığınız bir proje şablonundan başlayabilirsiniz.

::: moniker range="vs-2017"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

2. Sol bölmede **Visual C# öğesini genişletin** ve Test **kategorisini** seçin. Orta bölmede MSTest Test Testi Project **(.NET Core) proje** şablonunu seçin. Projeye **QuickTest adını ve** ardından Tamam'ı **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.cs* adlı bir dosya düzenleyicide açılır.

   ![İki projeyle Çözüm Gezgini gösteren ekran görüntüsü.](media/tutorial-projects-solution-explorer.png "Çözüm Gezgini 2017'de iki Visual Studio projeyle birlikte.")

::: moniker-end

::: moniker range="vs-2019"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

2. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna metin birimi **testini** girin ve dil'in altında **C#** öğesini **seçin.**

3. .NET Core **Project** birim testi proje şablonunu ve ardından Sonraki'yi **seçin.**

   > [!NOTE]
   > 2019 Visual Studio 16.9 sürümünden başlayarak, MSTest proje şablonu adı **MSTest Birim Testi Project (.NET Core)** olarak Birim **Testi** Project. Bu güncelleştirmede proje oluşturma işlemiyle ilgili birkaç adım değiştirildi.

4. Projeye **QuickTest adını ve** ardından Sonraki'yi **seçin.**

5. Önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.cs* adlı bir dosya düzenleyicide açılır.

   ![İki projeyle Çözüm Gezgini gösteren ekran görüntüsü.](media/vs-2019/tutorial-projects-solution-explorer.png "Çözüm Gezgini iki projeyle Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.** > 

1. Yeni proje **ekle iletişim kutusunda,** en üstte yer alan arama kutusuna birim *testi* yazın ve ardından Tüm diller'in altında **C#** **öğesini seçin.**

1. C# Birim **Testi Project (.NET Framework) proje** şablonunu ve ardından Sonraki'yi **seçin.**

1. Yeni **projenizi yapılandır sayfasında,** projeye *QuickTest* adını ve ardından Oluştur'a **tıklayın.**

   Visual Studio **QuickTest** projesini **Çözüm Gezgini** ekler ve **UnitTest1.cs** dosyası düzenleyicide açılır.

   :::image type="content" source="media/vs-2022/tutorial-projects-solution-explorer.png" alt-text="İki projeyle Çözüm Gezgini gösteren ekran görüntüsü." border="false":::

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

Yeni birim testi projesini **kullanarak Yönteminizi QuickDate** projesinde test etmek için kullanır, bu nedenle **QuickTest** projesine **QuickDate** başvurusu eklemeniz gerekir. Başvuru eksildi, *iki* proje arasında bir derleme bağımlılığı oluşturur, yani çözümü derlemek için **QuickDate,** QuickTest'den önce **derlemeler oluşturur.**

::: moniker range="vs-2017"

1. QuickTest **projesinde** **Bağımlılıklar düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Başvuru Ekle'yi **seçin.**

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i **genişletin ve** Çözüm'i **seçin.** Orta bölmede **QuickDate** seçeneğinin yanındaki onay kutusunu ve ardından Tamam'ı **seçin.**

   **QuickDate projesine bir** başvuru eklenir.

   ![Proje başvurularını Çözüm Gezgini gösteren ekran görüntüsü Visual Studio.](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Uygulamanın içinde Çözüm Gezgini başvurularını gösteren ekran Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. QuickTest **projesinde** Bağımlılıklar **düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Add **Project Reference (Başvuru) öğesini seçin.**

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i **genişletin ve** çözüm'i **seçin.** Orta bölmede **QuickDate** seçeneğinin yanındaki onay kutusunu ve ardından Tamam'ı **seçin.**

   **QuickDate projesine bir** başvuru eklenir.

   ![2019'Çözüm Gezgini proje başvurularını gösteren Visual Studio ekran görüntüsü.](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Bu **Çözüm Gezgini,** **QuickTest** projesinin Başvurular düğümüne sağ tıklayın ve bağlam  **menüsünden Başvuru** Ekle'yi seçin.

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

Birim testinizin çalışa çalışa çalışanı kontrol etmek için menü **çubuğundan Test**  >   Çalıştırması Tüm Testleri'i seçin. **Test Gezgini penceresi** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

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
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğundan **Test** Gezgini'ni  >  **seçerek** açın.

::: moniker-end

## <a name="project-properties"></a>Proje özellikleri

Özniteliği içeren *Calendar.cs* dosyasındaki satır, QuickTest projesinin derleme adına <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> veya dosya adına başvurur.  Derleme adı her zaman proje adıyla aynı olmayacaktır. Projenin derleme adını bulmak için proje özelliklerini kullanın. Özellik sayfaları, proje için çeşitli ayarlar içerir.

1. Bu **Çözüm Gezgini** Hızlı Test projesine  sağ tıklayın ve Özellikler'i **seçin** veya projeyi seçin ve Alt Enter **tuşuna** + **basın.**

   Projenin *özellik* sayfaları Uygulama **sekmesine** açılır. QuickTest **projesinin** derleme adı aslında **QuickTest'tir.**

   2004'e göre, adı burada değiştirebilirsiniz. Test projesini derlemek için sonuçta elde edilen ikili dosyanın adıQuickTest.dll *olarak* *\<NewName>.dll.*

    ::: moniker range="<=vs-2019"

    ![Proje özelliklerini gösteren ekran görüntüsü.](media/tutorial-projects-netcore-properties.png)

    ::: moniker-end

    ::: moniker range=">=vs-2022"

    :::image type="content" source="media/vs-2022/tutorial-project-properties.png" alt-text="Proje özelliklerini gösteren ekran görüntüsü." border="false":::

    ::: moniker-end

1. Projenin özellik sayfalarının Build ve Debug gibi diğer **sekmelerini** **keşfedin.** Bu sekmeler farklı proje türleri için farklıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümlerle çalışma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
