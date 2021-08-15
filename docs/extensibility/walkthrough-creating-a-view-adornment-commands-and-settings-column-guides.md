---
title: görünüm kenarlığı, komutlar ve Ayarlar oluşturma | Microsoft Docs
description: bu kılavuzu kullanarak Visual Studio kod düzenleyicisini sütun kılavuzlarıyla genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ae56da8cc30e40048fd454b2f99105d4dcce2dbd9d97e679bfca5be4d4f3b06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121234830"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>İzlenecek yol: Görünüm kenarlığı, komutlar ve ayarlar oluşturma (sütun Kılavuzu)
Visual Studio metin/kod düzenleyicisini komutlarla genişletebilir ve etkileri görüntüleyebilirsiniz. Bu makalede, popüler bir uzantı özelliği olan sütun kılavuzlarıyla çalışmaya başlama işlemi gösterilmektedir. Sütun kılavuzlarında, kodunuzun belirli sütun genişliklerine yönetilmesine yardımcı olmak için metin düzenleyici görünümünde çizilmiş görsel açıdan açık çizgiler bulunur. Özellikle, belge, blog gönderilerini veya hata raporlarını içeren örnekler için biçimlendirilen kod önemli olabilir.

Bu izlenecek yolda şunları yapabilirsiniz:
- VSıX projesi oluşturma
- Bir düzenleyici görünümü kenarlığı ekleme
- Ayarları kaydetme ve alma (sütun kılavuzlarını ve bunların renklerini çizme) için destek ekleme
- Komut ekleme (sütun kılavuzlarını Ekle/Kaldır, renklerini değiştir)
- Komutları düzenleme menüsüne ve metin belgesi bağlam menülerine yerleştirin
- komutları Visual Studio komut penceresinden çağırma desteği ekleyin

  sütun kılavuzu özelliğinin bir sürümünü bu Visual Studio galeri[uzantısıyla](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)deneyebilirsiniz.

  > [!NOTE]
  > bu kılavuzda, Visual Studio uzantısı şablonları tarafından oluşturulan birkaç dosyaya büyük miktarda kod yapıştırırsınız. ancak yakında bu izlenecek yol, diğer uzantı örnekleriyle birlikte GitHub tamamlanan bir çözüme başvuracaktır. Tamamlanan kod, generictemplate simgeleri kullanmak yerine gerçek komut simgelerine sahip olan biraz farklıdır.

