---
title: 'öğretici: Visual Basic Windows Forms uygulama oluşturma'
description: bu öğreticide, Visual Basic ile Visual Studio Windows Forms uygulama oluşturmayı öğrenin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.workload:
- multiple
dev_langs:
- VB
ms.date: 01/07/2022
ms.custom: vs-acquisition, get-started
ms.openlocfilehash: 86c0f162662c98383ba849db4ae78313143f8480
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650463"
---
# <a name="tutorial-create-a-winforms-app-with-visual-basic"></a>Öğretici: Visual Basic bir WinForms uygulaması oluşturma

bu öğreticide, Windows Forms kullanıcı arabirimine sahip bir Visual Basic uygulaması oluşturacaksınız.
Visual Studio tümleşik geliştirme ortamı (ıde), bir Windows Forms uygulaması oluşturmak için ihtiyacınız olan tüm araçları içerir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> - Proje oluşturma
> - Forma Düğme Ekle
> - Etiket ve kod ekleme
> - Uygulamayı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ziyaret edin.
::: moniker-end
::: moniker range="vs-2019"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/) ziyaret edin.
::: moniker-end
::: moniker range=">=vs-2022"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/downloads) ziyaret edin.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Visual Basic bir uygulama projesi oluşturun.
Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce.

::: moniker range="vs-2017"
1. Visual Studio 2017'yi açın.

1. üstteki menüden **dosya** > **yeni** > **Project**' yi seçin.

1. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual Basic**' i genişletin ve ardından **Windows masaüstü**' nü seçin.
   orta bölmede **Windows Forms uygulama (.NET Framework)** öğesini seçin. Sonra dosyayı adlandırın `HelloWorldApp` .

   ![ekran görüntüsü Visual Studio Yükleyicisi seçili .net Core iş yükünü gösterir.](../ide/media/install-dot-net-desktop-env.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** proje şablonunu görmüyorsanız, **yeni Project** iletişim kutusunu iptal edin.
   > Araçlar   >  **ve Özellikler Al ' ı** seçin.
   > Visual Studio Yükleyicisi başlatılır.
   > **.Net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

::: moniker-end

::: moniker range="vs-2019"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![ekran görüntüsünde yeni proje oluştur seçiliyken Visual Studio 2019 başlangıç penceresi gösterilir.](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin.

   İstediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz.
   örneğin, arama kutusuna *Windows Forms uygulaması* girin.
   ardından, **dil** listesinden **Visual Basic** ' yi seçin ve ardından **Platform** listesinden **Windows** .  

   ![ekran görüntüsü Windows Forms App (.NET Framework) seçiliyken yeni proje oluştur penceresini gösterir.](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz.
   > **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![Ekran görüntüsü ' daha fazla araç ve özellik yükler ' bağlantısının ' ' aradığınızı bulmuyor ' iletisini gösterir.](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > ![ekran görüntüsü Visual Studio Yükleyicisi seçili .net Core iş yükünü gösterir.](../ide/media/install-dot-net-desktop-env.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** ' i seçin. İşinizi kaydetmeniz istenebilir.

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** olarak *HelloWorld* girin. Ardından **Oluştur**’u seçin.

   ![Ekran görüntüsü, yeni projeyi HelloWorld adlı adı ile yapılandırma ' yı gösterir.](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![ekran görüntüsünde yeni proje oluştur seçiliyken Visual Studio 2022 başlangıç penceresi gösterilir.](../get-started/media/vs-2022/create-new-project.png)

1. **yeni proje oluştur** penceresinde Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin.

   İstediğiniz şablona hızlıca ulaşmak için aramanızı iyileştirebilirsiniz.
   örneğin, arama kutusuna *Windows Forms uygulaması* girin.
   ardından, **dil** listesinden **Visual Basic** ' yi seçin ve ardından **Platform** listesinden **Windows** .  

   ![ekran görüntüsü Windows Forms App (.NET Framework) seçiliyken yeni proje oluştur penceresini gösterir.](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz.
   > **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![Ekran görüntüsü ' daha fazla araç ve özellik yükler ' bağlantısının ' ' aradığınızı bulmuyor ' iletisini gösterir.](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > ![ekran görüntüsü Visual Studio Yükleyicisi seçili .net Core iş yükünü gösterir.](../ide/media/install-dot-net-desktop-env.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** ' i seçin. İşinizi kaydetmeniz istenebilir.

1. **yeni projenizi yapılandırın** penceresinde, **Project adı** olarak *HelloWorld* girin. Ardından **Oluştur**’u seçin.

   ![Ekran görüntüsü, yeni projeyi HelloWorld adlı adı ile yapılandırma ' yı gösterir.](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="add-a-button-to-the-form"></a>Forma Düğme Ekle

Visual Basic proje şablonunuzu seçip dosyanızı verdikten sonra, Visual Studio sizin için bir form açar.
form, Windows bir kullanıcı arabirimidir.
Forma denetimler ekleyerek bir "Merhaba Dünya" uygulaması oluşturacaksınız.

1. Visual Studio ıde 'nin sol tarafında **araç kutusu** sekmesini seçin. Bunu görmüyorsanız,  > menü çubuğundan veya **CTRL** alt X ' ten Görünüm **araç kutusunu** seçin +  + .

   ![Ekran görüntüsü araç kutusu penceresini açan araç kutusu sekmesini gösterir.](media/create-a-visual-basic-winform-in-visual-studio/toolbox-tab.png)

   İsterseniz, **araç kutusu** penceresini sabitlemek için **sabitle** simgesini seçin.

1. **Düğme** denetimini seçip form üzerine sürükleyin.

   ![Ekran görüntüsü, forma eklenen düğme denetimini gösterir.](media/create-a-visual-basic-winform-in-visual-studio/toolbox-button-form.png)

1. **Özellikler** penceresinin **Görünüm** bölümünde **metin** Için, buraya *tıklayın* ve ardından **ENTER** tuşuna basın.

   ![Ekran görüntüsü metin özelliğini bu değere tıklamada gösterir.](media/create-a-visual-basic-winform-in-visual-studio/button-text-property.png)

   **Özellikler** penceresini görmüyorsanız, menüyü menü çubuğundan açabilirsiniz. Özellikleri **görüntüle**  >  **penceresini** seçin veya **F4** tuşuna basın.

1. **Özellikler** penceresinin **Tasarım** bölümünde, **button1** *olarak adı ve sonra da* **ENTER** tuşuna basın.

   ![Ekran görüntüsünde Name özelliği b t değeri ile gösterilir.](media/create-a-visual-basic-winform-in-visual-studio/button-name-property.png)

   > [!NOTE]
   > **Özellikler** penceresinde liste sıralama yaptıysanız, Button1 **(DataBindings)** bölümünde bunun yerine **button1** görüntülenir.

## <a name="add-a-label-and-code"></a>Etiket ve kod ekleme

Artık bir eylem oluşturmak için bir düğme denetimi eklemişseniz, metin göndermek için bir etiket denetimi ekleyin.

1. **Araç kutusu** penceresinde **etiket** denetimini seçin ve ardından form üzerine sürükleyin.
   Buraya **tıklayarak bu düğmeye tıklayın** .

1. **Özellikler** penceresinin **Tasarım** bölümünde veya **(DataBindings)** bölümünde, **Label1** adını *lblhelloworld* olarak değiştirin ve ardından **ENTER** tuşuna basın.

1. **Form1. vb &#91;tasarım&#93;** penceresinde, **Bu düğmeye tıklayarak** **Form1. vb** penceresini açın.

   Diğer bir seçenek de Çözüm Gezgini **Form1. vb** ' i genişletmenizi ve ardından **Form1**' i seçmenizi sağlar.

1. **Form1. vb** penceresinde, **özel alt** ve **bitiş alt** çizgileri arasında *lblhelloworld. Text = "Merhaba Dünya!"* yazın Aşağıdaki ekran görüntüsünde gösterildiği gibi:

     ![ekran görüntüsü, Visual Basic kod ekleyebileceğiniz Form1. vs sekmesinde bir sınıfı gösterir.](media/create-a-visual-basic-winform-in-visual-studio/click-handle-code-visual-basic.png)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamanız derlemek ve çalıştırmak için hazırlayın.

1. Uygulamayı çalıştırmak için **Başlat** ' ı seçin.

   ![Ekran görüntüsünde, uygulamanızı çalıştıran Başlat düğmesi gösterilir.](media/create-a-visual-basic-winform-in-visual-studio/visual-studio-start-debug.png)

   Birkaç şey meydana gelir.
   Visual Studio ıde 'de, **tanılama araçları** penceresi açılır ve bir **çıkış** penceresi açılır.
   IDE dışında bir **Form1** iletişim kutusu belirir.
   **Bu** düğme ve **Label1** görüntülenen metni içerir.

1. **Form1** iletişim kutusunda **Bu düğmeye tıklayın** .

   ![Ekran görüntüsünde Merhaba Dünya metin görüntüleyen form 1 başlıklı iletişim kutusu gösterilir!](media/create-a-visual-basic-winform-in-visual-studio/visual-studio-dialog-hello-world.png)

   **Label1** metni **Merhaba Dünya!** olarak değişir.

1. Uygulamayı çalıştırmayı durdurmak için **Form1** iletişim kutusunu kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Windows Forms hakkında daha fazla bilgi edinmek için aşağıdaki öğreticiye geçin:

> [!div class="nextstepaction"]
> [Öğretici: resim görüntüleyici oluşturma](tutorial-windows-forms-picture-viewer-layout.md)

## <a name="see-also"></a>Ayrıca bkz.

* [daha fazla Visual Basic öğretici](../get-started/visual-basic/index.yml)
* [C# öğreticileri](../get-started/csharp/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)
