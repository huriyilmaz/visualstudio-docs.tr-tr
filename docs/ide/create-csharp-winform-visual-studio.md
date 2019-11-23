---
title: İle Windows Forms uygulama oluşturmaC#
description: Visual Studio 'da, adım adım ile C#Windows Forms uygulama oluşturmayı öğrenin.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4017ee2da040ccef36c58b17d896abab199c3517
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682146"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Visual Studio 'da ile Windows Forms uygulama oluşturmaC#

Visual Studio tümleşik geliştirme ortamına (IDE) bu kısa girişte, Windows tabanlı kullanıcı arabirimi (UI) olan C# basit bir uygulama oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yüklemek için sayfa.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, Git [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) ücretsiz yüklemek için sayfa.

> [!NOTE]
> Bu öğreticideki ekran görüntülerinin bazıları koyu temayı kullanır. Koyu tema kullanmayan ancak öğrenmek istiyorsanız [Düzenleyicisi ve Visual Studio IDE'yi kişiselleştirme](../ide/quickstart-personalize-the-ide.md) öğrenmek için sayfa nasıl.

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir C# uygulama projesi oluşturacaksınız. Proje türü bile herhangi bir şey ekledik önce ihtiyacınız olacak tüm şablon dosyaları ile birlikte gelir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin.

1. Sol bölmedeki **Yeni proje** iletişim kutusunda, **görsel C#** ' i genişletin ve ardından **Windows Masaüstü**' ne tıklayın. Orta bölmede seçin **Windows Forms uygulaması (.NET Framework)** . Dosya adı `HelloWorld`.

     Görmüyorsanız **Windows Forms uygulaması (.NET Framework)** proje şablonu, / İptal **yeni proje** iletişim kutusu ve üst menü çubuğundan seçin **Araçları**  >  **Araçları ve özellikleri Al**. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** iş yükü, ardından **Değiştir**.

     ![Visual Studio Yükleyicisi'nde .NET core iş yükü](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, Için C# **Windows Forms uygulama (.NET Framework)** şablonunu seçin.

   (İsterseniz, istediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz. Örneğin, arama kutusuna *Windows Forms uygulama* girin veya yazın. Ardından, dil **C#** listesinden seçin ve ardından platform listesinden **Windows** ' u seçin.)  

   ![Windows Forms uygulaması C# için şablonu seçin (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** Iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi'nde .NET core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-the-application"></a>Uygulama oluşturma

C# Proje şablonunuzu seçtikten ve dosyanızı adınızla, Visual Studio sizin için bir form açar. Bir Windows kullanıcı arabirimi biçimidir. Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacağız ve uygulamayı çalıştıracağız.

### <a name="add-a-button-to-the-form"></a>Forma bir düğme ekleyin

1. Araç **kutusu ' nu seçerek araç** kutusu açılır penceresini açın.

     ![Araç kutusu penceresini açmak için araç kutusunu seçin](../ide/media/csharp-toolbox-toolwindow.png)

     (Görmüyorsanız **araç kutusu** çıkış seçeneği açabilirsiniz, menü çubuğundan. Bunu yapmak için > **araç kutusunu** **görüntüleyin** . Veya basın **Ctrl**+**Alt**+**X**.)

1. **Araç kutusu** penceresini sabitlemek için **raptiye** simgesini seçin.

     ![Araç kutusu penceresini IDE 'ye sabitlemek için raptiye simgesini seçin](../ide/media/vb-pin-the-toolbox-window.png)

1. **Düğme** denetimini seçin ve ardından form üzerine sürükleyin.

     ![Forma bir düğme ekleyin](../ide/media/csharp-add-button-form1.png)

1. **Özellikler** penceresinde, **metin**bulun, **button1** ' den adı `Click this`değiştirin ve ardından **ENTER**tuşuna basın.

     ![Düğmeyi form üzerinde metin ekleme](../ide/media/vb-button-control-text.png)

     (Görmüyorsanız **özellikleri** penceresinde açabilirsiniz, menü çubuğundan. Bunu yapmak için > **Özellikler penceresini** **görüntüle** ' yi seçin. Veya basın **F4**.)

1. İçinde **tasarım** bölümünü **özellikleri** penceresinde adını değiştirmek **Button1** için `btnClickThis`ve tuşuna **Enter**.

     ![Düğmeyi form üzerinde bir işlev ekleme](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > **Özellikler** penceresinde liste sıralama yaptıysanız, Button1 **(DataBindings)** bölümünde bunun yerine **button1** görüntülenir.

### <a name="add-a-label-to-the-form"></a>Forma bir etiket ekleyin

Bir eylem oluşturmak için bir düğme denetimi ekledik, metni göndermek için bir etiket denetimi ekleyelim.

1. Seçin **etiket** denetimi **araç kutusu** pencere, form üzerine sürükleyin ve altındaki açılan **tıklatın** düğmesi.

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** bölümünde, **Label1** adını `lblHelloWorld`olarak değiştirin ve ardından **ENTER**tuşuna basın.

### <a name="add-code-to-the-form"></a>Forma kod ekleyin

1. **Form1.cs &#91;tasarım&#93;**  penceresinde **Bu düğmeye tıklayarak** **Form1.cs** penceresini açın.

      (Alternatif olarak, **Çözüm Gezgini**' de **Form1.cs** genişletebilir ve ardından **Form1**' i seçebilirsiniz.)

1. **Form1.cs** penceresinde, **özel void** satırından sonra, aşağıdaki ekran görüntüsünde gösterildiği gibi `lblHelloWorld.Text = "Hello World!";` yazın veya girin:

     ![Forma kod ekleyin](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Başlat** düğmesini seçin.

     ![Hata ayıklamak ve uygulamayı çalıştırmak için Başlat 'ı seçin](../ide/media/vb-click-start-hello-world.png)

   Birden fazla işlem gerçekleşir. Visual Studio IDE'de **tanılama araçları** penceresi açılır ve bir **çıkış** penceresi açılır, çok. Ancak IDE dışında bir **Form1** iletişim kutusu görüntülenir. Dahil edilir, **tıklatın** düğme ve metin bildiren **Label1**.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** . Dikkat **Label1** metin değişiklikleri **Merhaba Dünya!** .

    ![Label1 metin içeren bir Form1 iletişim kutusu ](../ide/media/vb-form1-dialog-hello-world.png)

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticiler](/visualstudio/get-started/csharp/)
* [Visual Basic öğreticileri](/visualstudio/get-started/visual-basic/)
* [C++izleyin](/cpp/get-started/tutorial-console-cpp)
