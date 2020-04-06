---
title: Görünüm Süslemesi Oluşturma, Komutlar ve Ayarlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697641"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>İzlenme: Görünüm süslemesi, komutlar ve ayarlar (sütun kılavuzları) oluşturma
Visual Studio metin/kod düzenleyicisini komutlarla ve görünüm efektleriyle genişletebilirsiniz. Bu makalede, popüler bir uzantı özelliği, sütun kılavuzları ile başlamak için nasıl gösterir. Sütun kılavuzları, kodunuzu belirli sütun genişliklerine yönetmenize yardımcı olmak için metin düzenleyicisinin görünümüne görsel olarak hafif çizgiler çizilir. Özellikle, biçimlendirilmiş kod belgelere, blog gönderilerine veya hata raporlarına eklediğiniz örnekler için önemli olabilir.

Bu gözden geçirmede, siz:
- VSIX projesi oluşturma
- Editör görünümü süslemesi ekleme
- Kaydetme ve alma ayarları için destek ekleyin (sütun kılavuzları ve renkleri çizilir)
- Komut ekleme (sütun kılavuzları ekleme/kaldırma, renk değiştirme)
- Komutları Edit menüsüne ve metin belgesi bağlam menüsüne yerleştirin
- Visual Studio Komut Penceresinden komutları çağırmak için destek ekleme

  Bu Visual Studio Gallery[uzantısı](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)ile sütun kılavuzları özelliğinin bir sürümünü deneyebilirsiniz.

  > [!NOTE]
  > Bu gözden geçirme de, Visual Studio uzantı şablonları tarafından oluşturulan birkaç dosyaya büyük miktarda kod yapıştırın. Ancak, yakında bu izlenecek yol diğer uzantı örnekleri ile GitHub tamamlanmış bir çözüm anlamına gelecektir. Tamamlanan kod, genel şablon simgeleri kullanmak yerine gerçek komut simgelerine sahip olması açısından biraz farklıdır.

## <a name="get-started"></a>başlarken
Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="set-up-the-solution"></a>Çözümü ayarlama
İlk olarak, bir VSIX projesi oluşturmak, bir düzenleyici görünümü süseklemek ve sonra bir komut eklemek (komut sahibi bir VSPackage ekler). Temel mimari aşağıdaki gibidir:
- Görünüm başına bir nesne oluşturan bir `ColumnGuideAdornment` metin görünümü oluşturma dinleyiciniz var. Bu nesne, görünümün değiştirilmesi veya sütun kılavuzlarının gerektiği gibi değiştirilmesi, güncellenmesi veya yeniden çizilmesi yle ilgili olayları dinler.
- Visual Studio `GuidesSettingsManager` ayarları depolama okuma ve yazma işleyen bir var. Ayarlar yöneticisi, kullanıcı komutlarını destekleyen ayarları güncelleştirme işlemleri de vardır (sütun ekleme, sütun kaldırma, renk değiştirme).
- Kullanıcı komutlarınız varsa gerekli olan bir VSIP paketi vardır, ancak komutuygulama nesnesini başlatan yalnızca ortak koddur.
- Kullanıcı komutlarını `ColumnGuideCommands` çalıştıran ve *.vsct* dosyasında bildirilen komutların komut işleyicilerini bağlayan bir nesne vardır.

  **VSIX**. Proje oluşturmak için **Dosya &#124; Yeni ...** komutunu kullanın. Sol gezinti bölmesinde **C#** altındaki **Genişletilebilirlik** düğümini seçin ve sağ bölmede **VSIX Project'i** seçin. **Sütun Kılavuzları** adını girin ve projeyi oluşturmak için **Tamam'ı** seçin.

  **Süslemeyi görüntüleyin.** Çözüm Gezgini'ndeki proje düğümünde sağ işaretçi düğmesine basın. Yeni görünüm süsleme öğesi eklemek için Yeni Öğe &#124; Ekle komutunu **seçin.** Sol gezinti bölmesinde **Genişletilebilirlik &#124; Editörü'nu** seçin ve sağ bölmede **Editor Viewport Adornment'ı** seçin. Öğe adı olarak **ColumnGuideAdornment** adını girin ve eklemek için **Ekle'yi** seçin.

  Bu öğe şablonu projeye iki dosya (yanı sıra başvurular, ve benzeri) eklendi görebilirsiniz: **ColumnGuideAdornment.cs** ve **ColumnGuideAdornmentTextViewCreationListener.cs**. Şablonlar görünüme mor bir dikdörtgen çizer. Aşağıdaki bölümde, görünüm oluşturma dinleyicisindeki birkaç satırı değiştirir ve **ColumnGuideAdornment.cs**içeriğini değiştirirsiniz.

  **Komutlar**. **Çözüm Gezgini'nde,** proje düğümündeki sağ işaretçi düğmesine basın. Yeni görünüm süsleme öğesi eklemek için Yeni Öğe &#124; Ekle komutunu **seçin.** Sol gezinti bölmesinde **Genişletilebilirlik &#124; VSPackage'ı** seçin ve sağ bölmede **Özel Komut'u** seçin. Sütun Adı **SütunRehber Komutları'nı** öğe adı olarak girin ve **Ekle'yi**seçin. Çeşitli referanslar ek olarak, komutları ve paketi ekleyerek de **ColumnGuideCommands.cs**eklendi , **ColumnGuideCommandsPackage.cs**, ve **ColumnGuideCommandsPackage.vsct**. Aşağıdaki bölümde, komutları tanımlamak ve uygulamak için ilk ve son dosyaların içeriğini değiştirirsiniz.

