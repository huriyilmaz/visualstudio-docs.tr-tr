---
title: '1. Adım: Windows Forms Uygulaması projesi oluşturma'
description: resim görüntüleyiciniz için Windows Forms uygulama projesi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d3f3bacb4c0a08e6a9bd2948fcc9a70637706111
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724872"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>1. Adım: Windows Forms Uygulaması projesi oluşturma

bir resim görüntüleyici oluşturduğunuzda, ilk adım Windows Forms bir uygulama projesi oluşturmaktır.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Visual Studio açın 2017

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin. İletişim kutusu aşağıdaki ekran görüntüsüne benzer görünmelidir.

     ![Yeni proje iletişim kutusu](../ide/media/newprojectdialogcallouts.png)<br/>***Yeni proje** _ _dialog kutusu *

2. **yeni Project** iletişim kutusunun sol tarafında, **Visual C#** veya **Visual Basic** seçeneklerinden birini seçin ve ardından **Windows masaüstü**' ne tıklayın.

3. proje şablonları listesinde **Windows Forms uygulama (.NET Framework)** öğesini seçin. Yeni formu *PictureViewer olarak adlandırın* olarak adlandırın ve ardından **Tamam** düğmesini seçin.

    >[!NOTE]
    >**Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.<br/><br/>![Visual Studio Yükleyicisi .net masaüstü geliştirme iş yükü](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> daha fazla bilgi için, [Visual Studio yüklemesi](../install/install-visual-studio.md) sayfasına bakın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde, arama kutusuna *Windows Forms* girin veya yazın. sonra, **Project türü** listesinden **masaüstü** ' ne tıklayın.

   **Project tür** filtresini uyguladıktan sonra C# veya Visual Basic için **Windows Forms uygulama (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   ![Windows Forms uygulaması için C# veya Visual Basic şablonunu seçin (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *pictureviewer olarak adlandırın* yazın veya girin. Ardından **Oluştur**' u seçin.

::: moniker-end

Visual Studio, uygulamanız için bir çözüm oluşturur. Bir çözüm, uygulamanız için gereken tüm proje ve dosyalar için bir kapsayıcı görevi görür. Bu terimler, Bu öğreticinin ilerleyen kısımlarında daha ayrıntılı olarak açıklanacaktır.

## <a name="about-the-windows-forms-app-project"></a>Windows Forms uygulama projesi hakkında

1. Geliştirme ortamı üç pencere içerir: Ana pencere, **Çözüm Gezgini** ve **Özellikler** penceresi.

     Bu pencerelerin herhangi biri eksikse, varsayılan pencere yerleşimini geri yükleyebilirsiniz. Menü çubuğunda **pencere**  >  **sıfırlama pencere düzeni**' ni seçin.

     Ayrıca, menü komutlarını kullanarak da Windows görüntüleyebilirsiniz. Menü çubuğunda, **Görünüm**  >  **Özellikleri penceresi** ' ni veya **Çözüm Gezgini**' ı seçin.

     Başka herhangi bir pencere açıksa, sağ üst köşelerindeki **Kapat** (x) düğmesini seçerek onları kapatın.

    ::: moniker range="vs-2017"

    * **Ana pencere** Bu pencerede, yaptığınız gibi, formlarla çalışma ve kod düzenlemeyle ilgili birçok iş olacaktır. Pencere, **form düzenleyicisinde** bir form gösterir. Pencerenin üst kısmında, **Başlangıç sayfası** sekmesi ve **Form1. cs [Tasarım]** sekmesi görüntülenir. (Visual Basic, sekme adı *. cs* yerine *. vb* ile biter.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Ana pencere** Bu pencerede, yaptığınız gibi, formlarla çalışma ve kod düzenlemeyle ilgili birçok iş olacaktır. Pencere, **form düzenleyicisinde** bir form gösterir.

    ::: moniker-end

    * **Çözüm Gezgini penceresi** Bu pencerede, çözümünüzdeki tüm öğeleri görüntüleyebilir ve buna gidebilirsiniz.

    Bir dosya seçerseniz, **Özellikler** penceresinin içeriği değişir. bir kod dosyası açarsanız (C# ve *. vb* içinde *. cs* ile biten) Visual Basic), kod dosyası veya kod dosyası tasarımcısı görüntülenir. Tasarımcı, üzerinde düğme ve liste gibi denetimler ekleyebileceğiniz görsel bir yüzeydir. Visual Studio formlarında, tasarımcı **Windows Form Tasarımcısı** olarak adlandırılır.

    * **Özellikler penceresi** Bu pencerede, diğer pencereler üzerinde seçtiğiniz öğelerin özelliklerini değiştirebilirsiniz. Örneğin, Form1 ' i seçerseniz, **Text** özelliğini ayarlayarak başlığını değiştirebilir ve **BackColor** özelliğini ayarlayarak arka plan rengini değiştirebilirsiniz.

      > [!NOTE]
      > **Çözüm Gezgini** üst çizgi **' pictureviewer olarak adlandırın ' (1 proje) çözümünü** gösterir, bu da Visual Studio bir çözüm oluşturduğu anlamına gelir. Bir çözüm birden fazla proje içerebilir, ancak şimdilik yalnızca bir proje içeren çözümlerle çalışırsınız.

1. Menü çubuğunda **Dosya**  >  **Tümünü Kaydet**' i seçin.

     Alternatif olarak, aşağıdaki görüntüde gösterildiği gibi, araç çubuğunda **Tümünü Kaydet** düğmesini seçin.

     ![Tümünü Kaydet araç çubuğu düğmesi](../ide/media/express_iconsaveall.png)<br/>
     ***Tümünü Kaydet** _ _toolbar düğmesi *

     Visual Studio, klasör adı ve proje adını otomatik olarak doldurur ve projeyi projeler klasörünüze kaydeder.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. 2. **[Adım: uygulamanızı çalıştırma](../ide/step-2-run-your-program.md)**.

* Genel bakış konusuna dönmek için bkz. [öğretici 1: resim görüntüleyici oluşturma](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
