---
title: Projeler ve çözümler giriş
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579979"
---
# <a name="learn-about-projects-and-solutions"></a>Projeler ve çözümler hakkında bilgi edinin

Bu giriş makalesinde, Visual Studio 'da bir *çözüm* ve *Proje* oluşturmak için ne anlama geldiğini keşfedeceğiz. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Bir proje özelliklerini ve bazı içerebileceği dosyalara göz atacağız. Ayrıca bir başvuru bir projeden diğerine oluşturacağız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bir proje kavramı anlamak için eğitim bir alıştırma olarak size bir çözüm ve proje sıfırdan oluşturmak. Visual Studio 'nun genel kullanım ortamınızda, yeni bir proje oluşturduğunuzda Visual Studio 'nun sunduğu çeşitli proje *şablonlarından* bazılarını kullanırsınız.

> [!NOTE]
> Çözümler ve projeler, Visual Studio'da uygulama geliştirme gerekmez. Ayrıca, kod ve kodlama, derleme ve hata ayıklama başlangıç içeren bir klasör açabilirsiniz. Örneğin, bir [GitHub](https://github.com/) deposu klonladığınızda, Visual Studio projeleri ve çözümleri içermeyebilir. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. Visual Studio 'da bir çözüm açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Bir çözüm oluşturun

Bizim araştırması boş bir çözüm oluşturarak başlayacağız. Visual Studio bilmek aldıktan sonra büyük olasılıkla çok sık boş çözüm oluşturduğunuzu bulamaz. Yeni bir proje oluşturduğunuzda, Visual Studio otomatik olarak değil bir çözüm zaten varsa açık proje barındırmak için bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio’yu açın.

1. Üstteki menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

