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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5c9136b5047f835ecbf56df71bb226b5f56a6e19
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586958"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama

Bağlayarak uygulamanızın kullanıcılarına veri gösterebilirsiniz [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrol eder. Bu verilere dayalı denetimleri oluşturmak için, **veri kaynakları** penceresinden öğeleri Visual Studio 'daki [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] sürükleyebilirsiniz. Bu konuda en yaygın görevleri, araçları ve verilere bağlı oluşturmak için kullanabileceğiniz sınıfların bazılarını açıklar [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] uygulamalar.

Visual Studio'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] veri bağlaması bkz [Data Binding Overview](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlamada kullanılan görevler

Aşağıdaki tabloda sürükleyerek gerçekleştirilebilir görevleri listeler **veri kaynakları** penceresine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Görev|Daha fazla bilgi|
|----------| - |
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Oluşturma bir *arama tablosu* bir tablodaki başka bir tablodaki bir yabancı anahtar alanının değere göre görüntüler.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri

Öğeleri sürükleyebilirsiniz **veri kaynakları** içindeki geçerli bırakma hedeflerine yalnızca penceresine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

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

- Veri kümesi ve yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına için. <xref:System.Windows.Data.CollectionViewSource> Gidin ve veri kümesindeki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> için olay işleyicisi [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] denetimi içeren öğe. Olay işleyicisi tabloyu verilerle alır doldurur <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynakları ve yapar sonra ilk veri öğesini geçerli öğe. <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri

**Veri kaynakları** penceresinden tasarımcıya bir varlık veya varlık özelliği sürüklediğinizde, Visual Studio aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] üretir:

- Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına için. <xref:System.Windows.Data.CollectionViewSource> Gidin ve varlıktaki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi oluşturur sürüklenen öğe için seçilmiş ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntemin adı `Get<EntityName>Query`vardır; burada `\<EntityName>` varlığın adıdır.

- Oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> için olay işleyicisi [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] denetimi içeren öğe. Olay işleyicisi, varlığı verilerle birlikte dolduracak `Get<EntityName>Query` yöntemini çağırır, kapsayıcının kaynaklarından <xref:System.Windows.Data.CollectionViewSource> alır ve ardından ilk veri öğesini geçerli öğe yapar. <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi zaten varsa, Visual Studio bu kodu var olan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler

Bir hizmet nesnesini veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, Visual Studio proxy hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz: [denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio aşağıdakileri yapan XAML oluşturur:

- Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına. <xref:System.Windows.Data.CollectionViewSource> Gidin ve hizmet tarafından döndürülen nesnedeki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi oluşturur sürüklenen öğe için seçilmiş ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Nesneler

Bir nesne veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, Visual Studio veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak Visual Studio, nesneyi veriyle dolduracak kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar genel olmalıdır ve, varsayılan olarak, parametresiz bir oluşturucusu vardır. Bunlar, sözdiziminde "nokta" olan iç içe geçmiş sınıflar olamaz. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] üretir:

- Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına. <xref:System.Windows.Data.CollectionViewSource> Gidip nesnedeki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