## <a name="set-up-the-text-view-creation-listener"></a>Metin görünümü oluşturma dinleyicisini ayarlama
Editörde *ColumnGuideAdornmentTextViewCreationListener.cs* aç. Bu kod, Visual Studio metin görünümleri oluşturduğunda bir işleyici uygular. Görüntünün özelliklerine bağlı olarak işleyici çağrıldığında denetleyen öznitelikler vardır.

Kod da bir süs katmanı bildirmek gerekir. Editör görünümleri güncellediğinde, görünüm için süsleme katmanlarını alır ve bundan da süsleme öğelerini alır. Katmanınızın siparişini özniteliklere sahip diğer özelliklere göre bildirebilirsiniz. Aşağıdaki satırı değiştirin:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

bu iki satır ile:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Değiştirdiğiniz satır, bir süsleme katmanı bildiren bir öznitelik grubundadır. Değiştirdiğiniz ilk satır yalnızca sütun kılavuz çizgilerini nisbende değiştirir. Görünümdeki metni "önce" olarak çizmek, metnin arkasında veya altında göründükleri anlamına gelir. İkinci satır, sütun kılavuzu süslemelerinin belge kavramınıza uyan metin varlıkları için geçerli olduğunu bildirir, ancak örneğin, yalnızca düzenlenebilir metin için çalışmak üzere süslemeyi bildirebilirsiniz. Dil hizmeti ve [editör uzantı noktalarında](../extensibility/language-service-and-editor-extension-points.md) daha fazla bilgi var

## <a name="implement-the-settings-manager"></a>Ayarlar yöneticisini uygulama
*GuidesSettingsManager.cs* içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present.  Allow user to remove the last column
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Bu\<kodun çoğu ayarlar biçimini oluşturur ve ayrıştırır:\<"RGB(int>, int>,\<int>) \<int>, \<int>, ...".  Sonundaki tümerler, sütun kılavuzlarını istediğiniz tek tabanlı sütunlardır. Sütun kılavuzları uzantısı, tüm ayarlarını tek bir ayar değer dizesinde yakalar.

