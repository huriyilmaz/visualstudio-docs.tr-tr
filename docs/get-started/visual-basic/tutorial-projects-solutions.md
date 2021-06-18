---
title: Eğitim projeleri ve çözümleri Visual Basic
description: Visual Studio 'da Visual Basic geliştirici olarak bir çözüm ve proje oluşturmayı öğrenin.
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4f27973fcfb76d019cff31787b117f05f8266ad8
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308187"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Visual Basic kullanarak projeler ve çözümler hakkında bilgi edinin

Bu giriş makalesinde, Visual Studio 'da bir *çözüm* ve *Proje* oluşturmak için ne anlama geldiğini keşfedeceğiz. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Projenin özelliklerine ve içerdikleri bazı dosyalara bakacağız. Ayrıca bir projeden diğerine bir başvuru oluşturacağız.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Visual Studio Preview sürümünü henüz yüklemediyseniz, [Visual studio 2022 Önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Bir proje kavramını anlamak için eğitim alıştırması olarak sıfırdan bir çözüm ve proje oluşturacağız. Visual Studio 'nun genel kullanım ortamınızda, yeni bir proje oluşturduğunuzda Visual Studio 'nun sunduğu çeşitli proje *şablonlarından* bazılarını kullanırsınız.

> [!NOTE]
> Visual Studio 'da uygulama geliştirmek için çözümler ve projeler gerekli değildir. Ayrıca yalnızca kod içeren ve kodlamaya, oluşturmaya ve hata ayıklamaya başlayan bir klasörü açabilirsiniz. Örneğin, bir [GitHub](https://github.com/) deposu klonladığınızda, Visual Studio projeleri ve çözümleri içermeyebilir. Daha fazla bilgi için bkz. [Visual Studio 'da projeler veya çözümler olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. Visual Studio 'da bir çözüm açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Çözüm oluşturma

Boş bir çözüm oluşturarak araştırmayla başlayacağız. Visual Studio 'Yu öğrendikten sonra, belki de boş çözümler oluşturmayacağınızı fark edersiniz. Yeni bir proje oluşturduğunuzda, zaten açık bir çözüm yoksa, Visual Studio projeyi barındırmak için otomatik olarak bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda **Dosya** > **Yeni** > **Proje**' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

1. Sol bölmede **diğer proje türleri**' ni genişletin ve ardından **Visual Studio çözümleri**' ni seçin. Orta bölmede **boş çözüm** şablonunu seçin. Çözümünüzü **hızlı çözümünüz** olarak adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio 'da boş çözüm şablonu](../media/tutorial-projects-new-solution.png)

   **Başlangıç sayfası** kapanır ve Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 'de boş çözüm şablonu](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüm **hızlı çözümünü** adlandırın ve ardından **Oluştur**' u seçin.

   Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Genellikle **Çözüm Gezgini** , projelerinizdeki içeriğe gözatabilmeniz için çok büyük bir zaman kullanırsınız.

::: moniker-end

### <a name="add-a-project"></a>Proje ekleme

Şimdi çözüme ilk projemizi ekleyelim. Boş bir proje ile başlayacağız ve proje için ihtiyacımız olan öğeleri ekleyeceğiz.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **Yeni proje** Ekle ' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

