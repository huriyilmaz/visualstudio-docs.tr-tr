---
title: Eğitim projeleri ve çözümleri Visual Basic
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48b3f2c9aae099e3ae5f2cf2d8c438fb0f9062a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590221"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Visual Basic kullanarak projeler ve çözümler hakkında bilgi edinin

Giriş niteliğindeki bu makalede şunları oluşturma ne demek keşfedeceğiz bir *çözüm* ve *proje* Visual Studio'da. Bir çözüm, bir veya daha fazla ilgili kod projesini (örneğin, bir sınıf kitaplığı projesi ve karşılık gelen bir test projesi) düzenlemek için kullanılan bir kapsayıcıdır. Bir proje özelliklerini ve bazı içerebileceği dosyalara göz atacağız. Ayrıca bir başvuru bir projeden diğerine oluşturacağız.

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

::: moniker-end

Bir proje kavramı anlamak için eğitim bir alıştırma olarak size bir çözüm ve proje sıfırdan oluşturmak. Visual Studio içinde genel kullanımı, büyük olasılıkla çeşitli proje bazılarını kullanacaksınız *şablonları* yeni bir proje oluşturduğunuzda, Visual Studio sunar.

> [!NOTE]
> Çözümler ve projeler, Visual Studio'da uygulama geliştirme gerekmez. Ayrıca, kod ve kodlama, derleme ve hata ayıklama başlangıç içeren bir klasör açabilirsiniz. Örneğin, kopyalama, bir [GitHub](https://github.com/) depo, Visual Studio projeleri ve çözümleri içermeyebilir. Daha fazla bilgi için [kod Visual Studio'da projeler veya çözümler olmadan geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Çözümler ve projeler

Adına rağmen çözüm bir "yanıt" değildir. Bir çözüm, yalnızca bir veya daha fazla ilgili projeyi düzenlemek için Visual Studio tarafından kullanılan bir kapsayıcıdır. Visual Studio 'da bir çözüm açtığınızda, çözüm içerdiği tüm projeleri otomatik olarak yükler.

### <a name="create-a-solution"></a>Bir çözüm oluşturun

Bizim araştırması boş bir çözüm oluşturarak başlayacağız. Visual Studio bilmek aldıktan sonra büyük olasılıkla çok sık boş çözüm oluşturduğunuzu bulamaz. Yeni bir proje oluşturduğunuzda, Visual Studio otomatik olarak değil bir çözüm zaten varsa açık proje barındırmak için bir çözüm oluşturur.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

   **Yeni proje** iletişim kutusu açılır.

1. Sol bölmede genişletin **diğer proje türleri**, ardından **Visual Studio çözümleri**. Orta bölmede seçin **boş çözüm** şablonu. Çözümünüzü **hızlı çözümünüz**olarak adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio'da boş çözüm şablonu](../media/tutorial-projects-new-solution.png)

   **Başlangıç sayfası** kapatır ve çözüm görünür **Çözüm Gezgini** Visual Studio penceresinin sağ tarafındaki. Büyük olasılıkla kullanacağınız **Çözüm Gezgini** genellikle projelerinizi içeriğini gidin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasında, arama kutusuna **boş çözüm** girin, **boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 2019 'de boş çözüm şablonu](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Çözüm **hızlı çözümünü**adlandırın ve ardından **Oluştur**' u seçin.

   Visual Studio penceresinin sağ tarafında **Çözüm Gezgini** bir çözüm görüntülenir. Büyük olasılıkla kullanacağınız **Çözüm Gezgini** genellikle projelerinizi içeriğini gidin.

::: moniker-end

### <a name="add-a-project"></a>Bir proje ekleyin

Artık ilk Projemizin çözüme ekleyelim. Biz ile boş bir proje başlatın ve ihtiyacımız öğe projeye ekleyin.

::: moniker range="vs-2017"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni Proje Ekle** iletişim kutusu açılır.

