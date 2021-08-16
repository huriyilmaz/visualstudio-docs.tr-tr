---
title: '1. Adım: Windows Forms Uygulaması projesi oluşturma'
description: Resim görüntüleyiciniz için Windows Forms Uygulaması projesi oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b3e8ce4817b7f9040334137feb88a6cbac3b709aa73e2b0446d5fc51dea3795b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371677"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>1. Adım: Windows Forms Uygulaması projesi oluşturma

Resim görüntüleyici oluşturmanın ilk adımı bir Windows Forms Uygulaması projesi oluşturmaktır.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Open Visual Studio 2017

1. Menü çubuğunda Dosya Yeni **Dosya'Project.**  >    >   İletişim kutusu aşağıdaki ekran görüntüsüne benzer şekilde görünür.

     ![Yeni proje iletişim kutusu](../ide/media/newprojectdialogcallouts.png)<br/>***Yeni proje** _ _dialog kutusu*

2. Yeni Project iletişim kutusunun **sol** tarafında **Visual C#** veya **Visual Basic'ı seçin** ve ardından Masaüstü'Windows **seçin.**

3. Proje şablonları listesinde, Windows **Forms Uygulaması (.NET Framework) seçin.** Yeni forma *PictureViewer adını* ve ardından Tamam **düğmesini** seçin.

    >[!NOTE]
    >**Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız. **.NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.<br/><br/>![.NET masaüstü geliştirme iş yükü Visual Studio Yükleyicisi](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Daha fazla bilgi için Yükleme [Visual Studio](../install/install-visual-studio.md) bakın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="open-visual-studio"></a>Visual Studio’yu açın

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** arama kutusuna *Windows Formlar* yazın veya yazın. Ardından, uygulama **türü** listesinden **Masaüstü Project seçin.**

   Uygulama türü **filtresini Project** C# veya Windows için **Windows Forms Uygulaması (.NET Framework)** şablonunu seçin ve Visual Basic'yi **seçin.**

   ![Windows Forms Uygulaması (.NET Framework) için C# veya Visual Basic şablonunu seçin](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresine** resim adı kutusuna *PictureViewer* **yazın Project girin.** Ardından **Oluştur'a seçin.**

::: moniker-end

Visual Studio için bir çözüm oluşturur. Çözüm, uygulamanıza gereken tüm projeler ve dosyalar için kapsayıcı olarak davranır. Bu terimler bu öğreticinin devamlarında daha ayrıntılı olarak açıklanmaktadır.

## <a name="about-the-windows-forms-app-project"></a>Windows Forms Uygulaması projesi hakkında

1. Geliştirme ortamı üç pencere içerir: ana pencere, **Çözüm Gezgini** ve **Özellikler** penceresi.

     Bu pencerelerden herhangi biri eksikse varsayılan pencere düzenini geri yükleyebilirsiniz. Menü çubuğunda Pencere Sıfırlama Penceresi  >  **Düzeni'ne tıklayın.**

     Menü komutlarını kullanarak da pencereleri görüntüebilirsiniz. Menü çubuğunda Özellikleri Görüntüle **Penceresi'ne**  >  **tıklayın veya Çözüm Gezgini.** 

     Başka pencereler açıksa, sağ üst köşelerinde **Kapat** (x) düğmesini seçerek bunları kapatın.

    ::: moniker range="vs-2017"

    * **Ana pencere** Bu pencerede, formlarla çalışma ve kod düzenleme gibi çoğu işi siz yapacaksınız. Pencerede Form Düzenleyicisi'nde bir **form gösterilir.** Pencerenin üst kısmında Başlangıç Sayfası **sekmesi ve** **Form1.cs [Tasarım]** sekmesi görüntülenir. (Visual Basic sekme adı .cs *yerine .vb* *ile biter.*

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Ana pencere** Bu pencerede, formlarla çalışma ve kod düzenleme gibi çoğu işi siz yapacaksınız. Pencerede Form Düzenleyicisi'nde bir **form gösterilir.**

    ::: moniker-end

    * **Çözüm Gezgini penceresi** Bu pencerede, çözümünüzdeki tüm öğeleri görüntüp gezinebilirsiniz.

    Bir dosya seçerseniz Özellikler penceresinin **içeriği** değişir. Bir kod dosyası açarsanız (C# ile *.cs* ve *.vb* ile Visual Basic), kod dosyası veya kod dosyası için bir tasarımcı görüntülenir. Tasarımcı, üzerine düğmeler ve listeler gibi denetimler ekln bir görsel yüzeydir. Daha Visual Studio için tasarımcı, Windows **Forms Tasarımcısı olarak çağrılır.**

    * **Özellikler penceresi** Bu pencerede, diğer pencerelerde seçtiğiniz öğelerin özelliklerini değiştirebilirsiniz. Örneğin Form1'i seçerseniz Text özelliğini ayarerek başlığını değiştirebilir ve **Backcolor** özelliğini ayarerek arka plan **rengini değiştirebilirsiniz.**

      > [!NOTE]
      > Çözüm Gezgini **üst** Çözüm Gezgini **Çözüm 'PictureViewer' (1 proje)** gösterir. Bu da sizin Visual Studio çözüm oluşturduğunuz anlamına gelir. Bir çözüm birden fazla proje içerebilir, ancak şimdilik yalnızca bir proje içeren çözümlerle çalışacaktır.

1. Menü çubuğunda Dosya Hepsini **Kaydet'i**  >  **seçin.**

     Alternatif olarak, araç **çubuğundaki** Aşağıdaki görüntüde yer alan Tüm Kaydet düğmesini seçin.

     ![Tüm araç çubuğunu kaydet düğmesi](../ide/media/express_iconsaveall.png)<br/>
     ***Save All** _ _toolbar düğmesi*

     Visual Studio klasör adını ve proje adını otomatik olarak doldurur ve ardından projeyi projeler klasörünüze kaydeder.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. **[2. Adım: Uygulamanızı çalıştırma.](../ide/step-2-run-your-program.md)**

* Genel bakış konu başlığına dönmek için [bkz. Öğretici 1: Resim görüntüleyici oluşturma.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
