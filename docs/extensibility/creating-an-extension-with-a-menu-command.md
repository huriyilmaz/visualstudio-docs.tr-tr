---
title: Menü Komut Satırı ile Uzantı | Microsoft Docs
description: Uzantıyı başlatan bir menü komutuyla uzantı Not Defteri. Bir menü komutu oluşturun ve ardından menü komut işleyicisini değiştirebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d6fe7776e331fc9918035cb9c9edc7e8cf4c8ae9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051124"
---
# <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

Bu kılavuzda, uzantıyı başlatan bir menü komutuyla uzantının nasıl Not Defteri.

## <a name="prerequisites"></a>Önkoşullar

2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-command"></a>Menü komutu oluşturma

1. **FirstMenuCommand adlı bir** VSIX projesi oluşturun. VSIX proje şablonunu New **Project** iletişim kutusunda "vsix" ifadesini arayarak bulabilirsiniz.

::: moniker range="vs-2017"

2. Proje açıldığında **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Özel **Komut'ı seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *FirstCommand.cs olarak değiştirebilirsiniz.*

::: moniker-end

::: moniker range=">=vs-2019"

2. Proje açıldığında **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Komut'ı **seçin.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *FirstCommand.cs olarak değiştirebilirsiniz.*

::: moniker-end

3. Projeyi derleme ve hata ayıklamayı başlatma.

    Deneysel örnek Visual Studio görünür. Deneysel örnek hakkında daha fazla bilgi için [bkz. Deneysel örnek.](../extensibility/the-experimental-instance.md)

::: moniker range="vs-2017"

4. Deneysel örnekte Araçlar Uzantıları **ve**  >  **Güncelleştirmeler penceresini** açın. **FirstMenuCommand uzantısını burada** görüyorsanız. (Uzantılar ve **Güncelleştirmeler'i** çalışma örneğinize açarsanız Visual Studio **FirstMenuCommand'i görmezsiniz).**

::: moniker-end

::: moniker range=">=vs-2019"

