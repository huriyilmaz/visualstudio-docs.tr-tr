---
title: 'İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d95d41024bd839c8c556ac94501b20d1a81b7a97
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647894"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma
Düzenleyici uzantıdaki kısayol tuşlarına yanıt verebilirsiniz. Aşağıdaki izlenecek yol, bir kısayol tuşu kullanarak bir metin görünümüne Görünüm kenarlığı nasıl ekleneceğini gösterir. Bu izlenecek yol, görünüm penceresinin kenarlığı düzenleyici şablonunu temel alır ve + karakterini kullanarak kenarlığı eklemenize olanak tanır.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma

1. C# VSIX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **görsel C# /genişletilebilirlik**, sonra **VSIX projesi**' ni seçin.) @No__t_4 çözümü adlandırın.

2. Projeye bir düzenleyici metni kenarlığı öğe şablonu ekleyin ve `KeyBindingTest` adlandırın. Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Aşağıdaki başvuruları ekleyin ve **CopyLocal** öğesini `false` olarak ayarlayın:

    Microsoft. VisualStudio. Editor

    Microsoft. VisualStudio. OLE. Interop

    Microsoft. VisualStudio. Shell. 14.0

    Microsoft. VisualStudio. TextManager. Interop

   KeyBindingTest sınıfı dosyasında, sınıf adını Purpleköşeli kutusu olarak değiştirin. Diğer uygun değişiklikleri yapmak için sol kenar boşluğunda görünen ampul ' i kullanın. Oluşturucunun içinde, kenarlığı katmanının adını **KeyBindingTest** öğesinden **purpleucu kutusuna**değiştirin:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

KeyBindingTestTextViewCreationListener.cs sınıf dosyasında, **KeyBindingTest** ' den Purnmentlayer ' ın adını **Espleköşeli kutusuna**değiştirin:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Tanıtıcı TYPECHAR komutu
Visual Studio 2017 sürüm 15,6 ' den önce, bir düzenleyici uzantısında komutları işlemenin tek yolu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tabanlı bir komut filtresi uygulamamıştı. Visual Studio 2017 sürüm 15,6, düzenleyici komut işleyicilerine dayalı modern basitleştirilmiş bir yaklaşım getirmiştir. Sonraki iki bölümde hem eski hem de modern yaklaşımı kullanarak bir komutun nasıl işleneceği gösterilmektedir.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Komut filtresini tanımlama (Visual Studio 2017 sürüm 15,6 ' den önce)

 Komut filtresi, kenarlığı örneğini oluşturarak komutu işleyen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulamasıdır.

1. Bir sınıf dosyası ekleyin ve `KeyBindingCommandFilter` adlandırın.

2. Aşağıdaki using yönergelerini ekleyin.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. KeyBindingCommandFilter adlı sınıf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 'ten devralması gerekir.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Metin görünümü için özel alanlar, komut zincirindeki bir sonraki komut ve komut filtresinin zaten eklenip eklenmeyeceğini temsil eden bir bayrak ekleyin.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Metin görünümünü ayarlayan bir Oluşturucu ekleyin.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. @No__t_0 yöntemini aşağıdaki şekilde uygulayın.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Bir artı işareti ( **+** ) karakteri yazılmışsa görünüme mor bir kutu eklemek için `Exec()` yöntemini uygulayın.

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
 Kenarlığı sağlayıcının metin görünümüne bir komut filtresi eklemesi gerekir. Bu örnekte sağlayıcı, metin görünümü oluşturma olaylarını dinlemek için <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> uygular. Bu kenarlığı sağlayıcısı ayrıca kenarlığı 'in Z düzenini tanımlayan kenarlığı katmanını dışarı aktarır.

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

2. Metin görünümü bağdaştırıcısını almak için <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> içeri aktarmanız gerekir.

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. @No__t_0 yöntemini `KeyBindingCommandFilter` eklemesi için değiştirin.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. @No__t_0 işleyicisi metin görünümü bağdaştırıcısını alır ve komut filtresini ekler.

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

Komut işleyicisi, kenarlığı örneğini oluşturarak komutu işleyen <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> uygulamasıdır.

1. Bir sınıf dosyası ekleyin ve `KeyBindingCommandHandler` adlandırın.

2. Aşağıdaki using yönergelerini ekleyin.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. KeyBindingCommandHandler adlı sınıf `ICommandHandler<TypeCharCommandArgs>` 'ten devralması ve <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> olarak dışarı aktarmanız gerekir:

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

5. @No__t_0 yöntemini aşağıdaki şekilde uygulayın. Bu komut işleyici, çekirdek Düzenleyicisi TYPECHAR komutunu işletiğinden, komutu çekirdek düzenleyicide etkinleştirmek için temsilci seçebilirsiniz.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Bir artı işareti ( **+** ) karakteri yazılmışsa görünüme mor bir kutu eklemek için `ExecuteCommand()` yöntemini uygulayın.

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

Özgün kenarlığı, metin dosyasındaki her ' a ' karakteriyle görüldü. **@No__t_1** karaktere yanıt olarak kenarlığı eklemek için kodu değiştirdiğimiz için, yalnızca **+** karakterin yazıldığı satıra kenarlığı ekler. Kenarlığı kodunu, her ' a ' üzerinde daha fazla kenarlığı bir kez daha görünecek şekilde değiştirebiliriz.

*KeyBindingTest.cs* dosyasında, ' a ' karakterini süslemek için görünümdeki tüm satırlarda yinelemek üzere `CreateVisuals()` yöntemini değiştirin.

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

2. Bir metin dosyası oluşturun veya açın. ' A ' karakterini içeren bazı sözcükler yazın ve sonra metin görünümünde **+** yazın.

     Dosyadaki her ' a ' karakteriyle mor bir kare görünmelidir.
