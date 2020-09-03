---
title: 'İzlenecek yol: bir düzenleyici uzantısıyla kısayol tuşu kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201941"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>İzlenecek Yol: Düzenleyici Uzantısı ile Kısayol Tuşu Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici uzantıdaki kısayol tuşlarına yanıt verebilirsiniz. Aşağıdaki izlenecek yol, bir kısayol tuşu kullanarak bir metin görünümüne Görünüm kenarlığı nasıl ekleneceğini gösterir. Bu izlenecek yol, görünüm penceresinin kenarlığı düzenleyici şablonunu temel alır ve + karakterini kullanarak kenarlığı eklemenize olanak tanır.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) projesi oluşturma  
  
1. C# VSıX projesi oluşturun. ( **Yeni proje** iletişim kutusunda, **Visual C#/genişletilebilirliği**, sonra **VSIX projesi**' ni seçin.) Çözümü adlandırın `KeyBindingTest` .  
  
2. Projeye bir düzenleyici metni kenarlığı öğe şablonu ekleyin ve bunu adlandırın `KeyBindingTest` . Daha fazla bilgi için bkz. [bir düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Aşağıdaki başvuruları ekleyin ve **CopyLocal** öğesini şu şekilde ayarlayın `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft. VisualStudio. OLE. Interop  
  
    Microsoft. VisualStudio. Shell. 14.0  
  
    Microsoft. VisualStudio. TextManager. Interop  
  
   KeyBindingTest sınıfı dosyasında, sınıf adını Purpleköşeli kutusu olarak değiştirin. Diğer uygun değişiklikleri yapmak için sol kenar boşluğunda görünen ampul ' i kullanın. Oluşturucunun içinde, kenarlığı katmanının adını **KeyBindingTest** öğesinden **purpleucu kutusuna**değiştirin:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Komut filtresini tanımlama  
 Komut filtresi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kenarlığı örneğini oluşturarak komutu işleyen öğesinin bir uygulamasıdır.  
  
1. Bir sınıf dosyası ekleyin ve adlandırın `KeyBindingCommandFilter` .  
  
2. Aşağıdaki using deyimlerini ekleyin.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. KeyBindingCommandFilter adlı sınıf öğesinden devralması gerekir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
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
  
6. `QueryStatus()`Yöntemini aşağıdaki şekilde uygulayın.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. `Exec()`Bir + karakteri yazıldığında görünüme mor bir kutu eklemek için yöntemini uygulayın.  
  
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
  
## <a name="adding-the-command-filter"></a>Komut filtresi ekleme  
 Kenarlığı sağlayıcının metin görünümüne bir komut filtresi eklemesi gerekir. Bu örnekte sağlayıcı, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> metin görünümü oluşturma olaylarını dinlemek için uygular. Bu kenarlığı sağlayıcısı ayrıca kenarlığı 'in Z düzenini tanımlayan kenarlığı katmanını dışarı aktarır.  
  
1. KeyBindingTestTextViewCreationListener dosyasında aşağıdaki using deyimlerini ekleyin:  
  
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
  
2. Kenarlığı katman tanımında, Donnmentlayer adını **KeyBindingTest** öğesinden **Purpleköşeli kutusuna**değiştirin.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Metin görünümü bağdaştırıcısını almak için, öğesini içeri aktarmanız gerekir <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Yöntemi, eklemesi için değiştirin `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter`İşleyici, metin görünümü bağdaştırıcısını alır ve komut filtresini ekler.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Kenarlığı her satırda görünür hale getirme  
 Özgün kenarlığı, metin dosyasındaki her ' a ' karakteriyle görüldü. Artık kodu, ' + ' karakterine yanıt olarak kenarlığı eklemek üzere değiştirdiğimiz için, kenarlığı yalnızca ' + ' karakterinin yazıldığı satıra eklenir. Kenarlığı kodunu, her ' a ' üzerinde daha fazla kenarlığı bir kez daha görünecek şekilde değiştirebiliriz.  
  
 KeyBindingTest.cs dosyasında, ' a ' karakterini süslemek için görünümdeki tüm satırlarda yinelemek üzere Creategörselleri () yöntemini değiştirin.  
  
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
  
## <a name="building-and-testing-the-code"></a>Kodu derleme ve test etme  
  
1. KeyBindingTest çözümünü derleyin ve deneysel örnekte çalıştırın.  
  
2. Bir metin dosyası oluşturun veya açın. ' A ' karakterini içeren bazı sözcükler yazın ve ardından metin görünümünde her yere + yazın.  
  
     Dosyadaki her ' a ' karakteriyle mor bir kare görünmelidir.
