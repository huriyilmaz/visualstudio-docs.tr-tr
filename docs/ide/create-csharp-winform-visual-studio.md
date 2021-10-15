---
title: 'C ile Windows Forms uygulama oluşturma #'
description: C# ile Visual Studio bir Windows Forms uygulamasının nasıl oluşturulduğunu adım adım öğrenin.
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
ms.openlocfilehash: 282dd4fb2fc1f3f68d3f4c4b6b5d5d0b17f5e947
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130011425"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>C ile Visual Studio Windows Forms uygulama oluşturma\#

Visual Studio tümleşik geliştirme ortamına (ıde) bu kısa girişte, Windows tabanlı kullanıcı arabirimi (uı) olan basit bir C# uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio henüz yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) sayfasına bakın.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturacaksınız. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual C#**' ı genişletin ve ardından **Windows masaüstü**' ne tıklayın. orta bölmede **Windows Forms uygulama (.NET Framework)** öğesini seçin. Sonra dosyayı adlandırın `HelloWorld` .

     **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusundan ve üst menü çubuğundan **araçlar**  >  **al araçlar ve özellikler**' i seçin. Visual Studio Yükleyicisi başlatılır. **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

     ![Visual Studio Yükleyicisi .net Core iş yükü](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde C# için **Windows Forms App (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz. örneğin, arama kutusuna *Windows Forms uygulama* girin veya yazın. ardından, dil listesinden **C#** öğesini seçin ve ardından Platform listesinden **Windows** öğesini seçin.)  

   ![Windows Forms uygulaması için C# şablonunu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

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

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

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

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)