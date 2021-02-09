---
title: Bir düzenleyici uzantısıyla kısayol tuşu kullanma
description: Bir kısayol tuşu kullanarak bir metin görünümüne Görünüm kenarlığı ekleme hakkında bilgi edinin. Bu izlenecek yol, görünüm penceresinin kenarlığı düzenleyici şablonunu temel alır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0f6cb0d3cc0bef03539428bafeff5ae3da64964
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931272"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma
Düzenleyici uzantıdaki kısayol tuşlarına yanıt verebilirsiniz. Aşağıdaki izlenecek yol, bir kısayol tuşu kullanarak bir metin görünümüne Görünüm kenarlığı nasıl ekleneceğini gösterir. Bu izlenecek yol, görünüm penceresinin kenarlığı düzenleyici şablonunu temel alır ve + karakterini kullanarak kenarlığı eklemenize olanak tanır.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `KeyBindingTest` .

2. Projeye bir düzenleyici metni kenarlığı öğe şablonu ekleyin ve bunu adlandırın `KeyBindingTest` . Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Aşağıdaki başvuruları ekleyin ve **CopyLocal** öğesini şu şekilde ayarlayın `false` :

    Microsoft. VisualStudio. Editor

    Microsoft. VisualStudio. OLE. Interop

    Microsoft. VisualStudio. Shell. 14.0

    Microsoft. VisualStudio. TextManager. Interop

   KeyBindingTest sınıfı dosyasında, sınıf adını Purpleköşeli kutusu olarak değiştirin. Diğer uygun değişiklikleri yapmak için sol kenar boşluğunda görünen ampul ' i kullanın. Oluşturucunun içinde, kenarlığı katmanının adını **KeyBindingTest** öğesinden **purpleucu kutusuna** değiştirin:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

KeyBindingTestTextViewCreationListener.cs sınıf dosyasında, **KeyBindingTest** ' den Purnmentlayer ' ın adını **Espleköşeli kutusuna** değiştirin:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Tanıtıcı TYPECHAR komutu
Visual Studio 2017 sürüm 15,6 ' den önce, bir düzenleyici uzantısında komutları işlemenin tek yolu bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> temel komut filtresi uygulamamıştı. Visual Studio 2017 sürüm 15,6, düzenleyici komut işleyicilerine dayalı modern basitleştirilmiş bir yaklaşım getirmiştir. Sonraki iki bölümde hem eski hem de modern yaklaşımı kullanarak bir komutun nasıl işleneceği gösterilmektedir.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Komut filtresini tanımlama (Visual Studio 2017 sürüm 15,6 ' den önce)

 Komut filtresi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kenarlığı örneğini oluşturarak komutu işleyen öğesinin bir uygulamasıdır.

1. Bir sınıf dosyası ekleyin ve adlandırın `KeyBindingCommandFilter` .

2. Aşağıdaki using yönergelerini ekleyin.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. KeyBindingCommandFilter adlı sınıf öğesinden devralması gerekir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Metin görünümü için özel alanlar, komut zincirindeki bir sonraki komut ve komut filtresinin zaten eklenip eklenmeyeceğini temsil eden bir bayrak ekleyin.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Metin görünümünü ayarlayan bir Oluşturucu ekleyin.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. `QueryStatus()`Yöntemini aşağıdaki şekilde uygulayın.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. `Exec()`Bir artı işareti () karakteri yazılmışsa görünüme mor bir kutu eklemek için yöntemini uygulayın **+** .

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Komut filtresini ekleme (Visual Studio 2017 sürüm 15,6 ' den önce)
 Kenarlığı sağlayıcının metin görünümüne bir komut filtresi eklemesi gerekir. Bu örnekte sağlayıcı, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metin görünümü oluşturma olaylarını dinlemek için uygular. Bu kenarlığı sağlayıcısı ayrıca kenarlığı 'in Z düzenini tanımlayan kenarlığı katmanını dışarı aktarır.

1. KeyBindingTestTextViewCreationListener dosyasında, aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. Metin görünümü bağdaştırıcısını almak için, öğesini içeri aktarmanız gerekir <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Yöntemi, eklemesi için değiştirin `KeyBindingCommandFilter` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. `AddCommandFilter`İşleyici, metin görünümü bağdaştırıcısını alır ve komut filtresini ekler.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Bir komut işleyici uygulama (Visual Studio 2017 sürüm 15,6 ' den başlayarak)

İlk olarak, en son Düzenleyici API 'sine başvurmak için projenin NuGet başvurularını güncelleştirin:

1. Projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.

2. **NuGet Paket Yöneticisi**' nde **güncelleştirmeler** sekmesini seçin, **tüm paketleri Seç** onay kutusunu seçin ve ardından **Güncelleştir**' i seçin.

Komut işleyicisi <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> , kenarlığı örneğini oluşturarak komutu işleyen öğesinin uygulamasıdır.

1. Bir sınıf dosyası ekleyin ve adlandırın `KeyBindingCommandHandler` .

2. Aşağıdaki using yönergelerini ekleyin.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. KeyBindingCommandHandler adlı sınıf öğesinden devralması ve şu `ICommandHandler<TypeCharCommandArgs>` şekilde dışarı aktarmanız gerekir <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> :

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Komut işleyicisinin görünen adını ekleyin:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. `GetCommandState()`Yöntemini aşağıdaki şekilde uygulayın. Bu komut işleyici, çekirdek Düzenleyicisi TYPECHAR komutunu işletiğinden, komutu çekirdek düzenleyicide etkinleştirmek için temsilci seçebilirsiniz.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. `ExecuteCommand()`Bir artı işareti () karakteri yazılmışsa görünüme mor bir kutu eklemek için yöntemini uygulayın **+** .

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. *KeyBindingTestTextViewCreationListener.cs* dosyasındaki kenarlığı katman tanımını *KeyBindingCommandHandler.cs* olarak kopyalayın ve *KeyBindingTestTextViewCreationListener.cs* dosyasını silin:

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Kenarlığı her satırda görünmesini sağlama

Özgün kenarlığı, metin dosyasındaki her ' a ' karakteriyle görüldü. Artık kodu, kenarlığı yanıt olarak karakteri eklemek üzere değiştirdiğimiz için **+** , kenarlığı yalnızca **+** karakterin yazıldığı satıra eklenir. Kenarlığı kodunu, her ' a ' üzerinde daha fazla kenarlığı bir kez daha görünecek şekilde değiştirebiliriz.

*KeyBindingTest.cs* dosyasında, `CreateVisuals()` ' a ' karakterini süslemek için görünümdeki tüm satırlarda yinelemek üzere yöntemini değiştirin.

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin

1. KeyBindingTest çözümünü derleyin ve deneysel örnekte çalıştırın.

2. Bir metin dosyası oluşturun veya açın. ' A ' karakterini içeren bazı sözcükler yazın ve **+** metin görünümünde herhangi bir yere yazın.

     Dosyadaki her ' a ' karakteriyle mor bir kare görünmelidir.