1. Sol bölmede **Visual Basic** ' ı genişletin ve **Windows Masaüstü**' nu seçin. Orta bölmede seçin **boş proje (.NET Framework)** şablonu. Projeyi adlandırın **QuickDate**, ardından **Tamam** düğmesi.

   QuickDate adlı bir proje çözümde altında görünür **Çözüm Gezgini**. Şu anda tek dosya adlı içerdiği *App.config*.

   > [!NOTE]
   > İletişim kutusunun sol bölmesinde **Visual Basic** görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü*yüklemeniz gerekir. Visual Studio iş yükü tabanlı yükleme yalnızca bunu geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için kullanır. Yeni bir iş yükünü yüklemek için kolay bir yolu seçmektir **açık Visual Studio yükleyicisi** sol alt köşesine bağlantıyı **Yeni Proje Ekle** iletişim kutusu. Visual Studio Yükleyicisi'ni başlattıktan sonra seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir** düğmesi.
   >
   > ![Visual Studio yükleyicisi bağlantıyı aç](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** **' hızlı çözüm ' çözümünün** sağ tıklama veya bağlam menüsünde, > **Yeni proje** **Ekle** ' yi seçin.

   **Yeni bir proje ekleyen**bir iletişim kutusu açılır.

1. Üstteki arama kutusuna **boş** metin girin ve ardından **dil**altında **Visual Basic** ' yi seçin.

1. **Boş proje (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

1. Proje **Quickdate**olarak adlandırın, sonra **Oluştur**' u seçin.

   QuickDate adlı bir proje çözümde altında görünür **Çözüm Gezgini**. Şu anda tek dosya adlı içerdiği *App.config*.

   > [!NOTE]
   > **Boş proje (.NET Framework)** şablonu görmüyorsanız, **.net masaüstü geliştirme** Visual Studio *iş yükünü*yüklemeniz gerekir. Visual Studio iş yükü tabanlı yükleme yalnızca bunu geliştirme türü için gereksinim duyduğunuz bileşenleri yüklemek için kullanır. Yeni bir proje oluştururken yeni bir iş yükü yüklemenin kolay bir yolu, **ne aradığınızı bulmadığını**belirten metin altında **daha fazla araç ve özellik yüklesin** bağlantısını seçiyoruz. Visual Studio Yükleyicisi'ni başlattıktan sonra seçin **.NET masaüstü geliştirme** iş yükü ve ardından **Değiştir** düğmesi.
   >
   > ![Visual Studio 2019 ' de yükleyici bağlantısı](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Projeye bir öğe ekleyin

Boş bir proje sahibiz. Bir kod dosyası ekleyelim.

1. Sağ tıklayın veya bağlam menüsünde **QuickDate** projesi **Çözüm Gezgini**, seçin **Ekle** > **yeni öğe** .

   **Yeni Öğe Ekle** iletişim kutusu açılır.

1. **Ortak öğeler**' i genişletin ve **kod**öğesini seçin. Orta bölmede seçin **sınıfı** öğe şablonu. Sınıf adı **Takvim**ve ardından **Ekle** düğmesi.

   Projeye *Calendar. vb* adlı bir dosya eklenir. Uçtaki *. vb* , Visual Basic kod dosyalarına verilen dosya uzantısıdır. Dosya **Çözüm Gezgini**içinde görsel proje hiyerarşisinde ve içeriği düzenleyicide açılır.

1. *Calendar. vb* dosyasının içeriğini aşağıdaki kodla değiştirin:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar` sınıfı, geçerli tarihi döndüren `GetCurrentDate`tek bir işlev içerir.

1. **Çözüm Gezgini**' de **projem** ' a çift tıklayarak proje özelliklerini açın. **Uygulama** sekmesinde **uygulama türünü** **sınıf kitaplığı**olarak değiştirin. Projeyi başarıyla derlemek için bu adım gereklidir.

1. **Çözüm Gezgini** ' de **Hızlı Tarih** ' i sağ tıklayıp **Oluştur**' u seçerek projeyi derleyin. **Çıkış** penceresinde başarılı bir derleme iletisi görmeniz gerekir.

## <a name="add-a-second-project"></a>İkinci bir proje ekleyin

Birden fazla proje içermesi ve genellikle bu projelerin birbirlerine başvurması yaygın bir çözümdür. Çözümdeki bazı projeler sınıf kitaplıkları, yürütülebilir bazı uygulamalar olabilir ve bazı Birim testi projelerini veya Web sitesi olabilir.

Birim testi projesi, çözüm ekleyelim. Biz bir ek kod dosyası projeye eklemek zorunda kalmamak için bu kez proje şablonundan başlayacağız.

1. Sağ tıklayın veya bağlam menüsünde **çözüm 'QuickSolution'** içinde **Çözüm Gezgini**, seçin **Ekle** > **YeniProje**.

::: moniker range="Vs-2017"

2. Sol bölmede genişletin **Visual Basic** ve **Test** kategorisi. Orta bölmede seçin **birim testi projesi (.NET Framework)** proje şablonu. Projeyi **hızlı test**olarak adlandırın ve ardından **Tamam**' ı seçin.

   İkinci bir proje eklenir **Çözüm Gezgini**ve adlı bir dosya *UnitTest1.vb* düzenleyicisinde açılır.

   ![İki proje ile Visual Studio Çözüm Gezgini](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni Proje Ekle** iletişim kutusunda, üstteki arama kutusuna metin **birimi testini** girin ve ardından **dil**altında **Visual Basic** ' yi seçin.

3. **Birim testi projesi (.NET Framework)** proje şablonunu seçin ve ardından **İleri**' yi seçin.

4. Projeyi **hızlı teste**adlandırın ve ardından **Oluştur**' u seçin.

   İkinci bir proje eklenir **Çözüm Gezgini**ve adlı bir dosya *UnitTest1.vb* düzenleyicisinde açılır.

::: moniker-end

## <a name="add-a-project-reference"></a>Bir proje başvurusu Ekle

Yeni birim test projesi bizim yöntemi test etmek için kullanılacak yapacağız **QuickDate** proje Biz bu projeye bir başvuru eklemeniz gerekir. Bu oluşturur bir *derleme bağımlılığı* çözümü oluşturduğunuzda iki projeler arasında güncelleştirmeyeceği **QuickDate** önce oluşturulan **QuickTest**.

1. Seçin **başvuruları** düğümünde **QuickTest** proje ve seçin sağ tıklayın veya bağlam menüsünden **Başvuru Ekle**.

   ![Başvuru menü ekleme](media/tutorial-projects-add-reference-vb.png)

   **Başvuru Yöneticisi** iletişim kutusu açılır.

1. Sol bölmede genişletin **projeleri** ve **çözüm**. Orta bölmede yanındaki onay kutusunu seçin **QuickDate**ve ardından **Tamam** düğmesi.

   Bir başvuru **QuickDate** projesi eklenir.

## <a name="add-test-code"></a>Test kodu ekleyin

1. Visual Basic kod dosyasına test kodu artık ekleyeceğiz. Öğesinin içeriğini değiştirin *UnitTest1.vb* aşağıdaki kod ile.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Bazı kodlar altında kırmızı renkli bir çizgi görürsünüz. Bu hatayı test projesini yaparak gidereceğiz bir [arkadaş derleme](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) için **QuickDate** proje.

1. **Quickdate** projesine geri döndüğünüzde, zaten açık değilse *Takvim. vb* dosyasını açın ve Test projesindeki hatayı çözümlemek için aşağıdaki [Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini ekleyin.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Kod dosyası şu şekilde görünmelidir:

   ![Visual Basic kodu](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Proje Özellikleri

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini içeren *Calendar. vb* dosyasındaki çizgi, **QuickTest** projesinin derleme adına (dosya adı) başvurur. Proje adı ile aynı derleme adı her zaman olmayabilir. Proje derleme adını bulmak için proje özelliklerini açın.

1. İçinde **Çözüm Gezgini**seçin **QuickTest** proje. Sağ tıklayın veya bağlam menüsünü seçin **özellikleri**, veya tuşuna basarak **Alt**+**Enter**. (Ayrıca **Çözüm Gezgini**, **projem** ' de çift tıklayabilirsiniz.)

   Projenin *Özellik sayfaları* **uygulama** sekmesinde açılır. Özellik sayfaları, proje için çeşitli ayarlar içerir. Dikkat derleme adını **QuickTest** projedir gerçekten "QuickTest". Bunu değiştirmek istiyorsanız, burada yaptığınız budur. Test projesi oluşturduğunuzda, daha sonra elde edilen ikili dosyasının adı gelen değiştirirsiniz *QuickTest.dll* , seçtiğiniz için.

   ![Proje Özellikleri](../media/tutorial-projects-properties.png)

1. Projenin özellik sayfalarındaki, diğer sekmelerdeki gibi keşfedebilirsiniz **derleme** ve **ayarları**. Bu sekme, farklı proje türleri için farklıdır.

## <a name="optional-run-the-test"></a>Seçim Testi çalıştırın

Birim testinizi çalıştığını denetlemek istiyorsanız seçin **Test** > **çalıştırma** > **tüm testleri** menü çubuğundan. Bir pencere olarak adlandırılan **Test Gezgini** açar, görmelisiniz, **TestGetCurrentDate** test geçer.

![Başarılı testi gösteren Visual Studio 'da metin Gezgini](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Varsa **Test Gezgini** değil, otomatik olarak Aç seçerek açın **Test** > **Windows** > **TestGezgini** menü çubuğundan.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 'Yu daha fazla incelemek istiyorsanız [Visual Basic öğreticilerden](index.yml)birini izleyerek bir uygulama oluşturmayı düşünün.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeler ve çözümler oluşturma](../../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../../ide/managing-project-and-solution-properties.md)
- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Visual Studio’da projeler veya çözümler olmadan kod geliştirme](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE'ye genel bakış](../../get-started/visual-studio-ide.md)