## <a name="get-started"></a>başlarken
Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Çözümü ayarlama
İlk olarak, bir VSıX projesi oluşturun, bir düzenleyici görünümü kenarlığı ekleyin ve ardından bir komut (komutuna bir VSPackage ekler) ekleyin. Temel mimari aşağıdaki gibidir:
- Görünüm başına nesne oluşturan bir metin görünümü oluşturma dinleyicisine sahipsiniz `ColumnGuideAdornment` . Bu nesne, sütun kılavuzlarını gerektiği şekilde değiştirme, güncelleştirme veya yeniden çizme gibi ayarlarla ilgili olayları dinler.
- `GuidesSettingsManager`Visual Studio ayarları depolamadan okumayı ve yazmayı işleyen bir. Ayarlar Yöneticisi, Kullanıcı komutlarını destekleyen ayarları güncelleştirme (sütun Ekle, sütunu Kaldır, rengi değiştir) için de işlemler içerir.
- Kullanıcı komutlarınız varsa gerekli bir VSıP paketi vardır ancak komutlar uygulama nesnesini Başlatan yalnızca ortak koddur.
- `ColumnGuideCommands`Kullanıcı komutlarını çalıştıran bir nesne vardır ve *. vsct* dosyasında belirtilen komutlar için komut işleyicilerini takar.

  **VSIX**. Bir proje oluşturmak için **File &#124; New...** komutunu kullanın. sol gezinti bölmesindeki **C#** altında **genişletilebilirlik** düğümünü seçin ve sağ bölmedeki **vsıx Project** seçin. **Columnguides** adını girip projeyi oluşturmak için **Tamam** ' ı seçin.

  **Kenarlığı görüntüleyin**. Çözüm Gezgini proje düğümünde sağ işaretçi düğmesine basın. Yeni bir View kenarlığı öğesi eklemek için **&#124; yeni öğe Ekle...** komutunu seçin. Sol gezinti bölmesinde **genişletilebilirlik &#124; düzenleyici** ' yi seçin ve sağ bölmedeki **Düzenleyici Görünüm penceresi kenarlığı** ' ni seçin. Öğe adı olarak **ColumnGuideAdornment** adını girin ve eklemek için **Ekle** ' yi seçin.

  Bu öğe şablonunun projeye iki dosya eklendiğini (Ayrıca, başvurular vb.) görebilirsiniz: **ColumnGuideAdornment. cs** ve **Columnkılavuz Donnmenttextviewcreationlistener. cs**. Şablonlar, görünümde mor bir dikdörtgen çizer. Aşağıdaki bölümde, görünüm oluşturma dinleyicisinde birkaç satırı değiştirirsiniz ve **ColumnGuideAdornment. cs** içeriğini değiştirirsiniz.

  **Komutlar**. **Çözüm Gezgini**, proje düğümündeki sağ işaretçi düğmesine basın. Yeni bir View kenarlığı öğesi eklemek için **&#124; yeni öğe Ekle...** komutunu seçin. Sol gezinti bölmesinde **genişletilebilirlik &#124; VSPackage** ' ı seçin ve sağ bölmedeki **özel komut** ' yi seçin. Sütun adı olarak **Columnkılavuz komutlarını** girin ve **Ekle**' yi seçin. Birkaç başvuruya ek olarak, komutlar ve paket eklendiğinde **Columnkılavuz komutları. cs**, **columnkılavuz commandspackage. cs** ve **columnkılavuz commandspackage. vsct** de eklenmiştir. Aşağıdaki bölümde, komutları tanımlamak ve uygulamak için birinci ve son dosyaların içeriğini değiştirirsiniz.

## <a name="set-up-the-text-view-creation-listener"></a>Metin görünümü oluşturma dinleyicisini ayarlama
Düzenleyicide *Columneditdonnmenttextviewcreationlistener. cs* dosyasını açın. bu kod, her Visual Studio metin görünümü oluşturduğunda için bir işleyici uygular. İşleyicinin, görünümün özelliklerine bağlı olarak ne zaman çağrıldığını denetleyen öznitelikler vardır.

Kod ayrıca bir kenarlığı katmanı bildirmelidir. Düzenleyici görünümleri güncelleştirdiğinde, görünüm için kenarlığı katmanlarını alır ve bu kenarlığı öğelerini alır. Katman sıralamasına göre, diğer özelliklere göre katmanınızı bildirebilirsiniz. Aşağıdaki satırı değiştirin:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

Şu iki satır ile:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Değiştirdiğiniz çizgi, bir kenarlığı katmanını bildiren bir öznitelik grubu içinde yer alır. Değiştirdiğiniz ilk satır yalnızca sütun kılavuzu çizgilerinin göründüğü değişikliklerle değiştirilir. "Önce" satırlarını çizme, görünümdeki metin metnin arkasında veya altında göründüğü anlamına gelir. İkinci satır, sütun kılavuzunun bir belge kavramına uyan metin varlıkları için geçerli olduğunu bildirir, ancak örneğin yalnızca düzenlenebilir metin için çalışmak üzere kenarlığı bildirebilirsiniz. [Dil hizmeti ve Düzenleyici uzantı noktalarında](../extensibility/language-service-and-editor-extension-points.md) daha fazla bilgi mevcuttur

## <a name="implement-the-settings-manager"></a>Ayarlar yöneticisini uygulama
Aşağıdaki kodla, *kılavuz. cs* ' nin içeriğini (aşağıda açıklanmıştır) değiştirin:

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

Bu kodun çoğu, ayarlar biçimini oluşturur ve ayrıştırır: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Sonundaki tamsayılar, sütun kılavuzlarını istediğiniz tek tabanlı sütunlardır. Sütun kılavuzu uzantısı, tüm ayarlarını tek bir ayar değeri dizesinde yakalar.

