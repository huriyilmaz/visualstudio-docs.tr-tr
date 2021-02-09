---
title: Kalıcı Iletişim kutuları oluşturma ve yönetme | Microsoft Docs
description: Visual Studio içinde, DialogWindow kullanarak ve DialogWindow 'u kullanmadan kalıcı iletişim kutusu oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 949f136913a30848ba13185bc699fa0bc51ac456
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884981"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Kalıcı iletişim kutuları oluşturma ve yönetme
Visual Studio içinde kalıcı iletişim kutusu oluşturduğunuzda iletişim kutusu görüntülenirken iletişim kutusunun ana penceresinin devre dışı olduğundan emin olmanız gerekir ve iletişim kutusu kapatıldıktan sonra üst pencereyi yeniden etkinleştirin. Bunu yapmazsanız, şu hatayı alabilirsiniz: *kalıcı bir iletişim kutusu etkin olduğundan Microsoft Visual Studio kapatılamadı. Etkin iletişim kutusunu kapatın ve yeniden deneyin.*

Bunu yapmanın iki yolu vardır. Önerilen yol, bir WPF iletişim kutusu varsa, bunu türetirsiniz <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> ve <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> iletişim kutusunu göstermek için öğesini çağırın. Bunu yaparsanız, ana pencerenin kalıcı durumunu yönetmeniz gerekmez.

İletişim kutusu WPF değilse veya başka bir nedenden dolayı iletişim kutusu sınıfınızı türetimiyorsanız, iletişim kutusunu görüntülemeden ve iletişim <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> kutusunu kapattıktan sonra yöntemi bir 1 (true) parametresiyle yeniden çağırarak, iletişim kutusunun üst öğesini bir parametresi olarak çağırarak ve bir parametre ile tekrar çağırarak, iletişim kutusunun üst öğesini almanız ve yönetmeniz gerekir.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow 'dan türetilmiş bir iletişim kutusu oluştur

1. **OpenDialogTest** ADLı bir VSIX projesi oluşturun ve **OpenDialog** adlı bir menü komutu ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Sınıfını kullanmak için <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , aşağıdaki derlemelere başvurular eklemelisiniz ( **Başvuru Ekle** iletişim kutusunun Framework sekmesinde):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System. xaml*

3. *OpenDialog.cs* içinde aşağıdaki `using` ifadeyi ekleyin:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Şu kaynaktan türetilen adlı bir sınıf bildirin `TestDialogWindow` <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

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

6. Yönteminde, `OpenDialog.ShowMessageBox` mevcut kodu şu kodla değiştirin:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Uygulamayı derleyin ve çalıştırın. Visual Studio 'nun deneysel örneği görünmelidir. Deneysel örneğin **Araçlar** menüsünde, **OpenDialog Invoke** adlı bir komut görmeniz gerekir. Bu komuta tıkladığınızda, iletişim kutusu penceresini görmeniz gerekir. Pencereyi simge durumuna küçültebilir ve ekranı kaplamasını sağlayabilmelisiniz.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>DialogWindow 'dan türetilmeyen bir iletişim kutusu oluşturma ve yönetme

1. Bu yordam için, önceki yordamda oluşturduğunuz **OpenDialogTest** çözümünü aynı derleme başvurularına sahip olacak şekilde kullanabilirsiniz.

2. Aşağıdaki bildirimleri ekleyin `using` :

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Öğesinden türetilen adlı bir sınıf oluşturun `TestDialogWindow2` <xref:System.Windows.Window> :

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

6. Yönteminde, `OpenDialog.ShowMessageBox` mevcut kodu şu kodla değiştirin:

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

7. Uygulamayı derleyin ve çalıştırın. **Araçlar** menüsünde, **OpenDialog Invoke** adlı bir komut görmeniz gerekir. Bu komuta tıkladığınızda, iletişim kutusu penceresini görmeniz gerekir.
