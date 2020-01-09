---
title: Projeler ve çözümler giriş
ms.date: 07/22/2019
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c130f7f55409bd24520dd55e949d20e8d5bbb97
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567287"
---
# <a name="learn-about-projects-and-solutions"></a>Projeler ve çözümler hakkında bilgi edinin

Giriş niteliğindeki bu makalede şunları oluşturma ne demek keşfedeceğiz bir *çözüm* ve *proje* Visual Studio'da. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Bir proje özelliklerini ve bazı içerebileceği dosyalara göz atacağız. Ayrıca bir başvuru bir projeden diğerine oluşturacağız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

Bir proje kavramı anlamak için eğitim bir alıştırma olarak size bir çözüm ve proje sıfırdan oluşturmak. Visual Studio içinde genel kullanımı, büyük olasılıkla çeşitli proje bazılarını kullanacaksınız *şablonları* yeni bir proje oluşturduğunuzda, Visual Studio sunar.

> [!NOTE]
> Çözümler ve projeler, Visual Studio'da uygulama geliştirme gerekmez. Ayrıca, kod ve kodlama, derleme ve hata ayıklama başlangıç içeren bir klasör açabilirsiniz. Örneğin, kopyalama, bir [GitHub](https://github.com/) depo, Visual Studio projeleri ve çözümleri içermeyebilir. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. Visual Studio 'da bir çözüm açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Bir çözüm oluşturun

Bizim araştırması boş bir çözüm oluşturarak başlayacağız. Visual Studio bilmek aldıktan sonra büyük olasılıkla çok sık boş çözüm oluşturduğunuzu bulamaz. Yeni bir proje oluşturduğunuzda, Visual Studio otomatik olarak değil bir çözüm zaten varsa açık proje barındırmak için bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Üstteki menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

