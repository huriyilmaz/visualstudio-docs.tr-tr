---
title: Bir kabuk komutunu düzenleyici uzantısıyla kullanma
description: Bir menü komutunu çağırarak düzenleyicide bir metin görünümüne kenarlığı eklemeyi öğrenin. VSPackage 'da, düzenleyiciye menü komutları gibi özellikler ekleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f36d141c75b43dfaf90960261e40c4a619069802
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061998"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>İzlenecek yol: Düzenleyici uzantısı ile bir Shell komutu kullanma
VSPackage 'da, düzenleyiciye menü komutları gibi özellikler ekleyebilirsiniz. Bu izlenecek yol, bir menü komutunu çağırarak düzenleyicide bir metin görünümüne nasıl kenarlığı ekleneceğini gösterir.

 Bu izlenecek yol, bir VSPackage 'ın Managed Extensibility Framework (MEF) bileşeni bölümüyle birlikte kullanımını gösterir. Menü komutunu Visual Studio Kabuğu ile kaydetmek için VSPackage kullanmanız gerekir. Ve, MEF bileşeni bölümüne erişmek için komutunu da kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yükleyemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 **Araçlar** menüsüne **Add kenarlığı** adlı bir menü komutu koyan VSPackage oluşturun.

1. Adlı bir C# VSıX projesi oluşturun `MenuCommandTest` ve özel bir komut öğesi şablon adı **AddAdornment** ekleyin. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. MenuCommandTest adlı bir çözüm açılır. MenuCommandTestPackage dosyası, menü komutunu oluşturan ve **Araçlar** menüsüne yerleştiren koda sahiptir. Bu noktada, komut yalnızca bir ileti kutusunun görünmesine neden olur. Sonraki adımlarda, kenarlığı yorumunu görüntülemek için bunun nasıl değiştirileceği gösterilmektedir.

3. VSıX bildirim düzenleyicisinde *Source. Extension. valtmanifest* dosyasını açın. `Assets`Sekme, MenuCommandTest adlı bir Microsoft. VisualStudio. VsPackage için bir satıra sahip olmalıdır.

4. *Source. Extension. valtmanifest* dosyasını kaydedin ve kapatın.

## <a name="add-a-mef-extension-to-the-command-extension"></a>Komut uzantısına bir MEF uzantısı ekleyin

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın. **Yeni Proje Ekle** iletişim kutusunda, **Visual C#**, sonra **VSIX projesi** altında **genişletilebilirlik** ' e tıklayın. Projeyi adlandırın `CommentAdornmentTest` .

2. Bu proje, tanımlayıcı adlı VSPackage derlemesi ile etkileşime gireceğinden, derlemeyi imzalamanız gerekir. VSPackage derlemesi için önceden oluşturulmuş olan anahtar dosyasını yeniden kullanabilirsiniz.

    1. Proje özelliklerini açın ve **imzalama** sekmesini seçin.

    2. **Derlemeyi imzala**' yı seçin.

    3. **Tanımlayıcı ad anahtar dosyası seçin** altında, MenuCommandTest derlemesi Için oluşturulan *Key. snk* dosyasını seçin.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>VSPackage projesindeki MEF uzantısına bakın
 VSPackage 'a bir MEF bileşeni ekliyorsanız, bildirimde her iki varlık türünü de belirtmeniz gerekir.

> [!NOTE]
> MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>VSPackage projesindeki MEF bileşenine başvurmak için

1. MenuCommandTest projesinde, VSıX bildirim düzenleyicisinde *Source. Extension. valtmanifest* dosyasını açın.

2. **Varlıklar** sekmesinde **Yeni**' ye tıklayın.

3. **Tür** listesinde, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Proje** listesinde **Yorumtadornmenttest**' i seçin.

6. *Source. Extension. valtmanifest* dosyasını kaydedin ve kapatın.

7. MenuCommandTest projesinin Yorumtadornmenttest projesine bir başvurusu olduğundan emin olun.

8. Yorumtadornmenttest projesinde, projeyi derleme oluşturacak şekilde ayarlayın. **Çözüm Gezgini**, projeyi seçin ve **derleme çıkışını OutputDirectory 'ye Kopyala** özelliğinin **Özellikler** penceresine bakın ve bunu **true** olarak ayarlayın.

