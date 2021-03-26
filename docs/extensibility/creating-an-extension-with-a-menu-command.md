---
title: Menü komutuyla uzantı oluşturma | Microsoft Docs
description: Not defteri 'Ni başlatan menü komutuyla bir uzantı oluşturmayı öğrenin. Bir menü komutu oluşturun ve menü komut işleyicisini değiştirin.
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
ms.workload:
- vssdk
ms.openlocfilehash: de79662494a3228dd301e8d08480c6aa0a0192a2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089218"
---
# <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

Bu izlenecek yol, Not defteri 'Ni başlatan menü komutuyla bir uzantının nasıl oluşturulacağını gösterir.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Menü komutu oluştur

1. **FirstMenuCommand** ADLı bir VSIX projesi oluşturun. "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

::: moniker range="vs-2017"

2. Proje açıldığında, **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *FirstCommand. cs* olarak değiştirin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Proje açıldığında, **FirstCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *FirstCommand. cs* olarak değiştirin.

::: moniker-end

3. Projeyi derleyin ve hata ayıklamayı başlatın.

    Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. Deneysel örnekte, **Araçlar**  >  **Uzantılar ve güncelleştirmeler** penceresini açın. **FirstMenuCommand** uzantısını burada görmeniz gerekir. (Visual Studio 'nun çalışma Örneğinizde **Uzantılar ve güncelleştirmeler** açarsanız, **FirstMenuCommand**' i görmezsiniz).

::: moniker-end

::: moniker range=">=vs-2019"

4. Deneysel örnekte **, uzantılar**  >  **Yönet** penceresini açın. **FirstMenuCommand** uzantısını burada görmeniz gerekir. (Visual Studio 'nun çalışma Örneğinizde **Uzantıları Yönet** ' i açarsanız, **FirstMenuCommand**' i görmezsiniz).

::: moniker-end

Şimdi deneysel örnekteki **Araçlar** menüsüne gidin. **Invoke FirstCommand** komutunu görmeniz gerekir. Bu noktada, komut **FirstMenuCommand. FirstCommand. Menuıitemcallback () Içinde FirstCommand** yazan bir ileti kutusu görüntüler. Bir sonraki bölümde bu komuttan Not defteri 'ni gerçekten nasıl başlatacağız.

## <a name="change-the-menu-command-handler"></a>Menü komut işleyicisini değiştirme

Şimdi komut işleyicisini Not defteri 'Ni başlatacak şekilde güncelleştirelim.

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

3. Yöntemi kaldırın `Execute` ve `StartNotepad` yalnızca Notepad 'i başlatacak bir yöntem ekleyin:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();

        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Şimdi deneyin. Projede hata ayıklamayı başlattığınızda ve **Araçlar**  >  **FirstCommand komutunu** tıklattığınızda, Not defteri 'nin bir örneğini görmeniz gerekir.

    <xref:System.Diagnostics.Process>Yalnızca Not defteri değil, çalıştırılabilir dosyayı çalıştırmak için sınıfının bir örneğini kullanabilirsiniz. `calc.exe`Örneğin, ile deneyin.

## <a name="clean-up-the-experimental-environment"></a>Deneysel ortamı temizle

Birden çok uzantı geliştirmekte veya yalnızca uzantı kodunuzun farklı sürümleriyle sonuçları araştırıyorsanız, deneysel ortamınız bu şekilde çalışmayı durdurabilir. Bu durumda, sıfırlama betiğini çalıştırmanız gerekir. **Visual Studio Deneysel örneğini sıfırlayın** olarak adlandırılır ve Visual Studio SDK 'sının bir parçası olarak dağıtılır. Bu betik, deneysel ortamdan uzantılarınızın tüm başvurularını kaldırır, böylece sıfırdan başlayabilirsiniz.

Bu betiğe iki şekilde ulaşabilirsiniz:

1. Masaüstünden, **Visual Studio Deneysel örneğini Sıfırla**' yı bulun.

2. Komut satırından aşağıdakileri çalıştırın:

    ```cmd
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Uzantınızı dağıtın

Araç uzantınızı istediğiniz şekilde çalıştırdığınıza göre, arkadaşlarınızı ve iş arkadaşlarınızla paylaşmayı düşünmek zaman atalım. Bu, Visual Studio 2015 ' nin yüklü olduğu sürece oldukça kolaydır. Yapmanız gerekirse, sizin oluşturduğunuz *. vsix* dosyasını göndermektir. (Yayın modunda derlemeyi unutmayın.)

Bu uzantı için *. vsix* dosyasını *FirstMenuCommand* bin dizininde bulabilirsiniz. Özellikle, yayın yapılandırmasını oluşturduğunuz varsayılarak, şu şekilde olacaktır:

*\<code directory>\Firstmenucommand\firstmenucommand\bin\release\firstmenucommand.exe*

Uzantıyı yüklemek için, arkadaşınızın Visual Studio 'nun tüm açık örneklerini kapatması gerekir ve ardından **VSIX yükleyicisini** getiren *. vsix* dosyasına çift tıklayın. Dosyalar, *%LocalAppData%\microsoft\visualstudio \<version> \Extensions* dizinine kopyalanır.

Arkadaşınız Visual Studio 'yu tekrar getirdiklerinde, **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' de FirstMenuCommand uzantısını bulacağız. Uzantıyı kaldırmak veya devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** 'e gidebilir.

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yol, Visual Studio uzantısıyla yapabileceklerinizi yalnızca küçük bir parçasını göstermiştir. Aşağıda, Visual Studio uzantıları ile gerçekleştirebileceğiniz diğer (makul ölçüde kolay) şeyler için kısa bir liste verilmiştir:

1. Basit bir menü komutuyla birçok şeyi daha yapabilirsiniz:

   1. Kendi simgenizi ekleyin: [menü komutlarına simgeler ekleme](../extensibility/adding-icons-to-menu-commands.md)

   2. Menü komutunun metnini değiştirme: [bir menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Komuta Menü kısayolu ekleme: [menü öğelerine klavye kısayollarını bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Farklı türlerde komutlar, menüler ve araç çubukları ekleyin: [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)

3. Araç pencereleri ekleme ve yerleşik Visual Studio araç pencerelerini genişletme: [araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)

4. Mevcut kod düzenleyicilerine IntelliSense, kod önerileri ve diğer özellikler ekleme: [düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)

5. Uzantınızın seçeneklerini ve özellik sayfalarını ve Kullanıcı ayarlarını ekleyin: [özellikleri ve özellik penceresini genişletin](../extensibility/extending-properties-and-the-property-window.md) ve [Kullanıcı ayarlarını ve seçeneklerini genişletin](../extensibility/extending-user-settings-and-options.md)

   Diğer tür uzantılar, yeni bir proje türü oluşturma ([projeleri genişletme](../extensibility/extending-projects.md)), yeni bir düzenleyici türü oluşturma ([özel düzenleyiciler oluşturma ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md)) veya uzantınızı yalıtılmış bir kabukta uygulama gibi biraz daha fazla Iş gerektirir: [Visual Studio yalıtılmış Kabuğu](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