Kodun vurgulanmasına değer bazı bölümleri vardır. Aşağıdaki kod satırı, Visual Studio'nun ayarlar depolaması için yönetilen sarıcıyı almasını sağlar. Çoğunlukla, bu Windows kayıt defteri üzerinde özetler, ancak bu API depolama mekanizması bağımsızdır.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio ayarları depolama, tüm ayarları benzersiz olarak tanımlamak için bir kategori tanımlayıcısı ve ayar tanımlayıcısı kullanır:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Kategori adı olarak `"Text Editor"` kullanmanız gerekmez. İstediğin her şeyi seçebilirsin.

İlk birkaç işlev, ayarları değiştirmek için giriş noktalarıdır. İzin verilen maksimum kılavuz sayısı gibi üst düzey kısıtlamaları denetlerler.  Daha sonra, `WriteSettings`bir ayar dizesi oluşturan `GuideLinesConfiguration`ve özelliği ayarlar , diyoruz. Bu özelliğiayarlamak, ayarlar değerini Visual Studio ayarları deposuna kaydeder ve `ColumnGuideAdornment` her biri metin görünümüyle ilişkili tüm nesneleri güncelleştirmek için `SettingsChanged` olayı ateşler.

Ayarları değiştiren komutları uygulamak için `CanAddGuideline`kullanılan birkaç giriş noktası işlevi vardır. Visual Studio menüleri gösterdiğinde, komutun şu anda etkin olup olmadığını, adının ne olduğunu ve benzeri olduğunu görmek için komut uygulamalarını sorgular.  Aşağıda komut uygulamaları için bu giriş noktalarını nasıl bağladığınızı görebilirsiniz. Komutlar hakkında daha fazla bilgi için [menüleri ve komutları genişlet'e](../extensibility/extending-menus-and-commands.md)bakın.

## <a name="implement-the-columnguideadornment-class"></a>ColumnGuideAdornment sınıfını uygulayın
Sınıf, `ColumnGuideAdornment` süsler olabilir her metin görünümü için anında. Bu sınıf, görünümün değiştirilmesi veya ayarların değiştirilmesi ve sütun kılavuzlarının gerektiği şekilde güncelleştirilmesi veya yeniden çizilmesi yle ilgili olayları dinler.

*ColumnGuideAdornment.cs* içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Bu sınıfın örnekleri ilişkili <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> ve görünümde çizilen `Line` nesnelerin listesini tutun.

Oluşturucu (Visual `ColumnGuideAdornmentTextViewCreationListener` Studio yeni görünümler oluşturduğunda çağrılır) sütun kılavuzu `Line` nesneleri oluşturur.  Oluşturucu `SettingsChanged` ayrıca olay (tanımlı) `GuidesSettingsManager`ve görünüm olayları `LayoutChanged` ve `Closed`için işleyicileri ekler.

Olay, `LayoutChanged` Visual Studio'nun görünümü oluşturması da dahil olmak üzere görünümdeki çeşitli değişiklikler nedeniyle yangın lar. Işleyici `OnViewLayoutChanged` yürütmeyi çağırır. `AddGuidelinesToAdornmentLayer` Kod, `OnViewLayoutChanged` yazı tipi boyutu değişiklikleri, görünüm olukları, yatay kaydırma gibi değişikliklere göre satır konumlarını güncelleştirmesi gerekip gerekmeden belirlemez. Kod, `UpdatePositions` kılavuz çizgilerinin karakterler arasında veya metin satırında belirtilen karakter ofsetinde bulunan metin sütunundan hemen sonra çizilmesine neden olur.

Ayarlar değiştirildiğinde `SettingsChanged` işlev, yeni ayarlar `Line` ne olursa olsun tüm nesneleri yeniden oluşturur. Satır konumlarını ayarladıktan sonra, kod `Line` önceki tüm `ColumnGuideAdornment` nesneleri süsleme katmanından kaldırır ve yenilerini ekler.

## <a name="define-the-commands-menus-and-menu-placements"></a>Komutları, menüleri ve menü yerleşimlerini tanımlama
Komutları ve menüleri bildirmek, komut grupları veya menüleri çeşitli diğer menülere yerleştirmek ve komut işleyicilerini bağlamak çok şey olabilir. Bu izbis, komutların bu uzantıda nasıl çalıştığını vurgular, ancak daha derin bilgi için [bkz.](../extensibility/extending-menus-and-commands.md)

### <a name="introduction-to-the-code"></a>Koda giriş
Sütun Kılavuzları uzantısı, bir araya ait bir komut grubunu bildiren (sütun ekleme, sütun kaldırma, satır rengini değiştirme) ve ardından bu grubu düzenleyicinin bağlam menüsünün alt menüsüne yerleştirmeyi gösterir.  Sütun Kılavuzları uzantısı da ana **Düzenle** menüsüne komutları ekler, ancak aşağıda ortak bir desen olarak tartışılan, bunları görünmez tutar.

Komutların uygulanmasıiçin üç bölüm vardır: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct ve ColumnGuideCommands.cs. Şablonlar tarafından oluşturulan kod, uygulama olarak bir iletişim kutusu açılan **Araçlar** menüsüne bir komut koyar. Basit olduğundan *.vsct* ve *ColumnGuideCommands.cs* dosyalarında bunun nasıl uygulandığına bakabilirsiniz. Aşağıdaki dosyalardaki kodu değiştirirsiniz.

Paket kodu, Visual Studio'nun uzantının komutlar sunduğunu keşfetmesi ve komutların nereye yerleştirileni bulması için gerekli ortak bildirimleri içerir. Paket baş harfe döndüğünde, komutlar uygulama sınıfını anında alarır. Komutlarla ilgili paketler hakkında daha fazla bilgi için [menüleri ve komutları genişlet'e](../extensibility/extending-menus-and-commands.md)bakın.

