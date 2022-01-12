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
ms.openlocfilehash: a101e8988f1fc59e320ccfa1c1872101b48bb81e
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135808626"
---
# <a name="tutorial-create-a-picture-viewer-windows-forms-app-in-visual-studio"></a>Öğretici: Windows Forms uygulamasında resim görüntüleyici Visual Studio

Bu üç öğretici serisinde, bir resim yük Windows bir Windows Forms uygulaması oluşturacak ve görüntüleyebilirsiniz.
Visual Studio Tümleşik Tasarım Ortamı (IDE), uygulamayı oluşturmak için ihtiyacınız olan araçları sağlar.
Daha fazla bilgi için [bkz. IDE'Visual Studio hoş geldiniz.](../get-started/visual-studio-ide.md)

Bu ilk öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Windows Forms Visual Studio bir Windows oluşturma
> - Düzen öğesi ekleme
> - Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi Visual Studio için bir adıma ihtiyacınız var.
Ücretsiz sürüm [Visual Studio indirmeler](https://visualstudio.microsoft.com/vs/) sayfasını ziyaret edin.

## <a name="create-your-windows-forms-project"></a>Windows Forms projenizi oluşturma

Resim görüntüleyici oluşturmanın ilk adımı bir Windows Forms Uygulaması projesi oluşturmaktır.

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni'yi **seçin** > **ve** > **Project.**

     ![Yeni proje iletişim kutusunu gösteren ekran görüntüsü.](../ide/media/newprojectdialogcallouts.png)

1. Yeni Uygulama iletişim kutusunun sol **Project** **Visual C#** veya Visual Basic seçin ve ardından Masaüstü'Windows **seçin.**

1. Proje şablonları listesinde form formlarını **Windows Forms Uygulaması (.NET Framework) seçin.** Yeni forma *PictureViewer adını ve* ardından Tamam'ı **seçin.**

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız. **.NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.
   >
   > ![Uygulamanın içinde nokta NET masaüstü geliştirme iş yükünü Visual Studio Yükleyicisi.](../ide/media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > Daha fazla bilgi için Yükleme [Visual Studio](../install/install-visual-studio.md) bakın.

::: moniker-end

::: moniker range="vs-2019"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   ![Başlangıç penceresinde Yeni proje oluştur seçeneğini gösteren Visual Studio görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/create-new-project-dark-theme-2019.png)

1. Yeni proje **oluştur penceresinde Formlar** için *arama Windows.* Ardından, **uygulama** türü **listesinden Project'yi** seçin.

1. C# Windows formlar için .NET Framework Forms Uygulaması **(.NET Framework)** şablonunu Visual Basic ve ardından Sonraki'yi **seçin.**

   ![Windows Forms'a girilen yeni proje oluştur iletişim kutusunu ve Windows Forms Uygulaması için seçenekleri gösteren ekran görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > ![Yeni proje oluştur iletişim kutusunda, Arayıcınız ne arıyorsanız bu değil iletisiyle Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/install-more-tools.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin.**
   >
   > ![Uygulamanın .NET Core iş yükünü gösteren Visual Studio Yükleyicisi.](../ide/media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > **Dosyanın** içinde Değiştir'Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** *PictureViewer* adını ve ardından Oluştur'u **seçin.**

::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   ![Başlangıç penceresinde Yeni proje oluştur seçeneğini gösteren Visual Studio görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/create-new-project-dark-theme.png)

1. Yeni proje **oluştur penceresinde Formlar** için *arama Windows.* Ardından, **uygulama** türü **listesinden Project'yi** seçin.

1. C# Windows formlar için .NET Framework Forms Uygulaması **(.NET Framework)** şablonunu Visual Basic ve ardından Sonraki'yi **seçin.**

   ![Windows Forms'a girilen yeni proje oluştur iletişim kutusunu ve Windows Forms Uygulaması için seçenekleri gösteren ekran görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > ![Yeni proje oluştur iletişim kutusunda, Arayıcınız ne arıyorsanız bu değil iletisiyle Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](./media/tutorial-windows-forms-picture-viewer-layout/install-more-tools.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin.**
   >
   > ![Uygulamanın .NET Core iş yükünü gösteren Visual Studio Yükleyicisi.](../ide/media/tutorial-windows-forms-picture-viewer-layout/install-dot-net-desktop-env.png)
   >
   > **Dosyanın** içinde Değiştir'Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** *PictureViewer* adını ve ardından Oluştur'u **seçin.**

::: moniker-end

Visual Studio için bir çözüm oluşturur.
Çözüm, uygulamanıza gereken tüm projeler ve dosyalar için bir kapsayıcıdır.

Bu noktada, Visual Studio Form Tasarımcısı'nda **boş Windows görüntüler.**

## <a name="add-a-layout-element"></a>Düzen öğesi ekleme

Resim görüntüleme uygulamanıza resim kutusu, onay kutusu ve dört düğme ekleyen bir sonraki öğreticide [ekleyebilirsiniz.](tutorial-windows-forms-picture-viewer-controls.md)
Düzen öğesi, formda konumlarını kontrol eder.
Bu bölümde form başlığını değiştirme, formu yeniden boyutlandırma ve düzen öğesi ekleme ile ilgili nasıl bir değişiklik olduğu gösterir.

1. Projenize Form Tasarımcısı'Windows seçin.
   Sekme C# için **Form1.cs [Tasarım]** veya **form1.vb [Tasarım]** Visual Basic.

1. **Form1'de herhangi bir yeri seçin.**

1. Özellikler **penceresi** artık formun özelliklerini görüntüler.
   Özellikler **penceresi** genellikle dosyanın sağ alt Visual Studio.
   Bu bölüm ön plan ve arka plan rengi, formun en üstünde görünen başlık metni ve formun boyutu gibi çeşitli özellikleri kontrol eder.

   Özellikler'i görmüyorsanız **Özellikler** Penceresini   >  **Görüntüle'yi seçin.**

1. Özellikler **penceresinde Text** **özelliğini** bulun.
   Listenin nasıl sıralanmış olduğunu bağlı olarak, aşağı kaydırmak için ihtiyacınız olabilir.
   Resim Görüntüleyicisi *değerini girin* ve Enter tarak **seçin.**

   Formunuz artık başlık çubuğunda **Resim Görüntüleyici** metnine sahip.

   > [!NOTE]
   > Özellikleri kategoriye veya alfabetik olarak görüntüebilirsiniz.
   > Geri ve ileri geçiş **yapmak** için Özellikler penceresindeki düğmeleri kullanın.

1. Formu tekrar seçin. Formun sağ alt sürükleme tutamacı seçin.
   Tutamaç, formun sağ alt köşesindeki küçük bir beyaz karedir.

   ![Sağ altta Tutamacı sürükleyin'in yer alan Formlar penceresini gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-layout/windows-form-drag-handle.png)

   Formu daha geniş ve biraz daha uzun olacak şekilde yeniden boyutlandırmak için tutamacı sürükleyin.
   Özellikler penceresine **bakarsanız** **Size özelliği** değişmiştir.
   Size özelliğini değiştirerek formun boyutunu da **değiştirebilirsiniz.**

1. IDE'nin sol Visual Studio Araç Kutusu **sekmesini** seçin. Bunu görmüyorsanız menü çubuğundan  Görünüm Araç > **Kutusu'nı veya** **Ctrl** Alt X tuşlarını +  + **kullanın.**

1. Kapsayıcılar'ın yanındaki küçük üçgen **simgesini** seçerek grubu açın.

   ![Araç Kutusu sekmesindeki Kapsayıcılar grubunu gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-layout/toolbox-container-table-layout-panel.png)

1. Araç Kutusunda **TableLayoutPanel'e** **çift tıklayın.**
   Bir denetimi araç kutusundan forma da sürükleyebilirsiniz.
   TableLayoutPanel denetimi form içinde görünür.

   ![TableLayoutPanel denetimi eklenmiş formun ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-layout/table-layout-format-added.png)

   > [!NOTE]
   > TableLayoutPanel'inizi ekledikten sonra form içinde **TableLayoutPanel Görevleri** başlığıyla bir pencere görünürse formu kapatmak için formun herhangi bir yerine tıklayın.

1. **TableLayoutPanel öğesini seçin.**
   Özellikler penceresine bakarak hangi denetimin seç olduğunu **doğruabilirsiniz.**

   ![TableLayoutPanel Özellikler penceresi gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-layout/table-layout-panel-properties.png)

1. TableLayoutPanel seçiliyken, Hiçbiri değerine sahip **Dock** özelliğini **bulun.**
   Açılan oku seçin ve ardından açılan **menenin** ortasındaki büyük düğme olan Dolgu'ya tıklayın.

   ![Dolgu seçiliyken Özellikler penceresi ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-layout/dock-property.png)

   *Yerleştirme,* bir pencerenin başka bir pencereye veya alana nasıl ekli olduğunu ifade eder.

   TableLayoutPanel artık formun tamamını doldurur.
   Formu yeniden boyutlandırırsanız, TableLayoutPanel sabitlenmiş kalır ve kendisini sığacak şekilde yeniden boyutlandırır.

1. Formda TableLayoutPanel öğesini seçin.
   Sağ üst köşede küçük bir siyah üçgen düğmesi vardır.

   Denetimin görev listesini göstermek için üçgeni seçin.

   ![Ekran görüntüsünde TableLayoutPanel görevleri gösterilmektedir.](../ide/media/tutorial-windows-forms-picture-viewer-layout/table-layout-panel-tasks.png)

1. **Sütun ve satır stilleri** iletişim kutusunu göstermek için **satırları ve sütunları Düzenle '** yi seçin.

1. **Sütun1** ' yi seçin ve boyutunu yüzde 15 olarak ayarlayın. **Yüzde** düğmesinin seçili olduğundan emin olun.

1. **Sütun2** 'yi seçin ve yüzde 85 olarak ayarlayın.

   ![Ekran görüntüsü TableLayoutPanel sütununu ve satır stillerini gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-layout/layout-column-row-styles.png)

1. **Sütun ve satır stilleri** iletişim kutusunun üstünde **göster** ' in içinden **Satırlar**' ı seçin. **Row1** değerini yüzde 90 ve **Row2** olarak ayarlayın. Değişikliklerinizi kaydetmek için **Tamam**’ı seçin. 

   TableLayoutPanel artık büyük bir üst satıra, küçük bir alt satıra, küçük bir sola sütuna ve büyük bir sütun ve sağ sütuna sahiptir.

   ![Ekran görüntüsü, yeniden boyutlandırılan TableLayoutPanel ile formu gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-layout/form-layout.png)

Düzeniniz tamamlanmıştır.

   > [!NOTE]
   > Uygulamanızı çalıştırmadan önce **Tümünü Kaydet** araç çubuğu düğmesini seçerek uygulamanızı kaydedin.
   > Alternatif olarak, uygulamanızı kaydetmek için, **Dosya**  >  **Tümünü** menü çubuğundan Kaydet ' i seçin veya **CTRL** + **SHIFT** + **S** tuşuna basın.
   > Bu, erken ve sık tasarrufu sağlamak için en iyi uygulamadır.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Windows Forms bir uygulama projesi oluşturduğunuzda, çalıştıran bir program oluşturursunuz.
Bu aşamada, resim görüntüleyici uygulamanız çok uygun değildir.
Şimdilik başlık çubuğunda **resim görüntüleyicisini** gösteren boş bir pencere görüntülenir.

Uygulamayı çalıştırmak için aşağıdaki adımları izleyin.

1. Aşağıdaki yöntemlerden birini kullanın:

   - **F5** tuşunu seçin.
   - Menü çubuğunda **hata**  >  **ayıklamayı Başlat hata** Ayıkla ' yı seçin.
   - Araç çubuğunda **Başlat** düğmesini seçin.

   Visual Studio uygulamanızı çalıştırır. **Picture** of başlıklı bir pencere görüntülenir.

   ![ekran görüntüsü, çalışan Windows Forms uygulamayı gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-layout/run-empty-windows-forms-app.png)

   Visual Studio ıde araç çubuğuna bakın.
   Bir uygulamayı çalıştırdığınızda, araç çubuğunda daha fazla düğme görüntülenir.
   Bu düğmeler, uygulamanızı durdurma ve başlatma gibi işlemleri yapmanızı ve hataları izlemenize yardımcı olur.

   ![Ekran görüntüsü, uygulamanın durdurulabileceğiniz hata ayıklama araç çubuğunu gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-layout/debug-toolbar.png)

1. Uygulamanızı durdurmak için aşağıdaki yöntemlerden birini kullanın:

   - Araç çubuğunda **hata ayıklamayı Durdur** düğmesini seçin.
   - Menü çubuğunda **hata**  >  **ayıklamayı Durdur** Hata Ayıkla ' yı seçin.
   - Klavyeden **SHIFT** + **F5**' i girin.
   - **Resim görüntüleyici** penceresinin üst köşesindeki **X** ' i seçin.

   uygulamanızı Visual Studio ıde 'nin içinden çalıştırdığınızda hata ayıklama olarak adlandırılır.
   Hataları bulmak ve onarmak için uygulamanızı çalıştırın.
   Diğer programları çalıştırmak ve hatalarını ayıklamak için aynı yordamı izleyin.
   Hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Resim görüntüleyici programınıza denetim ekleme hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Eğitim Bölüm 2: resim görüntüleyiciye denetim ekleme](tutorial-windows-forms-picture-viewer-controls.md)
