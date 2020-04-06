---
title: 'Walkthrough: Bir Düzenleyici Uzantısı ile Bir Shell Komutu kullanma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697162"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Walkthrough: Düzenleyici uzantılı bir kabuk komutu kullanma
VSPackage'dan, editöre menü komutları gibi özellikler ekleyebilirsiniz. Bu izlenme, bir menü komutunu çağırarak düzenleyicideki metin görünümüne nasıl bir süs ekleyeceğinizi gösterir.

 Bu izbis, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçasıyla birlikte bir VSPackage kullanımını gösterir. Menü komutunu Visual Studio kabuğuna kaydetmek için bir VSPackage kullanmanız gerekir. Ayrıca, MEF bileşen kısmına erişmek için komutu kullanabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 **Araçlar** menüsüne **Adornment Ekle** adlı bir menü komutu koyan bir VSPackage oluşturun.

1. C# VSIX projesi `MenuCommandTest`adlı oluşturun ve Özel Komut öğesi şablon adı **AddAdornment**ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. MenuCommandTest adlı bir çözüm açılır. MenuCommandTestPackage dosyası, menü komutunu oluşturan ve **Araçlar** menüsüne koyan koda sahiptir. Bu noktada, komut sadece bir ileti kutusu görünmesine neden olur. Daha sonraki adımlar, yorum süslemesini görüntülemek için bunun nasıl değiştirilebildiğini gösterir.

3. VSIX Manifest *Editor'da source.extension.vsixmanifest* dosyasını açın. Sekme, `Assets` MenuCommandTest adlı bir Microsoft.VisualStudio.VsPackage için bir satır olmalıdır.

4. *Source.extension.vsixmanifest* dosyasını kaydedin ve kapatın.

## <a name="add-a-mef-extension-to-the-command-extension"></a>Komut uzantısına MEF uzantısı ekleme

1. **Çözüm Gezgini'nde**çözüm düğümüne sağ tıklayın, **Ekle'yi**tıklatın ve ardından **Yeni Proje'yi**tıklatın. Yeni **Proje Ekle** iletişim kutusunda, **Visual C#** altında **Genişletilebilirlik'i** tıklatın, ardından **VSIX Project'i**tıklatın. Projeyi `CommentAdornmentTest`adlandırın.

2. Bu proje güçlü adlı VSPackage derlemesi ile etkileşime girecektir, çünkü derleme imzalamanız gerekir. VSPackage montajı için oluşturulmuş anahtar dosyasını yeniden kullanabilirsiniz.

    1. Proje özelliklerini açın ve **İmzasekmesini** seçin.

    2. **Montajı İmzala'yı**seçin.

    3. **Güçlü bir ad tuşu dosyası seçin,** MenuCommandTest derlemesi için oluşturulan *Key.snk* dosyasını seçin.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage projesindeki MEF uzantısına bakın
 VSPackage'a bir MEF bileşeni eklediğiniz için, bildirimde her iki varlık türünde belirtmeniz gerekir.