### <a name="a-common-commands-pattern"></a>Ortak bir komut deseni
Sütun Kılavuzları uzantısındaki komutlar Visual Studio'da çok yaygın bir modele örnektir. İlgili komutları bir gruba koyarsınız ve bu grubu genellikle "`<CommandFlag>CommandWellOnly</CommandFlag>`komutu görünmez yapmak için ayarlanmış " ile bir ana menüye koyarsınız.  Ana menülere komutkoymak **(Edit**gibi) **onlara, Araçlar Seçenekleri'nde**anahtar bağlamaları yeniden atarken komutları bulmak için yararlı olan güzel adlar **(Edit.AddColumnGuide**gibi) verir. **Komut Penceresinden**komutları çağırArak tamamlama almak için de yararlıdır.

Daha sonra, kullanıcının komutları kullanmasını beklediğiniz bağlam menülerine veya alt menülere komut grubu eklersiniz. Visual Studio `CommandWellOnly` yalnızca ana menüler için görünmezlik bayrağı olarak davranır. Aynı komut grubunu bağlam menüsüne veya alt menüye yerleştirdiğinizde, komutlar görünür.

Ortak desenin bir parçası olarak, Sütun Kılavuzları uzantısı tek bir alt menü tutan ikinci bir grup oluşturur. Sırayla alt menü dört sütunlu kılavuz komutları ile ilk grubu içerir. Alt menüyü tutan ikinci grup, çeşitli bağlam menülerine yerleştirdiğiniz ve bu bağlam menülerine bir alt menü koyan yeniden kullanılabilir varlıktır.

### <a name="the-vsct-file"></a>.vsct dosyası
*.vsct* dosyası komutları ve nereye gittiklerini, simgelerle birlikte ve saire bildirir. *.vsct* dosyasının içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**REHBER CAND** Visual Studio'nun komut işleyicilerinizi bulup çağırabilmesi için, *ColumnGuideCommandsPackage.cs* dosyasında (proje öğesi şablonundan oluşturulan) bildirilen GUID paketinin *.vsct* dosyasında (yukarıdan kopyalanan) bildirilen GUID paketiyle eşleştiğinden emin olmanız gerekir. Bu örnek kodu yeniden kullanırsanız, bu kodu kopyalamış olabilecek başka biriyle çakışmamak için farklı bir GUID'e sahip olduğunuzdan emin olmalısınız.