## <a name="define-a-comment-adornment"></a>Yorum kenarlığı tanımlama
 Kenarlığı yorumu, <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Seçilen metni izleyen bir, ve yazarı temsil eden bazı dizeleri ve metin açıklamasını içerir.

#### <a name="to-define-a-comment-adornment"></a>Bir yorum kenarlığı tanımlamak için

1. Yorumtadornmenttest projesinde yeni bir sınıf dosyası ekleyin ve adlandırın `CommentAdornment` .

2. Aşağıdaki başvuruları ekleyin:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System. ComponentModel. Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Aşağıdaki yönergeyi ekleyin `using` .

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Dosya adında bir sınıf içermelidir `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. `CommentAdornment`, Yazarı ve açıklaması için sınıfına üç alan ekleyin <xref:Microsoft.VisualStudio.Text.ITrackingSpan> .

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Alanları Başlatan bir Oluşturucu ekleyin.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Kenarlığı için görsel öğe oluşturma
 Kenarlığı için görsel bir öğe tanımlayın. Bu izlenecek yol için, Windows Presentation Foundation (WPF) sınıfından devralan bir denetim tanımlayın <xref:System.Windows.Controls.Canvas> .

1. Yorumtadornmenttest projesinde bir sınıf oluşturun ve bunu adlandırın `CommentBlock` .

2. Aşağıdaki yönergeleri ekleyin `using` .

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

3. `CommentBlock`Sınıfın devralmasını sağlayın <xref:System.Windows.Controls.Canvas> .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Kenarlığı görsel yönlerini tanımlamak için bazı özel alanlar ekleyin.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Kenarlığı yorumunu tanımlayan ve ilgili metni ekleyen bir Oluşturucu ekleyin.

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

6. Ayrıca <xref:System.Windows.Controls.Panel.OnRender%2A> , kenarlığı çizen bir olay işleyicisi de uygular.

    ```csharp
    protected override void OnRender(DrawingContext dc)
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

## <a name="add-an-iwpftextviewcreationlistener"></a>IWpfTextViewCreationListener ekleme
 , <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Oluşturma olaylarını görüntülemeyi dinlemek için kullanabileceğiniz BIR MEF bileşeni bölümüdür.

1. Yorumtadornmenttest projesine bir sınıf dosyası ekleyin ve bunu adlandırın `Connector` .

2. Aşağıdaki yönergeleri ekleyin `using` .

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Uygulayan bir sınıf bildirin <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ve bunu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "metin" ve bir ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . İçerik türü özniteliği, bileşenin uygulandığı içerik türünü belirtir. Metin türü, ikili olmayan tüm dosya türlerinin temel türüdür. Bu nedenle, neredeyse her metin görünümü bu türden olacaktır. Metin görünümü rolü özniteliği, bileşenin geçerli olduğu metin görünümü türünü belirtir. Belge metni görünümü rolleri genellikle satırlardan oluşan ve bir dosyada depolanan metni gösterir.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>Yöntemini, ' nin statik olayını çağıracak şekilde uygulayın `Create()` `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Komutu yürütmek için kullanabileceğiniz bir yöntem ekleyin.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
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

## <a name="define-an-adornment-layer"></a>Bir kenarlığı katmanı tanımlama
 Yeni bir kenarlığı eklemek için bir kenarlığı katmanı tanımlamanız gerekir.

### <a name="to-define-an-adornment-layer"></a>Bir kenarlığı katmanını tanımlamak için

1. Sınıfında, `Connector` türünde bir ortak alan bildirin <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> ve bunu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> kenarlığı katmanı için benzersiz bir ad belirten bir ile dışarı aktarın ve <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Bu kenarlığı katmanının diğer metin görünümü katmanlarına (metin, giriş Işareti ve seçim) Z düzeni ilişkisini tanımlar.

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Açıklama donbesleri sağla
 Bir kenarlığı tanımladığınızda, bir Comment kenarlığı sağlayıcısı ve bir Comment kenarlığı Manager da uygular. Comment kenarlığı sağlayıcısı, açıklama donatılarının bir listesini tutar, <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> temel alınan metin arabelleğindeki olayları dinler ve temel alınan metin silindiğinde donnments açıklamalarını siler.

1. Yorumtadornmenttest projesine yeni bir sınıf dosyası ekleyin ve bunu adlandırın `CommentAdornmentProvider` .