1. Sol bölmede **diğer proje türleri**' ni genişletin ve ardından **Visual Studio çözümleri**' ni seçin. Orta bölmede **boş çözüm** şablonunu seçin. Çözümünüzü **hızlı çözümünüz**olarak adlandırın, sonra **Tamam** düğmesini seçin.

   ![Visual Studio 2017 'de boş çözüm şablonu](media/tutorial-projects-new-solution.png)

   **Başlangıç sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio’yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 'de boş çözüm şablonu](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüm **hızlı çözümünü**adlandırın ve ardından **Oluştur**' u seçin.

   Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

### <a name="add-a-project"></a>Bir proje ekleyin

Artık ilk Projemizin çözüme ekleyelim. Biz ile boş bir proje başlatın ve ihtiyacımız öğe projeye ekleyin.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

1. Sol bölmede,  **C# görsel** ' i genişletin ve **Windows Masaüstü**' nu seçin. Ardından Ortadaki bölmede **boş proje (.NET Framework)** şablonunu seçin. Proje **Quickdate**olarak adlandırın ve ardından **Tamam**' ı seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini**çözümünün altında görünür. Şu anda *app. config*adlı tek bir dosya içeriyor.

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **görsel C#**  görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemelisiniz. Visual Studio yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir iş yükünü yüklemenin kolay bir yolu, **Yeni Proje Ekle** iletişim kutusunun sol alt köşesindeki **Aç Visual Studio yükleyicisi** bağlantısını seçeklemektir. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio yükleyicisi bağlantıyı aç](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni bir proje ekleyen**bir iletişim kutusu açılır.

1. Üstteki arama kutusuna **boş** metin girin ve ardından **C#** **dil**altında öğesini seçin.

1. **Boş proje (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Proje **Quickdate**olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini**çözümünün altında görünür. Şu anda *app. config*adlı tek bir dosya içeriyor.

   > [!NOTE]
   > **Boş proje (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio iş yükünü yüklemelisiniz. Visual Studio yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını**belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio yükleyicisi bağlantıyı aç](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye bir öğe ekleyin

Boş bir proje sahibiz. Bir kod dosyası ekleyelim.

1. **Çözüm Gezgini**' de **quickdate** projesinin sağ tıklama veya kısayol menüsünden > **Yeni öğe** **Ekle** ' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. **C# Görsel öğeler**' i genişletin ve **kod**öğesini seçin. Orta bölmede **sınıf** öğesi şablonunu seçin. Sınıf **takvimini**adlandırın ve ardından **Ekle** düğmesini seçin.

   Projeye *Calendar.cs* adlı bir dosya eklenir. Uçtaki *. cs* C# kod dosyalarına verilen dosya uzantısıdır. Dosya **Çözüm Gezgini**' deki görsel proje hiyerarşisinde görüntülenir ve içeriği düzenleyicide açılır.

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

   Kodun ne yaptığını anlamanız gerekmez, ancak isterseniz, **Ctrl**+**F5** tuşuna basarak ve bugünün tarihini konsol (veya standart çıkış) penceresine yazdırdığınızı görmek için programı çalıştırabilirsiniz.

## <a name="add-a-second-project"></a>İkinci bir proje ekleyin

Birden fazla proje ve genellikle bu projeler başvuru birbirini içeren çözümler için yaygın bir durumdur. Çözümdeki bazı projeler sınıf kitaplıkları, yürütülebilir bazı uygulamalar olabilir ve bazı Birim testi projelerini veya Web sitesi olabilir.

Birim testi projesi, çözüm ekleyelim. Biz bir ek kod dosyası projeye eklemek zorunda kalmamak için bu kez proje şablonundan başlayacağız.

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

::: moniker range="vs-2017"

2. Sol bölmede, **görsel C#**  ' i genişletin ve **Test** kategorisini seçin. Orta bölmede, **MSTest test projesi (.NET Core)** proje şablonunu seçin. Projeyi **hızlı test**olarak adlandırın ve ardından **Tamam**' ı seçin.

   **Çözüm Gezgini**ikinci bir proje ve düzenleyicide *UnitTest1.cs* adlı bir dosya açılır.

   ![İki proje ile Visual Studio Çözüm Gezgini](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni Proje Ekle** iletişim kutusunda, üstteki arama kutusuna metin **birimi testini** girin ve ardından **C#** **dil**altında ' ı seçin.

3. **MSTest test projesi (.NET Core)** proje şablonunu seçin ve ardından **İleri**' yi seçin.

4. Projeyi **hızlı teste**adlandırın ve ardından **Oluştur**' u seçin.

   **Çözüm Gezgini**ikinci bir proje ve düzenleyicide *UnitTest1.cs* adlı bir dosya açılır.

   ![İki proje ile Visual Studio Çözüm Gezgini](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Bir proje başvurusu Ekle

**Hızlı Tarih** projesindeki yöntemizi test etmek için yeni birim testi projesini kullanacağız, bu nedenle bu projeye bir başvuru eklememiz gerekiyor. Bu, iki proje arasında bir *derleme bağımlılığı* oluşturur. Bu, çözümü oluşturduğunuzda hızlı **Test**öncesinde hızlı bir **Tarih** oluşturulur.

1. **Hızlı test** projesinde **Bağımlılıklar** düğümünü seçin ve sağ tıklama ya da bağlam menüsünden **Başvuru Ekle**' yi seçin.

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede, **Projeler** ' i genişletin ve **çözüm**' ü seçin. Orta bölmede, **Quickdate**seçeneğinin yanındaki onay kutusunu seçin ve ardından **Tamam**' ı seçin.

   **Quickdate** projesine bir başvuru eklenir.

   ![Visual Studio 2019 Çözüm Gezgini proje başvurusunu gösterme](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Test kodu ekleyin

1. Şimdi test kodu dosyasına test kodu C# ekleyeceğiz. *UnitTest1.cs* içeriğini aşağıdaki kodla değiştirin:

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

1. **Quickdate** projesine geri döndüğünüzde, zaten açık değilse *Calendar.cs* dosyasını açın. Test projesindeki hatayı çözümlemek için aşağıdaki [using ifadesini](/dotnet/csharp/language-reference/keywords/using-statement) ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini dosyanın en üstüne ekleyin.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Kod dosyası şu şekilde görünmelidir:

   ![CSharp kod](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Proje özellikleri

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini içeren *Calendar.cs* dosyasındaki satır, **hızlı test** projesinin derleme adına (dosya adı) başvurur. Proje adı ile aynı derleme adı her zaman olmayabilir. Proje derleme adını bulmak için proje özelliklerini açın.

1. **Çözüm Gezgini**' de **hızlı test** projesini seçin. Sağ tıklama veya bağlam menüsünde **Özellikler**' i seçin veya **enter** **tuşuna basın+** .

   Projenin *Özellik sayfaları* **uygulama** sekmesinde açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **Hızlı test** projesinin derleme adının gerçekten "QuickTest" olduğuna dikkat edin. Bunu değiştirmek istiyorsanız, burada yaptığınız budur. Ardından, test projesi oluşturduğunuzda, elde edilen ikili dosyanın adı *hızlı test. dll* ' den seçtiğiniz her şeyi değiştirecek.

   ![Proje özellikleri](media/tutorial-projects-netcore-properties.png)

1. Projenin özellik sayfalarındaki **derleme** ve **hata ayıklama**gibi diğer sekmelerin bazılarını keşfedelim. Bu sekme, farklı proje türleri için farklıdır.

## <a name="next-steps"></a>Sonraki adımlar

Birim testinizin çalıştığını denetlemek istiyorsanız, **test** > menü çubuğundan **tüm testleri** > **Çalıştır** ' ı seçin. **Test Gezgini** adlı bir pencere açılır ve **TestGetCurrentDate** testin başarılı olduğunu görmeniz gerekir.

![Visual Studio gösteren test Gezgini'nde test geçildi](media/tutorial-projects-test-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> **Test Gezgini** otomatik olarak açılmazsa, menü çubuğundan **test > ** **Windows** > **Test Gezgini** ' ni seçerek açın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> **Test Gezgini** otomatik olarak açılmazsa, menü çubuğundan **Test > test** **Gezgini** ' ni seçerek açın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve çözüm oluşturma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