Bu satırı *ColumnGuideCommandsPackage.cs* olarak bulun ve GUID'i tırnak işaretleri arasında kopyalayın:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Ardından, *.vsct* dosyasına GUID'i yapıştırın, böylece bildirimlerinizde `Symbols` aşağıdaki satır alabilirsiniz:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Komut kümesi ve bitmap resim dosyası için GUIDs uzantıları için de benzersiz olmalıdır:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Ancak, kodun çalışması için komut kümesini ve bitmap görüntü GUID'lerini değiştirmeniz gerekmez. GUID komut kümesinin *ColumnGuideCommands.cs* dosyasındaki bildirimi eşleştirmesi gerekir, ancak bu dosyanın içeriğini de siz değiştirirsiniz; bu nedenle, GUID'ler eşleşecektir.

*.vsct* dosyasındaki diğer GUID'ler, sütun kılavuzu komutlarının eklendiği önceden varolan menüleri tanımlar, böylece hiçbir zaman değişmezler.

**Dosya bölümleri**. *.vsct'ın* üç dış bölümü vardır: komutlar, yerleşimler ve semboller. Komutlar bölümünde komut grupları, menüler, düğmeler veya menü öğeleri ve simgeler için bit eşlemleri tanımlanır. Yerleşimler bölümü, grupların menülerde veya ek yerleşimlerde önceden varolan menülere nereye gittiğini bildirir. Semboller *bölümü,.vsct* dosyasının başka bir yerinde kullanılan tanımlayıcıları bildirir ve bu da *.vsct* kodunu her yerde GUID ve hex numaralarına sahip olmaktan daha okunabilir hale getirir.

**Komutlar bölümü, gruplar tanımları**. Komutlar bölümü önce komut gruplarını tanımlar. Komut grupları, grupları ayıran hafif gri çizgilere sahip menülerde gördüğünüz komutlardır. Bir grup, bu örnekte olduğu gibi alt menünün tamamını doldurabilir ve bu durumda gri ayırma satırlarını göremezsin. *.vsct* dosyaları iki grup `GuidesMenuItemsGroup` bildirir, bu `IDM_VS_MENU_EDIT` (ana **Edit** menüsü) ve `GuidesContextMenuGroup` bu `IDM_VS_CTXT_CODEWIN` (kod düzenleyicisinin bağlam menüsü) için ebeveynli olduğunu.

İkinci grup bildiriminin `0x0600` bir önceliği vardır:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Amaç, sütun kılavuzları alt menüsünü alt menü grubunu eklediğiniz herhangi bir bağlam menüsünün sonuna koymaktır. Ancak, en iyi bildiğinizi varsaymamalı ve alt menüyü her `0xFFFF`zaman bir öncelik kullanarak son olmaya zorlamamalısınız. Alt menünüzün yerleştirdiğiniz bağlam menülerinde nerede olduğunu görmek için numarayı denemeniz gerekir. Bu durumda, `0x0600` gördüğünüz kadar menülerin sonuna koymak için yeterince yüksek, ancak bu arzu edilirse sütun kılavuzları uzantısı daha düşük olması için uzantıları tasarlamak için başka sıyrık için yer bırakır.

**Komutlar bölümü, menü tanımı**. Daha sonra, komut bölümü alt `GuidesSubMenu`menü tanımlar `GuidesContextMenuGroup`, . İlgili `GuidesContextMenuGroup` tüm bağlam menülerine eklediğiniz gruptur. Yerleşimler bölümünde kod, bu alt menüde dört sütunlu kılavuz komutları bulunan grubu yerleştirir.

