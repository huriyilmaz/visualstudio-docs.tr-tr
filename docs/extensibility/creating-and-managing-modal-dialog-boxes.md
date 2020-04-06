---
title: Modal İletişim Kutuları Oluşturma ve Yönetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739487"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Modal iletişim kutuları oluşturma ve yönetme
Visual Studio içinde bir modal iletişim kutusu oluşturduğunuzda, iletişim kutusu görüntülenirken iletişim kutusunun üst penceresinin devre dışı bırakıldığından emin olmalısınız ve iletişim kutusu kapatıldıktan sonra üst pencereyi yeniden etkinleştirin. Bunu yapmazsanız, hata alabilirsiniz: *Microsoft Visual Studio bir modal iletişim etkin olduğu için kapatılamaz. Etkin iletişim kutusunu kapatın ve yeniden deneyin.*

Bunu yapmanın iki yolu vardır. WPF iletişim kutunuz varsa önerilen yol, bu <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>kutuyu ve iletişim <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> kutusunu görüntülemek için aramaktır. Bunu yaparsanız, üst pencerenin modal durumunu yönetmeniz gerekmez.

İletişim kutunuz WPF değilse veya başka bir nedenle iletişim kutusu sınıfınızı <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>türetemiyorsanız, iletişim kutusunu kapattıktan sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> iletişim kutusunu görüntülemeden önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> yöntemi 0 (yanlış) parametreyle arayarak ve yöntemi tekrar arayarak, iletişim kutusunu arayarak iletişim kutusunun üst öğesini kendiniz aramanız ve yönetmeniz gerekir.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>DialogWindow'dan türetilen bir iletişim kutusu oluşturma

1. **OpenDialogTest** adında bir VSIX projesi oluşturun ve **OpenDialog**adlı bir menü komutu ekleyin. Bunun nasıl yapılacılaştırılaçılacılığı hakkında daha fazla bilgi için, [menü komutuyla uzantıcı oluştur'](../extensibility/creating-an-extension-with-a-menu-command.md)a bak

2. <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Sınıfı kullanmak için aşağıdaki derlemelere **(Başvuru Ekle** iletişim kutusunun Çerçeve sekmesinde) göndermeler eklemeniz gerekir:

    - *Presentationcore*

    - *Presentationframework*

    - *Windowsbase*

    - *Sistem.Xaml*

3. *OpenDialog.cs*olarak, aşağıdaki `using` ifadeyi ekleyin:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Bu türlerden `TestDialogWindow` türeyen adlı bir sınıf bildirin: <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. İletişim kutusunu en aza indirmek ve en <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> üst düzeye çıkarmak için, ayarlayın ve doğru:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. `OpenDialog.ShowMessageBox` Yöntemde, varolan kodu aşağıdakilerle değiştirin:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Uygulamayı derleyin ve çalıştırın. Visual Studio'nun deneysel örneği görünmelidir. Deneme örneğinin **Araçlar** menüsünde **Invoke OpenDialog**adlı bir komut görmeniz gerekir. Bu komutu tıklattığınızda, iletişim penceresini görmeniz gerekir. Pencereyi en aza indirip en üst düzeye çıkarabilmelisin.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>DialogWindow'dan türetilen bir iletişim kutusu oluşturma ve yönetme

1. Bu yordam için, önceki yordamda oluşturduğunuz **OpenDialogTest** çözümünü aynı derleme başvurularıyla kullanabilirsiniz.

2. Aşağıdaki `using` bildirimleri ekleyin:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Şundan türeyen bir sınıf oluşturun: `TestDialogWindow2` <xref:System.Windows.Window>

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Özel bir başvuru <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ekleyin:

    ```
    private IVsUIShell shell;
    ```

5. Başvuruyu ayarlayan bir oluşturucu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>ekleyin:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. `OpenDialog.ShowMessageBox` Yöntemde, varolan kodu aşağıdakilerle değiştirin:

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

7. Uygulamayı derleyin ve çalıştırın. **Araçlar** menüsünde **Invoke OpenDialog**adlı bir komut görmeniz gerekir. Bu komutu tıklattığınızda, iletişim penceresini görmeniz gerekir.
