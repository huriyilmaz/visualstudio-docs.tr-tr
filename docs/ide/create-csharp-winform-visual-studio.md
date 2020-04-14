---
title: 'C ile Windows Forms uygulaması oluşturma #'
description: Visual Studio'da adım adım C#ile bir Windows Forms uygulaması oluşturmayı öğrenin.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8c798640ea80900c633b5b7d0817cc278a772a51
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224543"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Visual Studio'da C ile Windows Forms uygulaması oluşturma #

Visual Studio tümleşik geliştirme ortamına (IDE) kısa girişte, Windows tabanlı kullanıcı arabirimi (UI) olan basit bir C# uygulaması oluşturursunuz.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları karanlık teonu kullanır. Karanlık temayı kullanmıyorsanız ancak kullanmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio IDE ve Editor](../ide/quickstart-personalize-the-ide.md) sayfasını Kişiselleştir sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturursunuz. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

1. Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual C#** seçeneğini genişletin ve ardından **Windows Desktop'ı**seçin. Orta bölmede Windows **Forms App (.NET Framework) seçeneğini belirleyin.** Sonra dosyayı `HelloWorld`adlandırın.

     **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **Yeni Proje** iletişim kutusunu iptal edin ve üst menü çubuğundan **Araçlar** > **Araçları ve Özellikleri Al'ı**seçin. Visual Studio Installer başlattı. **.NET masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir'i**seçin.

     ![.NET Core iş yükü Visual Studio Yükleyici](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **bir proje oluşturma** penceresinde, C# için **Windows Forms App (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızla ulaşmak için aramanızı hassaslaştırabilirsiniz. Örneğin, arama kutusuna *Windows Forms Uygulaması* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin.)  

   ![Windows Forms Uygulaması (.NET Framework) için C# şablonunu seçin](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Windows Forms App **(.NET Framework)** şablonunu görmüyorsanız, **yeni bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Installer'da **.NET masaüstü geliştirme** iş yükünü seçin'i seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyici](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da,** **Project ad** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'HelloWorld' adını](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açıyor.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

C# proje şablonunuzu seçtikten ve dosyanızı adlandırdıktan sonra Visual Studio sizin için bir form açar. Form, Windows kullanıcı arabirimidir. Forma denetimler ekleyerek bir "Hello World" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

### <a name="add-a-button-to-the-form"></a>Forma bir düğme ekleme

1. Araç Kutusu fly-out penceresini açmak için **Araç Kutusu'nu** seçin.

     ![Araç Kutusu penceresini açmak için Araç Kutusu'nu seçin](../ide/media/csharp-toolbox-toolwindow.png)

     **(Toolbox** fly-out seçeneğini görmüyorsanız, menü çubuğundan açabilirsiniz. Bunu yapmak için,**Araç Kutusunu** **Görüntüle** > . Veya **Ctrl**+**Alt**+**X**tuşuna basın .)

1. **Araç Kutusu** penceresini sabitlemek için **Pin** simgesini seçin.

     ![Araç Kutusu penceresini IDE'ye sabitlemek için Pin simgesini seçin](../ide/media/vb-pin-the-toolbox-window.png)

1. **Düğme** denetimini seçin ve ardından forma sürükleyin.

     ![Forma bir düğme ekleme](../ide/media/csharp-add-button-form1.png)

1. **Özellikler** penceresinde, **Metin'i**bulun, adı **Button1'den** 'e `Click this`değiştirin ve sonra **Enter**tuşuna basın.

     ![Formdaki düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     **(Özellikler** penceresini görmüyorsanız, menü çubuğundan açabilirsiniz. Bunu yapmak için**Özellikler Penceresini** **Görüntüle'yi** > seçin. Veya **F4**tuşuna basın .)

1. **Özellikler** penceresinin **Tasarım** bölümünde, adı **Button1'den** 'e `btnClickThis`değiştirin ve sonra **Enter**tuşuna basın.

     ![Formdaki düğmeye işlev ekleme](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > **Özellikler** penceresindelistesırasını sıralarsanız, **Button1** **(DataBindings)** bölümünde görünür.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Artık bir eylem oluşturmak için bir düğme denetimi eklediğimize göre, metin göndermek için bir etiket denetimi ekleyelim.

1. **Araç Kutusu** penceresinden **Etiket** denetimini seçin ve ardından forma sürükleyin ve **bu düğmeyi tıklat'ın** altına bırakın.

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** **bölümünde, Label1'in** `lblHelloWorld`adını değiştirin ve enter **tuşuna**basın.

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. tasarım **&#93;** Form1.cs &#91;penceresinde, **Form1.cs** penceresini açmak için bu düğmeye **çift tıklayın.**

      (Alternatif olarak, **Çözüm Gezgini'nde** **Form1.cs** genişletebilir ve ardından **Form1'i**seçebilirsiniz.)

1. **Form1.cs** penceresinde, özel **boşluk** satırından sonra `lblHelloWorld.Text = "Hello World!";` aşağıdaki ekran görüntüsünde gösterildiği gibi yazın veya girin:

     ![Forma kod ekleme](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Başlat** düğmesini seçin.

     ![Hata ayıklama ve uygulamayı çalıştırmayı Başlat'ı seçin](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey olacak. Visual Studio IDE'de **Tanılama Araçları** penceresi açılır ve **Çıktı** penceresi de açılır. Ancak IDE dışında bir **Form1** iletişim kutusu görüntülenir. Bu düğmeyi ve **Label1**yazan metni **tonuyla** içerecektir.

1. **Form1** iletişim kutusundaki bu düğmeyi **tıklatın'ı** seçin. **Label1** metninin Hello **World'e**değiştiğine dikkat edin! .

    ![Label1 metnini içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: Resim görüntüleyicisi oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# eğitimleri](/visualstudio/get-started/csharp/)
* [Visual Basic eğitimleri](/visualstudio/get-started/visual-basic/)
* [C++ eğitimleri](/cpp/get-started/tutorial-console-cpp)