**Komutlar bölümü, düğmeler tanımları**. Komutlar bölümünde daha sonra dört sütunlu kılavuzkomutları olan menü öğeleri veya düğmeleri tanımlar. `CommandWellOnly`, yukarıda tartışılan, komutları bir ana menüye yerleştirildiğinde görünmez anlamına gelir. Menü öğesi düğmesi bildirimlerinden ikisinin (kılavuz ekleme ve `AllowParams` kaldırma kılavuzu) da bir bayrağı vardır:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Bu bayrak, ana menü yerleşimlerine sahip olmanın yanı sıra Visual Studio komut işleyicisini çağırdığında bağımsız değişkenleri alan komutu da sağlar.  Kullanıcı komutu Komut Penceresinden çalıştırUrsa, bağımsız değişken olay bağımsız değişkeninde komut işleyicisine geçirilir.

**Komut bölümleri, bitmaps tanımları**. Son olarak, komutlar bölümünde komutlar için kullanılan bit eşlemleri veya simgeleri bildirir. Bu bölüm, proje kaynağını tanımlayan ve kullanılan simgelerin tek tabanlı dizinlerini listeleyen basit bir bildirimdir. *.vsct* dosyasının semboller bölümü dizin olarak kullanılan tanımlayıcıların değerlerini bildirir. Bu izlenecek yol, projeye eklenen özel komut öğesi şablonuyla sağlanan bit eşlemi şeridini kullanır.

**Yerleşimler bölümü**. Komutlar bölümünden sonra yerleşimler bölümüdür. Bunlardan ilki, kodun yukarıda tartışılan ve dört sütunlu kılavuz komutlarını komutların göründüğü alt menüye tutan ilk grubu eklediği yerdir:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Diğer yerleşimlerin tümü diğer `GuidesContextMenuGroup` düzenleyici bağlam `GuidesSubMenu`menülerine (içerir) ekler. Kod, `GuidesContextMenuGroup`kod düzenleyicisinin bağlam menüsüne eklenmiş olarak beyan edildiğinde. Bu nedenle kod düzenleyicisinin bağlam menüsü için bir yerleşim görmüyorsunuz.

**Semboller bölümü**. Yukarıda belirtildiği gibi, semboller bölümü *.vsct* dosyasının başka bir yerinde kullanılan tanımlayıcıları bildirir ve bu da *.vsct* kodunu her yerde GUID ve hex numaralarına sahip olmaktan daha okunabilir hale getirir. Bu bölümdeki önemli noktalar, GUID paketinin paket sınıfındaki bildirimle aynı fikirde olması gerektiğidir. Guid komut kümesi, komut uygulama sınıfındaki bildirimle aynı fikirde olmalıdır.

## <a name="implement-the-commands"></a>Komutları uygulayın
*ColumnGuideCommands.cs* dosyası komutları uygular ve işleyicileri bağlar. Visual Studio paketi yükler ve başlatılması, sırayla komutları uygulama sınıfı çağırır. `Initialize` Komutlar başlatma sadece sınıf anında ve oluşturucu tüm komut işleyicileri kadar bağlanır.

*ColumnGuideCommands.cs* dosyanın içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Başvuruları düzeltin.** Şu anda bir referansı kaçırıyorsun. Çözüm Gezgini'ndeki Başvurudüğümün sağ işaretçi düğmesine basın. Ekle **...** komutunu seçin. **Başvuru Ekle** iletişim kutusunda sağ üst köşede bir arama kutusu vardır. "Editör" (çift tırnak olmadan) girin. **Microsoft.VisualStudio.Editor** öğesini seçin (yalnızca öğeyi seçmekle kalmayıp öğenin solundaki kutuyu işaretlemelisiniz) ve başvuruyu eklemek için **Tamam'ı** seçin.

**Başlatma**.  Paket sınıfı başharfe geçtiğinde, `Initialize` komutlar uygulama sınıfını çağırır. Başlatma `ColumnGuideCommands` sınıfı anında kaydeder ve sınıf örneğini ve paket başvuruyu sınıf üyelerine kaydeder.

