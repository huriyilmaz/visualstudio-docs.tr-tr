---
title: 'C ile Windows Forms uygulaması oluşturma #'
description: C# ile Windows adım Visual Studio Formlar uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: vs-acquisition, get-started
ms.date: 09/26/2019
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2b0f9c7ebcdf89ae193118afa5f90af4efb1f4b5
ms.sourcegitcommit: da5efd7698e357c59ba9b7dbbcaaceb5d1cfade2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128329460"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>C ile Windows formlarda Visual Studio Forms uygulaması oluşturma\#

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimine (UI) sahip basit bir C# uygulaması oluşturacağız.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio [2022 Preview'Visual Studio](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidip ücretsiz olarak yükleyin.

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir C# uygulama projesi oluşturabilirsiniz. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

1. Sol **bölmede yeni Project** iletişim kutusunda Visual **C#** öğesini genişletin ve ardından Masaüstü'Windows **seçin.** Orta bölmede form form Windows **(.NET Framework) seçin.** Ardından dosyaya adını `HelloWorld` girin.

     **Windows Forms Uygulaması (.NET Framework)** proje şablonunu görmüyorsanız Yeni Project iletişim kutusundan  iptal edin ve üst menü çubuğunda Araçlar Araçları ve Özellikleri  >  **Al'ı seçin.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

     ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni proje **oluştur penceresinde C#** için **Windows Forms Uygulaması (.NET Framework)** şablonunu seçin.

   (Tercih ederseniz, istediğiniz şablona hızla gitmek için aramanızı geliştirebilirsiniz. Örneğin, arama kutusuna *Windows Form Uygulaması yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin.)  

   ![Windows Forms Uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

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

1. Yeni **projenizi yapılandır penceresine** *HelloWorld* yazın veya **Project** girin. Ardından **Oluştur'a seçin.**

   !['Yeni projenizi yapılandırma' penceresinde projenize 'HelloWorld' adını girin](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

C# proje şablonlarınızı seçerek dosyanıza bir ad verdikten Visual Studio form açarsınız. Form, Windows arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacak ve ardından uygulamayı çalıştıracak.

### <a name="add-a-button-to-the-form"></a>Forma düğme ekleme

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.

     ![Araç Kutusu penceresini açmak için Araç Kutusunu seçin](../ide/media/csharp-toolbox-toolwindow.png)

     (Araç Kutusu açılır öğesi **seçeneğini** görmüyorsanız menü çubuğundan açabilirsiniz. Bunu yapmak için Araç **Kutusunu**  >  **Görüntüle'ye tıklayın.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için **Sabitle simgesini** seçin.

     ![Araç Kutusu penceresini IDE'ye sabitlemek için Sabitle simgesini seçin](../ide/media/vb-pin-the-toolbox-window.png)

1. Düğme **denetimi'ne** tıklayın ve forma sürükleyin.

     ![Forma düğme ekleme](../ide/media/csharp-add-button-form1.png)

1. Özellikler penceresinde **Metin'i** **bulun, Düğme1** olan adı **olarak değiştirin** ve `Click this` Enter tuşuna **basın.**

     ![Formda düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     (Özellikler penceresini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Özellikler Penceresini  >  **Görüntüle'yi seçin.** Veya **F4 tuşuna basın.)**

1. Özellikler **penceresinin** Tasarım **bölümünde Düğme1** olan adı olarak değiştirin ve **Enter** `btnClickThis` tuşuna **basın.**

     ![Formda düğmeye işlev ekleme](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Listeyi Özellikler penceresinde alfabetik olarak  alfabetik olarak kullandıysanız **Düğme1,** bunun yerine **(DataBindings)** bölümünde görünür.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Eylem oluşturmak için bir düğme denetimi ekledik, şimdi de metin göndermek için bir etiket denetimi ekleyebiliriz.

1. Araç **Kutusu penceresinden** **Etiket denetimi'ne** tıklayın, ardından forma sürükleyin ve Bu düğmeye tıklayın **düğmesinin altına** bırakın.

1. Özellikler **penceresinin Tasarım** bölümünde **veya (DataBindings)** bölümünde **Label1** adını olarak değiştirin ve Enter  `lblHelloWorld` tuşuna **basın.**

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1.cs &#91;Tasarım&#93;** penceresinde Bu düğmeye çift tıklayarak  **Form1.cs penceresini** açın.

      (Alternatif olarak, **form1.cs'yi** Çözüm Gezgini **ve** ardından **Form1'i seçebilirsiniz.)**

1. **Form1.cs penceresinde,** aşağıdaki ekran **görüntüsünde** gösterildiği gibi özel void `lblHelloWorld.Text = "Hello World!";` satırına yazın veya girin:

     ![Forma kod ekleme](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak** için Başlat düğmesini seçin.

     ![Hata ayıklamak ve uygulamayı çalıştırmak için Başlat'ı seçin](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey olur. IDE Visual Studio de Tanılama Araçları **penceresi** açılır ve bir **Çıkış** penceresi de açılır. Ancak IDE'nin dışında **bir Form1 iletişim** kutusu görüntülenir. Bu düğmeye tıklayın **ve Etiket1** metnini **içerir.**

1. Form1 **iletişim** kutusunda Bu **düğmeye tıklayın'ı** seçin. **Label1 metninin şu** şekilde değişti: **Merhaba Dünya.**

    ![Label1 metni içeren form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı **çalıştırmayı durdurmak** için Form1 iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: Resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)