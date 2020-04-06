---
title: Merhaba Dünya uzantısı öğretici | Microsoft Dokümanlar
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711659"
---
# <a name="create-your-first-extension-hello-world"></a>İlk uzantınızı oluşturun: Hello World

Bu Hello World örneği Visual Studio için ilk uzantısı oluşturma yoluyla size yol. Bu öğretici, Visual Studio'ya nasıl yeni bir komut ekleyeceğinizi gösterir.

Bu süreçte, nasıl öğreneceksiniz:

* **[Genişletilebilirlik projesi oluşturma](#create-an-extensibility-project)**
* **[Özel komut ekleme](#add-a-custom-command)**
* **[Kaynak kodu değiştirme](#modify-the-source-code)**
* **[Çalıştırın](#run-it)**

Bu örnekiçin, "Merhaba Dünya Deyin!" adlı özel bir menü düğmesi eklemek için Visual C# öğesi kullanırsınız. bu gibi görünüyor:

![Merhaba Dünya komutu](media/hello-world-say-hello-world.png)

> [!NOTE]
> Bu makale, Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio [için, Mac için Visual Studio'da Genişletilebilirlik walkthrough](/visualstudio/mac/extending-visual-studio-mac-walkthrough)bakın.

## <a name="prerequisites"></a>Ön koşullar

Başlamadan önce, gereksinim duyduğunuz VSIX şablonu ve örnek kodu içeren **Visual Studio uzantı geliştirme** iş yükünü yüklediğinizden emin olun.

> [!NOTE]
> Visual Studio'nun (Topluluk, Profesyonel veya Kurumsal) herhangi bir sürümünü visual studio genişletilebilirlik projesi oluşturmak için kullanabilirsiniz.

## <a name="create-an-extensibility-project"></a>Genişletilebilirlik projesi oluşturma

::: moniker range="vs-2017"

1. Adım. **Dosya** menüsünden **Yeni** > **Proje'yi**seçin.

2. Adım Sağ üstteki arama kutusuna "vsix" yazın ve Visual C# **VSIX Project'i**seçin. İletişim kutusunun altındaki **Ad** için "HelloWorld" girin ve **Tamam'ı**seçin.

![yeni proje](media/hello-world-new-project.png)

Şimdi Başlarken sayfasını ve bazı örnek kaynakları görmeniz gerekir.

Bu öğreticiyi bırakıp ona geri dönmeniz gerekiyorsa, yeni HelloWorld projenizi Başlangıç **Sayfasında** **son** bölümde bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Adım. **Dosya** menüsünden **Yeni** > **Proje'yi**seçin. "vsix" için arama ve Visual C# **VSIX Project** ve sonra **Sonraki**seçin.

2. Adım **Proje adı** için "HelloWorld" girin ve **Oluştur'u**seçin.

![yeni proje](media/hello-world-new-project-2019.png)

Şimdi **Solution Explorer**HelloWorld proje görmelisiniz.

::: moniker-end

## <a name="add-a-custom-command"></a>Özel komut ekleme

1. Adım. *.vsixmanifest* bildirim dosyasını seçerseniz, açıklama, yazar ve sürüm gibi hangi seçeneklerin değiştirilebilir olduğunu görebilirsiniz.

2. Adım Projeyi sağ tıklatın (çözüm edeğil). Bağlam menüsünde **Ekle**ve ardından **Yeni Öğe'yi**seçin.

3. Adım **Genişletilebilirlik** bölümünü seçin ve ardından **Komut'u**seçin.

4. Adım. Alttaki **Ad** alanına *Command.cs*gibi bir dosya adı girin.

![özel komut](media/hello-world-vsix-command.png)

Yeni komut dosyanız **Çözüm Gezgini'nde**görünür. **Kaynaklar** düğümü altında, komutunuzun diğer dosyalarını bulabilirsiniz. Örneğin, görüntüyü değiştirmek isterseniz, PNG dosyası buradadır.

## <a name="modify-the-source-code"></a>Kaynak kodu değiştirme

Bu noktada, komut ve Düğme metni otomatik olarak oluşturulur ve çok ilginç değildir. Değişiklik yapmak istiyorsanız VSCT dosyasını ve CS dosyasını değiştirebilirsiniz.

* VSCT dosyası, komutlarınızı yeniden adlandırabileceğiniz ve Visual Studio komut sisteminde nereye gittiklerini tanımlayabileceğiniz yerdir. VSCT dosyasını incelerken, VSCT kodunun her bölümünün neyi kontrol ettiğini açıklayan yorumlar fark edeceksiniz.

* CS dosyası, tıklama işleyicisi gibi eylemleri tanımlayabileceğiniz yerdir.

::: moniker range="vs-2017"

1. Adım. **Çözüm Gezgini'nde,** yeni komutunuzun VSCT dosyasını bulun. Bu durumda, *CommandPackage.vsct*olarak adlandırılacaktır.

![komut paketi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Adım. **Çözüm Gezgini'nde,** uzantı VS paketiniz için VSCT dosyasını bulun. Bu durumda, *HelloWorldPackage.vsct*çağrılacak.

::: moniker-end

2. Adım Parametreyi `ButtonText` `Say Hello World!`' ile değiştirme

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

3. Adım **Solution Explorer'a** geri dön ve *Command.cs* dosyasını bulun. `Execute` Yöntemde, dizeyi `message` `string.Format(..)` ' `Hello World!`den ' e değiştirin

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Değişikliklerinizi her dosyaya kaydettiğinizden emin olun.

## <a name="run-it"></a>Çalıştırın

Artık Kaynak Kodunu Visual Studio Deneme Örneği'nde çalıştırabilirsiniz.

1. Adım. **Başlangıç Hata Ayıklama** komutunu çalıştırmak için **F5** tuşuna basın. Bu komut projenizi oluşturur ve hata ayıklama yı başlatır, Visual Studio'nun **Deneysel Örnek**adlı yeni bir örneğini başlatın.

::: moniker range="vs-2017"

Visual Studio başlık çubuğunda **Deneysel Örnek** sözcüklerini göreceksiniz.

![deneysel örnek başlık çubuğu](media/hello-world-exp-instance.png)

::: moniker-end

2. Adım **Deneysel Örnek** **Araçlar** menüsünde, **Merhaba Dünya Deyin'i tıklatın!**

![nihai sonuç](media/hello-world-final-result.png)

Yeni özel komutunuzdan çıktıyı görmelisiniz, bu durumda ekranın ortasında size Merhaba Dünya'yı veren iletişim **kutusu!** iletisi döndürmektedir.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio Extensibility ile çalışmanın temellerini bildiğinize göre, burada daha fazla bilgi edinebilirsiniz:

* [Visual Studio uzantıları geliştirmeye başlayın](starting-to-develop-visual-studio-extensions.md) - Örnekler, öğreticiler. ve uzantınızı yayınlama
* [Visual Studio 2017 SDK'daki yenilikler](what-s-new-in-the-visual-studio-2017-sdk.md) - Visual Studio 2017'de yeni genişletilebilirlik özellikleri
* [Visual Studio 2019 SDK'daki yenilikler](whats-new-visual-studio-2019-sdk.md) - Visual Studio 2019'da yeni genişletilebilirlik özellikleri
* [Inside the Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) - Visual Studio Extensibility ayrıntılarını öğrenin
