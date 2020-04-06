---
title: 'Walkthrough: Bir Kısayol Anahtarı bir Editör Uzantısı ile kullanma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697145"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Walkthrough: Düzenleyici uzantısı ile kısayol tuşu kullanma
Editör uzantınızdaki kısayol tuşlarına yanıt verebilirsiniz. Aşağıdaki izlik, kısayol tuşu kullanarak metin görünümüne görünüm süslemesinin nasıl ekleyeceğini gösterir. Bu izlenme, viewport süsleme düzenleyicisi şablonuna dayanır ve + karakterini kullanarak süslemeyi eklemenize olanak tanır.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Yönetilen Genişletilebilirlik Çerçevesi (MEF) Projesi Oluşturma

1. Bir C# VSIX projesi oluşturun. (Yeni **Proje** iletişim kutusunda Visual **C# / Genişletilebilirlik,** ardından **VSIX Project'i**seçin.) Çözümü `KeyBindingTest`adlandırın.

2. Projeye bir Düzenleyici Metin Süsleme öğesi şablonu `KeyBindingTest`ekleyin ve adını adlandırın. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Aşağıdaki referansları ekleyin ve `false` **CopyLocal'ı** şu şekilde ayarlayın:

    Microsoft.VisualStudio.Editor

    Microsoft.visualstudio.ole

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   KeyBindingTest sınıf dosyasında sınıf adını PurpleCornerBox olarak değiştirin. Diğer uygun değişiklikleri yapmak için sol kenar boşluğunda görünen ampulü kullanın. Oluşturucunun içinde, Adornment katmanının adını **KeyBindingTest'ten** **PurpleCornerBox'a**değiştirin:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

KeyBindingTestTextViewCreationListener.cs sınıf dosyasında, AdornmentLayer'ın adını **KeyBindingTest'ten** **PurpleCornerBox'a**değiştirin:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>TYPECHAR komutunu işleme
Visual Studio 2017 sürüm 15.6'dan önce bir düzenleyici uzantısındaki komutları işlemenin tek yolu tabanlı komut <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> filtresi uygulamaktı. Visual Studio 2017 sürüm 15.6, editör komut işleyicilerine dayalı modern basitleştirilmiş bir yaklaşım sundu. Sonraki iki bölüm, hem eski hem de modern yaklaşımı kullanarak bir komutun nasıl işleyeceğini gösterir.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Komut filtresini tanımlayın (Visual Studio 2017 sürümü 15.6'dan önce)

 Komut filtresi, süslemeyi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>anında oluşturarak komutu işleyen bir uygulamadır.

1. Bir sınıf dosyası ekleyin `KeyBindingCommandFilter`ve adlandırın.

2. Yönergeleri kullanarak aşağıdakileri ekleyin.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. KeyBindingCommandFilter adlı sınıf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Metin görünümü için özel alanlar, komut zincirindeki bir sonraki komut ve komut filtresinin zaten eklenip eklenmediğini temsil edecek bir bayrak ekleyin.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Metin görünümünü ayarlayan bir oluşturucu ekleyin.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Yöntemi `QueryStatus()` aşağıdaki gibi uygulayın.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Bir `Exec()` artı işareti (**+**) karakteri yazılırsa görünüme mor bir kutu ekecek şekilde yöntemi uygulayın.

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Komut filtresini ekleyin (Visual Studio 2017 sürümü 15.6'dan önce)
 Süsleme sağlayıcısının metin görünümüne bir komut filtresi eklemesi gerekir. Bu örnekte, sağlayıcı <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metin görünümü oluşturma olaylarını dinlemek için uygular. Bu süs sağlayıcı aynı zamanda süslemezzz'in Z sırasını tanımlayan süs tabakasını da ihraç eder.

1. KeyBindingTestTextViewCreationListener dosyasında, aşağıdaki yönergeleri kullanarak ekleyin:

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

2. Metin görünümü bağdaştırıcısını almak <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>için .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Yöntemi <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> değiştirin, böylece `KeyBindingCommandFilter`.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. İşleyici `AddCommandFilter` metin görünümü bağdaştırıcısını alır ve komut filtresini ekler.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Bir komut işleyicisi uygulayın (Visual Studio 2017 sürüm 15.6'dan itibaren)

İlk olarak, projenin Nuget başvurularını en son düzenleyici API'ye başvurmak için güncelleştirin:

1. Projeye sağ tıklayın ve **Nuget Paketlerini Yönet'i**seçin.

2. **Nuget Paket**Yöneticisi'nde, **Güncellemeler** sekmesini seçin, **tüm paketleri seç** onay kutusunu seçin ve ardından **Güncelleştir'i**seçin.

Komut <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>işleyicisi, süslemeyi anında oluşturarak komutu işleyen bir uygulamadır.

1. Bir sınıf dosyası ekleyin `KeyBindingCommandHandler`ve adlandırın.

2. Yönergeleri kullanarak aşağıdakileri ekleyin.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. KeyBindingCommandHandler adlı sınıf devralmalı `ICommandHandler<TypeCharCommandArgs>`ve şu <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>şekilde dışa aktarmalıdır:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Komut işleyicisinin ekran adı ekleyin:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Yöntemi `GetCommandState()` aşağıdaki gibi uygulayın. Bu komut işleyicisi çekirdek düzenleyici TYPECHAR komutunu işlediği için, komutu etkinle'yi çekirdek düzenleyiciye devredebilir.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Bir `ExecuteCommand()` artı işareti (**+**) karakteri yazılırsa görünüme mor bir kutu ekecek şekilde yöntemi uygulayın.

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

   7. KeyBindingTestTextViewCreationListener.cs *dosyadan* *KeyBindingCommandHandler.cs'a* süsleme katmanı tanımını kopyalayın ve *ardından KeyBindingTestTextViewCreationListener.cs* dosyayı silin:

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

## <a name="make-the-adornment-appear-on-every-line"></a>Süslemenin her satırda görünmesini sağla

Orijinal süsleme bir metin dosyasında her karakter 'a' çıktı. Şimdi biz **+** karaktere yanıt olarak süsleme eklemek için kodu değiştirdik, sadece **+** karakter yazılır satırına süsleme ekler. Süs kodunu değiştirebiliriz, böylece süs her 'a'da bir kez daha görünür.

*KeyBindingTest.cs* dosyasında, 'a' karakterini süslemek için `CreateVisuals()` yöntemdeki tüm satırları yinelemek için değiştirin.

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

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin

1. KeyBindingTest çözümlerini oluşturun ve deneysel örnekte çalıştırın.

2. Metin dosyası oluşturun veya açın. 'a' karakterini içeren bazı sözcükler yazın **+** ve ardından metin görünümünde herhangi bir yere yazın.

     Dosyadaki her 'a' karakterinde mor bir kare görünmelidir.
