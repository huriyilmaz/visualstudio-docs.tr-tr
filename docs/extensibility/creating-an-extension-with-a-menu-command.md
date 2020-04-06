---
title: Menü Komutu yla Uzantı Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739553"
---
# <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

Bu gözden geçirme, Not Defteri'ni başlatan bir menü komutuyla uzantı oluşturmanın nasıl yapılacağını gösterir.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-command"></a>Menü komutu oluşturma

1. **FirstMenuCommand**adında bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **FirstCommand**adlı özel bir komut öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında komut dosyası adını *FirstCommand.cs*olarak değiştirin.

3. Projeyi oluşturun ve hata ayıklamaya başlayın.

    Visual Studio'nun deneysel örneği ortaya çıkar. Deneysel örnek hakkında daha fazla bilgi için, [bkz.](../extensibility/the-experimental-instance.md)

::: moniker range="vs-2017"

4. Deneysel örnekte, **Araçlar** > **Uzantıları ve Güncelleştirmeleri** penceresini açın. **Burada FirstMenuCommand** uzantısı görmelisiniz. (Visual Studio'nun çalışma örneğinde **Uzantıları ve Güncelleştirmeleri** açarsanız, **FirstMenuCommand'ı**görmezsiniz).

::: moniker-end

::: moniker range=">=vs-2019"

