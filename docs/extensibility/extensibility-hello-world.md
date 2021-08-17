---
title: Merhaba Dünya uzantısı öğreticisi | Microsoft Docs
description: Proje oluşturmayı, komut eklemeyi ve kaynak kodu değiştirmeyi içeren Visual Studio uzantısı olarak yeni bir komut eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7ae5cb6712a872844685e167996f1d68c4771a40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063622"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Öğretici - İlk uzantınızı oluşturma: Merhaba Dünya

Bu Merhaba Dünya örnek, uygulama için ilk uzantınızı oluşturma Visual Studio. Bu öğreticide, uygulamanıza yeni bir komut Visual Studio.

Bu süreçte şunları yapmayı öğrenirsiniz:

* **[Genişletilebilirlik projesi oluşturma](#create-an-extensibility-project)**
* **[Özel komut ekleme](#add-a-custom-command)**
* **[Kaynak kodu değiştirme](#modify-the-source-code)**
* **[Çalıştırın](#run-it)**

Bu örnekte Visual C# kullanarak "Say Merhaba Dünya!" adlı özel bir menü düğmesi Merhaba Dünya. şu şekilde görünüyor:

![Merhaba Dünya komutu](media/hello-world-say-hello-world.png)

> [!NOTE]
> Bu makale, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Genişletilebilirlik için Mac için Visual Studio.](/visualstudio/mac/extending-visual-studio-mac-walkthrough)

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce ihtiyacınız olan VSIX şablonunu ve **Visual Studio** uzantısı geliştirme iş yükünü yüklemiş olduğundan emin olun.

> [!NOTE]
> Genişletilebilirlik projesi oluşturmak için Visual Studio (Community, Professional veya Enterprise) Visual Studio kullanabilirsiniz.

## <a name="create-an-extensibility-project"></a>Genişletilebilirlik projesi oluşturma

::: moniker range="vs-2017"

Adım 1. Dosya **menüsünden** Yeni **dosya'Project.**  >  

Adım 2. Sağ üstteki arama kutusuna "vsix" yazın ve Visual C# **VSIX Project.** İletişim kutusunun alt kısmında yer alan **Ad alanına** "HelloWorld" yazın ve Tamam'ı **seçin.**

![yeni proje](media/hello-world-new-project.png)

Şimdi veri kaynağı sayfasını Başlarken bazı örnek kaynakları görüyor gerekir.

Bu öğreticiden ayrılmanız ve geri dönmeniz gerekirse, yeni HelloWorld projenizi En Son bölümündeki **Başlangıç Sayfasında** **bulabilirsiniz.**

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. Dosya **menüsünden** Yeni **dosya'Project.**  >   "vsix" ifadesini arayın, Visual C# **VSIX** Project ve ardından Sonraki seçeneğini **seçin.**

Adım 2. Uygulama adı olarak "HelloWorld" **Project Oluştur'a** **seçin.**

![yeni proje](media/hello-world-new-project-2019.png)

Şimdi helloworld projesini içinde görüyor **Çözüm Gezgini.**

::: moniker-end

## <a name="add-a-custom-command"></a>Özel komut ekleme

Adım 1. *.vsixmanifest* bildirim dosyasını seçersiniz; açıklama, yazar ve sürüm gibi hangi seçeneklerin değiştirilebilir olduğunu seçebilirsiniz.

Adım 2. Projeye sağ tıklayın (çözüme değil). Bağlam menüsünde Ekle'yi **ve ardından** Yeni Öğe'yi **seçin.**

3. Adım **Genişletilebilirlik bölümünü ve** ardından Komut'ı **seçin.**

4. Adım: Alttaki **Ad** alanına *Command.cs* gibi bir dosya adı girin.

![özel komut](media/hello-world-vsix-command.png)

Yeni komut dosyanız dosyasında **Çözüm Gezgini.** Kaynaklar **düğümü** altında komutunuzla ilgili diğer dosyaları bulabilirsiniz. Örneğin, görüntüyü değiştirmek isterseniz PNG dosyası buradadır.

## <a name="modify-the-source-code"></a>Kaynak kodu değiştirme

Bu noktada, komut ve Düğme metni otomatik olarak ojendir ve pek ilgi çekici değildir. Değişiklik yapmak için VSCT dosyasını ve CS dosyasını değiştirebilirsiniz.

* VSCT dosyası, komutlarınızı yeniden adlandırabilirsiniz ve komut sisteminde nereye Visual Studio tanımlayabilirsiniz. VSCT dosyasını keşfederken, VSCT kod denetimlerinin her bir bölümünü açıklayan açıklamalar fark edersiniz.

* CS dosyası, tıklama işleyicisi gibi eylemleri tanımladığınız dosyadır.

::: moniker range="vs-2017"

Adım 1. Bu **Çözüm Gezgini** yeni komutunuz için VSCT dosyasını bulun. Bu durumda, *CommandPackage.vsct olarak çağrılır.*

![komut paketi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. Bu **Çözüm Gezgini,** uzantı VS paketinizin VSCT dosyasını bulun. Bu durumda *HelloWorldPackage.vsct olarak çağrılır.*

::: moniker-end

Adım 2. parametresini `ButtonText` olarak `Say Hello World!` değiştirme.

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

3. Adım Geri dön komutu **Çözüm Gezgini** *Command.cs dosyasını* bulun. yönteminde `Execute` dizesini olarak `message` `string.Format(..)` `Hello World!` değiştirebilirsiniz.

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

Her dosyada yaptığınız değişiklikleri kaydetmeyi emin olun.

## <a name="run-it"></a>Çalıştırın

Artık kaynak kodu Deneysel Örnekte Visual Studio çalıştırabilirsiniz.

Adım 1. Hata **Ayıklamayı Başlat** komutunu çalıştırmak için F5 **tuşuna** basın. Bu komut projenizi derlemek ve deneysel örneği adlı yeni bir Visual Studio başlatarak hata **ayıklayıcısını başlatır.**

::: moniker range="vs-2017"

Deneysel Örnek **sözcüklerini başlık** çubuğunda Visual Studio görüyorsunuz.

![deneysel örnek başlık çubuğu](media/hello-world-exp-instance.png)

::: moniker-end

Adım 2. Deneysel Örneğin **Araçlar** menüsünde **Say** **Merhaba Dünya!**.

![son sonuç](media/hello-world-final-result.png)

Yeni özel komutun çıkışını görüyor gerekir. Bu durumda, ekranın merkezinde size özel komut **Merhaba Dünya!** iletisi döndürmektedir.

## <a name="next-steps"></a>Sonraki adımlar

Artık Genişletilebilirlik ve Genişletilebilirlik ile Visual Studio temel bilgilerine sahip olduğunuza göre, burada daha fazla bilgi veresiniz:

* [Uzantılar geliştirmeye Visual Studio -](starting-to-develop-visual-studio-extensions.md) Örnekler, öğreticiler. ve uzantınızı yayımlama
* [Visual Studio 2017 SDK'sı - 2017'de](what-s-new-in-the-visual-studio-2017-sdk.md) yeni Visual Studio özellikleri
* [Visual Studio 2019 SDK'sı](whats-new-visual-studio-2019-sdk.md) - Visual Studio 2019'daki yeni genişletilebilirlik özellikleri
* [Visual Studio SDK'sı](internals/inside-the-visual-studio-sdk.md) içinde - Genişletilebilirlik Visual Studio öğrenin
