---
title: Kalıcı Iletişim kutuları oluşturma ve yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431582"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Kalıcı İletişim Kutuları Oluşturma ve Bunları Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio içinde kalıcı iletişim kutusu oluşturduğunuzda iletişim kutusu görüntülenirken iletişim kutusunun ana penceresinin devre dışı olduğundan emin olmanız gerekir ve iletişim kutusu kapatıldıktan sonra üst pencereyi yeniden etkinleştirin. Bunu yapmazsanız, "Microsoft Visual Studio kalıcı bir iletişim kutusu etkin olduğu için kapatılamıyor. Etkin iletişim kutusunu kapatın ve yeniden deneyin. "  
  
 Bunu yapmanın iki yolu vardır. Önerilen yol, bir WPF iletişim kutusu varsa, bunu türetirsiniz <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> ve <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> iletişim kutusunu göstermek için öğesini çağırın. Bunu yaparsanız, ana pencerenin kalıcı durumunu yönetmeniz gerekmez.  
  
 İletişim kutusu WPF değilse veya başka bir nedenden dolayı iletişim kutusu sınıfınızı türetimiyorsanız, iletişim kutusunu görüntülemeden ve iletişim <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> kutusunu kapattıktan sonra yöntemi bir 1 (true) parametresiyle yeniden çağırarak, iletişim kutusunun üst öğesini bir parametresi olarak çağırarak ve bir parametre ile tekrar çağırarak, iletişim kutusunun üst öğesini almanız ve yönetmeniz gerekir.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow 'dan türetilen iletişim kutusu oluşturma  
  
1. **OpenDialogTest** ADLı bir VSIX projesi oluşturun ve **OpenDialog**adlı bir menü komutu ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için, bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Sınıfını kullanmak için <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , aşağıdaki derlemelere başvurular eklemelisiniz ( **Başvuru Ekle** iletişim kutusunun Framework sekmesinde):  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System. xaml  
  
3. OpenDialog.cs içinde aşağıdaki `using` ifadeyi ekleyin:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. Öğesinden türetilen **Testdialogwindow** adlı bir sınıf bildirin <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5. İletişim kutusunu en aza indirebilmek ve en üst düzeye çıkarmak için, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> ve <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> true olarak ayarlayın:  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6. **OpenDialog. ShowMessageBox** yönteminde, mevcut kodu şu kodla değiştirin:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. Uygulamayı derleyin ve çalıştırın. Visual Studio 'nun deneysel örneği görünmelidir. Deneysel örneğin **Araçlar** menüsünde, **OpenDialog Invoke**adlı bir komut görmeniz gerekir. Bu komuta tıkladığınızda, iletişim kutusu penceresini görmeniz gerekir. Pencereyi simge durumuna küçültebilir ve ekranı kaplamasını sağlayabilmelisiniz.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>DialogWindow 'dan türetilmeyen bir iletişim kutusu oluşturma ve yönetme  
  
1. Bu yordam için, önceki yordamda oluşturduğunuz **OpenDialogTest** çözümünü aynı derleme başvurularına sahip olacak şekilde kullanabilirsiniz.  
  
2. Aşağıdaki bildirimleri ekleyin `using` :  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. **TestDialogWindow2** adlı ve öğesinden türetilen bir sınıf oluşturun <xref:System.Windows.Window> :  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4. Özel bir başvuru ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5. Başvuruyu ayarlayan bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6. **OpenDialog. ShowMessageBox** yönteminde, mevcut kodu şu kodla değiştirin:  
  
    ```csharp  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7. Uygulamayı derleyin ve çalıştırın. **Araçlar** menüsünde, **OpenDialog Invoke**adlı bir komut görmeniz gerekir. Bu komuta tıkladığınızda, iletişim kutusu penceresini görmeniz gerekir.