2. Aşağıdaki yönergeleri ekleyin `using` .

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Adlı bir sınıf ekleyin `CommentAdornmentProvider` .

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Metin arabelleği için özel alanlar ve arabelleğin ilişkili olduğu açıklama listesini ekleyin.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. İçin bir Oluşturucu ekleyin `CommentAdornmentProvider` . Sağlayıcı yöntemi tarafından örneklendiği için bu oluşturucunun özel erişimi olmalıdır `Create()` . Oluşturucu olay `OnBufferChanged` işleyicisini <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> olaya ekler.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Yöntemini ekleyin `Create()` .

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Yöntemini ekleyin `Detach()` .

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. `OnBufferChanged`Olay işleyicisini ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Bir olay için bildirim ekleyin `CommentsChanged` .

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. `Add()`Kenarlığı eklemek için bir yöntem oluşturun.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

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

11. Bir `RemoveComments()` Yöntem ekleyin.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
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

12. `GetComments()`Belirli bir anlık görüntü yayılma alanındaki tüm yorumları döndüren bir yöntem ekleyin.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Adlı bir sınıfı `CommentsChangedEventArgs` aşağıdaki şekilde ekleyin.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Açıklama donbeslerinizi Yönet
 Comment kenarlığı Manager, kenarlığı öğesini oluşturur ve kenarlığı katmanına ekler. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> Kenarlığı taşıyabilmesi veya silebilmesi için ve olaylarını dinler. Ayrıca `CommentsChanged` , açıklamalar eklendiğinde veya kaldırıldığında Comment kenarlığı sağlayıcısı tarafından tetiklenen olayı dinler.

1. Yorumtadornmenttest projesine bir sınıf dosyası ekleyin ve bunu adlandırın `CommentAdornmentManager` .

2. Aşağıdaki yönergeleri ekleyin `using` .

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Adlı bir sınıf ekleyin `CommentAdornmentManager` .

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Bazı özel alanlar ekleyin.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Yöneticiyi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> ve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> olayları ve ayrıca olayına abone olan bir Oluşturucu ekleyin `CommentsChanged` . Yönetici statik yöntem tarafından örneklendiği için Oluşturucu özeldir `Create()` .

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

6. `Create()`Sağlayıcıyı alan veya gerekirse bir sağlayıcı oluşturan yöntemi ekleyin.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. İşleyiciyi ekleyin `CommentsChanged` .

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. İşleyiciyi ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> .

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. İşleyiciyi ekleyin <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> .

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
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

10. Yorumu çizen özel yöntemi ekleyin.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Kenarlığı açıklamasını eklemek için menü komutunu kullanın
 VSPackage metodunu uygulayarak bir açıklama kenarlığı oluşturmak için menü komutunu kullanabilirsiniz `MenuItemCallback` .

1. Aşağıdaki başvuruları MenuCommandTest projesine ekleyin:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. *AddAdornment. cs* dosyasını açın ve aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Yöntemi silin `Execute()` ve aşağıdaki komut işleyicisini ekleyin.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Etkin görünümü almak için kod ekleyin. `SVsTextManager`Etkin bir şekilde yararlanmak Için Visual Studio Kabuğu ' nu almalısınız `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Bu metin görünümü bir düzenleyici metin görünümünün bir örneği ise, bunu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> arabirime çevirebilirsiniz ve ardından onunla ilişkili olduğunu sağlayabilirsiniz <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> `Connector.Execute()` Comment kenarlığı sağlayıcısını alan ve kenarlığı ekleyen yöntemini çağırmak için öğesini kullanın. Komut işleyicisi şu kod gibi görünmelidir:

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

6. Addaddornmenthandler yöntemini AddAdornment oluşturucusunda AddAdornment komutu için işleyici olarak ayarlayın.

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

## <a name="build-and-test-the-code"></a>Kodu derleyin ve test edin

1. Çözümü oluşturun ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

2. Bir metin dosyası oluşturun. Biraz metin yazın ve ardından seçin.

3. **Araçlar** menüsünde, **kenarlığı Ekle öğesini çağır**' a tıklayın. Bir balon, metin penceresinin sağ tarafında görüntülenmelidir ve aşağıdaki metne benzer bir metin içermelidir.

     Adınız

     On puan...

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: bir içerik türünü bir dosya adı uzantısına bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
