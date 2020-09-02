---
title: Menü komutuyla uzantı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3bbf6b3b1ed2565d5e58806bd0935f713ba5bfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62572893"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Bir Menü Komutuyla Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Not defteri 'Ni başlatan menü komutuyla bir uzantının nasıl oluşturulacağını gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Menü komutu oluşturma  
  
1. **FirstMenuCommand**ADLı bir VSIX projesi oluşturun. VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Proje açıldığında, **FirstCommand**adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **FirstCommand.cs**olarak değiştirin.  
  
3. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
     Visual Studio 'nun deneysel örneği görüntülenir. Deneysel örnek hakkında daha fazla bilgi için bkz. [deneysel örnek](../extensibility/the-experimental-instance.md).  
  
4. Deneysel örnekte,  **Araçlar/Uzantılar ve güncelleştirmeler** penceresini açın. **FirstMenuCommand** uzantısını burada görmeniz gerekir. (Visual Studio 'nun çalışma Örneğinizde **Uzantılar ve güncelleştirmeler** açarsanız, **FirstMenuCommand**' i görmezsiniz).  
  
     Şimdi deneysel örnekteki **Araçlar** menüsüne gidin. **Invoke FirstCommand** komutunu görmeniz gerekir. Bu noktada, yalnızca FirstMenuCommand. FirstCommand. Menuıitemcallback () "Içinde" FirstCommandPackage "yazan bir ileti kutusu görüntüler. Bir sonraki bölümde bu komuttan Not defteri 'ni gerçekten nasıl başlatacağız.  
  
## <a name="changing-the-menu-command-handler"></a>Menü komut Işleyicisini değiştirme  
 Şimdi komut işleyicisini Not defteri 'Ni başlatacak şekilde güncelleştirelim.  
  
1. Hata ayıklamayı durdurun ve Visual Studio çalışma örneğinizi geri dönün. FirstCommand.cs dosyasını açın ve aşağıdaki using ifadesini ekleyin:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2. Özel FirstCommand oluşturucusunu bulun. Bu, komutun komut hizmetine takılmış olduğu ve komut işleyicisi belirtildiği yerdir. Komut işleyicisinin adını StartNotepad ile aşağıdaki gibi değiştirin:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3. MenuItemCallback metodunu kaldırın ve yalnızca Notepad 'i başlatacak bir StartNotepad yöntemi ekleyin:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4. Şimdi deneyin. Projede hata ayıklamayı başlattığınızda ve **Araçlar/Invoke FirstCommand**' e tıkladığınızda bir not defteri örneği görürsünüz.  
  
     <xref:System.Diagnostics.Process>Yalnızca Not defteri değil, çalıştırılabilir dosyayı çalıştırmak için sınıfının bir örneğini kullanabilirsiniz. Örneğin calc.exe deneyin.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Deneysel ortamı Temizleme  
 Birden çok uzantı geliştirmekte veya yalnızca uzantı kodunuzun farklı sürümleriyle sonuçları araştırıyorsanız, deneysel ortamınız bu şekilde çalışmayı durdurabilir. Bu durumda, sıfırlama betiğini çalıştırmanız gerekir. **Visual studio 2015 Deneysel örneğini sıfırlayın**olarak adlandırılır ve Visual Studio SDK 'sının bir parçası olarak dağıtılır. Bu betik, deneysel ortamdan uzantılarınızın tüm başvurularını kaldırır, böylece sıfırdan başlayabilirsiniz.  
  
 Bu betiğe iki şekilde ulaşabilirsiniz:  
  
1. Masaüstünden, **Visual Studio 2015 Deneysel örneğini Sıfırla**' yı bulun.  
  
2. Komut satırından aşağıdakileri çalıştırın:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Uzantınızı dağıtma  
 Araç uzantınızı istediğiniz şekilde çalıştırdığınıza göre, arkadaşlarınızı ve iş arkadaşlarınızla paylaşmayı düşünmek zaman atalım. Bu, Visual Studio 2015 ' nin yüklü olduğu sürece oldukça kolaydır. Yapmanız gerekirse, sizin oluşturduğunuz. vsix dosyasını göndermektir. (Yayın modunda derlemeyi unutmayın.)  
  
 Bu uzantı için. vsix dosyasını FirstMenuCommand bin dizininde bulabilirsiniz. Özellikle, yayın yapılandırmasını oluşturduğunuz varsayılarak, şu şekilde olacaktır:  
  
 **\<code directory>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand. vsix**  
  
 Uzantıyı yüklemek için, arkadaşınızın Visual Studio 'nun tüm açık örneklerini kapatması gerekir ve ardından **VSIX yükleyicisini**getiren. vsix dosyasına çift tıklayın. Dosyalar, **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** dizinine kopyalanır.  
  
 Arkadaşınız Visual Studio 'Yu tekrar **getirirse, Araçlar/Uzantılar ve güncelleştirmeler**' de FirstMenuCommand uzantısını bulur. Uzantıyı kaldırmak veya devre dışı bırakmak için **Uzantılar ve güncelleştirmeler** 'e gidebilir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu izlenecek yol, Visual Studio uzantısıyla yapabileceklerinizi yalnızca küçük bir parçasını göstermiştir. Aşağıda, Visual Studio uzantıları ile gerçekleştirebileceğiniz diğer (makul ölçüde kolay) şeyler için kısa bir liste verilmiştir:  
  
1. Basit bir menü komutuyla birçok şeyi daha yapabilirsiniz:  
  
   1. Kendi simgenizi ekleyin: [menü komutlarına simgeler ekleme](../extensibility/adding-icons-to-menu-commands.md)  
  
   2. Menü komutunun metnini değiştirme: [bir menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3. Komuta Menü kısayolu ekleme: [menü öğelerine klavye kısayollarını bağlama](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Farklı türlerde komutlar, menüler ve araç çubukları ekleyin: [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)  
  
3. Araç pencereleri ekleme ve yerleşik Visual Studio araç pencerelerini genişletme: [araç pencerelerini genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Mevcut kod düzenleyicilerine IntelliSense, kod önerileri ve diğer özellikler ekleme: [Düzenleyici ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Uzantınızın seçeneklerini ve özellik sayfalarını ve Kullanıcı ayarlarını ekleyin: [özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md) ve [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md)  
  
   Diğer tür uzantılar, yeni bir proje türü oluşturma ([projeleri genişletme](../extensibility/extending-projects.md)), yeni bir düzenleyici türü oluşturma ([özel düzenleyiciler ve tasarımcılar oluşturma](../extensibility/creating-custom-editors-and-designers.md)) veya uzantınızı yalıtılmış bir kabukta uygulama gibi biraz daha fazla Iş gerektirir: [Visual Studio yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md)
