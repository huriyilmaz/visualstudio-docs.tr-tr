---
title: 'Adım 1: Windows Forms App projesi oluşturma'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579905"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Adım 1: Windows Forms App projesi oluşturma

Bir resim görüntüleyicisi oluşturduğunuzda, ilk adım bir Windows Forms App projesi oluşturmaktır.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Açık Görsel Stüdyo 2017

1. Menü çubuğunda**Yeni** > **Proje** **yi seçin.** >  İletişim kutusu aşağıdaki ekran görüntüsüne benzer olmalıdır.

     ![Yeni proje iletişim kutusu](../ide/media/newprojectdialogcallouts.png)<br/>***Yeni proje*** *iletişim kutusu*

2. **Yeni Proje** iletişim kutusunun sol tarafında, **Visual C#** veya **Visual Basic'i**seçin ve ardından **Windows Desktop'ı**seçin.

3. Proje şablonları listesinde **Windows Forms App (.NET Framework)** seçeneğini belirleyin. Yeni form *PictureViewer'ı*adlandırın ve ardından **Tamam** düğmesini seçin.

    >[!NOTE]
    >**Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.NET masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisini kullanın.<br/><br/>![.NET masaüstü geliştirme iş yükü Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Daha fazla bilgi için [Visual Studio'yu yükle](../install/install-visual-studio.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Açık Görsel Stüdyo 2019

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *Windows Formları* girin veya yazın. Ardından, **Proje türü** listesinden **Masaüstü'nü** seçin.

   **Proje türü** filtresini uyguladıktan sonra C# veya Visual Basic için Windows Forms **App (.NET Framework)** şablonunu seçin ve **ardından İleri'yi**seçin.

   ![Windows Forms Uygulaması (.NET Framework) için C# veya Visual Basic şablonundan birini seçin](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, yeni **bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Installer'da **.NET masaüstü geliştirme** iş yükünü seçin'i seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyici](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin.

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *PictureViewer* yazın veya girin. Ardından **Oluştur'u**seçin.

::: moniker-end

Visual Studio uygulamanız için bir çözüm oluşturur. Bir çözüm, uygulamanızın gerektirdiği tüm projeler ve dosyalar için bir kapsayıcı görevi görür. Bu terimler daha sonra bu öğreticide daha ayrıntılı olarak açıklanacaktır.

## <a name="about-the-windows-forms-app-project"></a>Windows Forms App projesi hakkında

1. Geliştirme ortamı üç pencere içerir: ana pencere, **Çözüm Gezgini**ve **Özellikler** penceresi.

     Bu pencerelerden herhangi biri eksikse, varsayılan pencere düzenini geri yükleyebilirsiniz. Menü çubuğunda **Pencere** > **Sıfırlama Düzenini**seçin.

     Menü komutlarını kullanarak pencereleri de görüntüleyebilirsiniz. Menü çubuğunda**Özellikler Penceresini** veya **Çözüm Gezgini'ni** **görüntüle'yi** > seçin.

     Başka pencereler varsa, sağ üst köşelerindeki **Kapat** (x) düğmesini seçerek kapatın.

    ::: moniker range="vs-2017"

    * **Ana pencere** Bu pencerede, formlarla çalışma ve kod düzenleme gibi çalışmanızın çoğunu yaparsınız. Pencere, Form Düzenleyicisi'nde bir form gösterir. **Form Editor** Pencerenin üst kısmında, **Başlat Sayfası** sekmesi ve **Form1.cs [Tasarım]** sekmesi görüntülenir. (Visual Basic'te sekme adı *.cs*yerine *.vb* ile biter.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Ana pencere** Bu pencerede, formlarla çalışma ve kod düzenleme gibi çalışmanızın çoğunu yaparsınız. Pencere, Form Düzenleyicisi'nde bir form gösterir. **Form Editor**

    ::: moniker-end

    * **Çözüm Gezgini penceresi** Bu pencerede, çözümünüzdeki tüm öğeleri görüntüleyebilir ve gezinebilirsiniz.

    Bir dosya seçerseniz, **Özellikler** penceresinin içeriği değişir. Bir kod dosyasını açarsanız (Visual Basic'te *C# ve* *.vb* ile biten) kod dosyası veya kod dosyasının tasarımcısı görüntülenir. Tasarımcı, üzerine düğmeler ve listeler gibi denetimler ekleyebileceğiniz görsel bir yüzeydir. Visual Studio formları için, tasarımcı **Windows Forms Designer**denir.

    * **Özellikler penceresi** Bu pencerede, diğer pencerelerde seçtiğiniz öğelerin özelliklerini değiştirebilirsiniz. Örneğin, Form1'i seçerseniz, **Metin** özelliğini ayarlayarak başlığını değiştirebilir ve **Arka Renk** özelliğini ayarlayarak arka plan rengini değiştirebilirsiniz.

      > [!NOTE]
      > **Solution Explorer'daki** en üst satırda **Solution 'PictureViewer' (1 proje) (1 proje)** gösterilmektedir, bu da Visual Studio'nun sizin için bir çözüm oluşturduğu anlamına gelir. Bir çözüm birden fazla proje içerebilir, ancak şimdilik yalnızca bir proje içeren çözümlerle çalışırsınız.

1. Menü çubuğunda**Tümlerini Kaydet'i** **seçin.** > 

     Alternatif olarak, araç çubuğundaki aşağıdaki resimde görünen **Tümlerini Kaydet** düğmesini seçin.

     ![Tüm araç çubuğu düğmesini kaydet](../ide/media/express_iconsaveall.png)<br/>
     Tüm *araç çubuğu düğmesini* ***kaydet***

     Visual Studio klasör adını ve proje adını otomatik olarak doldurur ve projeyi proje klasörünüze kaydeder.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için bkz: **[Adım 2: Uygulamanızı çalıştırın.](../ide/step-2-run-your-program.md)**

* Genel bakış konusuna dönmek için [bkz.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
