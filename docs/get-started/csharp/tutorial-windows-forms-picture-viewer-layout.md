---
title: "Öğretici: Forms uygulamasında 'resim görüntüleyici' Windows oluşturma"
description: IDE'de resim görüntüleyici uygulaması için C# veya VB WinForms Visual Studio öğrenin. Uygulama düzeninizi yapılandıracak ve çalıştırabilirsiniz.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/05/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: 3f713c01208c0dec3909aa219a190e063c1d00d1
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887484"
---
# <a name="tutorial-create-a-picture-viewer-windows-forms-app-in-visual-studio"></a>Öğretici: Visual Studio'de Forms Windows resim görüntüleyicisi oluşturma

Bu üç öğretici serisinde, bir resim yük Windows görüntüleyen bir Windows Forms uygulaması oluşturabilirsiniz.
Visual Studio Tümleşik Tasarım Ortamı (IDE), uygulamayı oluşturmak için ihtiyacınız olan araçları sağlar.
Daha fazla bilgi edinmek için bkz[. IDE'Visual Studio hoş geldiniz](../visual-studio-ide.md).

Bu ilk öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Windows Forms Visual Studio bir Windows oluşturma
> - Düzen öğesi ekleme
> - Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi Visual Studio için bir adıma ihtiyacınız var.
Ücretsiz sürüm [Visual Studio indirmeler](https://visualstudio.microsoft.com/vs/) sayfasını ziyaret edin.

## <a name="create-your-windows-forms-project"></a>Windows Forms projenizi oluşturma

Resim görüntüleyici  oluşturmanın ilk adımı bir Windows Forms Uygulaması projesi oluşturmaktır.

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni **Dosya'Project** >  > **.**

     ![Yeni proje iletişim kutusunu gösteren ekran görüntüsü.](../media/new-project-dialog-callouts.png)

1. Yeni Uygulama iletişim kutusunun sol **Project** **Visual C#** veya **Visual Basic'ı seçin** ve Windows **Masaüstü'Windows seçin**.

1. Proje şablonları listesinde form formlarını Windows **(.NET Framework) seçin**. Yeni forma *PictureViewer adını ve* ardından Tamam'ı **seçin**.

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız **. .NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.
   >
   > ![Uygulamanın içinde nokta NET masaüstü geliştirme iş yükünü Visual Studio Yükleyicisi.](../media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > Daha fazla bilgi için Yükleme [Visual Studio](../../install/install-visual-studio.md) bakın.

::: moniker-end

::: moniker range="vs-2019"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın**.

   ![Yeni proje oluştur seçeneğini başlangıç penceresinde gösteren Visual Studio görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/create-new-project-dark-theme-2019.png)

1. Yeni proje **oluştur penceresinde Yeni** Formlar için *Windows arama.* Ardından, **uygulama** türü **listesinden Project'yi** seçin.

1. C# **Windows formlar için .NET Framework Forms Uygulaması (Visual Basic)** şablonunu seçin ve ardından Sonraki'yi **seçin**.

   ![Windows Forms'ların girildi olduğu yeni proje oluştur iletişim kutusunu ve Windows Forms Uygulaması'nın seçeneklerini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz**. Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > ![Yeni proje oluştur iletişim kutusunda, Arayıcınız ne arıyorsanız bu değil iletisiyle Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/install-more-tools.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin**.
   >
   > ![Uygulamanın .NET Core iş yükünü gösteren Visual Studio Yükleyicisi.](../media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > **Dosyanın içinde** Değiştir'Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** *PictureViewer* adını ve ardından Oluştur'u **seçin**.

::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın**.

   ![Yeni proje oluştur seçeneğini başlangıç penceresinde gösteren Visual Studio görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/create-new-project-dark-theme.png)

1. Yeni proje **oluştur penceresinde Yeni** Formlar için *Windows arama.* Ardından, **uygulama** türü **listesinden Project'yi** seçin.

1. C# **Windows formlar için .NET Framework Forms Uygulaması (Visual Basic)** şablonunu seçin ve ardından Sonraki'yi **seçin**.

   ![Windows Forms'ların girildi olduğu yeni proje oluştur iletişim kutusunu ve Windows Forms Uygulaması'nın seçeneklerini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz**. Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > ![Yeni proje oluştur iletişim kutusunda, Arayıcınız ne arıyorsanız bu değil iletisiyle Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/install-more-tools.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin**.
   >
   > ![Uygulamanın .NET Core iş yükünü gösteren Visual Studio Yükleyicisi.](../media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > **Dosyanın içinde** Değiştir'Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** *PictureViewer* adını ve ardından Oluştur'u **seçin**.

::: moniker-end

Visual Studio için bir çözüm oluşturur.
Çözüm, uygulamanıza gereken tüm projeler ve dosyalar için bir kapsayıcıdır.

Bu noktada, Visual Studio Form Tasarımcısı'nda boş **Windows görüntüler**.

## <a name="add-a-layout-element"></a>Düzen öğesi ekleme

Resim görüntüleme uygulamanıza bir resim kutusu, bir onay kutusu ve bir sonraki öğreticide ek olarak ekley istediğiniz dört [düğme bulunur](tutorial-windows-forms-picture-viewer-controls.md).
Düzen öğesi, formda konumlarını kontrol eder.
Bu bölümde form başlığını değiştirme, formu yeniden boyutlandırma ve düzen öğesi ekleme ile ilgili nasıl bir değişiklik olduğu gösterir.

1. Projenize Form Tasarımcısı'Windows seçin.
   Sekme C# için **Form1.cs [Design]** veya **form1.vb [Design]** Visual Basic.

1. **Form1'de herhangi bir yeri seçin**.

1. Özellikler **penceresi** artık formun özelliklerini görüntüler.
   Özellikler **penceresi** genellikle dosyanın sağ alt Visual Studio.
   Bu bölüm ön plan ve arka plan rengi, formun en üstünde görünen başlık metni ve formun boyutu gibi çeşitli özellikleri kontrol eder.

   Özellikler'i görmüyorsanız **GörünümÖz** **özellikler** >  **Penceresi'ne tıklayın**.

1. Özellikler **penceresinde Text** **özelliğini** bulun.
   Listenin nasıl sıralanmış olduğunu bağlı olarak, aşağı kaydırmak için ihtiyacınız olabilir.
   Resim Görüntüleyicisi *değerini girin* ve Enter tarak **seçin**.

   Formunuz artık başlık çubuğunda **Resim Görüntüleyici** metnine sahip.

   > [!NOTE]
   > Özellikleri kategoriye veya alfabetik olarak görüntüebilirsiniz.
   > Geri ve ileri geçiş **yapmak** için Özellikler penceresindeki düğmeleri kullanın.

1. Formu tekrar seçin. Formun sağ alt sürükleme tutamacı seçin.
   Tutamaç, formun sağ alt köşesindeki küçük bir beyaz karedir.

   ![Sağ altta Tutamacı sürükleyin'in yer alan Formlar penceresini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/windows-form-drag-handle.png)

   Formu daha geniş ve biraz daha uzun olacak şekilde yeniden boyutlandırmak için tutamacı sürükleyin.
   Özellikler penceresine **bakarsanız** **Size özelliği** değişmiştir.
   Size özelliğini değiştirerek formun boyutunu da **değiştirebilirsiniz** .

1. IDE'nin sol Visual Studio Araç Kutusu **sekmesini** seçin. Bu seçeneği görmüyorsanız  menü çubuğundan **veya** >**CtrlAltX** tuşlarına basarak Araç **Kutusunu Görüntüle'yi**++ seçin.

1. Kapsayıcılar'ın yanındaki küçük üçgen **simgesini** seçerek grubu açın.

   ![Araç Kutusu sekmesindeki Kapsayıcılar grubunu gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/toolbox-container-table-layout-panel.png)

1. Araç Kutusunda **TableLayoutPanel'e** **çift tıklayın**.
   Bir denetimi araç kutusundan forma da sürükleyebilirsiniz.
   TableLayoutPanel denetimi form içinde görünür.

   ![TableLayoutPanel denetimi eklenmiş formun ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/table-layout-format-added.png)

   > [!NOTE]
   > TableLayoutPanel'inizi ekledikten sonra form içinde **TableLayoutPanel Görevleri** başlığıyla bir pencere görünürse formu kapatmak için formun herhangi bir yerine tıklayın.

1. **TableLayoutPanel'i seçin**.
   Özellikler penceresine bakarak hangi denetimin seç olduğunu **doğruabilirsiniz** .

   ![TableLayoutPanel Özellikler penceresi gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/table-layout-panel-properties.png)

1. TableLayoutPanel seçili durumdayken Hiçbiri değerine sahip **Dock** özelliğini **bulun**.
   Açılan oku ve ardından açılan **menenin** ortasındaki büyük düğme olan Fill'i seçin.

   ![Dolgu seçiliyken Özellikler penceresi ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/dock-property.png)

   *Yerleştirme,* bir pencerenin başka bir pencereye veya alana nasıl ekli olduğunu ifade eder.

   TableLayoutPanel artık formun tamamını doldurur.
   Formu yeniden boyutlandırırsanız TableLayoutPanel yerleştirmede kalır ve sığacak şekilde yeniden boyutlandırılır.

1. Formda TableLayoutPanel'i seçin.
   Sağ üst köşede küçük bir siyah üçgen düğmesi vardır.

   Denetimin görev listesini görüntülemek için üçgeni seçin.

   ![TableLayoutPanel görevlerini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/table-layout-panel-tasks.png)

1. Sütun **ve Satır Stilleri iletişim kutusunu** görüntülemek için **Satırları ve Sütunları Düzenle'yi** seçin.

1. **Sütun1'i** seçin ve boyutunu yüzde 15 olarak ayarlayın. Yüzde düğmesinin **seçili** olduğundan emin olun.

1. **Sütun2'yi** seçin ve yüzde 85 olarak ayarlayın.

   ![TableLayoutPanel sütun ve satır stillerini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/layout-column-row-styles.png)

1. Sütun **ve** Satır Stilleri iletişim kutusunun **en üstünde yer alan Göster'den** Satırlar'ı **seçin**. **Satır1'i** yüzde 90 ve **Satır2'i yüzde** 10 olarak ayarlayın. Değişikliklerinizi kaydetmek için **Tamam**’ı seçin. 

   TableLayoutPanel artık büyük bir üst satıra, küçük bir alt satıra, sol küçük bir sütuna ve büyük bir sağ sütuna sahiptir.

   ![Yeniden boyutlandırıldı TableLayoutPanel formunu gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/form-layout.png)

Düzeniniz tamamlandı.

   > [!NOTE]
   > Uygulamayı çalıştırmadan önce, Tüm araç çubuğunu kaydet düğmesini **seçerek uygulamanızı** kaydedin.
   > Alternatif olarak, uygulamanızı kaydetmek için menü **çubuğundan DosyaSave** >  **All** seçeneğini belirleyin veya **CtrlShiftS tuşlarına**++ **basın**.
   > Erken ve sık tasarruf etmek en iyi yöntemdir.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Windows Forms Uygulaması projesi  oluşturursanız, çalışan bir program oluşturursanız.
Bu aşamada Resim Görüntüleyicisi uygulamanız pek bir şey yapmaz.
Şimdilik başlık çubuğunda Resim Görüntüleyicisi'ni **gösteren boş** bir pencere görüntülenir.

Uygulamayı çalıştırmak için aşağıdaki adımları izleyin.

1. Aşağıdaki yöntemlerden birini kullanın:

   - **F5 anahtarını** seçin.
   - Menü çubuğunda Hata Ayıkla Hata **Ayıklamayı** **Başlat'ı** >  seçin.
   - Araç çubuğunda Başlat **düğmesini** seçin.

   Visual Studio çalıştırabilirsiniz. Resim Görüntüleyici başlığına **sahip bir pencere** görüntülenir.

   ![Windows Forms uygulamasını gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/run-empty-windows-forms-app.png)

   IDE araç Visual Studio bakın.
   Bir uygulamayı çalıştırarak araç çubuğunda daha fazla düğme görünür.
   Bu düğmeler, uygulamayı durdurma ve başlatma gibi şeyler yapma ve hataları takip etmeye yardımcı olur.

   ![Uygulamayı durdurabilirsiniz Hata ayıklama araç çubuğunu gösteren ekran görüntüsü.](../media/tutorial-windows-forms-picture-viewer-layout/debug-toolbar.png)

1. Uygulamanızı durdurmak için aşağıdaki yöntemlerden birini kullanın:

   - Araç çubuğunda Hata Ayıklamayı **Durdur düğmesini** seçin.
   - Menü çubuğunda Hata **AyıklaStop Hata** >  **Ayıklama'ya tıklayın**.
   - Klavyeden **ShiftF5**+ girin.
   - Resim Görüntüleyicisi penceresinin üst **köşesindeki X** **seçeneğini** seçin.

   Uygulamalarınızı IDE'nin içinden Visual Studio hata ayıklama olarak adlandırılan bir işlemdir.
   Hataları bulmak ve düzeltmek için uygulamanızı çalıştırın.
   Diğer programları çalıştırmak ve hata ayıklamak için aynı yordamı izleyin.
   Hata ayıklama hakkında daha fazla bilgi edinmek için bkz [. Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Resim Görüntüleyicisi programınıza denetimler ekleme hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici 2. Bölüm: Resim Görüntüleyicinize denetimler ekleme](tutorial-windows-forms-picture-viewer-controls.md)
