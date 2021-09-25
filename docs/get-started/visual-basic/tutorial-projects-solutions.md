---
title: Eğitim projeleri ve çözümleri Visual Basic
description: Visual Basic geliştiricisi olarak Visual Studio bir çözüm ve proje oluşturmayı öğrenin.
ms.date: 09/14/2021
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
ms.openlocfilehash: 816b72782866bc8c44e88431db3782a182428969
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430699"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Visual Basic kullanarak projeler ve çözümler hakkında bilgi edinin

Bu giriş makalesinde, Visual Studio bir *çözüm* ve *Proje* oluşturmanın ne anlama geldiğini keşfedeceğiz. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Projenin özelliklerine ve içerdikleri bazı dosyalara bakacağız. Ayrıca bir projeden diğerine bir başvuru oluşturacağız.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

Bir proje kavramını anlamak için eğitim alıştırması olarak sıfırdan bir çözüm ve proje oluşturacağız. Visual Studio genel kullanım ortamınızda, yeni bir proje oluşturduğunuzda Visual Studio sunduğu çeşitli proje *şablonlarından* bazılarını kullanacaksınız.

> [!NOTE]
> Visual Studio içinde uygulama geliştirmek için çözümler ve projeler gerekli değildir. Ayrıca yalnızca kod içeren ve kodlamaya, oluşturmaya ve hata ayıklamaya başlayan bir klasörü açabilirsiniz. örneğin, bir [GitHub](https://github.com/) depoyu klonladığınızda, Visual Studio projeleri ve çözümleri içermeyebilir. daha fazla bilgi için bkz. [proje veya çözüm olmadan Visual Studio kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. bir çözümü Visual Studio açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmayla başlayacağız. Visual Studio öğrendikten sonra, çoğunlukla boş çözümler oluşturmayacağınızı fark edersiniz. yeni bir proje oluşturduğunuzda, zaten açık bir çözüm yoksa, Visual Studio projeyi barındırmak için otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   **yeni Project** iletişim kutusu açılır.

1. sol bölmede **diğer Project türler**' i genişletin ve ardından **Visual Studio çözümler**' i seçin. Orta bölmede **boş çözüm** şablonunu seçin. Çözümünüzü **hızlı çözümünüz** olarak adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio 'de boş çözüm şablonu](../media/tutorial-projects-new-solution.png)

   **başlangıç sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Arama kutusunda ' boş çözüm ' ile yeni proje oluştur penceresini ve seçili boş çözüm proje şablonunu gösteren ekran görüntüsü.](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüm **hızlı çözümünü** adlandırın ve ardından **Oluştur**' u seçin.

   bir çözüm, Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/tutorial-projects-blank-solution-template.png" alt-text="Arama kutusunda ' boş çözüm ' ile yeni proje oluştur penceresini ve seçili boş çözüm proje şablonunu gösteren ekran görüntüsü.":::

1. Çözüm **hızlı çözümünü** adlandırın ve ardından **Oluştur**' u seçin.

   bir çözüm, Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ekleyelim. Boş bir proje ile başlayacağız ve proje için ihtiyacımız olan öğeleri ekleyeceğiz.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **yeni Project ekle** iletişim kutusu açılır.

1. sol bölmede **Visual Basic** ' ı genişletin ve **Windows masaüstü**' ni seçin. ardından ortadaki bölmede **boş Project (.NET Framework)** şablonunu seçin. Proje **Quickdate** olarak adlandırın, sonra **Tamam** düğmesini seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > iletişim kutusunun sol bölmesinde **Visual Basic** görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü* yüklemeniz gerekir. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. yeni bir iş yükünü yüklemenin kolay bir yolu, **yeni Project ekle** iletişim kutusunun sol alt köşesindeki **aç Visual Studio Yükleyicisi** bağlantısını seçeklemektir. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyicisi bağlantısını aç](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range="vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **Yeni bir proje ekleyen** bir iletişim kutusu açılır.

1. üstteki arama kutusuna **boş** metin girin ve ardından **dil** altında **Visual Basic** ' yi seçin.

1. **boş Project (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

1. Proje **Quickdate** olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > **boş Project (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü* yüklemeniz gerekir. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını** belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > ![' Daha fazla araç ve özellik yükler ' bağlantısı vurgulanmış şekilde yeni proje oluştur penceresini gösteren ekran görüntüsü.](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **yeni Project** ekle ' yi seçin.

   **Yeni bir proje ekleyen** bir iletişim kutusu açılır.

1. üstteki arama kutusuna **boş** metin girin ve ardından **tüm diller** açılan listesinde **Visual Basic** ' ı seçin.

1. **boş Project (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

1. Proje **Quickdate** olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > **boş Project (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü* yüklemeniz gerekir. Visual Studio, yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını** belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **değiştir** düğmesini seçin.
   >
   > :::image type="content" source="media/vs-2022/tutorial-projects-open-installer.png" alt-text="' Daha fazla araç ve özellik yükler ' bağlantısı vurgulanmış şekilde yeni proje oluştur penceresini gösteren ekran görüntüsü.":::

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projem var. Bir kod dosyası ekleyelim.

1. **Çözüm Gezgini** içindeki **quickdate** projesinin sağ tıklama veya kısayol menüsünden   >  **Yeni öğe** Ekle ' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. **Ortak öğeler**' i genişletin ve **kod** öğesini seçin. Orta bölmede **sınıf** öğesi şablonunu seçin. Sınıf **takvimini** adlandırın ve ardından **Ekle** düğmesini seçin.

   Projeye *Calendar. vb* adlı bir dosya eklenir. uçtaki *. vb* , Visual Basic kod dosyalarına verilen dosya uzantısıdır. Dosya **Çözüm Gezgini** içinde görsel proje hiyerarşisinde ve içeriği düzenleyicide açılır.

1. *Calendar. vb* dosyasının içeriğini aşağıdaki kodla değiştirin:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar`Sınıfı, geçerli tarihi döndüren tek bir işlevi içerir `GetCurrentDate` .

1. **Çözüm Gezgini** **Project** , proje özelliklerini açmak için tıklayın. **Uygulama** sekmesinde **uygulama türünü** **sınıf kitaplığı** olarak değiştirin. Projeyi başarıyla derlemek için bu adım gereklidir.

1. Proje derlemesinde **QuickDate'e sağ tıklar ve** **Çözüm Gezgini'i** **seçerek projeyi derleme.** Çıkış penceresinde başarılı bir derleme iletisi **görüyorsanız.**

## <a name="add-a-second-project"></a>İkinci proje ekleme

Çözümlerin birden fazla proje içermesi yaygındır ve bu projeler genellikle birbirine başvurur. Bir çözümde bulunan bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim testi projeleri veya web siteleri olabilir.

Şimdi çözüme bir birim testi projesi ekleriz. Bu kez projeye ek bir kod dosyası eklememiz gerekmay için bir proje şablonundan başlayacağız.

1. içinde Çözüm **'QuickSolution'** öğesinin sağ tıklama veya bağlam **menüsünden Çözüm Gezgini** Ekle'yi **Project.**  >  

::: moniker range="vs-2017"

2. Sol bölmede, **Visual Basic'yi** genişletin ve **Test kategorisini** seçin. Orta bölmede Birim Testi Project **(.NET Framework) proje** şablonunu seçin. Projeye **QuickTest adını ve** ardından Tamam'ı **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.vb adlı bir dosya* düzenleyicide açılır.

   ![Visual Studio Çözüm Gezgini projeyle çalışma](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range="vs-2019"

2. Yeni **proje ekle iletişim kutusunda,** en üstte yer alan arama kutusuna metin birimi **testini** girin ve **dil'in Visual Basic** **seçin.**

3. Birim Testi **Project (.NET Framework) proje** şablonunu ve ardından Sonraki'yi **seçin.**

4. Projeye **QuickTest adını ve** ardından Oluştur'a **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.vb adlı bir dosya* düzenleyicide açılır.

::: moniker-end

::: moniker range=">=vs-2022"

2. Yeni **proje ekle iletişim** kutusunda, en üstte yer alan arama kutusuna metin birimi **testini**  girin ve ardından Tüm diller **Visual Basic'yi** seçin.

3. Birim Testi **Project (.NET Framework) proje** şablonunu ve ardından Sonraki'yi **seçin.**

4. Projeye **QuickTest adını ve** ardından Oluştur'a **seçin.**

   dosyasına ikinci bir proje **Çözüm Gezgini** *unitTest1.vb adlı bir dosya* düzenleyicide açılır.

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu ekleme

**QuickDate** projesinde yöntemimizi test etmek için yeni birim testi projesini kullaneceğimiz için bu projeye bir başvuru eklememiz gerekiyor. Başvuru, iki proje *arasında bir derleme* bağımlılığı oluşturur, yani çözümü derlemek için **QuickDate,** QuickTest'den önce **inşa edilmiştir.**

::: moniker range="vs-2019"

1. QuickTest **projesinde** **Başvurular düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Başvuru Ekle'yi **seçin.**

   !['Başvuru Ekle' seçeneğinin seçili olduğu QuickTest projesinde Başvurular düğümünün bağlam menüsünü gösteren creenshot.](media/tutorial-projects-add-reference-vb.png)

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i genişletin **ve** Çözüm'i **seçin.** Orta bölmede **QuickDate'in** yanındaki onay kutusunu ve ardından Tamam **düğmesini** seçin.

   **QuickDate projesine bir** başvuru eklenir.

::: moniker-end

::: moniker range=">=vs-2022"

1. QuickTest **projesinde** **Başvurular düğümünü** seçin ve sağ tıklama veya bağlam menüsünden Başvuru Ekle'yi **seçin.**

   :::image type="content" source="media/vs-2022/tutorial-projects-add-reference-vb.png" alt-text="'Başvuru Ekle' seçeneğinin seçili olduğu QuickTest projesinde Başvurular düğümünün bağlam menüsünü gösteren ekran görüntüsü.":::

   Başvuru **Yöneticisi iletişim** kutusu açılır.

1. Sol bölmede Projeler'i genişletin **ve** Çözüm'i **seçin.** Orta bölmede **QuickDate'in** yanındaki onay kutusunu ve ardından Tamam **düğmesini** seçin.

   **QuickDate projesine bir** başvuru eklenir.

::: moniker-end

## <a name="add-test-code"></a>Test kodu ekleme

::: moniker range="vs-2019"

1. Şimdi test kodunu yeni kod dosyasına Visual Basic ekleyebilirsiniz. *UnitTest1.vb içeriğini* aşağıdaki kodla değiştirin.

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

   ![Imports deyimi ve Assembly öznitelik satırları eklendikten sonra Visual Basic düzenleyicisi penceresinde Calendar.vb kodunu gösteren ekran görüntüsü.](media/tutorial-projects-code-vb.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Şimdi test kodunu yeni kod dosyasına Visual Basic ekleyebilirsiniz. *UnitTest1.vb içeriğini* aşağıdaki kodla değiştirin.

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

   :::image type="content" source="media/vs-2022/tutorial-projects-code-vb.png" alt-text="Imports deyimi ve Derleme öznitelik satırları eklendikten sonra Visual Basic düzenleyicisi penceresinde Calendar.vb kodunu gösteren ekran görüntüsü.":::

::: moniker-end

## <a name="project-properties"></a>Proje özellikleri

::: moniker range="vs-2019"

*Calendar.vb dosyasında özniteliğini* içeren satır, QuickTest projesinin derleme adına <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> (dosya adı) başvurur.  Derleme adı her zaman proje adıyla aynı olmayacaktır. Projenin derleme adını bulmak için proje özelliklerini açın.

1. Bu **Çözüm Gezgini** **QuickTest projesini** seçin. Sağ tıklama veya bağlam menüsünde Özellikler'i seçin **veya** Alt Enter **tuşuna** + **basın.** (Ayrıca, Çözüm Gezgini **.)** Project **My** Çözüm Gezgini tıklar.

   *Projenin özellik* sayfaları Uygulama **sekmesinde** açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **QuickTest** projesinin derleme adının gerçekten de "QuickTest" olduğunu fark ediyorum. Derleme adını değiştirmek için bunu burada yapacak oluruz. Ardından test projesini derlemeniz sonucunda elde edilen ikili dosyanın adı,QuickTest.dll *olarak* değişir.

   ![QuickTest projesinin özellik sayfalarının Uygulama sekmesini gösteren ekran görüntüsü. Derleme adı alanı vurgulanmış ve değer 'QuickTest'tir.](../media/tutorial-projects-properties.png)

1. Projenin özellik sayfalarının Compile ve Ayarlar gibi **diğer** **sekmelerinden Ayarlar.** Bu sekmeler farklı proje türleri için farklıdır.

::: moniker-end

::: moniker range=">=vs-2022"

*Calendar.vb dosyasında* özniteliğini içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> satır, **QuickTest** projesinin derleme adına (dosya adı) başvurur. Derleme adı her zaman proje adıyla aynı olmayacaktır. Projenin derleme adını bulmak için proje özelliklerini açın.

1. Bu **Çözüm Gezgini** **QuickTest projesini** seçin. Sağ tıklama veya bağlam menüsünde Özellikler'i seçin **veya** Alt Enter **tuşuna** + **basın.** (Ayrıca, Çözüm Gezgini **.)** Project **My** Çözüm Gezgini tıklar.

   *Projenin özellik* sayfaları Uygulama **sekmesinde** açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **QuickTest** projesinin derleme adının gerçekten de "QuickTest" olduğunu fark ediyorum. Derleme adını değiştirmek için bunu burada yapacak oluruz. Ardından test projesini derlemeniz sonucunda elde edilen ikili dosyanın adı,QuickTest.dll *olarak* değişir.

   :::image type="content" source="media/vs-2022/tutorial-projects-properties.png" alt-text="QuickTest projesinin özellik sayfalarının Uygulama sekmesini gösteren ekran görüntüsü. Derleme adı alanı vurgulanmış ve değer 'QuickTest'tir.":::

1. Projenin özellik sayfalarının Compile ve Ayarlar gibi **diğer** **sekmelerinden Ayarlar.** Bu sekmeler farklı proje türleri için farklıdır.

::: moniker-end
## <a name="optional-run-the-test"></a>(İsteğe bağlı) Testi çalıştırma

::: moniker range="vs-2019"

Birim testinizin çalışa çalışa çalışa bir kontrol etmek için menü **çubuğundan Test**  >    >  **Çalıştırması Tüm Testleri'i** seçin. Test Gezgini adlı **bir pencere** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

![TestGetCurrentDate testinin Visual Studio Test Gezgini'nin ekran görüntüsü.](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğunda **Test** Gezgini'ni  >  **Windows** Test  >  **Gezgini'ni** seçerek açın.

::: moniker-end

::: moniker range=">=vs-2022"

Birim testinizin çalışa çalışa çalışa bir kontrol etmek için menü **çubuğundan Test**  >  **Çalıştırması Tüm Testleri'i** seçin. Test Gezgini adlı **bir pencere** açılır ve **TestGetCurrentDate testinin başarılı** olduğunu görüyor olun.

:::image type="content" source="media/vs-2022/tutorial-projects-test-explorer.png" alt-text="TestGetCurrentDate testinin Visual Studio Test Gezgini'nin ekran görüntüsü.":::

> [!TIP]
> **Test Gezgini otomatik** olarak açılmazsa, menü çubuğunda **Test** Gezgini'ni  >  **Windows** Test  >  **Gezgini'ni** seçerek açın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla araştırma yapmak Visual Studio öğreticilerinden birini kullanarak bir uygulama [Visual Basic düşünün.](index.yml)

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](../../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../../get-started/visual-studio-ide.md)
