---
title: 'C ile Windows Forms uygulaması oluşturma #'
description: C# ile Windows Formlar Visual Studio oluşturma hakkında bilgi edinmek için adım adım bilgi edinebilirsiniz.
ms.custom: vs-acquisition, get-started
ms.date: 11/08/2021
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
ms.openlocfilehash: 7d8c83d308d0d3f08c9469d45b725bb9fc8f34e9
ms.sourcegitcommit: 5f60dd61e7f281db7892118dbed6387c4903701f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132079753"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>C ile Windows formlarda Visual Studio Forms uygulaması oluşturma\#

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimine (UI) sahip basit bir C# uygulaması oluşturacağız.

::: moniker range="vs-2017"

Visual Studio'i henüz yüklememiş Visual Studio [indirmeler](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidip ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'i henüz yüklememiş Visual Studio [indirmeler](https://visualstudio.microsoft.com/downloads) sayfasına gidip ücretsiz yükleyin.

> [!NOTE]
> Bu öğreticide yer alan ekran görüntülerden bazıları koyu temayı kullanır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio [2022](https://visualstudio.microsoft.com/downloads) indirmeleri sayfasına Visual Studio ücretsiz olarak yükleyin.

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

::: moniker range="vs-2019"

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
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; varsa, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından **Oluştur'a seçin.**

   !['Yeni projenizi yapılandırma' penceresinde projenize 'HelloWorld' adını girin](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**
    
    :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="Yeni proje oluştur penceresinin ekran görüntüsü.":::

1. Yeni proje **oluştur penceresinde** C# için Windows Forms **Uygulaması (.NET Framework)** şablonunu seçin.

   (Tercih ederseniz, istediğiniz şablona hızla gitmek için aramanızı geliştirebilirsiniz. Örneğin, arama kutusuna *Windows Form Uygulaması yazın* veya yazın. Ardından Dil **listesinden C#** dilini ve ardından Platform **listesinden Windows'yi** seçin.)  

    :::image type="content" source="media/vs-2022/csharp-winform-create-a-new-project.png" alt-text="Windows Forms Uygulaması (.NET Framework) için C# şablonunu seçme ekran görüntüsü.":::

   > [!NOTE]
   > Windows Forms Uygulaması **(.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > :::image type="content" source="../get-started/media/vs-2019/not-finding-what-looking-for.png" alt-text="'Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısının ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.
   >
   > :::image type="content" source="media/vs-2022/install-dot-net-desktop-env.png" alt-text=".NET Core iş yükünü uygulamanın içinde gösterme Visual Studio Yükleyicisi.":::
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; varsa, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından **Oluştur**’u seçin.

    :::image type="content" source="media/vs-2022/csharp-winform-configure-new-project.png" alt-text="'Yeni projenizi yapılandır' penceresini gösterme ve projenize 'HelloWorld' adını ekleme ekran görüntüsü":::

   Visual Studio projenizi açar.

## <a name="create-the-application"></a>Uygulama oluşturma

C# proje şablonlarınızı seçerek dosyanıza bir ad verdikten Visual Studio form açarsınız. Form, Windows arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacak ve ardından uygulamayı çalıştıracak.

### <a name="add-a-button-to-the-form"></a>Forma düğme ekleme

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.
    
     :::image type="content" source="media/vs-2022/csharp-winform-hello-world-project-toolbox.png" alt-text="Araç Kutusu penceresini açmak için Araç Kutusunu seçme ekran görüntüsü.":::

     (Araç Kutusu açılır öğesi **seçeneğini** görmüyorsanız menü çubuğundan açabilirsiniz. Bunu yapmak için Araç **Kutusunu**  >  **Görüntüle'ye tıklayın.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için **Sabitle simgesini** seçin.

     :::image type="content" source="media/vs-2022/csharp-winform-toolbox-flyout-pin.png" alt-text="Araç Kutusu penceresini IDE'ye sabitlemek için Sabitle simgesini seçme ekran görüntüsü.":::

1. Düğme **denetimi'ne** tıklayın ve forma sürükleyin.

     :::image type="content" source="media/vs-2022/csharp-winform-add-button-on-form.png" alt-text="Forma düğme ekleme ekran görüntüsü.":::

1. Özellikler penceresinde **Metin'i** **bulun,** **düğme1** olan adı olarak değiştirin `Click this` ve Enter tuşuna **basın.**

     :::image type="content" source="media/vs-2022/csharp-winform-button-properties-text.png" alt-text="Form üzerinde düğmeyi kullanarak metin ekleme ekran görüntüsü Özellikler penceresi.":::

     (Özellikler penceresini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Özellikler Penceresini  >  **Görüntüle'yi seçin.** Veya **F4 tuşuna basın.)**

1. Özellikler **penceresinin** Tasarım **bölümünde düğme1** olan adı olarak değiştirin ve **Enter** `btnClickThis` tuşuna **basın.**

     :::image type="content" source="media/vs-2022/csharp-winform-button-properties-design-name.png" alt-text="Form üzerinde düğmeyi kullanarak işlev ekleme ekran görüntüsü Özellikler penceresi.":::

   > [!NOTE]
   > Listeyi Özellikler penceresinde alfabetik olarak  alfabetik olarak kullandıysanız **düğme1,** **bunun yerine (DataBindings)** bölümünde görünür.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Eylem oluşturmak için bir düğme denetimi ekledik, şimdi de metin göndermek için bir etiket denetimi eklenmiştir.

1. Araç **Kutusu penceresinden** **Etiket denetimi'ne** tıklayın, ardından forma sürükleyin ve Bu düğmeye tıklayın **düğmesinin altına** bırakın.

1. Özellikler **penceresinin Tasarım** bölümünde **veya (DataBindings)** bölümünde **label1** etiketinin adını olarak değiştirin ve enter  `lblHelloWorld` tuşuna **basın.**

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1.cs &#91;Tasarım&#93;** penceresinde Bu düğmeye çift tıklayarak  **Form1.cs penceresini** açın.

      (Alternatif olarak, **form1.cs'yi** Çözüm Gezgini **ve** ardından **Form1'i seçebilirsiniz.)**

1. **Form1.cs penceresinde,** aşağıdaki ekran **görüntüsünde** gösterildiği gibi özel void `lblHelloWorld.Text = "Hello World!";` satırına yazın veya girin:

     :::image type="content" source="media/vs-2022/csharp-winform-button-click-code.png" alt-text="Forma kod ekleme ekran görüntüsü":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak** için Başlat düğmesini seçin.

     :::image type="content" source="media/vs-2022/csharp-winform-visual-studio-start-run-program.png" alt-text="Hata ayıklamaya ve uygulamayı çalıştırmaya başla seçeneğinin ekran görüntüsü.":::

   Birkaç şey olur. IDE Visual Studio de **Tanılama** Araçları penceresi açılır ve bir **Çıkış** penceresi de açılır. Ancak IDE'nin dışında **bir Form1 iletişim** kutusu görüntülenir. Bu düğme, **Bu düğmeye tıklayın** ve **Label1** belirten metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . **Label1** metninin **Merhaba Dünya!** olarak değiştiğine dikkat edin.

     :::image type="content" source="media/vs-2022/csharp-winform-form.png" alt-text="Label1 metnini içeren bir Form1 iletişim kutusu gösteren ekran görüntüsü.":::

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

::: moniker-end

::: moniker range="<=vs-2019"
## <a name="create-the-application"></a>Uygulama oluşturma

C# proje şablonunuzu seçip dosyanızı adlandırın Visual Studio, sizin için bir form açar. form, Windows bir kullanıcı arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

### <a name="add-a-button-to-the-form"></a>Forma Düğme Ekle

1. Araç **kutusu ' nu seçerek araç** kutusu açılır penceresini açın.

     ![Araç kutusu penceresini açmak için araç kutusunu seçin](../ide/media/csharp-toolbox-toolwindow.png)

     ( **Araç kutusu** açılır seçeneğini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için   >  **araç kutusunu** görüntüleyin. Ya da **CTRL** + **alt** + **X** tuşlarına basın.)

1. **Araç kutusu** penceresini sabitlemek için **raptiye** simgesini seçin.

     ![Araç kutusu penceresini IDE 'ye sabitlemek için raptiye simgesini seçin](../ide/media/vb-pin-the-toolbox-window.png)

1. **Düğme** denetimini seçin ve ardından form üzerine sürükleyin.

     ![Forma Düğme Ekle](../ide/media/csharp-add-button-form1.png)

1. **Özellikler** penceresinde, **metni** bulun, **button1** olarak adı değiştirin `Click this` ve ardından **ENTER** tuşuna basın.

     ![Formdaki düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     ( **Özellikler** penceresini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için   >  **Özellikler penceresini** görüntüle ' yi seçin. Ya da **F4** tuşuna basın.)

1. **Özellikler** penceresinin **Tasarım** bölümünde, **button1** olarak adı değiştirin `btnClickThis` ve ardından **ENTER** tuşuna basın.

     ![Formdaki düğmeye bir işlev ekleyin](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > **Özellikler** penceresinde liste sıralama yaptıysanız, Button1 **(DataBindings)** bölümünde bunun yerine **button1** görüntülenir.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Bir eylem oluşturmak için bir düğme denetimi ekledik, artık metin göndermek için bir etiket denetimi ekleyelim.

1. **Araç kutusu** penceresinden **etiket** denetimini seçin ve sonra bu düğmenin altına sürükleyip bırakın ve sonra **Bu düğmeye tıklayın** .

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** bölümünde, **Label1** adını olarak değiştirin `lblHelloWorld` ve ardından **ENTER** tuşuna basın.

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1. cs &#91;tasarım&#93;** penceresinde, **Bu düğmeye tıklayarak** **Form1. cs** penceresini açın.

      (Alternatif olarak, **Çözüm Gezgini** içinde **Form1. cs** ' i genişletebilir ve ardından **Form1**' i seçebilirsiniz.)

1. **Form1. cs** penceresinde, **özel void** satırından sonra, `lblHelloWorld.Text = "Hello World!";` aşağıdaki ekran görüntüsünde gösterildiği gibi yazın veya girin:

     ![Forma kod ekleme](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Başlat** düğmesini seçin.

     ![Hata ayıklamak ve uygulamayı çalıştırmak için Başlat 'ı seçin](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey meydana gelir. Visual Studio ıde 'de, **tanılama araçları** penceresi açılır ve bir **çıkış** penceresi de açılır. Ancak IDE dışında bir **Form1** iletişim kutusu belirir. Bu düğme, **Bu düğmeye tıklayın** ve **Label1** belirten metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . **Label1** metninin **Merhaba Dünya!** olarak değiştiğine dikkat edin.

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)