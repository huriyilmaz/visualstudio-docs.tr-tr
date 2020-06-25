---
title: WPF denetimlerini veriye bağlama-Bölüm 1
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 27d0c14bcf09a3b0d30cd23dea0f8348c45fcab7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282887"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama

Verileri denetimlere bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] . Bu verilere dayalı denetimleri oluşturmak için, **veri kaynakları** penceresinden öğeleri [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio 'da üzerine sürükleyebilirsiniz. Bu konuda, veri bağlantılı uygulamalar oluşturmak için kullanabileceğiniz en yaygın görevlerden, araçların ve sınıfların bazıları açıklanmaktadır [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] .

Visual Studio 'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Veri bağlama hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] bkz. [veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlama ile ilgili görevler

Aşağıdaki tabloda, öğeleri **veri kaynakları** penceresinden öğesine sürükleyerek yapılabilecek görevler listelenmiştir [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] .

|Görev|Daha fazla bilgi|
|----------| - |
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Bir tablodaki bilgileri başka bir tablodaki yabancı anahtar alanının değerine göre görüntüleyen bir *arama tablosu* oluşturun.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri

**Veri kaynakları** penceresindeki öğeleri yalnızca içindeki geçerli bırakma hedeflerine sürükleyebilirsiniz [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] . İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod

**Veri kaynakları** penceresinden bir öğeyi öğesine sürüklediğinizde [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] , Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] Yeni bir veri bağlama denetimi tanımlar (veya varolan bir denetimi veri kaynağına bağlar). Visual Studio, bazı veri kaynakları için veri kaynağını verilerle dolduran arka plan kod dosyasında da kod üretir.

Aşağıdaki tabloda, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] **veri kaynakları** penceresinde Visual Studio 'nun her veri kaynağı türü için oluşturduğu kod ve kod listelenmektedir.

| Veri kaynağı | Bir denetimi veri kaynağına bağlayan XAML oluşturma | Veri kaynağını verilerle dolduran kod oluşturma |
| - | - | - |
| Veri kümesi | Yes | Yes |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Yes | Yes |
| Hizmet | Evet | Hayır |
| Nesne | Evet | Hayır |

### <a name="datasets"></a>Veri kümeleri

**Veri kaynakları** penceresinden tasarımcıya bir tablo veya sütun sürüklediğinizde, Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] aşağıdakileri yapar:

- Veri kümesini ve <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Veri kümesindeki verileri gezinmek ve göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- <xref:System.Windows.FrameworkElement.Loaded>Denetimi içeren öğe için bir olay işleyicisi oluşturur [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] . Olay işleyicisi tabloyu verilerle doldurur, <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynaklarından öğesini alır ve ardından ilk veri öğesini geçerli öğe yapar. Bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri

**Veri kaynakları** penceresinden tasarımcıya bir varlık veya varlık özelliği sürüklediğinizde, Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] aşağıdakileri yapar:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Varlıktaki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklediğiniz öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni Yöntem ada sahiptir `Get<EntityName>Query` , burada `\<EntityName>` varlığın adıdır.

- <xref:System.Windows.FrameworkElement.Loaded>Denetimi içeren öğe için bir olay işleyicisi oluşturur [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] . Olay işleyicisi, `Get<EntityName>Query` varlığı verilerle birlikte dolduracak şekilde yöntemini çağırır, <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynaklarından öğesini alır ve ardından ilk veri öğesini geçerli öğe yapar. Bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler

Bir hizmet nesnesini veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio bunu [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] bir veri bağlama denetimi oluşturduğunu (veya varolan bir denetimi nesne veya özelliğe bağlar) oluşturur. Ancak, Visual Studio proxy hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz. [WPF denetimlerini BIR WCF veri hizmetine bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio aşağıdakileri yapan XAML oluşturur:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Hizmet tarafından döndürülen nesnedeki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklediğiniz öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

### <a name="objects"></a>Nesneler

Bir nesne veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio bunu [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] bir veri bağlama denetimi oluşturduğunu (veya varolan bir denetimi nesne veya özelliğe bağlar) oluşturur. Ancak Visual Studio, nesneyi veriyle dolduracak kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar public olmalıdır ve varsayılan olarak parametresiz bir oluşturucuya sahip olmalıdır. Bunlar, sözdiziminde "nokta" olan iç içe geçmiş sınıflar olamaz. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] şunları yapar:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Nesnesinde gezinmek ve verileri göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
