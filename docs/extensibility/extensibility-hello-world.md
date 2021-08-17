---
title: Merhaba Dünya uzantısı öğreticisi | Microsoft Docs
description: bir proje oluşturmayı, komut eklemeyi ve kaynak kodu değiştirmeyi içeren Visual Studio bir uzantı olarak yeni bir komut eklemeyi öğrenin.
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
ms.openlocfilehash: c53e0312de7d687c761546c0d5bd5d125665744fd6b78b71531a2eff749950f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376991"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Öğretici-ilk uzantınızı oluşturun: Merhaba Dünya

Bu Merhaba Dünya örnek, Visual Studio için ilk uzantınızı oluşturma konusunda size yol gösterir. Bu öğreticide, Visual Studio için nasıl yeni bir komut ekleyeceğiniz gösterilmektedir.

İşlemde şunları yapmayı öğreneceksiniz:

* **[Genişletilebilirlik projesi oluşturma](#create-an-extensibility-project)**
* **[Özel komut ekleme](#add-a-custom-command)**
* **[Kaynak kodunu değiştirme](#modify-the-source-code)**
* **[Çalıştırın](#run-it)**

Bu örnekte, "deyin Merhaba Dünya!" adlı özel bir menü düğmesi eklemek Için Visual C# kullanacaksınız şöyle görünür:

![Merhaba Dünya komutu](media/hello-world-say-hello-world.png)

> [!NOTE]
> bu makale Windows Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio genişletilebilirlik](/visualstudio/mac/extending-visual-studio-mac-walkthrough)kılavuzu.

## <a name="prerequisites"></a>Önkoşullar

başlamadan önce, ihtiyacınız olan vsıx şablonunu ve örnek kodu içeren **Visual Studio uzantısı geliştirme** iş yükünü yüklediğinizden emin olun.

> [!NOTE]
> bir Visual Studio genişletilebilirlik projesi oluşturmak için Visual Studio herhangi bir sürümünü (Community, Professional veya Enterprise) kullanabilirsiniz.

## <a name="create-an-extensibility-project"></a>Genişletilebilirlik projesi oluşturma

::: moniker range="vs-2017"

Adım 1. **dosya** menüsünden **yeni**  >  **Project**' yi seçin.

Adım 2. Sağ üst köşedeki arama kutusuna "VSIX" yazın ve Visual C# **vsıx Project** seçin. İletişim kutusunun alt kısmındaki **ad** Için "HelloWorld" yazın ve **Tamam**' ı seçin.

![Yeni proje](media/hello-world-new-project.png)

Artık başlangıç sayfasını ve bazı örnek kaynakları görmeniz gerekir.

Bu öğreticiyi bırakmanız ve geri dönebilmeniz gerekiyorsa, yeni HelloWorld projenizi **son** bölümdeki **başlangıç sayfasından** bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. **dosya** menüsünden **yeni**  >  **Project**' yi seçin. "vsıx" araması yapın ve Visual C# **vsıx Project** seçin ve ardından **ileri**' ye tıklayın.

Adım 2. **Project adı** için "HelloWorld" girin ve **oluştur**' u seçin.

![Yeni proje](media/hello-world-new-project-2019.png)

Artık **Çözüm Gezgini**' de HelloWorld projesini görmeniz gerekir.

::: moniker-end

## <a name="add-a-custom-command"></a>Özel komut ekleme

Adım 1. *. Valtmanifest* bildirim dosyasını seçerseniz, açıklama, yazar ve sürüm gibi hangi seçeneklerin değiştirilebilir olduğunu görebilirsiniz.

Adım 2. Projeye sağ tıklayın (çözüme değil). Bağlam menüsünde **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

3. Adım **Genişletilebilirlik** bölümünü ve ardından **komut** öğesini seçin.

4. Adım: Alttaki **ad** alanına *Command. cs* gibi bir dosya adı girin.

![özel komut](media/hello-world-vsix-command.png)

Yeni komut dosyanız **Çözüm Gezgini** görünür. **Kaynaklar** düğümü altında komutlarınızla ilgili diğer dosyaları bulacaksınız. Örneğin, görüntüyü değiştirmek istiyorsanız PNG dosyası burada bulunur.

## <a name="modify-the-source-code"></a>Kaynak kodunu değiştirme

Bu noktada, komut ve düğme metni otomatik olarak oluşturulur ve çok ilginç değildir. Değişiklik yapmak istiyorsanız VSCT dosyasını ve CS dosyasını değiştirebilirsiniz.

* vsct dosyası, komutlarınızı yeniden adlandırabileceğiniz ve Visual Studio komut sisteminde nereye gittikleri de tanımlayabileceğiniz yerdir. VSCT dosyasını keşfederken, VSCT Code denetimlerinin her bir bölümünü açıklayan açıklamalar görürsünüz.

* CS dosyası, tıklama işleyicisi gibi eylemleri tanımlayabileceğiniz yerdir.

::: moniker range="vs-2017"

Adım 1. **Çözüm Gezgini**' de, yeni komutunuz IÇIN vsct dosyasını bulun. Bu durumda, *Commandpackage. vsct* olarak adlandırılacaktır.

![komut paketi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. **Çözüm Gezgini**' de, uzantı vs paketinizin vsct dosyasını bulun. Bu durumda, *Merhaba Dünya Package. vsct* olarak adlandırılacaktır.

::: moniker-end

Adım 2. `ButtonText`Parametresini olarak değiştirin `Say Hello World!` .

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

3. Adım **Çözüm Gezgini** dönün ve *Command. cs* dosyasını bulun. Yönteminde, `Execute` dizesini `message` `string.Format(..)` olarak değiştirin `Hello World!` .

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

artık Visual Studio deneysel örneğinde kaynak kodu çalıştırabilirsiniz.

Adım 1. **Hata ayıklamayı Başlat** komutunu çalıştırmak için **F5** tuşuna basın. bu komut, projenizi oluşturur ve **deneysel örnek** olarak adlandırılan Visual Studio yeni bir örneğini başlatarak hata ayıklayıcıyı başlatır.

::: moniker range="vs-2017"

Visual Studio başlık çubuğunda **deneysel örnek** sözcüklerini görürsünüz.

![deneysel örnek başlık çubuğu](media/hello-world-exp-instance.png)

::: moniker-end

Adım 2. **Deneysel örneğin** **araçlar** menüsünde **deyin Merhaba Dünya!**' e tıklayın.

![nihai sonuç](media/hello-world-final-result.png)

Yeni özel komutınızdan çıktıyı görmeniz gerekir, bu durumda **Merhaba Dünya** size sunan ekranın merkezindeki iletişim kutusu. iletisi döndürmektedir.

## <a name="next-steps"></a>Sonraki adımlar

artık Visual Studio genişletilebilirlik ile çalışmanın temellerini öğrenmiş olduğunuza göre buradan daha fazla bilgi edinebilirsiniz:

* [Visual Studio uzantıları geliştirmeye başlayın](starting-to-develop-visual-studio-extensions.md) -örnekler, öğreticiler. ve uzantınızı yayımlama
* [Visual Studio 2017 SDK 'daki](what-s-new-in-the-visual-studio-2017-sdk.md) yenilikler-Visual Studio 2017 ' deki yeni genişletilebilirlik özellikleri
* [Visual Studio 2019 SDK 'daki](whats-new-visual-studio-2019-sdk.md) yenilikler-Visual Studio 2019 ' deki yeni genişletilebilirlik özellikleri
* [Visual Studio SDK 'nın içinde](internals/inside-the-visual-studio-sdk.md) -Visual Studio genişletilebilirliği ayrıntılarını öğrenin
