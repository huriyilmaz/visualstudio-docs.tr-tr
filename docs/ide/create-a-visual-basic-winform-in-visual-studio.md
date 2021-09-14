---
title: Windows Forms uygulaması Visual Basic
description: Visual Basic adım Windows formlar Visual Studio formlar uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.date: 09/27/2019
ms.topic: tutorial
ms.devlang: vb
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 85318331f7359400c1428af9047791e6c5f3079f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628832"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Windows ile Visual Studio Forms Visual Basic

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimine (UI) sahip basit bir Visual Basic uygulaması oluşturacağız.

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanmadıysanız ama bunu öğrenmek için Visual Studio [IDE](../ide/quickstart-personalize-the-ide.md) ve Düzenleyici sayfasını kişiselleştirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio [2022 Preview'Visual Studio](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidip ücretsiz olarak yükleyin.

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanmadıysanız ama bunu öğrenmek için Visual Studio [IDE](../ide/quickstart-personalize-the-ide.md) ve Düzenleyici sayfasını kişiselleştirme sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir uygulama projesi Visual Basic oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

1. Sol **bölmede yeni Project** iletişim kutusunda, Visual Basic'ı **genişletin** ve ardından Masaüstü'Windows **seçin.** Orta bölmede form form Windows **(.NET Framework) seçin.** Ardından dosyaya adını `HelloWorld` girin.

     **Windows Forms Uygulaması (.NET Framework)** proje şablonunu görmüyorsanız Yeni Project iletişim kutusundan  iptal edin ve üst menü çubuğunda Araçlar Araçları ve Özellikleri  >  **Al'ı seçin.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

     ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** yeni proje için **Windows Forms Uygulaması (.NET Framework)** şablonunu Visual Basic.

   (Tercih ederseniz, istediğiniz şablona hızla gitmek için aramanızı geliştirebilirsiniz. Örneğin, arama kutusuna *Windows Form Uygulaması yazın* veya yazın. Ardından Dil **Visual Basic** Seçin ve ardından Platform **listesinden Windows'yi** seçin.)  

   ![Windows Forms Visual Basic için Windows şablonunu seçin (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Windows Forms Uygulaması **(.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından **Oluştur'a seçin.**

   !['Yeni projenizi yapılandırma' penceresinde projenize 'HelloWorld' adını girin](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

Uygulama proje şablon Visual Basic ve dosyanıza ad verdikten sonra Visual Studio form açar. Form, Windows arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacak ve ardından uygulamayı çalıştıracak.

### <a name="add-a-button-to-the-form"></a>Forma düğme ekleme

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'na tıklayın.

     ![Araç Kutusu penceresini açmak için Araç Kutusuna tıklayın](../ide/media/vb-toolbox-toolwindow.png)

     (Araç Kutusu açılır öğesi **seçeneğini** görmüyorsanız menü çubuğundan açabilirsiniz. Bunu yapmak için Araç **Kutusunu**  >  **Görüntüle'ye tıklayın.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için **Sabitle simgesine** tıklayın.

     ![Araç Kutusu penceresini IDE'ye sabitlemek için Sabitle simgesine tıklayın](../ide/media/vb-pin-the-toolbox-window.png)

1. Düğme **denetimine** tıklayın ve forma sürükleyin.

     ![Forma düğme ekleme](../ide/media/vb-add-a-button-to-form1.png)

1. Özellikler **penceresinin** Görünüm bölümünde **(veya Yazı** Tipleri **bölümünde)** yazın ve `Click this` Enter tuşuna **basın.**

     ![Formda düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     (Özellikler penceresini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Özellikler Penceresini  >  **Görüntüle'ye tıklayın.** Veya **F4 tuşuna basın.)**

1. Özellikler **penceresinin** Tasarım **bölümünde Düğme1** olan adı olarak değiştirin ve **Enter** `btnClickThis` tuşuna **basın.**

     ![Formda düğmeye işlev ekleme](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Listeyi Özellikler penceresinde alfabetik olarak  alfabetik olarak kullandıysanız **Düğme1,** bunun yerine **(DataBindings)** bölümünde görünür.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Eylem oluşturmak için bir düğme denetimi ekledik, şimdi de metin göndermek için bir etiket denetimi ekleyebiliriz.

1. Araç **Kutusu penceresinden** **Etiket denetimi'ne** tıklayın, ardından forma sürükleyin ve Bu düğmeye tıklayın **düğmesinin altına** bırakın.

1. Özellikler **penceresinin Tasarım** bölümünde **veya (DataBindings)** bölümünde **Label1** adını olarak değiştirin ve Enter  `lblHelloWorld` tuşuna **basın.**

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1.vb &#91;Tasarım&#93;** penceresinde Bu düğmeye çift tıklayarak  **Form1.vb penceresini** açın.

      (Alternatif olarak, **form1.vb'yi** Çözüm Gezgini  **form1'e tıklar.)**

1. **Form1.vb penceresinde,** Özel  Alt ve Son **Alt** satırları arasına aşağıdaki ekran `lblHelloWorld.Text = "Hello World!"` görüntüsünde gösterildiği gibi yazın veya girin:

     ![Forma kod ekleme](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak** için Başlat düğmesine tıklayın.

     ![Uygulamada hata ayıklamak ve çalıştırmak için Başlat'a tıklayın](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey olur. IDE Visual Studio de Tanılama Araçları **penceresi** açılır ve bir **Çıkış** penceresi de açılır. Ancak IDE'nin dışında **bir Form1 iletişim** kutusu görüntülenir. Bu düğmeye tıklayın **ve Etiket1** metnini **içerir.**

1. **Form1** **iletişim** kutusunda Bu düğmeye tıklayın. **Label1 metninin şu** şekilde değişti: **Merhaba Dünya!**.

    ![Label1 metni içeren form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı **çalıştırmayı durdurmak** için Form1 iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: Resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C# öğreticileri](../get-started/csharp/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)