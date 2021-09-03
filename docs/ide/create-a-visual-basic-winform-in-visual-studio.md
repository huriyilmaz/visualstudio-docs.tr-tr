---
title: Visual Basic Windows Forms uygulama oluşturma
description: Visual Basic, adım adım Visual Studio Windows Forms uygulama oluşturmayı öğrenin.
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
ms.openlocfilehash: ba22da795a0a94033d252f82a48989b3c24f22e8
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398645"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Visual Basic ile Visual Studio Windows Forms uygulama oluşturma

Visual Studio tümleşik geliştirme ortamına (ıde) bu kısa giriş bölümünde Windows tabanlı kullanıcı arabirimi (uı) olan basit bir Visual Basic uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio henüz yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir Visual Basic uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual Basic**' i genişletin ve ardından **Windows masaüstü**' ne tıklayın. orta bölmede **Windows Forms uygulama (.NET Framework)** öğesini seçin. Sonra dosyayı adlandırın `HelloWorld` .

     **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusundan ve üst menü çubuğundan **araçlar**  >  **al araçlar ve özellikler**' i seçin. Visual Studio Yükleyicisi başlatılır. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .net Core iş yükü](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz. örneğin, arama kutusuna *Windows Forms uygulama* girin veya yazın. ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından Platform listesinden **Windows** ' ı seçin.)  

   ![Windows Forms uygulaması için Visual Basic şablonu seçin (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

Visual Basic proje şablonunuzu seçip dosyanızı verdikten sonra, Visual Studio sizin için bir form açar. form, Windows bir kullanıcı arabirimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

### <a name="add-a-button-to-the-form"></a>Forma Düğme Ekle

1. Araç **kutusu ' na** tıklayarak araç kutusu açılır penceresini açın.

     ![Araç kutusu penceresini açmak için araç kutusuna tıklayın](../ide/media/vb-toolbox-toolwindow.png)

     ( **Araç kutusu** açılır seçeneğini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için   >  **araç kutusunu** görüntüleyin. Ya da **CTRL** + **alt** + **X** tuşlarına basın.)

1. **Araç kutusu** penceresini sabitlemek için **sabitle** simgesine tıklayın.

     ![Araç kutusu penceresini IDE 'ye sabitlemek için Sabitle simgesine tıklayın](../ide/media/vb-pin-the-toolbox-window.png)

1. **Düğme** denetimine tıklayın ve sonra form üzerine sürükleyin.

     ![Forma Düğme Ekle](../ide/media/vb-add-a-button-to-form1.png)

1. **Özellikler** penceresinin **Görünüm** bölümünde (veya **Fonts** bölümünde), yazın `Click this` ve ardından **ENTER** tuşuna basın.

     ![Formdaki düğmeye metin ekleme](../ide/media/vb-button-control-text.png)

     ( **Özellikler** penceresini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Bunu yapmak için   >  **Özellikler penceresini** görüntüle ' ye tıklayın. Ya da **F4** tuşuna basın.)

1. **Özellikler** penceresinin **Tasarım** bölümünde, **button1** olarak adı değiştirin `btnClickThis` ve ardından **ENTER** tuşuna basın.

     ![Formdaki düğmeye bir işlev ekleyin](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > **Özellikler** penceresinde liste sıralama yaptıysanız, Button1 **(DataBindings)** bölümünde bunun yerine **button1** görüntülenir.

### <a name="add-a-label-to-the-form"></a>Forma etiket ekleme

Bir eylem oluşturmak için bir düğme denetimi ekledik, artık metin göndermek için bir etiket denetimi ekleyelim.

1. **Araç kutusu** penceresinden **etiket** denetimini seçin ve sonra bu düğmenin altına sürükleyip bırakın ve sonra **Bu düğmeye tıklayın** .

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** bölümünde, **Label1** adını olarak değiştirin `lblHelloWorld` ve ardından **ENTER** tuşuna basın.

### <a name="add-code-to-the-form"></a>Forma kod ekleme

1. **Form1. vb &#91;tasarım&#93;** penceresinde, **Bu düğmeye tıklayarak** **Form1. vb** penceresini açın.

      (Alternatif olarak, **Çözüm Gezgini** içinde **Form1. vb** ' i genişletebilir ve ardından **Form1**' e tıklayabilirsiniz.)

1. **Form1. vb** penceresinde, **özel alt** ve **bitiş alt** çizgileri arasında, `lblHelloWorld.Text = "Hello World!"` aşağıdaki ekran görüntüsünde gösterildiği gibi yazın veya girin:

     ![Forma kod ekleme](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Başlat** düğmesine tıklayın.

     ![Hata ayıklamak ve uygulamayı çalıştırmak için Başlat 'a tıklayın](../ide/media/vb-click-start-hello-world.png)

   Birkaç şey meydana gelir. Visual Studio ıde 'de, **tanılama araçları** penceresi açılır ve bir **çıkış** penceresi de açılır. Ancak IDE dışında bir **Form1** iletişim kutusu belirir. Bu düğme, **Bu düğmeye tıklayın** ve **Label1** belirten metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . **Label1** metninin **Merhaba Dünya!** olarak değiştiğine dikkat edin.

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [daha fazla Visual Basic öğretici](../get-started/visual-basic/index.yml)
* [C# öğreticileri](../get-started/csharp/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)