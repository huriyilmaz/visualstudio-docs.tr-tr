---
title: Menü komutuyla uzantı oluşturma | Microsoft Docs
description: Not Defteri başlatan menü komutuyla bir uzantı oluşturmayı öğrenin. Bir menü komutu oluşturun ve menü komut işleyicisini değiştirin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627687"
---
# <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

bu izlenecek yol, Not Defteri başlatan menü komutuyla bir uzantının nasıl oluşturulacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Menü komutu oluştur

1. **FirstMenuCommand** ADLı bir VSIX projesi oluşturun. vsıx proje şablonunu, **yeni Project** iletişim kutusunda "vsıx" arayarak bulabilirsiniz.

::: moniker range="vs-2017"

2. Proje açıldığında, **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *FirstCommand. cs* olarak değiştirin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Proje açıldığında, **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *FirstCommand. cs* olarak değiştirin.

::: moniker-end

3. Projeyi derleyin ve hata ayıklamayı başlatın.

    Visual Studio deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Deneysel örnekte, **Araçlar**  >  **Uzantılar ve güncelleştirmeler** penceresini açın. **FirstMenuCommand** uzantısını burada görmeniz gerekir. (Visual Studio çalışma örneğinizde **uzantılar ve güncelleştirmeler** açarsanız, **firstmenucommand**' i görmezsiniz).

::: moniker-end

::: moniker range=">=vs-2019"

4. Deneysel örnekte **, uzantılar**  >  **Yönet** penceresini açın. **FirstMenuCommand** uzantısını burada görmeniz gerekir. (Visual Studio çalışma örneğinizde **uzantıları yönet** ' i açarsanız, **firstmenucommand**' i görmezsiniz).

::: moniker-end

Şimdi deneysel örnekteki **Araçlar** menüsüne gidin. **Invoke FirstCommand** komutunu görmeniz gerekir. Bu noktada, komut **FirstMenuCommand. FirstCommand. Menuıitemcallback () Içinde FirstCommand** yazan bir ileti kutusu görüntüler. bir sonraki bölümde bu komuttan Not Defteri gerçekten başlatma hakkında bilgi edineceksiniz.

## <a name="change-the-menu-command-handler"></a>Menü komut işleyicisini değiştirme

şimdi de Not Defteri başlamak için komut işleyicisini güncelleştirelim.

1. Hata ayıklamayı durdurun ve Visual Studio çalışma örneğinizi geri dönün. *FirstCommand. cs* dosyasını açın ve aşağıdaki using ifadesini ekleyin:

    ```csharp
    using System.Diagnostics;
    ```

2. Özel FirstCommand oluşturucusunu bulun. Bu, komutun komut hizmetine takılmış olduğu ve komut işleyicisi belirtildiği yerdir. Komut işleyicisinin adını StartNotepad ile aşağıdaki gibi değiştirin:

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

3. yöntemi kaldırın `Execute` ve `StartNotepad` yalnızca Not Defteri başlatacak bir yöntem ekleyin:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Şimdi deneyin. projede hata ayıklamayı başlattığınızda ve **araçlar**  >  **firstcommand komutunu** tıklattığınızda, Not Defteri bir örneğini görmeniz gerekir.

    <xref:System.Diagnostics.Process>yalnızca Not Defteri değil, herhangi bir yürütülebiliri çalıştırmak için sınıfının bir örneğini kullanabilirsiniz. `calc.exe`Örneğin, ile deneyin.

## <a name="clean-up-the-experimental-environment"></a>Deneysel ortamı temizle

Birden çok uzantı geliştirmekte veya yalnızca uzantı kodunuzun farklı sürümleriyle sonuçları araştırıyorsanız, deneysel ortamınız bu şekilde çalışmayı durdurabilir. Bu durumda, sıfırlama betiğini çalıştırmanız gerekir. **Visual Studio deneysel örneği sıfırlama** olarak adlandırılır ve Visual Studio SDK 'sının bir parçası olarak dağıtılır. Bu betik, deneysel ortamdan uzantılarınızın tüm başvurularını kaldırır, böylece sıfırdan başlayabilirsiniz.

Bu betiğe iki şekilde ulaşabilirsiniz:

1. masaüstünden **Visual Studio deneysel örneği sıfırla**' yı bulun.

2. Komut satırından aşağıdakileri çalıştırın:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Uzantınızı dağıtın

Araç uzantınızı istediğiniz şekilde çalıştırdığınıza göre, arkadaşlarınızı ve iş arkadaşlarınızla paylaşmayı düşünmek zaman atalım. Visual Studio 2015 yüklü olduğu sürece bu çok kolay bir işlemdir. Yapmanız gerekirse, sizin oluşturduğunuz *. vsix* dosyasını göndermektir. (Yayın modunda derlemeyi unutmayın.)

Bu uzantı için *. vsix* dosyasını *FirstMenuCommand* bin dizininde bulabilirsiniz. Özellikle, yayın yapılandırmasını oluşturduğunuz varsayılarak, şu şekilde olacaktır:

*\<code directory>\Firstmenucommand\firstmenucommand\bin\release\firstmenucommand.exe*

uzantıyı yüklemek için, arkadaşınızın tüm Visual Studio açık örneklerini kapatması gerekir ve ardından **vsıx yükleyicisini** getiren *. vsix* dosyasına çift tıklayın. Dosyalar, *%LocalAppData%\microsoft\visualstudio \<version> \Extensions* dizinine kopyalanır.

arkadaşınız Visual Studio yeniden geldiğinde, **araçlar**  >  **uzantılar ve güncelleştirmeler**' de firstmenucommand uzantısını bulacağız. Uzantıyı kaldırmak veya devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** 'e gidebilir.

## <a name="next-steps"></a>Sonraki adımlar

bu izlenecek yol, Visual Studio uzantısıyla yapabileceklerinizi yalnızca küçük bir parçasını göstermiştir. Visual Studio uzantıları ile gerçekleştirebileceğiniz diğer (makul ölçüde kolay) şeyler için kısa bir liste aşağıda verilmiştir:

1. Basit bir menü komutuyla birçok şeyi daha yapabilirsiniz:

   1. Kendi simgenizi ekleyin: [menü komutlarına simgeler ekleme](../extensibility/adding-icons-to-menu-commands.md)

   2. Menü komutunun metnini değiştirme: [bir menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Komuta Menü kısayolu ekleme: [menü öğelerine klavye kısayollarını bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Farklı türlerde komutlar, menüler ve araç çubukları ekleyin: [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)

3. araç pencereleri ekleme ve yerleşik Visual Studio araç pencerelerini genişletme: [araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)

4. Mevcut kod düzenleyicilerine IntelliSense, kod önerileri ve diğer özellikler ekleme: [düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)

5. Uzantınızın seçeneklerini ve özellik sayfalarını ve Kullanıcı ayarlarını ekleyin: [özellikleri ve özellik penceresini genişletin](../extensibility/extending-properties-and-the-property-window.md) ve [Kullanıcı ayarlarını ve seçeneklerini genişletin](../extensibility/extending-user-settings-and-options.md)

   diğer tür uzantılar, yeni bir proje türü oluşturma ([projeleri genişletme](../extensibility/extending-projects.md)), yeni bir düzenleyici türü oluşturma ([özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md)) veya uzantınızı yalıtılmış bir kabukta uygulama gibi biraz daha fazla iş gerektirir: [yalıtılmış kabuğa Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
