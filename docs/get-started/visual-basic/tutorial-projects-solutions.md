---
title: Öğretici projeleri ve çözüm Visual Basic
description: Geliştirici olarak bir çözüm ve proje Visual Studio nasıl Visual Basic öğrenin.
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 86f9760806296b8c3906ef70d1557395d225ba23
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056595"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Visual Basic kullanarak projeler ve çözümler hakkında bilgi Visual Basic

Bu giriş makalesinde, bir çözüm ve bir  proje oluşturmanın ne anlama geldiğini Visual Studio.  Çözüm, bir veya daha fazla ilgili kod projesini (örneğin, sınıf kitaplığı projesini ve karşılık gelen bir test projesini) düzenlemek için kullanılan bir kapsayıcıdır. Bir projenin özelliklerine ve içerenin bazı dosyalarına göz atabilirsiniz. Ayrıca bir projeden diğerine başvuru da oluşturuz.

::: moniker range="vs-2017"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Visual Studio Preview [2022 Preview'Visual Studio](https://visualstudio.microsoft.com/vs/preview/vs2022) yüklemeleri sayfasına gidip ücretsiz olarak yükleyin.

::: moniker-end

Bir proje kavramını anlamak için eğitim amaçlı bir alıştırma olarak sıfırdan bir çözüm ve proje oluşturmamız gerekir. Visual Studio genel kullanımında, yeni bir proje oluşturmadan önce  büyük olasılıkla Visual Studio çeşitli proje şablonlarını kullanırsınız.

> [!NOTE]
> Bu hizmetlerde uygulama geliştirmek için çözümler ve Visual Studio. Ayrıca kod içeren bir klasör açıp kodlamaya, oluşturmaya ve hata ayıklamaya başlayabilirsiniz. Örneğin, bir GitHub [](https://github.com/) klonlarsanız, bu, tek bir Visual Studio ve çözüm içereyem olabilir. Daha fazla bilgi için [bkz. Proje veya Visual Studio olmadan kod geliştirme.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Çözüm, bir veya daha fazla ilgili Visual Studio düzenlemek için tek bir kapsayıcı tarafından kullanılan kapsayıcıdır. Bir çözümü Visual Studio, çözümün içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmamıza başlayacağız. Bu sorunları Visual Studio, büyük olasılıkla kendinizi çok sık boş çözümler oluştururken bulamazsınız. Yeni bir proje oluşturursanız, Visual Studio açık bir çözüm yoksa projeyi otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni **Dosya'Project.** >  > 

   Yeni **Project** iletişim kutusu açılır.

1. Sol bölmede Diğer Project **Türleri'ni genişletin** ve ardından **Çözümler'Visual Studio seçin.** Orta bölmede Boş Çözüm **şablonunu** seçin. Çözüme **QuickSolution adını ve** ardından Tamam'ı **seçin.**

   ![Visual Studio'de boş çözüm Visual Studio](../media/tutorial-projects-new-solution.png)

   Başlangıç **Sayfası** kapanır ve Çözüm Gezgini **penceresinin** sağ tarafında bir Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasında** arama kutusuna **boş çözüm** girin, Boş Çözüm şablonunu seçin ve **ardından** Sonraki'yi **seçin.**

   ![Visual Studio 2019'da Boş Çözüm şablonu](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüme **QuickSolution adını ve** ardından Oluştur'a **seçin.**

   Çözüm, **Çözüm Gezgini** penceresinin sağ tarafındaki Visual Studio görünür. Büyük olasılıkla **projenizin Çözüm Gezgini** göz atmak için bu bilgileri sık sık kullanacağız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ekleriz. Boş bir projeyle başlayacağız ve ihtiyacımız olan öğeleri projeye ekleyebilirsiniz.

::: moniker range="vs-2017"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam  **menüsünden Çözüm Gezgini** > **Ekle'yi Project.**

   Yeni **Veri Project** iletişim kutusu açılır.

1. Sol bölmede, **Visual Basic'yi genişletin** ve **Windows Masaüstü'Windows seçin.** Ardından orta bölmede Boş Bölme **(Project) .NET Framework** seçin. Projeye **QuickDate adını ve** ardından Tamam **düğmesini** seçin.

   Çözüm altında QuickDate adlı bir proje görüntülenir **ve** Çözüm Gezgini. Şu andaApp.configadlı tek *bir dosya içerir.*

   > [!NOTE]
   > İletişim kutusunun sol **bölmesinde Visual Basic** görmüyorsanız, **.NET** masaüstü geliştirmeyi iş yüküne Visual Studio *gerekir.* Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni bir iş yükü yüklemenin kolay bir yolu, **Yeni** Visual Studio Yükleyicisi Ekle iletişim kutusunun sol alt köşesindeki Open **Project** bağlantısını seçmektir. Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Bağlantı Visual Studio Yükleyicisi açma](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam  **menüsünden Çözüm Gezgini** > **Ekle'yi Project.**

   Yeni proje ekle seçeneğinin **yer alan bir iletişim kutusu açılır.**

1. En üstte **yer alan** arama kutusuna metni boş girin ve Dil'in **Visual Basic** **seçin.**

1. Boş Veri **(Project) .NET Framework ve** ardından Sonraki'yi **seçin.**

1. Projeye **QuickDate adını ve ardından** Oluştur'a **seçin.**

   Çözüm altında QuickDate adlı bir proje görüntülenir **ve** Çözüm Gezgini. Şu andaApp.configadlı tek *bir dosya içerir.*

   > [!NOTE]
   > Empty **Project (.NET Framework)** şablonunu görmüyorsanız , **.NET masaüstü** geliştirme ve yükleme Visual Studio *gerekir.* Visual Studio, yalnızca sahip olduğunuz geliştirme türü için ihtiyacınız olan bileşenleri yüklemek için iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay  bir yolu, arayabilirsiniz? metninin altındaki Daha fazla araç ve özellik yükle bağlantısını **seçmektir.** Uygulama Visual Studio Yükleyicisi sonra **.NET** masaüstü geliştirme iş yükünü ve ardından Değiştir **düğmesini** seçin.
   >
   > ![Visual Studio 2019'da yükleyici bağlantısı](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projemiz var. Şimdi bir kod dosyası ekleriz.

1. Çözüm Gezgini'daki **QuickDate** projesinin sağ tıklama veya bağlam **menüsünden** Yeni Öğe **Ekle'yi**  >  **seçin.**

   Yeni **Öğe Ekle iletişim** kutusu açılır.

1. Ortak **Öğeler'i genişletin,** ardından Kod'ı **seçin.** Orta bölmede Sınıf öğesi **şablonunu** seçin. Sınıfa **Takvim adını** ve ardından Ekle **düğmesini** seçin.

   Projeye *Calendar.vb adlı* bir dosya eklenir. Sonundaki *.vb,* kod dosyalarına verilen dosya Visual Basic uzantısıdır. Dosya, içindeki görsel proje hiyerarşisinde **Çözüm Gezgini** ve içeriği düzenleyicide açılır.

1. *Calendar.vb dosyasının içeriğini* aşağıdaki kodla değiştirin:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   sınıfı, `Calendar` geçerli tarihi döndüren tek bir `GetCurrentDate` işlevi içerir.

1. Çözüm Gezgini'de My **Project** tıklayarak **proje Çözüm Gezgini.** Uygulama sekmesinde **Uygulama** **türü'sini Sınıf** Kitaplığı **olarak ayarlayın.** Projeyi başarıyla derlemek için bu adım gereklidir.

1. Proje derlemesinde **QuickDate'e** sağ tıklar ve **Çözüm Gezgini'ı** **seçerek projeyi derleme.** Çıkış penceresinde başarılı bir derleme iletisi **görüyorsanız.**

## <a name="add-a-second-project"></a>İkinci proje ekleme

Çözümlerin birden fazla proje içermesi yaygındır ve bu projeler genellikle birbirine başvurur. Bir çözümde bulunan bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim testi projeleri veya web siteleri olabilir.

Şimdi çözüme bir birim testi projesi ekleriz. Bu kez projeye ek bir kod dosyası eklememiz gerekmay için bir proje şablonundan başlayacağız.

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklaması veya bağlam  **menüsünden Çözüm Gezgini**  >  **Ekle'yi** Project.

::: moniker range="Vs-2017"

2. Sol bölmede, **Visual Basic'yi** genişletin ve **Test kategorisini** seçin. Orta bölmede Birim Testi Project **(.NET Framework) proje** şablonunu seçin. Projeye **QuickTest adını ve** ardından Tamam'ı **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.vb* adlı bir dosya düzenleyicide açılır.

   ![Visual Studio Çözüm Gezgini projeyle çalışma](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna metin birimi **testini** girin ve **dil'in Visual Basic** **seçin.**

3. Birim Testi **Project (.NET Framework) proje** şablonunu ve ardından Sonraki'yi **seçin.**

4. Projeye **QuickTest adını ve** ardından Oluştur'a **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.vb* adlı bir dosya düzenleyicide açılır.

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

**QuickDate** projesinde yöntemimizi test etmek için yeni birim testi projesini kullanacak, bu nedenle bu projeye bir başvuru eklememiz gerekiyor. Bu, iki *proje arasında bir* derleme bağımlılığı oluşturur, yani çözümü derlemek için **QuickDate,** QuickTest'den önce **yerleşiktir.**

1. QuickTest **projesinde** **Başvurular düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Başvuru Ekle'yi **seçin.**

   ![Başvuru Ekle menüsü](media/tutorial-projects-add-reference-vb.png)

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i genişletin **ve** Çözüm'i **seçin.** Orta bölmede **QuickDate'in** yanındaki onay kutusunu ve ardından Tamam **düğmesini** seçin.

   **QuickDate projesine bir** başvuru eklenir.

## <a name="add-test-code"></a>Test kodu ekleme

1. Şimdi test kodunu Visual Basic ekleyebilirsiniz. *UnitTest1.vb içeriğini* aşağıdaki kodla değiştirin.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Bazı kodun altında kırmızı bir geçiş olduğunu görüyorsunuz. Test projesini **QuickDate** projesine arkadaş [derlemesi yaparak bu](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) hatayı düzelteceğiz.

1. **QuickDate** projesine geri dönüp *Calendar.vb* dosyasını (henüz açık değilse) açın ve test projesinde hatayı çözmek için aşağıdaki [Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) deyimini ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini ekleyin.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Kod dosyası aşağıdaki gibi görünüyor olmalı:

   ![Visual Basic kodu](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Proje özellikleri

*Calendar.vb dosyasında özniteliğini* içeren satır, QuickTest projesinin derleme adına <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> (dosya adı) başvurur.  Derleme adı her zaman proje adıyla aynı olmayacaktır. Projenin derleme adını bulmak için proje özelliklerini açın.

1. Bu **Çözüm Gezgini** **QuickTest projesini** seçin. Sağ tıklama veya bağlam menüsünde Özellikler'i seçin **veya** Yalnızca Alt Enter **tuşuna** + **basın.** (Ayrıca, Çözüm Gezgini **.) Project** **My** Çözüm Gezgini tıklar.

   Projenin *özellik* sayfaları Uygulama **sekmesinde** açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **QuickTest** projesinin derleme adının gerçekten de "QuickTest" olduğunu fark ediyorum. Bunu değiştirmek istediyysanız, bunu burada yapacak oluruz. Ardından test projesini derlemeniz sonucunda elde edilen ikili dosyanın adı,QuickTest.dll *olarak* değişir.

   ![Proje özellikleri](../media/tutorial-projects-properties.png)

1. Projenin özellik sayfalarının Compile ve Ayarlar gibi diğer  **sekmelerini Ayarlar.** Bu sekmeler farklı proje türleri için farklıdır.

## <a name="optional-run-the-test"></a>(İsteğe bağlı) Testi çalıştırma

Birim testinizin çalışa çalışa çalışa bir kontrol etmek için menü **çubuğundan Test**  >    >  **Çalıştırması Tüm Testleri'i** seçin. Test Gezgini adlı **bir pencere** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

![Visual Studio testini gösteren Metin Gezgini](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğunda Test Gezgini'ni  >  **Windows** Test  >  **Gezgini'ni** seçerek açın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama hakkında daha fazla Visual Studio, öğreticilerde yer alan öğreticilerden birini Visual Basic [düşünün.](index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](../../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../../get-started/visual-studio-ide.md)