Kod vurgulamanın bazı bölümleri vardır. aşağıdaki kod satırı, ayarlar depolama için Visual Studio yönetilen sarmalayıcı alır. çoğu bölüm için, bu Windows kayıt defteri üzerinden soyutlanıyor, ancak bu apı depolama mekanizmasından bağımsızdır.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Visual Studio settings storage, tüm ayarları benzersiz şekilde tanımlamak için bir kategori tanımlayıcısı ve bir ayar tanımlayıcısı kullanır:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Kategori adı olarak kullanmak zorunda değilsiniz `"Text Editor"` . Dilediğiniz şeyi seçebilirsiniz.

İlk birkaç işlev, ayarları değiştirmek için giriş noktalarıdır. İzin verilen en fazla kılavuz sayısı gibi üst düzey kısıtlamaları kontrol ederler.  Ardından, `WriteSettings` bir ayarlar dizesini oluşturan ve özelliğini ayarlayan çağrılarsa `GuideLinesConfiguration` . bu özelliği ayarlamak, ayarlar değerini Visual Studio ayarları deposuna kaydeder ve `SettingsChanged` `ColumnGuideAdornment` her biri bir metin görünümüyle ilişkili olan tüm nesneleri güncelleştirmek için olayı tetikler.

`CanAddGuideline`Ayarları değiştiren komutları uygulamak için kullanılan gibi birkaç giriş noktası işlevi vardır. Visual Studio menüleri gösteriyorsa, komutun şu anda etkin olup olmadığını, adının ne olduğunu ve bu şekilde çalıştığını görmek için komut uygulamalarını sorgular.  Aşağıda, komut uygulamaları için bu giriş noktalarını nasıl yedeklerim görürsünüz. Komutlar hakkında daha fazla bilgi için bkz. [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>ColumnGuideAdornment sınıfını uygulama
`ColumnGuideAdornment`Sınıfı, donatılamalarda bulunan her metin görünümü için oluşturulur. Bu sınıf, görünüm değişikliği veya ayarları değiştirme hakkındaki olayları dinler ve güncelleştirme ya da yeniden çizim sütununu gerektiği şekilde yönlendirir.

*ColumnGuideAdornment. cs* içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

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

Bu sınıfın örnekleri, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> görünümde çizilen bir nesne listesini ve ilişkili bir listesini tutar `Line` .

oluşturucu ( `ColumnGuideAdornmentTextViewCreationListener` Visual Studio yeni görünümler oluşturduğunda çağrılır), sütun kılavuzu `Line` nesnelerini oluşturur.  Oluşturucu Ayrıca olay için işleyiciler ekler `SettingsChanged` (içinde tanımlanmıştır `GuidesSettingsManager` ) ve olayları görüntüleme `LayoutChanged` ve `Closed` .

bu `LayoutChanged` olay, Visual Studio görünümü oluştururken de dahil olmak üzere görünümdeki çeşitli değişiklik türleri nedeniyle ateşlenir. `OnViewLayoutChanged`İşleyici `AddGuidelinesToAdornmentLayer` yürütmek için çağırır. İçindeki kod, `OnViewLayoutChanged` yazı tipi boyutu değişiklikleri, görüntüleme boşluğu, yatay kaydırma vb. gibi değişikliklere göre satır konumlarını güncelleştirme gerekip gerekmediğini belirler. İçindeki kod, `UpdatePositions` kılavuz çizgilerinin, metin satırındaki belirtilen karakter kaydırmasında yer alan metin sütununun arasına veya sonuna kadar çizim yapmasına neden olur.

Her ayar işlevi değiştirdiğinde, `SettingsChanged` tüm `Line` nesneleri yeni ayarların bulunduğu her şey yeniden oluşturur. Satır konumlarını ayarladıktan sonra kod, önceki tüm `Line` nesneleri `ColumnGuideAdornment` kenarlığı katmanından kaldırır ve yenilerini ekler.

## <a name="define-the-commands-menus-and-menu-placements"></a>Komutları, menüleri ve menü yerleştirmelerinin tanımlayın
Komutların ve menülerin bildirilmesi, çeşitli diğer menülere komut veya menü grupları yerleştirilmesi ve komut işleyicilerini bağlamak çok fazla olabilir. Bu kılavuzda, komutların bu uzantıda nasıl çalıştığı vurgulanmıştır, ancak daha ayrıntılı bilgi için bkz. [menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Koda giriş
Sütun Kılavuzları uzantısı, birlikte ait olan bir komut grubunu (sütun ekleme, sütunu kaldırma, satır rengini değiştirme) ve ardından bu grubu düzenleyicinin bağlam menüsünün alt menüsüne yerleştirmeyi gösterir.  Sütun Kılavuzları uzantısı, komutları ana Düzenle **menüsüne** de ekler ancak aşağıda ortak bir desen olarak ele alınarak görünmelerini sağlar.

Komut uygulamasının üç parçası vardır: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct ve ColumnGuideCommands.cs. Şablonlar tarafından oluşturulan kod, Araçlar menüsüne uygulama olarak **bir** iletişim kutusu açılan bir komut koyar. Basit bir işlem olduğu için *bunun .vsct* ve *ColumnGuideCommands.cs* dosyalarında nasıl uygulandığını bakabilirsiniz. Aşağıdaki dosyalarda yer alan kodu değiştirirsiniz.

Paket kodu, uzantının komutlar Visual Studio komutları bulmak ve komutların nereye ekli olduğunu bulmak için gereken ortak bildirimleri içerir. Paket başlatılırken komutlar uygulama sınıfının örneğini oluşturur. Komutlarla ilgili paketler hakkında daha fazla bilgi için bkz. [Menüleri ve komutları genişletme.](../extensibility/extending-menus-and-commands.md)

### <a name="a-common-commands-pattern"></a>Ortak komut deseni
Sütun Kılavuzları uzantısında yer alan komutlar, verilerde çok yaygın kullanılan bir Visual Studio. İlgili komutları bir gruba ve bu grubu bir ana menüye, genellikle " " komutu görünmez yapmak `<CommandFlag>CommandWellOnly</CommandFlag>` için ayarlanmış şekilde ayarlarsınız.  Ana menülere (Düzenle **gibi)** komutlar koymak, araçlar seçenekler'de anahtar bağlamalarını yeniden atarken komutları bulmak için yararlı olan güzel adlar **(Edit.AddColumnGuide** gibi) **verir.** Komut Penceresinden komutlar kullanılırken tamamlanmasını almak için **de yararlıdır.**

Ardından komut grubunu bağlam menülerine veya kullanıcının komutları kullanmalarını beklediğiniz alt menülere eklersiniz. Visual Studio, yalnızca `CommandWellOnly` ana menüler için bir görünmezlik bayrağı olarak davranır. Bir bağlam menüsüne veya alt menüye aynı komut grubunu ekleyebilirsiniz.

Ortak desenin bir parçası olarak Sütun Kılavuzları uzantısı, tek bir alt menüyü tutan ikinci bir grup oluşturur. Alt menü sırasıyla dört sütunlu kılavuz komutlarını içeren ilk grubu içerir. Alt menüyü tutan ikinci grup, çeşitli bağlam menülerine ek olarak bu bağlam menülerine bir alt menü koyan yeniden kullanılabilir varlıktır.

### <a name="the-vsct-file"></a>.vsct dosyası
*.vsct* dosyası komutları ve bunların nereye gittiğini simgelerle birlikte belirtir. *.vsct* dosyasının içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

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

**GUID'ler.** Komut Visual Studio işleyicilerinizi bulup çağırması için *ColumnGuideCommandsPackage.cs* dosyasında bildirilen paket GUID'sini (proje öğesi şablonundan oluşturulan) *.vsct* dosyasında bildirilen paket GUID'si ile (yukarıdan kopyalanan) eşle olduğundan emin olun. Bu örnek kodu yeniden kullanırsanız, bu kodu kopyalanmış olanlarla çakışmamanız için farklı bir GUID'niz olduğundan emin olun.

*ColumnGuideCommandsPackage.cs* içinde şu satırı bulun ve GUID'yi tırnak işaretleri arasında kopyalayın:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Ardından, bildirimlerinize aşağıdaki satıra sahip olmak için GUID'i *.vsct* dosyasına `Symbols` yapıştırın:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Komut kümesi ve bit eşlem görüntü dosyasının GUID'leri de uzantılarınız için benzersiz olmalıdır:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Ancak kodun çalışması için bu kılavuzda komut kümesi ve bit eşlem görüntüsü GUID'lerini değiştirmeniz gerek yoktur. Komut kümesi GUID'lerinin *ColumnGuideCommands.cs* dosyasındaki bildirimiyle eşleşmesi gerekir, ancak bu dosyanın içeriğini de değiştirirsiniz; Bu nedenle GUID'ler eşler.

*.vsct dosyasındaki diğer* GUID'ler, sütun kılavuzu komutlarının eklenmiştir ve bu nedenle hiçbir zaman değişmezler.

**Dosya bölümleri.** *.vsct'nin* üç dış bölümü vardır: komutlar, yerleştirmeler ve semboller. komutlar bölümü simgeler için komut gruplarını, menüleri, düğmeleri veya menü öğelerini ve bit eşlemleri tanımlar. Yerleştirmeler bölümü, grupların menülerde nereye gittiğini veya önceden var olan menülere ek yerleştirmeler olduğunu bildirer. Semboller *bölümü, .vsct* dosyasının başka bir yerinde kullanılan tanımlayıcıları belirtir ve bu da *.vsct* kodunun her yerde GUID'lere ve hex numaralarına sahip olmaktan daha okunabilir hale geldi.

**Komutlar bölümü, grupları tanımları.** Komutlar bölümü ilk olarak komut gruplarını tanımlar. Komut grupları, menülerde grupları ayıran küçük gri çizgiler ile gördüğünüz komutlardır. Bir grup, bu örnekte olduğu gibi bir alt menünün tamamını doldurabilirsiniz ve bu örnekte gri ayrım çizgilerini görmüyoruz. *.vsct* dosyaları, üst öğe (ana Düzenleme menüsü) ve üst öğesi (kod düzenleyicisinin bağlam menüsü) olan iki `GuidesMenuItemsGroup` `IDM_VS_MENU_EDIT` grup  `GuidesContextMenuGroup` `IDM_VS_CTXT_CODEWIN` bildirmektedir.

İkinci grup bildiriminin önceliği `0x0600` var:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Burada fikir, sütun kılavuzları alt menüsünü, alt menü grubunu eklemek istediğiniz bağlam menüsünün sonuna koymaktır. Ancak, en iyi şekilde biliyor olduğunu varsayma ve önceliğini kullanarak alt menüyü her zaman en son olacak şekilde `0xFFFF` zorlama. Alt men men ekleyebilirsiniz bağlam menülerinde nerede olduğunu görmek için sayıyla denemeler yapmak gerekir. Bu durumda, menülerin sonuna koyacak kadar yüksektir ancak tercih edilirse başka birinin uzantıyı sütun kılavuzları uzantısından daha düşük olacak şekilde tasarlaması için yer `0x0600` bırakır.

**Komutlar bölümü, menü tanımı.** Ardından, komut bölümü öğesinin üst öğesi `GuidesSubMenu` olan alt menüyü `GuidesContextMenuGroup` tanımlar. `GuidesContextMenuGroup`, tüm ilgili bağlam menülerine ekley istediğiniz grup olur. Yerleştirmeler bölümünde kod, grubu bu alt menüde dört sütunlu kılavuz komutlarıyla birlikte yer almaktadır.

**Komutlar bölümü, düğmeler tanımları.** Ardından komutlar bölümü, dört sütunlu kılavuz komutları olan menü öğelerini veya düğmelerini tanımlar. `CommandWellOnly`, yukarıda ele alınmıştır, komutların bir ana menüye yerleştirilebiliyorsa görünmez olduğu anlamına gelir. Menü öğesi düğme bildirimlerinin (kılavuz ekleme ve kılavuzu kaldırma) ikisinde de bayrağı `AllowParams` vardır:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Bu bayrak, ana menü yerleştirmeleri ile birlikte, komut işleyiciyi çağıran Visual Studio alma komutunu sağlar.  Kullanıcı komutu Komut Penceresinden çalıştırırsa, bağımsız değişkeni olay bağımsız değişkenlerinden komut işleyiciye geçiri.

**Komut bölümleri, bit eşlem tanımları.** Son olarak, komutlar bölümü komutlar için kullanılan bit eşlemleri veya simgeleri bildiriyor. Bu bölüm, proje kaynağını tanımlayan ve kullanılan simgelerin tek tabanlı dizinlerini listeleen basit bir bildirimdir. *.vsct dosyasının semboller bölümü,* dizin olarak kullanılan tanımlayıcıların değerlerini belirtir. Bu kılavuzda, projeye eklenen özel komut öğesi şablonuyla birlikte sağlanan bit eşlem şeridi kullanılır.

**Yerleştirmeler bölümü.** Komutlar bölümünden sonra yerleştirmeler bölümü olur. Birincisi, kodun yukarıda tartışılan ve dört sütunlu kılavuz komutlarını içeren ilk grubu komutların görüntü bulunduğu alt menüye ekleyebiliyor olduğudur:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Diğer tüm yerleştirmeler , `GuidesContextMenuGroup` (içeren ) diğer düzenleyici `GuidesSubMenu` bağlam menülerine ekler. Kod, öğesini bildirilen `GuidesContextMenuGroup` zaman, kod düzenleyicisinin bağlam menüsüne üst öğesi olarak kabul edildi. Bu nedenle kod düzenleyicisinin bağlam menüsü için bir yerleştirme görmüyoruz.

**Semboller bölümü.** Yukarıda belirtildiği gibi, semboller bölümü *.vsct* dosyasının başka bir yerinde kullanılan tanımlayıcıları bildirerek *.vsct* kodunu her yerde GUID'lere ve hex numaralarına sahip olandan daha okunabilir hale getirdi. Bu bölümdeki önemli noktalar, paket GUID'inin paket sınıfındaki bildirimle aynı olmasıdır. Ayrıca, komut kümesi GUID'si komut uygulama sınıfındaki bildirimiyle aynı kabul eder.

## <a name="implement-the-commands"></a>Komutları uygulama
*ColumnGuideCommands.cs* dosyası komutları uygulayan ve işleyicileri bağlar. Bu Visual Studio paketi yükp başlatıyorsa, paket de `Initialize` komutlar uygulama sınıfını çağırmaktadır. Komutları başlatma yalnızca sınıf örneğini oluşturur ve oluşturucu tüm komut işleyicilerini kancalar.

*ColumnGuideCommands.cs* dosyasının içeriğini aşağıdaki kodla değiştirin (aşağıda açıklanmıştır):

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

**Başvuruları düzeltin.** Bu noktada bir başvuru eksik. Kümenin Başvurular düğümünde sağ işaretçi düğmesine Çözüm Gezgini. Ekle **... komutunu** seçin. Başvuru **Ekle iletişim** kutusunun sağ üst köşesinde bir arama kutusu vardır. "editor" (çift tırnak olmadan) girin. **Microsoft.VisualStudio.Editor** öğesini seçin (öğeyi seçmekle değil, yalnızca öğenin sol tarafından kutuyu işaretleyin) ve başvuru eklemek için **Tamam'ı** seçin.

**başlatma.**  Paket sınıfı başlatılmışsa, `Initialize` komutlar uygulama sınıfına çağrır. Başlatma, `ColumnGuideCommands` sınıf örneğini verir ve sınıf örneğini ve paket başvurularını sınıf üyelerine kaydeder.

Şimdi sınıf oluşturucus undan komut işleyicisi kancalarından birini bakalım:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Bir `OleMenuCommand` oluşturabilirsiniz. Visual Studio, Microsoft Office sistemini kullanır. bir örneği ekleyebilirsiniz anahtar bağımsız değişkenleri komutunu uygulayan işlevidir ( ), komut () ile bir menü Visual Studio çağrısı yapmak için işlev `OleMenuCommand` `AddColumnGuideExecuted` ve komut `AddColumnGuideBeforeQueryStatus` kimliği. Visual Studio, menüde bir komut göstermeden önce sorgu durumu işlevini çağırarak komutun belirli bir menü görüntüsü için kendisini  görünmez veya gri hale (örneğin, seçim yoksa Kopyala'nın devre dışı bırakılması), simgesini değiştirme ve hatta adını değiştirme (örneğin, Bir Şey Ekle'den Bir Şeyi Kaldır'a) gibi) ve diğer tüm özellikleri gösterir. Komut kimliği, *.vsct* dosyasında bildirilen bir komut kimliğiyle eşleşmeli. Komut kümesi ve sütun kılavuzları ekleme komutu için dizeler *.vsct* dosyası ile *ColumnGuideCommands.cs arasında eşleşmeli.*

Aşağıdaki satır, kullanıcılar Komut Penceresi aracılığıyla komutu çağıran kullanıcılar için yardım sağlar (aşağıda açıklanmıştır):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Sorgu durumu.** Sorgu durumu işlevleriyle birlikte bazı ayarları (en fazla kılavuz sayısı veya maksimum sütun gibi) veya `AddColumnGuideBeforeQueryStatus` `RemoveColumnGuideBeforeQueryStatus` kaldırlanacak bir sütun kılavuzu olup ola bir kontrol eder. Koşullar doğru ise komutları etkinleştirir.  Sorgu durumu işlevlerinin verimli olması gerekir çünkü her Visual Studio menüyü ve her komut için gösterir.

 **Addcolumnkılavuz yürütüldü işlevi**. Kılavuz eklemenin ilginç bölümü, geçerli düzenleyici görünümü ve giriş işareti konumunu gösterir.  İlk olarak, bu işlev çağırır `GetApplicableColumn` , bu, komut işleyicisinin olay bağımsız değişkenlerinde Kullanıcı tarafından sağlanan bir bağımsız değişken olup olmadığını denetler ve hiçbiri yoksa, işlev düzenleyicinin görünümünü denetler:

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

`GetCurrentEditorColumn` kodun bir görünümünü almak için biraz şey yapmanız gerekebilir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .  , Ve ile izleyebilirsiniz `GetActiveTextView` , `GetActiveView` `GetTextViewFromVsTextView` bunun nasıl yapılacağını görebilirsiniz. Aşağıdaki kod, geçerli seçim ile başlayıp sonra seçimin çerçevesini alarak ve sonra da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> IVsTextView öğesinden bir görünüm ana bilgisayarı ve son olarak IWpfTextView 'dan elde edilecek şekilde soyutlanarak ilgili koddur.

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

Bir IWpfTextView olduktan sonra, giriş işaretinin bulunduğu sütunu alabilirsiniz:

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

Kullanıcının tıklandığı geçerli sütun ile, kod, sütunu eklemek veya kaldırmak için yalnızca ayarlar Yöneticisi üzerinde çağrılır. Ayarlar Yöneticisi tüm `ColumnGuideAdornment` nesnelerin dinleme olayını tetikler. Olay tetiklendiğinde, bu nesneler ilgili metin görünümlerini yeni sütun Kılavuzu ayarları ile güncelleştirir.

## <a name="invoke-command-from-the-command-window"></a>Komut penceresinden komut çağır
Sütun kılavuzu örneği, kullanıcıların komut penceresinden bir genişletilebilirlik formu olarak iki komut çağırmasına olanak sağlar. **&#124; diğer Windows görüntüle &#124; komut penceresi** komutunu kullanırsanız, komut penceresini görebilirsiniz. Komut penceresiyle etkileşime geçerek, "Düzenle" yazarak ve komut adı tamamlamada ve 120 bağımsız değişkenini sağlayarak aşağıdaki sonuca sahipsiniz:

```csharp
> Edit.AddColumnGuide 120
>
```

Bu davranışı etkinleştiren örnek parçaları *. vsct* dosya bildirimlerinde, `ColumnGuideCommands` sınıf oluşturucu komut işleyicilerini kancasında ve olay bağımsız değişkenlerini denetleyen komut işleyicisi uygulamalarıdır.

`<CommandFlag>CommandWellOnly</CommandFlag>`Komutları **düzenleme** menüsü Kullanıcı arabiriminde gösterilmese de, *. vsct* dosyasında ve **düzenleme** ana menüsündeki yerleştirme "" öğesini gördünüz. Bunları ana **düzenleme** menüsünde yapmanız, **düzenleme. addcolumnguide** gibi adlar sağlar. Dört komutu tutan komutlar grubu bildirimi, grubu doğrudan **düzenleme** menüsüne yerleştirdi:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Daha sonra düğmeler bölümü, `CommandWellOnly` bunları ana menüde görünmez tutmak için komutları ve bunlarla birlikte bu şekilde bildirilmiştir `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

`ColumnGuideCommands`Sınıf oluşturucusunda, izin verilen parametrenin açıklamasını verilen komut işleyici kancası kodunu gördünüz:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

`GetApplicableColumn` `OleMenuCmdEventArgs` Geçerli bir sütun için düzenleyicinin görünümünü denetlemeden önce bir değer için işlev denetimlerini gördünüz:

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
Artık sütun kılavuzlarınızın uzantısını yürütmek için **F5** 'e basabilirsiniz. Bir metin dosyası açın ve düzenleyicinin bağlam menüsünü kullanarak kılavuz çizgileri ekleyin, bunları kaldırın ve rengini değiştirin. Sütun kılavuzu eklemek için metinde (satırın sonuna kadar boşluk değil) tıklayın veya düzenleyici bunu satırdaki son sütuna ekler. Komut penceresini kullanır ve komutları bir bağımsız değişkenle çalıştırırsanız, her yere sütun kılavuzu ekleyebilirsiniz.

farklı komut yerleşimi denemek istiyorsanız, adları değiştirin, simgeleri değiştirin ve benzeri bir sorun varsa, menülerde en son kodu gösteren Visual Studio herhangi bir sorununuz varsa, hata ayıkladığınızda deneysel hive 'yi sıfırlayabilirsiniz. **Windows başlat menüsünü** açın ve "sıfırla" yazın. komutu bulup çalıştırın, **sonraki Visual Studio deneysel örneği sıfırlayın**. Bu komut tüm uzantı bileşenlerinin Deneysel kayıt defteri kovanını temizler. bileşenlerden ayarları temizlemez, bu nedenle Visual Studio deneysel hive 'yi kapattığınız zaman, kodunuzun bir sonraki başlatmada ayarlar deposunu okuduğunda hala orada olduğunu görürsünüz.

## <a name="finished-code-project"></a>Kod projesi tamamlandı
yakında GitHub bir proje Visual Studio genişletilebilirlik örnekleri olacak ve tamamlanmış proje orada olacaktır. Bu makale, ne zaman yapılacağını gösterecek şekilde güncelleştirilecektir. Tamamlanan örnek projenin GUID 'leri farklı olabilir ve komut simgeleri için farklı bit eşlem şeridine sahip olur.

sütun kılavuzu özelliğinin bir sürümünü bu Visual Studio galeri[uzantısıyla](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)deneyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenleyicinin içinde](../extensibility/inside-the-editor.md)
- [Düzenleyiciyi ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)
- [Dil hizmeti ve Düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)
- [Menüleri ve komutları Genişlet](../extensibility/extending-menus-and-commands.md)
- [Menüye alt menü ekleme](../extensibility/adding-a-submenu-to-a-menu.md)
- [Düzenleyici öğe şablonuyla uzantı oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)