> [!NOTE]
> MEF hakkında daha fazla bilgi için [Yönetilen Genişletilebilirlik Çerçevesi 'ne (MEF)](/dotnet/framework/mef/index)bakın.

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage projesindeki MEF bileşenine başvurmak için

1. MenuCommandTest projesinde, VSIX Manifest Editor'daki *source.extension.vsixmanifest* dosyasını açın.

2. **Varlıklar** sekmesinde **Yeni'yi**tıklatın.

3. **Tür** listesinde **Microsoft.VisualStudio.MefComponent'u**seçin.

4. **Kaynak** listesinde, **geçerli çözümdeki Bir projeyi**seçin.

5. **Proje** **listesinde, CommentAdornmentTest'i**seçin.

6. *Source.extension.vsixmanifest* dosyasını kaydedin ve kapatın.

7. MenuCommandTest projesinin CommentAdornmentTest projesine bir referansı olduğundan emin olun.

8. CommentAdornmentTest projesinde, projeyi bir derleme oluşturmak üzere ayarlayın. Çözüm **Gezgini'nde,** projeyi seçin ve **OutputDirectory özelliğine Kopya Oluştur Çıktısı** için **Özellikler** penceresinden bakın ve **doğru**ayarlayın.

## <a name="define-a-comment-adornment"></a>Yorum süslemesi tanımlama
 Yorum süslemesinin kendisi, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> seçili metni ve yazarı ve metnin açıklamasını temsil eden bazı dizeleri izleyen bir metinden oluşur.

#### <a name="to-define-a-comment-adornment"></a>Yorum süslemesini tanımlamak için

1. CommentAdornmentTest projesinde, yeni bir sınıf dosyası `CommentAdornment`ekleyin ve adlandırın.

2. Aşağıdaki referansları ekleyin:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentationcore

    8. Presentationframework

    9. Windowsbase

3. Aşağıdaki `using` yönergeyi ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Dosya adlı `CommentAdornment`bir sınıf içermelidir.

    ```csharp
    internal class CommentAdornment
    ```

5. `CommentAdornment` Sınıfa, yazara ve açıklamaya üç alan <xref:Microsoft.VisualStudio.Text.ITrackingSpan>ekleyin.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Alanları başharfe alan bir oluşturucu ekleyin.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Süsleme için görsel bir öğe oluşturun
 Süslemeniz için görsel bir öğe tanımlayın. Bu gözden geçirme için, Windows Sunu Temeli (WPF) <xref:System.Windows.Controls.Canvas>sınıfından devralınan bir denetim tanımlayın.

1. CommentAdornmentTest projesinde bir sınıf oluşturun `CommentBlock`ve adını adlandırın.

2. Aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Sınıfın `CommentBlock` devralını <xref:System.Windows.Controls.Canvas>yaratın.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Süslemegörsel yönlerini tanımlamak için bazı özel alanlar ekleyin.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Yorum süslemesini tanımlayan ve ilgili metni ekleyen bir oluşturucu ekleyin.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Ayrıca, <xref:System.Windows.Controls.Panel.OnRender%2A> süslemeyi çizen bir olay işleyicisi uygulayın.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Bir IWpfTextViewCreationListener ekle
 Oluşturma <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> olaylarını görüntülemek için kullanabileceğiniz bir MEF bileşeni parçasıdır.

1. CommentAdornmentTest projesine bir sınıf dosyası `Connector`ekleyin ve adlandırın.

2. Aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Uygulayan <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>bir sınıf bildirin ve "metin" ve bir <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>ile dışa aktarın. <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> İçerik türü özniteliği, bileşenin uygulandığı içeriğin türünü belirtir. Metin türü, ikili olmayan tüm dosya türleri için temel türüdür. Bu nedenle, oluşturulan hemen hemen her metin görünümü bu tür olacaktır. Metin görünümü rol özelliği, bileşenin uygulandığı metin görünümü türünü belirtir. Belge metin görünümü rolleri genellikle satırlardan oluşan ve bir dosyada depolanan metni gösterir.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Yöntemi, statik `Create()` olayı çağırır şekilde uygulayın. `CommentAdornmentManager`

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Komutu yürütmek için kullanabileceğiniz bir yöntem ekleyin.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Bir süsleme katmanı tanımlama
 Yeni bir süsleme eklemek için, bir süsleme katmanı tanımlamanız gerekir.

### <a name="to-define-an-adornment-layer"></a>Bir süsleme katmanı tanımlamak için

1. Sınıfta, genel bir <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>tür alanı bildirin ve <xref:Microsoft.VisualStudio.Utilities.NameAttribute> süsleme katmanı için benzersiz bir ad belirten <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> ve bu süsleme katmanının Z-sıra ilişkisini diğer metin görünümü katmanlarına (metin, özen ve seçim) tanımlayan bir adla dışa aktarın. `Connector`

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Yorum süsleri sağlayın
 Bir süsleme tanımladığınızda, aynı zamanda bir yorum süsleme sağlayıcısı ve bir yorum süsleme yöneticisi uygulayın. Yorum süsleme sağlayıcısı, yorum süslemelerinin bir listesini tutar, temel metin arabelleğindeki <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olayları dinler ve temel metin silindiğinde yorum süslemelerini siler.

1. CommentAdornmentTest projesine yeni bir sınıf dosyası `CommentAdornmentProvider`ekleyin ve adlandırın.

2. Aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Adlı sınıf `CommentAdornmentProvider`ekle.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Metin arabelleği için özel alanlar ve arabellekle ilgili yorum süslemeleri listesi ekleyin.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Için `CommentAdornmentProvider`bir oluşturucu ekleyin. Sağlayıcı `Create()` yöntem tarafından anında olduğundan, bu oluşturucu özel erişime sahip olmalıdır. Oluşturucu olay `OnBufferChanged` işleyicisini <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olaya ekler.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. `Create()` Yöntemi ekleyin.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. `Detach()` Yöntemi ekleyin.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Olay `OnBufferChanged` işleyicisini ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Bir `CommentsChanged` olay için bildirim ekleyin.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Süsleme `Add()` eklemek için bir yöntem oluşturun.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Bir `RemoveComments()` yöntem ekleyin.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Belirli `GetComments()` bir anlık görüntü aralığındaki tüm açıklamaları döndüren bir yöntem ekleyin.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Adlı `CommentsChangedEventArgs`bir sınıf ekleyin , aşağıdaki gibi.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Yorum süslemelerini yönetme
 Yorum süs yöneticisi süs oluşturur ve süs tabakası ekler. Süseşyayı <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> hareket <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> ettirebilmek veya silebilmek için olayları ve etkinlikleri dinler. Ayrıca, yorumlar eklendiğinde veya kaldırıldığında yorum süsleyici sağlayıcı tarafından ateşlenen `CommentsChanged` olayı da dinler.

1. CommentAdornmentTest projesine bir sınıf dosyası `CommentAdornmentManager`ekleyin ve adlandırın.

2. Aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Adlı sınıf `CommentAdornmentManager`ekle.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Bazı özel alanlar ekleyin.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Yöneticiyi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olaylara ve ayrıca `CommentsChanged` olaya abone olan bir oluşturucu ekleyin. Yönetici statik `Create()` yöntemle anında olduğundan, oluşturucu özeldir.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Sağlayıcı `Create()` alan veya gerekirse bir yöntem oluşturan yöntemi ekleyin.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Işleyiciyi `CommentsChanged` ekleyin.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Işleyiciyi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> ekleyin.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Işleyiciyi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ekleyin.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Yorumu çeken özel yöntemi ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Yorum süslemesini eklemek için menü komutunu kullanın
 VSPackage `MenuItemCallback` yöntemini uygulayarak yorum süslemesi oluşturmak için menü komutunu kullanabilirsiniz.

1. MenuCommandTest projesine aşağıdaki başvuruları ekleyin:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. *AddAdornment.cs* dosyasını açın ve `using` aşağıdaki yönergeleri ekleyin.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. `Execute()` Yöntemi silin ve aşağıdaki komut işleyicisini ekleyin.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Etkin görünümü elde etmek için kod ekleyin. Aktif almak `SVsTextManager` için Visual Studio kabuk almak `IVsTextView`gerekir.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Bu metin görünümü bir düzenleyici metin görünümü örneğiise, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> arabirimine döküm <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> ve daha <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>sonra ve ilişkili olsun. Yorum <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> süsleyici `Connector.Execute()` sağlayıcı alır ve süsleme ekler yöntemi aramak için kullanın. Komut işleyicisi şimdi bu kod gibi görünmelidir:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. AddAdornmentHandler yöntemini AddAdornment constructor'daki AddAdornment komutu için işleyici olarak ayarlayın.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Kodu oluşturma ve test edin

1. Çözümü oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

2. Bir metin dosyası oluşturun. Bazı metin yazın ve sonra seçin.

3. **Araçlar** menüsünde, **Çağrı'yı Tıklat'ı tıklatın Adornment ekle.** Balon metin penceresinin sağ tarafında görüntülenmelidir ve aşağıdaki metne benzeyen metin içermelidir.

     Kullanıcı Adınız

     Fourscore ...

## <a name="see-also"></a>Ayrıca bkz.
- [Walkthrough: İçerik türünü dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