4. Deneme örneğinde, **Uzantıları** > **Yönet Uzantıları** penceresini açın. **Burada FirstMenuCommand** uzantısı görmelisiniz. (Visual Studio'nun çalışma örneğinde **Uzantıları Yönet'i** açarsanız, **FirstMenuCommand'ı**görmezsiniz).

::: moniker-end

Şimdi deneysel örnekte **Araçlar** menüsüne gidin. **Invoke FirstCommand** komutunu görmelisiniz. Bu noktada, komut **FirstMenuCommand.FirstCommand.MenuItemCallback() içinde FirstCommandPackage**diyor bir ileti kutusu getiriyor. Not Defteri'ni bir sonraki bölümde bu komuttan nasıl başlatabileceğimizi göreceğiz.

## <a name="change-the-menu-command-handler"></a>Menü komut işleyicisini değiştirme

Şimdi Not Defteri'ni başlatmak için komut işleyicisini güncelleştirelim.

1. Hata ayıklamayı bırakın ve Visual Studio'daki çalışma örneğinize geri dön. *FirstCommand.cs* dosyasını açın ve aşağıdaki ifadesini ekleyin:

    ```csharp
    using System.Diagnostics;
    ```

2. Özel FirstCommand oluşturucuyu bulun. Burada komut komut hizmetine bağlanır ve komut işleyicisi belirtilir. Komut işleyicisinin adını Aşağıdaki gibi StartNotepad olarak değiştirin:

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

3. `MenuItemCallback` Yöntemi kaldırın ve `StartNotepad` not defterini başlatacak bir yöntem ekleyin:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Şimdi dene. Proje hata ayıklama başladığınızda ve **Araçlar** > **Çağırmak FirstCommand**tıkladığınızda , Not Defteri bir örnek gelip görmelisiniz.

    Sadece Not Defteri'ni <xref:System.Diagnostics.Process> değil, herhangi bir yürütülebilir çalıştırmak için sınıfın bir örneğini kullanabilirsiniz. `calc.exe`Örneğin,

## <a name="clean-up-the-experimental-environment"></a>Deneysel ortamı temizleme

Birden çok uzantı geliştiriyorsanız veya uzantı kodunuzdan farklı sürümleriyle sonuçları araştırıyorsanız, deneme ortamınız olması gerektiği gibi çalışmayı durdurabilir. Bu durumda, sıfırlama komut dosyasını çalıştırmalısınız. Bu Visual **Studio Deneysel Örnek Sıfırlama**denir , ve Visual Studio SDK bir parçası olarak gemi. Bu komut dosyası, uzantılarınıza yapılan tüm başvuruları deneysel ortamdan kaldırır, böylece sıfırdan başlayabilirsiniz.

Bu komut dosyasına iki şekilde ulaşabilirsiniz:

1. Masaüstünden Visual **Studio Deneysel Örneği Sıfırla'yı**bulun.

2. Komut satırından aşağıdakileri çalıştırın:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Uzantınızı dağıtma

Artık araç uzantınızın istediğiniz gibi çalıştığını düşünürsek, bunu arkadaşlarınızla ve iş arkadaşlarınızla paylaşmayı düşünmenin zamanı gelmiştir. Visual Studio 2015'i taktıkları sürece bu çok kolay. Tek yapmanız gereken onlara oluşturduğun *.vsix* dosyasını göndermek. (Sürüm modunda oluşturduğunuzdan emin olun.)

Bu uzantınla ilgili *.vsix* dosyasını *FirstMenuCommand* bin dizininde bulabilirsiniz. Özellikle, Sürüm yapılandırmasını oluşturduğunızı varsayarsak, aşağıdakiler olacaktır:

*\<kod dizini>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

Uzantıyı yüklemek için arkadaşınızın Visual Studio'nun tüm açık örneklerini kapatması ve **ardından VSIX Yükleyicisini**getiren *.vsix* dosyasını çift tıklatması gerekir. Dosyalar *%LocalAppData%\Microsoft\VisualStudio\<sürümü>\Extensions* dizinine kopyalanır.

Arkadaşınız Visual Studio'yu tekrar gündeme getirdiğinde, **Araçlar** > Uzantıları ve Güncellemeler'de FirstMenuCommand uzantısını**bulurlar.** Uzantıyı kaldırmak veya devre dışı kaldırmak için **Uzantılar ve Güncelleştirmeler'e de gidebilirler.**

## <a name="next-steps"></a>Sonraki adımlar

Bu izlik, Visual Studio uzantısı ile yapabileceklerinin yalnızca küçük bir bölümünü göstermiştir. Visual Studio uzantılarıyla yapabileceğiniz diğer (oldukça kolay) şeylerin kısa bir listesi aşağıda veda edebilirsiniz:

1. Basit bir menü komutu ile çok daha fazla şey yapabilirsiniz:

   1. Kendi simgenizi ekleyin: [Menü komutlarına simge ekleme](../extensibility/adding-icons-to-menu-commands.md)

   2. Menü komutunun metnini [değiştirme: Menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Komuta menü kısayolu ekleme: [Menü öğelerine klavye kısayollarını bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Farklı komutlar, menüler ve araç çubukları ekleyin: [Menüleri ve komutları genişletin](../extensibility/extending-menus-and-commands.md)

3. Araç pencereleri ekleyin ve yerleşik Visual Studio araç pencerelerini genişletin: [Araç pencerelerini genişletin ve özelleştirin](../extensibility/extending-and-customizing-tool-windows.md)

4. Varolan kod düzenleyicilerine IntelliSense, kod önerileri ve diğer özellikleri ekleyin: [Düzenleyiciyi ve dil hizmetlerini genişletin](../extensibility/extending-the-editor-and-language-services.md)

5. Uzantınıza Seçenekler ve Özellik sayfaları ve kullanıcı ayarları ekleyin: [Özellikleri ve Özellik penceresini genişletin](../extensibility/extending-properties-and-the-property-window.md) ve [kullanıcı ayarlarını ve seçeneklerini genişletin](../extensibility/extending-user-settings-and-options.md)

   Diğer uzantı türleri, yeni bir proje türü oluşturma[(Projeleri Genişletme),](../extensibility/extending-projects.md)yeni bir editör türü oluşturma[(Özel editörler ve tasarımcılar oluşturma)](../extensibility/creating-custom-editors-and-designers.md)veya uzantınızı yalıtılmış bir kabukta uygulamak gibi biraz daha fazla çalışma gerektirir: [Visual Studio yalıtılmış kabuk](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
