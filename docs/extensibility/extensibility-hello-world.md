---
title: Merhaba Dünya uzantısı öğreticisi | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404131"
---
# <a name="create-your-first-extension-hello-world"></a>İlk uzantınızı oluşturun: Merhaba Dünya

Bu Merhaba Dünya örnek, Visual Studio için ilk uzantınızı oluşturma konusunda size yol gösterir. Bu öğreticide, Visual Studio 'ya nasıl yeni bir komut ekleyeceğiniz gösterilmektedir.

İşlemde şunları yapmayı öğreneceksiniz:

* **[Genişletilebilirlik projesi oluşturma](#create-an-extensibility-project)**
* **[Özel komut ekleme](#add-a-custom-command)**
* **[Kaynak kodunu değiştirme](#modify-the-source-code)**
* **[Çalıştır](#run-it)**

Bu örnekte, "deyin Merhaba Dünya!" C# adlı özel bir menü düğmesi eklemek için görseli kullanacaksınız şöyle görünür:

![Merhaba Dünya komutu](media/hello-world-say-hello-world.png)

> [!NOTE]
> Bu makale Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio genişletilebilirlik](/visualstudio/mac/extending-visual-studio-mac-walkthrough)Kılavuzu.

## <a name="prerequisites"></a>Prerequisites

Başlamadan önce, ihtiyacınız olan VSıX şablonunu ve örnek kodu içeren **Visual Studio uzantısı geliştirme** iş yükünü yüklediğinizden emin olun.

> [!NOTE]
> Visual Studio genişletilebilirlik projesi oluşturmak için herhangi bir Visual Studio (Community, Professional veya Enterprise) sürümünü kullanabilirsiniz.

## <a name="create-an-extensibility-project"></a>Genişletilebilirlik projesi oluşturma

::: moniker range="vs-2017"

Adım 1. Gelen **dosya** menüsünde **yeni** > **proje**.

Adım 2. Sağ üst köşedeki arama kutusuna "VSIX" yazın ve Visual C# **VSIX projesi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** Için "HelloWorld" yazın ve **Tamam**' ı seçin.

![Yeni proje](media/hello-world-new-project.png)

Artık başlangıç sayfasını ve bazı örnek kaynakları görmeniz gerekir.

Bu öğreticiyi bırakmanız ve geri dönebilmeniz gerekiyorsa, yeni HelloWorld projenizi **son** bölümdeki **başlangıç sayfasından** bulabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. Gelen **dosya** menüsünde **yeni** > **proje**. "VSIX" araması yapın ve Visual C# **VSIX projesini** ve sonra **İleri**' yi seçin.

Adım 2. **Proje adı** Için "HelloWorld" girin ve **Oluştur**' u seçin.

![Yeni proje](media/hello-world-new-project-2019.png)

Artık **Çözüm Gezgini**' de HelloWorld projesini görmeniz gerekir.

::: moniker-end

## <a name="add-a-custom-command"></a>Özel komut ekleme

Adım 1. *. Valtmanifest* bildirim dosyasını seçerseniz, açıklama, yazar ve sürüm gibi hangi seçeneklerin değiştirilebilir olduğunu görebilirsiniz.

Adım 2. Projeye sağ tıklayın (çözüme değil). Bağlam menüsünde **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

Adım 3: **Genişletilebilirlik** bölümünü ve ardından **komut**öğesini seçin.

4\. adımı. Alttaki **ad** alanında, *Command.cs*gibi bir dosya adı girin.

![özel komut](media/hello-world-vsix-command.png)

Yeni komut dosyanız **Çözüm Gezgini**görünür. **Kaynaklar** düğümü altında komutlarınızla ilgili diğer dosyaları bulacaksınız. Örneğin, görüntüyü değiştirmek istiyorsanız PNG dosyası burada bulunur.

## <a name="modify-the-source-code"></a>Kaynak kodunu değiştirme

Bu noktada, komut ve düğme metni otomatik olarak oluşturulur ve çok ilginç değildir. Değişiklik yapmak istiyorsanız VSCT dosyasını ve CS dosyasını değiştirebilirsiniz.

* VSCT dosyası, komutlarınızı yeniden adlandırabileceğiniz ve Visual Studio komut sisteminde nerede gittikleri yeri tanımlayabileceğiniz yerdir. VSCT dosyasını keşfederken, VSCT Code denetimlerinin her bir bölümünü açıklayan açıklamalar görürsünüz.

* CS dosyası, tıklama işleyicisi gibi eylemleri tanımlayabileceğiniz yerdir.

::: moniker range="vs-2017"

Adım 1. **Çözüm Gezgini**' de, yeni komutunuz IÇIN vsct dosyasını bulun. Bu durumda, *Commandpackage. vsct*olarak adlandırılacaktır.

![komut paketi vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Adım 1. **Çözüm Gezgini**' de, uzantı vs paketinizin vsct dosyasını bulun. Bu durumda, *Merhaba Dünya Package. vsct*olarak adlandırılacaktır.

::: moniker-end

Adım 2. `ButtonText` parametresini `Say Hello World!`olarak değiştirin.

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

Adım 3: **Çözüm Gezgini** dönün ve *Command.cs* dosyasını bulun. `Execute` yönteminde, dize `message` `string.Format(..)` ' den `Hello World!`' e değiştirin.

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

Artık kaynak kodu Visual Studio deneysel örneğinde çalıştırabilirsiniz.

Adım 1. **Hata ayıklamayı Başlat** komutunu çalıştırmak için **F5** tuşuna basın. Bu komut, projenizi oluşturur ve hata ayıklayıcıyı başlatır ve **deneysel örnek**olarak adlandırılan yeni bir Visual Studio örneğini başlatır.

::: moniker range="vs-2017"

Visual Studio başlık çubuğunda **deneysel örnek** sözcüklerini görürsünüz.

![deneysel örnek başlık çubuğu](media/hello-world-exp-instance.png)

::: moniker-end

Adım 2. **Deneysel örneğin** **araçlar** menüsünde **deyin Merhaba Dünya!** ' e tıklayın.

![nihai sonuç](media/hello-world-final-result.png)

Yeni özel komutınızdan çıktıyı görmeniz gerekir, bu durumda **Merhaba Dünya** size sunan ekranın merkezindeki iletişim kutusu. .

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio genişletilebilirliği ile çalışmanın temellerini öğrenmiş olduğunuza göre buradan daha fazla bilgi edinebilirsiniz:

* [Visual Studio uzantıları geliştirmeye başlayın](starting-to-develop-visual-studio-extensions.md) -örnekler, Öğreticiler. ve uzantınızı yayımlama
* Visual [studio 2017 SDK 'daki](what-s-new-in-the-visual-studio-2017-sdk.md) yenilikler-visual Studio 2017 ' de yeni genişletilebilirlik özellikleri
* Visual [studio 2019 SDK 'daki](whats-new-visual-studio-2019-sdk.md) yenilikler-visual Studio 2019 ' de yeni genişletilebilirlik özellikleri
* [Visual STUDIO SDK içinde](internals/inside-the-visual-studio-sdk.md) -Visual Studio genişletilebilirliğine ilişkin ayrıntıları öğrenin