1. Sol bölmede genişletin **diğer proje türleri**, ardından **Visual Studio çözümleri**. Orta bölmede seçin **boş çözüm** şablonu. Çözümünüzü ad **QuickSolution**, ardından **Tamam** düğmesi.

   ![Visual Studio 2017 'de boş çözüm şablonu](media/tutorial-projects-new-solution.png)

   **Başlangıç sayfası** kapatır ve çözüm görünür **Çözüm Gezgini** Visual Studio penceresinin sağ tarafındaki. Büyük olasılıkla kullanacağınız **Çözüm Gezgini** genellikle projelerinizi içeriğini gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 'de boş çözüm şablonu](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüm **hızlı çözümünü**adlandırın ve ardından **Oluştur**' u seçin.

   Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Büyük olasılıkla kullanacağınız **Çözüm Gezgini** genellikle projelerinizi içeriğini gidin.

::: moniker-end

### <a name="add-a-project"></a>Bir proje ekleyin

Artık ilk Projemizin çözüme ekleyelim. Biz ile boş bir proje başlatın ve ihtiyacımız öğe projeye ekleyin.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

1. Sol bölmede genişletin **Visual C#** ve **Windows Masaüstü**. Orta bölmede seçin **boş proje (.NET Framework)** şablonu. Proje **Quickdate**olarak adlandırın ve ardından **Tamam**' ı seçin.

   QuickDate adlı bir proje çözümde altında görünür **Çözüm Gezgini**. Şu anda tek dosya adlı içerdiği *App.config*.

   > [!NOTE]
   > Görmüyorsanız **Visual C#** iletişim kutusunun sol bölmesinde yüklemeniz gerekir. **.NET masaüstü geliştirme** Visual Studio *iş yükü*. Visual Studio iş yükü tabanlı yükleme yalnızca bunu geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için kullanır. Yeni bir iş yükünü yüklemek için kolay bir yolu seçmektir **açık Visual Studio yükleyicisi** sol alt köşesine bağlantıyı **Yeni Proje Ekle** iletişim kutusu. Visual Studio Yükleyicisi'ni başlattıktan sonra seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir** düğmesi.
   >
   > ![Visual Studio yükleyicisi bağlantıyı aç](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni bir proje ekleyen**bir iletişim kutusu açılır.

1. Üstteki arama kutusuna **boş** metin girin ve ardından **C#** **dil**altında öğesini seçin.

1. **Boş proje (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Proje **Quickdate**olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje çözümde altında görünür **Çözüm Gezgini**. Şu anda tek dosya adlı içerdiği *App.config*.

   > [!NOTE]
   > **Boş proje (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü*yüklemeniz gerekir. Visual Studio iş yükü tabanlı yükleme yalnızca bunu geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını**belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi'ni başlattıktan sonra seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir** düğmesi.
   >
   > ![Visual Studio yükleyicisi bağlantıyı aç](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye bir öğe ekleyin

Boş bir proje sahibiz. Bir kod dosyası ekleyelim.

1. Sağ tıklayın veya bağlam menüsünde **QuickDate** projesi **Çözüm Gezgini**, seçin **Ekle** > **yeni öğe** .

   **Yeni Öğe Ekle** iletişim kutusu açılır.

1. Genişletin **Visual C# öğeleri**, ardından **kod**. Orta bölmede seçin **sınıfı** öğe şablonu. Sınıf adı **Takvim**ve ardından **Ekle** düğmesi.

   Adlı bir dosya *Calendar.cs* projeye eklenir. *.Cs* son C# kod dosyasına verilen dosya uzantısıdır. Dosya visual proje hiyerarşisinde görünür **Çözüm Gezgini**, ve içeriğinin düzenleyicide açılır.

1. Öğesinin içeriğini değiştirin *Calendar.cs* dosyasındaki kodu aşağıdaki kodla:

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

   Ne yaptığını anlamak gerekli değildir, ancak isterseniz tuşlarına basarak program çalışabilir **Ctrl**+**F5** ve bugünün tarihini konsolunu (veya standart çıktı) penceresini yazdırır.

## <a name="add-a-second-project"></a>İkinci bir proje ekleyin

Birden fazla proje ve genellikle bu projeler başvuru birbirini içeren çözümler için yaygın bir durumdur. Çözümdeki bazı projeler sınıf kitaplıkları, yürütülebilir bazı uygulamalar olabilir ve bazı Birim testi projelerini veya Web sitesi olabilir.

Birim testi projesi, çözüm ekleyelim. Biz bir ek kod dosyası projeye eklemek zorunda kalmamak için bu kez proje şablonundan başlayacağız.

1. Sağ tıklayın veya bağlam menüsünde **çözüm 'QuickSolution'** içinde **Çözüm Gezgini**, seçin **Ekle** > **YeniProje**.

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

Yeni birim test projesi bizim yöntemi test etmek için kullanılacak yapacağız **QuickDate** proje Biz bu projeye bir başvuru eklemeniz gerekir. Bu oluşturur bir *derleme bağımlılığı* çözümü oluşturduğunuzda iki projeler arasında güncelleştirmeyeceği **QuickDate** önce oluşturulan **QuickTest**.

1. **Hızlı test** projesinde **Bağımlılıklar** düğümünü seçin ve sağ tıklama ya da bağlam menüsünden **Başvuru Ekle**' yi seçin.

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede genişletin **projeleri** ve **çözüm**. Orta bölmede, **Quickdate**seçeneğinin yanındaki onay kutusunu seçin ve ardından * * Tamam ' ı seçin.

   Bir başvuru **QuickDate** projesi eklenir.

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

   Bazı kodlar altında kırmızı renkli bir çizgi görürsünüz. Bu hatayı test projesini yaparak gidereceğiz bir [arkadaş derleme](/dotnet/standard/assembly/friend-assemblies) için **QuickDate** proje.

1. **Quickdate** projesine geri döndüğünüzde, zaten açık değilse *Calendar.cs* dosyasını açın. Test projesindeki hatayı çözümlemek için aşağıdaki [using ifadesini](/dotnet/csharp/language-reference/keywords/using-statement) ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini dosyanın en üstüne ekleyin.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Kod dosyası şu şekilde görünmelidir:

   ![CSharp kod](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Proje Özellikleri

Satırda *Calendar.cs* içeren dosya <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği derleme adını (dosya adı) başvuruda **QuickTest** proje. Proje adı ile aynı derleme adı her zaman olmayabilir. Proje derleme adını bulmak için proje özelliklerini açın.

1. İçinde **Çözüm Gezgini**seçin **QuickTest** proje. Sağ tıklayın veya bağlam menüsünü seçin **özellikleri**, veya tuşuna basarak **Alt**+**Enter**.

   Projenin *Özellik sayfaları* **uygulama** sekmesinde açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. Dikkat derleme adını **QuickTest** projedir gerçekten "QuickTest". Bunu değiştirmek istiyorsanız, burada yaptığınız budur. Test projesi oluşturduğunuzda, daha sonra elde edilen ikili dosyasının adı gelen değiştirirsiniz *QuickTest.dll* , seçtiğiniz için.

   ![Proje Özellikleri](media/tutorial-projects-netcore-properties.png)

1. Projenin özellik sayfalarındaki **derleme** ve **hata ayıklama**gibi diğer sekmelerin bazılarını keşfedelim. Bu sekme, farklı proje türleri için farklıdır.

## <a name="next-steps"></a>Sonraki adımlar

Birim testinizi çalıştığını denetlemek istiyorsanız seçin **Test** > **çalıştırma** > **tüm testleri** menü çubuğundan. Bir pencere olarak adlandırılan **Test Gezgini** açar, görmelisiniz, **TestGetCurrentDate** test geçer.

![Visual Studio gösteren test Gezgini'nde test geçildi](media/tutorial-projects-test-explorer.png)

> [!TIP]
> Varsa **Test Gezgini** değil, otomatik olarak Aç seçerek açın **Test** > **Windows** > **TestGezgini** menü çubuğundan.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
