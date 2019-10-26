---
title: WPF denetimlerini veriye bağlama-Bölüm 1
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ee858c7c17798f327d323f632d4cb9e8a77b6712
ms.sourcegitcommit: bde55773485c9bca50a760ac9e4c919e0a208a51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72924535"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama

Verileri [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] denetimlerine bağlayarak uygulamanızın kullanıcılarına verileri gösterebilirsiniz. Bu verilere dayalı denetimleri oluşturmak için, **veri kaynakları** penceresinden öğeleri Visual Studio 'daki [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] sürükleyebilirsiniz. Bu konuda, veri bağlantılı [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] uygulamalar oluşturmak için kullanabileceğiniz en yaygın görevlerden, araçların ve sınıfların bazıları açıklanmaktadır.

Visual Studio 'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlama ile ilgili görevler

Aşağıdaki tabloda, **veri kaynakları** penceresinden [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]öğeler sürüklenerek yapılabilecek görevler listelenmiştir.

|Görev|Daha fazla bilgi|
|----------| - |
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Bir tablodaki bilgileri başka bir tablodaki yabancı anahtar alanının değerine göre görüntüleyen bir *arama tablosu* oluşturun.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri

**Veri kaynakları** penceresindeki öğeleri yalnızca [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]geçerli bırakma hedeflerine sürükleyebilirsiniz. İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod

Bir öğeyi **veri kaynakları** penceresinden [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]sürüklediğinizde, Visual Studio yeni bir veri bağlama denetimi tanımlayan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur (veya varolan bir denetimi veri kaynağına bağlar). Visual Studio, bazı veri kaynakları için veri kaynağını verilerle dolduran arka plan kod dosyasında da kod üretir.

Aşağıdaki tabloda, **veri kaynakları** penceresinde Visual Studio 'nun her veri kaynağı türü için oluşturduğu [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ve kod listelenmektedir.

| Veri kaynağı | Bir denetimi veri kaynağına bağlayan XAML oluşturma | Veri kaynağını verilerle dolduran kod oluşturma |
| - | - | - |
| Veri kümesi | Evet | Evet |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Evet | Evet |
| Hizmet | Evet | Hayır |
| Nesne | Evet | Hayır |

### <a name="datasets"></a>Veri kümeleri

**Veri kaynakları** penceresinden tasarımcıya bir tablo veya sütun sürüklediğinizde, Visual Studio aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına veri kümesini ve yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. <xref:System.Windows.Data.CollectionViewSource>, veri kümesindeki verileri gezinmek ve göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Denetimi içeren [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] öğesi için <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi oluşturur. Olay işleyicisi tabloyu verilerle doldurur, kapsayıcının kaynaklarından <xref:System.Windows.Data.CollectionViewSource> alır ve ardından ilk veri öğesini geçerli öğe yapar. <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri

**Veri kaynakları** penceresinden tasarımcıya bir varlık veya varlık özelliği sürüklediğinizde, Visual Studio aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. <xref:System.Windows.Data.CollectionViewSource>, varlıktaki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntemin adı `Get<EntityName>Query` vardır; burada `\<EntityName>` varlığın adıdır.

- Denetimi içeren [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] öğesi için <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi oluşturur. Olay işleyicisi, varlığı verilerle birlikte dolduracak `Get<EntityName>Query` yöntemini çağırır, kapsayıcının kaynaklarından <xref:System.Windows.Data.CollectionViewSource> alır ve ardından ilk veri öğesini geçerli öğe yapar. <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler

Bir hizmet nesnesini veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, Visual Studio proxy hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz. [WPF denetimlerini BIR WCF veri hizmetine bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio aşağıdakileri yapan XAML oluşturur:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. <xref:System.Windows.Data.CollectionViewSource>, hizmet tarafından döndürülen nesnedeki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

### <a name="objects"></a>Nesneler

Bir nesne veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak Visual Studio, nesneyi veriyle dolduracak kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar public olmalıdır ve varsayılan olarak parametresiz bir oluşturucuya sahip olmalıdır. Bunlar, sözdiziminde "nokta" olan iç içe geçmiş sınıflar olamaz. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. <xref:System.Windows.Data.CollectionViewSource>, nesnesinde gezinmek ve verileri göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