4. Deneysel örnekte Uzantıları Yönet **penceresini**  >   açın. **FirstMenuCommand uzantısını burada** görüyorsanız. (Çalışma **örneğinizin Çalışma Örneği'Visual Studio** Uzantıları Yönet'i açarsanız **FirstMenuCommand'i görmezsiniz).**

::: moniker-end

Şimdi deneysel örnekte **Araçlar** menüsüne gidin. **FirstCommand komutunu çağır komutunu görüyor** gerekir. Bu noktada komutu **FirstCommand Inside FirstMenuCommand.FirstCommand.MenuItemCallback()** komutunun yer alan bir ileti kutusu getirir. Sonraki bölümde bu komuttan Not Defteri başlatmayı göreceğiz.

## <a name="change-the-menu-command-handler"></a>Menü komut işleyicisini değiştirme

Şimdi komut işleyicisini güncelleştirin ve komut Not Defteri.

1. Hata ayıklamayı durdurun ve çalışma örneğinize geri Visual Studio. *FirstCommand.cs dosyasını* açın ve aşağıdaki using deyimini ekleyin:

    ```csharp
    using System.Diagnostics;
    ```

2. Özel FirstCommand oluşturucusu bulun. Burada komut, komut hizmetine bağlanarak komut işleyicisi belirtilir. Komut işleyicinin adını aşağıdaki gibi StartNotepad olarak değiştirin:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. yöntemini `Execute` kaldırın ve yeni `StartNotepad` bir yöntem ekleyin. Bu yöntem yalnızca Not Defteri:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Şimdi deneyin. Projede hata ayıklamaya başlarken ve **Araçlar**  >  **FirstCommand'i** Çağır'a tıklarken, bir Not Defteri örneğiyle karşılaşabilirsiniz.

    Sınıfın bir örneğini kullanarak yalnızca <xref:System.Diagnostics.Process> yürütülebilir dosyaları değil, herhangi bir yürütülebilir dosyayı Not Defteri. Örneğin ile `calc.exe` deneyin.

## <a name="clean-up-the-experimental-environment"></a>Deneysel ortamı temizleme

Birden çok uzantı geliştiriyorsanız veya yalnızca uzantı kodunuzun farklı sürümleriyle sonuçları keşfediyorsanız deneysel ortamınız olması gerektiği gibi çalışmayı durdurabilir. Bu durumda, sıfırlama betiği çalıştırmanız gerekir. Visual Studio Deneysel **Örneği'Visual Studio olarak adlandırılır** ve Visual Studio SDK'sı kapsamında birlikte iletir. Bu betik, deneysel ortamdan uzantılarınıza yapılan tüm başvuruları kaldırır, böylece sıfırdan başlayabilirsiniz.

Bu betiği iki şekilde elde etmek için:

1. Masaüstünden Deneysel **Örneği Visual Studio bulun.**

2. Komut satırına aşağıdakini çalıştırın:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Uzantınızı dağıtma

Araç uzantınızı istediğiniz gibi çalıştırabilirsiniz. Şimdi bunu arkadaşlarınızla ve iş arkadaşlarınızla paylaşmanın zamanı geldi. 2015'te yüklü Visual Studio bu kadar kolaydır. Tek yapmanız gereken, onlara kendi kendi *dosyanız olan .vsix* dosyasını göndermektir. (Bunu Yayın modunda derlemeyi emin olun.)

Bu uzantının *.vsix* dosyasını *FirstMenuCommand* bin dizininde bulabilirsiniz. Özellikle, Yayın yapılandırmasını sizin yapılandırmasını tamamlaya kadar şu şekildedir:

*\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\FirstMenuCommand.vsix*

Uzantıyı yüklemek için, arkadaşınızın tüm açık Visual Studio kapatması ve ardından VSIX Yükleyicisi'ne getiren *.vsix* dosyasına çift **tıklaması gerekir.** Dosyalar *%LocalAppData%\Microsoft\VisualStudio \<version> \Extensions dizinine kopyalanır.*

Arkadaşınız yeni bir Visual Studio geldiğinde, Araçlar Uzantıları ve Güncelleştirmeler'de FirstMenuCommand   >  **uzantısını bulur.** Uzantıyı kaldırmak veya **devre dışı bırakmak için** Uzantılar ve Güncelleştirmeler'e de gidebilirler.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, tek bir uzantıyla neler Visual Studio gösterilmiştir. Bu uzantılarla ekleyebilirsiniz diğer (makul düzeyde kolay) şeylerin kısa bir listesi Visual Studio:

1. Basit bir menü komutuyla çok daha fazlasını yapabilirsiniz:

   1. Kendi simgenizi ekleme: [Menü komutlarına simge ekleme](../extensibility/adding-icons-to-menu-commands.md)

   2. Menü komutunun metnini değiştirme: [Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Komuta menü kısayolu ekleme: [Klavye kısayollarını menü öğelerine bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Farklı türlerde komutlar, menüler ve araç çubukları ekleme: [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)

3. Araç pencereleri ekleme ve yerleşik araç Visual Studio genişletme: [Araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)

4. Mevcut kod düzenleyicilere IntelliSense, kod önerileri ve diğer özellikler ekleme: [Düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)

5. Uzantınıza Seçenekler ve Özellik sayfaları ve kullanıcı ayarları ekleme: Özellikleri ve Özellik [penceresini ve](../extensibility/extending-properties-and-the-property-window.md) Kullanıcı ayarlarını ve [seçeneklerini genişlet](../extensibility/extending-user-settings-and-options.md)

   Diğer uzantı türleri için yeni proje türü oluşturma[(](../extensibility/extending-projects.md)Projeleri genişletme), yeni bir düzenleyici türü oluşturma[(](../extensibility/creating-custom-editors-and-designers.md)Özel düzenleyiciler ve tasarımcılar oluşturma) veya uzantınızı yalıtılmış bir kabukta uygulama gibi daha fazla işlem gerekir: [Visual Studio yalıtılmış kabuk](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
