---
title: Visual Basic Windows Forms uygulama oluşturma
description: Visual Studio 'da Visual Basic, adım adım ile Windows Forms uygulama oluşturmayı öğrenin.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 65c7c3e34778a1bad3eb833c073c530db72b7a36
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809065"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Visual Basic ile Visual Studio 'da Windows Forms uygulaması oluşturma

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimi (UI) olan basit bir Visual Basic uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. Koyu tema kullanmıyorsanız, ancak isterseniz, nasıl yapılacağını öğrenmek için [Visual STUDIO IDE ve düzenleyici 'Yi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Visual Basic uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

1. Sol bölmedeki **Yeni proje** iletişim kutusunda, **Visual Basic**öğesini genişletin ve ardından **Windows Masaüstü**' nu seçin. Orta bölmede **Windows Forms uygulama (.NET Framework)** öğesini seçin. Sonra dosyayı adlandırın `HelloWorld` .

     **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **Yeni proje** iletişim kutusundan ve üst menü çubuğundan **Araçlar**  >  **Al araçlar ve Özellikler**' i seçin. Visual Studio Yükleyicisi başlatılır. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .NET Core iş yükü](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde Visual Basic Için **Windows Forms App (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz. Örneğin, arama kutusuna *Windows Forms uygulama* girin veya yazın. Ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **Windows** ' u seçin.)  

   ![Windows Forms uygulaması için Visual Basic şablonu seçin (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

Visual Basic proje şablonunuzu seçip Dosyanızı adlandırın, Visual Studio sizin için bir form açar. Form bir Windows kullanıcı arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

### <a name="add-a-button-to-the-form"></a>Forma Düğme Ekle

1. Araç **kutusu ' na** tıklayarak araç kutusu açılır penceresini açın.

     ![Araç kutusu penceresini açmak için araç kutusuna tıklayın](../ide/media/vb-toolbox-toolwindow.png)

     ( **Araç kutusu** açılır seçeneğini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için **View**  >  **araç kutusunu**görüntüleyin. Ya da **CTRL** + **alt** + **X**tuşlarına basın.)

1. **Araç kutusu** penceresini sabitlemek için **sabitle** simgesine tıklayın.

     ![Araç kutusu penceresini IDE 'ye sabitlemek için Sabitle simgesine tıklayın](../ide/media/vb-pin-the-toolbox-window.png)

1. **Düğme** denetimine tıklayın ve sonra form üzerine sürükleyin.

     ![Forma Düğme Ekle](../ide/media/vb-add-a-button-to-form1.png)

1. **Özellikler** penceresinin **Görünüm** bölümünde (veya **Fonts** bölümünde), yazın `Click this` ve ardından **ENTER**tuşuna basın.

     ![Formdaki düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     ( **Özellikler** penceresini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için **View**  >  **Özellikler penceresini**görüntüle ' ye tıklayın. Ya da **F4**tuşuna basın.)

1. **Özellikler** penceresinin **Tasarım** bölümünde, **button1** olarak adı değiştirin `btnClickThis` ve ardından **ENTER**tuşuna basın.

     ![Formdaki düğmeye bir işlev ekleyin](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > **Özellikler** penceresinde liste sıralama yaptıysanız, Button1 **(DataBindings)** bölümünde bunun yerine **button1** görüntülenir.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Bir eylem oluşturmak için bir düğme denetimi ekledik, artık metin göndermek için bir etiket denetimi ekleyelim.

1. **Araç kutusu** penceresinden **etiket** denetimini seçin ve sonra bu düğmenin altına sürükleyip bırakın ve sonra **Bu düğmeye tıklayın** .

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** bölümünde, **Label1** adını olarak değiştirin `lblHelloWorld` ve ardından **ENTER**tuşuna basın.

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1. vb &#91;tasarım&#93;** penceresinde, **Bu düğmeye tıklayarak** **Form1. vb** penceresini açın.

      (Alternatif olarak, **Çözüm Gezgini**içinde **Form1. vb** ' i genişletebilir ve ardından **Form1**' e tıklayabilirsiniz.)

1. **Form1. vb** penceresinde, **özel alt** ve **bitiş alt** çizgileri arasında, `lblHelloWorld.Text = "Hello World!"` aşağıdaki ekran görüntüsünde gösterildiği gibi yazın veya girin:

     ![Forma kod ekleme](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Başlat** düğmesine tıklayın.

     ![Hata ayıklamak ve uygulamayı çalıştırmak için Başlat 'a tıklayın](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey meydana gelir. Visual Studio IDE 'de, **Tanılama araçları** penceresi açılır ve bir **Çıkış** penceresi de açılır. Ancak IDE dışında bir **Form1** iletişim kutusu belirir. Bu düğme, **Bu düğmeye tıklayın** ve **Label1**belirten metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . **Label1** metninin **Merhaba Dünya!** olarak değiştiğine dikkat edin.

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Daha fazla Visual Basic öğretici](../get-started/visual-basic/index.yml)
* [C# öğreticileri](../get-started/csharp/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)