Sınıf oluşturucusundaki komut işleyici bağlantılarından birine bakalım:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Bir `OleMenuCommand`. Visual Studio, Microsoft Office komut sistemini kullanır. Bir anvesirirken anahtar `OleMenuCommand` bağımsız değişkenler, Visual`AddColumnGuideExecuted`Studio komutu (`AddColumnGuideBeforeQueryStatus`) ve komut kimliği ile bir menü gösterdiğinde aramak için gereken işlevi uygulayan işlevdir. Visual studio, komutun menünün belirli bir ekranı için kendisini görünmez veya soluk hale getirebilmek için menüde bir komut göstermeden önce sorgu durumu işlevini çağırır (örneğin, seçim yoksa **Kopya'yı** devre dışı bırakmak), simgesini değiştirir ve hatta adını değiştirir (örneğin, Bir Şeyi Kaldır'dan Kaldır'dan) vb. Komut kimliği *,vsct* dosyasında bildirilen bir komut kimliğiyle eşleşmelidir. Komut kümesi ve sütun kılavuzları için dizeleri komut eklemek *.vsct* dosyası ve *ColumnGuideCommands.cs*arasında eşleşmesi gerekir.

Aşağıdaki satır, kullanıcıların Komut Penceresi üzerinden komutu çağırmaları için yardım sağlar (aşağıda açıklanmıştır):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Sorgu durumu**. Sorgu durumu `AddColumnGuideBeforeQueryStatus` işlevleri `RemoveColumnGuideBeforeQueryStatus` ve bazı ayarları kontrol (kılavuzları veya max sütun max sayısı gibi) veya kaldırmak için bir sütun kılavuzu varsa. Koşullar uygunsa komutları etkinleştirirler.  Visual Studio her menü de ve menüdeki her komut için çalıştırıldığı için sorgu durumu işlevlerinin verimli olması gerekir.

 **AddColumnGuideExecuted işlevi**. Bir kılavuz ekleyerek ilginç kısmı geçerli editör görünümü ve caret konumu anlamaya olduğunu.  İlk olarak, `GetApplicableColumn`bu işlev, komut işleyicisinin olay bağımsız değişkenlerinde kullanıcı tarafından sağlanan bir bağımsız değişken olup olmadığını denetleyen ve yoksa işlev düzenleyicinin görünümünü denetleyen çağrıları çağırır:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn`kodun bir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> görünüm elde etmek için biraz kazmak zorunda.  Eğer , `GetActiveTextView`ve `GetActiveView` `GetTextViewFromVsTextView`, bunu nasıl yapacağını görebilirsiniz üzerinden iz. Aşağıdaki kod, geçerli seçimden başlayarak, seçimin çerçevesini alarak, daha sonra çerçevenin DocView'ını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> iVsTextView'den almak, sonra bir görünüm ana bilgisayarını almak ve son olarak IWpfTextView'i almak üzere özetlenmiş ilgili koddur:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Bir IWpfTextView'e sahip olduktan sonra, bakıcının bulunduğu sütunu alabilirsiniz:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Kullanıcının tıklatıldığı geçerli sütunda, kod yalnızca sütunu eklemek veya kaldırmak için ayarlar yöneticisini çağırır. Ayarlar yöneticisi, tüm `ColumnGuideAdornment` nesnelerin dinlediği olayı ateşler. Olay çıktığında, bu nesneler ilişkili metin görünümlerini yeni sütun kılavuzu ayarlarıyla günceller.

## <a name="invoke-command-from-the-command-window"></a>Komut Penceresinden komut çağırma
Sütun kılavuzları örneği, kullanıcıların genişletilebilirlik biçimi olarak Komut Penceresinden iki komut çağırmalarını sağlar. Diğer Windows **&#124; &#124; Komut Penceresi** komutunu &#124; Görünüm'u kullanırsanız, Komut Penceresi'ni görebilirsiniz. Komut Penceresi ile "düzenleme"yi girerek etkileşimkurabilirsiniz ve komut adı tamamlama ve bağımsız değişken 120'yi sağlayarak aşağıdaki sonuca sahip olabilirsiniz:

```csharp
> Edit.AddColumnGuide 120
>
```

Bu davranışı etkinleştiren örnekparçaları *.vsct* dosya bildirimleri, `ColumnGuideCommands` komut işleyicileri bağlandığında sınıf oluşturucu ve olay bağımsız değişkenlerini denetleyen komut işleyicisi uygulamaları bulunmaktadır.

Komutlar`<CommandFlag>CommandWellOnly</CommandFlag>` **Edit** menüsündeki UI'de gösterilmese de , *.vsct* dosyasında " " " ve **Edit** ana menüsündeki yerleşimleri gördünuz. Ana **Edit** menüsünde olması onlara **Edit.AddColumnGuide**gibi adlar verir. Dört komutu tutan komutgrubu bildirimi grubu doğrudan **Edit** menüsüne yerleştirdi:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Düğmeler bölümü daha sonra `CommandWellOnly` ana menüde görünmez tutmak için komutları ilan etti ve onları `AllowParams`ilan:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

`ColumnGuideCommands` Sınıf oluşturucusunda komut işleyicisi kanca kodunu gördün, izin verilen parametrenin açıklamasını sağladı:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Geçerli bir `GetApplicableColumn` sütun `OleMenuCmdEventArgs` için düzenleyicinin görünümünü denetlemeden önce işlevin bir değeri denetlediğinizi gördün:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="try-your-extension"></a>Uzantınızı deneyin
Artık Sütun Kılavuzları uzantınızı yürütmek için **F5** tuşuna basabilirsiniz. Bir metin dosyası açın ve kılavuz satırları eklemek, bunları kaldırmak ve renklerini değiştirmek için editörün bağlam menüsünü kullanın. Sütun kılavuzu eklemek için metne (satırın sonundan beyaz boşluk geçmez) tıklayın veya düzenleyici satırdaki son sütuna ekler. Komut Penceresi'ni kullanır ve komutları bir bağımsız değişkenle çağırırsanız, her yere sütun kılavuzları ekleyebilirsiniz.

Farklı komut yerleşimlerini denemek, adları değiştirmek, simgeleri değiştirmek ve Visual Studio'nun menülerde en son kodu göstermesiyle ilgili herhangi bir sorun yaşıyorsanız, hata ayıklama yaptığınız deneysel kovanı sıfırlayabilirsiniz. **Windows Başlat Menüsü'nü** getirin ve "sıfırlama" yazın. Komutu arayın ve çalıştırın, **Sonraki Visual Studio Deneysel Örneği Sıfırla.** Bu komut, tüm uzantı bileşenlerinin deneysel kayıt defteri kovanı temizler. Ayarları bileşenlerden temizlemez, bu nedenle Visual Studio'nun deneysel kovanını kapattığınızda sahip olduğunuz kılavuzlar, kodunuz bir sonraki lansmanda ayarlar deposunu okuduğunda hala oradadır.

## <a name="finished-code-project"></a>Bitmiş kod projesi
Yakında Visual Studio Genişletilebilirlik örneklerinden oluşan bir GitHub projesi olacak ve tamamlanan proje orada olacak. Bu makale, bu olduğunda orada işaret etmek için güncelleştirilir. Tamamlanan örnek proje farklı kılavuzlara sahip olabilir ve komut simgeleri için farklı bir bit eşlem şeridine sahip olacaktır.

Bu Visual Studio Gallery[uzantısı](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)ile sütun kılavuzları özelliğinin bir sürümünü deneyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Editörün içinde](../extensibility/inside-the-editor.md)
- [Editör ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md)
- [Düzenleyici öğesi şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)
