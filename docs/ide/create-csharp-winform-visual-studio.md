---
title: 'C ile Windows Forms uygulama oluşturma #'
description: Visual Studio 'da C# ile adım adım bir Windows Forms uygulama oluşturmayı öğrenin.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 26f13d12324beb0e414761ce2d79297767c5d708
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297125"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>C ile Visual Studio 'da Windows Forms uygulaması oluşturma\#

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimi (UI) olan basit bir C# uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. Koyu tema kullanmıyorsanız, ancak isterseniz, nasıl yapılacağını öğrenmek için [Visual STUDIO IDE ve düzenleyici 'Yi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

1. Sol bölmedeki **Yeni proje** iletişim kutusunda, **Visual C#** öğesini genişletin ve ardından **Windows Masaüstü**' ne tıklayın. Orta bölmede **Windows Forms uygulama (.NET Framework)** öğesini seçin. Sonra dosyayı adlandırın `HelloWorld` .

     **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusundan ve üst menü çubuğundan **Araçlar**  >  **Al araçlar ve Özellikler**' i seçin. Visual Studio Yükleyicisi başlatılır. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .NET Core iş yükü](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde C# için **Windows Forms App (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz. Örneğin, arama kutusuna *Windows Forms uygulama* girin veya yazın. Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **Windows** ' u seçin.)  

   ![Windows Forms uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** Iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .NET Core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

C# proje şablonunuzu seçip Dosyanızı adlandırın, Visual Studio sizin için bir form açar. Form bir Windows kullanıcı arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

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

   Birkaç şey meydana gelir. Visual Studio IDE 'de, **Tanılama araçları** penceresi açılır ve bir **Çıkış** penceresi de açılır. Ancak IDE dışında bir **Form1** iletişim kutusu belirir. Bu düğme, **Bu düğmeye tıklayın** ve **Label1** belirten metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . **Label1** metninin **Merhaba Dünya!** olarak değiştiğine dikkat edin.

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)