1. Sol bölmede **Visual Basic** ' ı genişletin ve **Windows Masaüstü**' nu seçin. Ardından Ortadaki bölmede **boş proje (.NET Framework)** şablonunu seçin. Proje **Quickdate** olarak adlandırın, sonra **Tamam** düğmesini seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **Visual Basic** görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü* yüklemeniz gerekir. Visual Studio yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir iş yükünü yüklemenin kolay bir yolu, **Yeni Proje Ekle** iletişim kutusunun sol alt köşesindeki **Aç Visual Studio yükleyicisi** bağlantısını seçeklemektir. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio Yükleyicisi bağlantısını aç](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden  > **Yeni proje** Ekle ' yi seçin.

   **Yeni bir proje ekleyen** bir iletişim kutusu açılır.

1. Üstteki arama kutusuna **boş** metin girin ve ardından **dil** altında **Visual Basic** ' yi seçin.

1. **Boş proje (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Proje **Quickdate** olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje, **Çözüm Gezgini** çözümünün altında görünür. Şu anda *App.config* adlı tek bir dosya içerir.

   > [!NOTE]
   > **Boş proje (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü* yüklemeniz gerekir. Visual Studio yalnızca sizin oluşturduğunuz geliştirme türü için gereken bileşenleri yüklemek üzere iş yükü tabanlı yükleme kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını** belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi başlatıldıktan sonra, **.net masaüstü geliştirme** iş yükünü ve sonra **Değiştir** düğmesini seçin.
   >
   > ![Visual Studio 2019 ' de yükleyici bağlantısı](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye öğe ekleme

Boş bir projem var. Bir kod dosyası ekleyelim.

1. **Çözüm Gezgini** içindeki **quickdate** projesinin sağ tıklama veya kısayol menüsünden   >  **Yeni öğe** Ekle ' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. **Ortak öğeler**' i genişletin ve **kod** öğesini seçin. Orta bölmede **sınıf** öğesi şablonunu seçin. Sınıf **takvimini** adlandırın ve ardından **Ekle** düğmesini seçin.

   Projeye *Calendar. vb* adlı bir dosya eklenir. Uçtaki *. vb* , Visual Basic kod dosyalarına verilen dosya uzantısıdır. Dosya **Çözüm Gezgini** içinde görsel proje hiyerarşisinde ve içeriği düzenleyicide açılır.

1. *Calendar. vb* dosyasının içeriğini aşağıdaki kodla değiştirin:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar`Sınıfı, geçerli tarihi döndüren tek bir işlevi içerir `GetCurrentDate` .

1. **Çözüm Gezgini**' de **projem** ' a çift tıklayarak proje özelliklerini açın. **Uygulama** sekmesinde **uygulama türünü** **sınıf kitaplığı** olarak değiştirin. Projeyi başarıyla derlemek için bu adım gereklidir.

1. **Çözüm Gezgini** ' de **Hızlı Tarih** ' i sağ tıklayıp **Oluştur**' u seçerek projeyi derleyin. **Çıkış** penceresinde başarılı bir derleme iletisi görmeniz gerekir.

## <a name="add-a-second-project"></a>İkinci bir proje ekleyin

Birden fazla proje içermesi ve genellikle bu projelerin birbirlerine başvurması yaygın bir çözümdür. Bir çözümdeki bazı projeler sınıf kitaplıkları, bazı yürütülebilir uygulamalar ve bazıları birim testi projeleri veya Web siteleri olabilir.

Çözümünüze bir birim testi projesi ekleyelim. Bu kez bir proje şablonundan başlayacağız, böylece projeye ek bir kod dosyası eklememiz gerekmez.

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünden   >  **Yeni proje** Ekle ' yi seçin.

::: moniker range="Vs-2017"

2. Sol bölmede **Visual Basic** ' ı genişletin ve **Test** kategorisini seçin. Orta bölmede, **birim testi projesi (.NET Framework)** proje şablonunu seçin. Projeyi **hızlı test** olarak adlandırın ve ardından **Tamam**' ı seçin.

   **Çözüm Gezgini** ikinci bir proje eklenir ve düzenleyicide *UnitTest1. vb* adlı bir dosya açılır.

   ![İki projeyle Visual Studio Çözüm Gezgini](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni Proje Ekle** iletişim kutusunda, üstteki arama kutusuna metin **birimi testini** girin ve ardından **dil** altında **Visual Basic** ' yi seçin.

3. **Birim testi projesi (.NET Framework)** proje şablonunu seçin ve ardından **İleri**' yi seçin.

4. Projeyi **hızlı teste** adlandırın ve ardından **Oluştur**' u seçin.

   **Çözüm Gezgini** ikinci bir proje eklenir ve düzenleyicide *UnitTest1. vb* adlı bir dosya açılır.

::: moniker-end

## <a name="add-a-project-reference"></a>Proje başvurusu Ekle

**Hızlı Tarih** projesindeki yöntemizi test etmek için yeni birim testi projesini kullanacağız, bu nedenle bu projeye bir başvuru eklememiz gerekiyor. Bu, iki proje arasında bir *derleme bağımlılığı* oluşturur. Bu, çözümü oluşturduğunuzda hızlı **Test** öncesinde hızlı bir **Tarih** oluşturulur.

1. **Hızlı test** projesinde **Başvurular** düğümünü seçin ve sağ tıklama ya da bağlam menüsünden **Başvuru Ekle**' yi seçin.

   ![Başvuru menüsü Ekle](media/tutorial-projects-add-reference-vb.png)

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede, **Projeler** ' i genişletin ve **çözüm**' ü seçin. Orta bölmede, **Quickdate** seçeneğinin yanındaki onay kutusunu seçin ve ardından **Tamam** düğmesini seçin.

   **Quickdate** projesine bir başvuru eklenir.

## <a name="add-test-code"></a>Test kodu ekle

1. Şimdi Visual Basic kod dosyasına test kodu ekleyeceğiz. *UnitTest1. vb* içeriğini aşağıdaki kodla değiştirin.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Bazı kodlar altında kırmızı renkli bir çizgi görürsünüz. Test projesini **Quickdate** projesine bir [Friend derlemesi](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) yaparak bu hatayı düzeltireceğiz.

1. **Quickdate** projesine geri döndüğünüzde, zaten açık değilse *Takvim. vb* dosyasını açın ve Test projesindeki hatayı çözümlemek için aşağıdaki [Imports ifadesini](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini ekleyin.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Kod dosyası şuna benzemelidir:

   ![Visual Basic kodu](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Proje özellikleri

Bu özniteliği içeren *Calendar. vb* dosyasındaki satır, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> **hızlı test** projesinin derleme adına (dosya adı) başvurur. Derleme adı, proje adı ile her zaman aynı olamaz. Projenin derleme adını bulmak için, proje özelliklerini açın.

1. **Çözüm Gezgini**' de **hızlı test** projesini seçin. Sağ tıklama veya bağlam menüsünde **Özellikler**' i seçin veya yalnızca **alt** + **ENTER** tuşuna basın. (Ayrıca **Çözüm Gezgini**, **projem** ' de çift tıklayabilirsiniz.)

   Projenin *Özellik sayfaları* **uygulama** sekmesinde açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. **Hızlı test** projesinin derleme adının gerçekten "QuickTest" olduğuna dikkat edin. Bunu değiştirmek isterseniz bunu yapmanız gerekir. Ardından, test projesi oluşturduğunuzda, sonuçta elde edilen ikili dosyanın adı *QuickTest.dll* ' den seçtiğiniz şeyle değişir.

   ![Proje özellikleri](../media/tutorial-projects-properties.png)

1. Projenin özellik sayfalarındaki **derleme** ve **Ayarlar** gibi diğer sekmelerin bazılarını keşfedebilir. Bu sekmeler farklı proje türleri için farklıdır.

## <a name="optional-run-the-test"></a>Seçim Testi çalıştırın

Birim testinizin çalıştığını denetlemek isterseniz,   >    >  menü çubuğundan **tüm testleri** Çalıştır test ' i seçin. **Test Gezgini** adlı bir pencere açılır ve **TestGetCurrentDate** testin başarılı olduğunu görmeniz gerekir.

![Başarılı testi gösteren Visual Studio 'da metin Gezgini](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> **Test Gezgini** otomatik olarak açılmazsa,   >    >  menü çubuğundan Windows **Test Gezgini** 'ni test et ' i seçerek açın.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 'Yu daha fazla incelemek istiyorsanız [Visual Basic öğreticilerden](index.yml)birini izleyerek bir uygulama oluşturmayı düşünün.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve çözüm oluşturma](../../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE 'ye Genel Bakış](../../get-started/visual-studio-ide.md)
