---
title: Verilere WPF denetimleri bağlama - Bölüm 1
description: WPF denetimlerini verilere bağlama. Bu veriye bağlı denetimleri oluşturmak için öğeleri Veri Kaynakları penceresinden veri kaynağı penceresindeki WPF Tasarımcısı'Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e491fcb8e7dad813eeb5594f6e8cbb9d64ade6ed
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631568"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama

Verileri denetimlere bağarak uygulamanın kullanıcılarına veri [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] görüntüebilirsiniz. Bu veriye bağlı denetimleri oluşturmak için, öğeleri Veri Kaynakları penceresinden veri **kaynakları** [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] penceresindeki Visual Studio. Bu konuda, veriye bağlı uygulamalar oluşturmak için kullanabileceğiniz en yaygın görev, araç ve sınıflardan bazıları [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] açıklanmıştır.

Veri bağımlı denetimler oluşturma hakkında genel bilgi Visual Studio bkz. [Visual Studio.](../data-tools/bind-controls-to-data-in-visual-studio.md). Veri bağlama hakkında daha [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] fazla bilgi için bkz. Veri [Bağlamaya Genel Bakış.](/dotnet/desktop-wpf/data/data-binding-overview)

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlamayla ilgili görevler

Aşağıdaki tabloda, Veri Kaynakları penceresinden öğeleri 'ye sürükleyerek **gerçekleştirebilir görevleri** listele [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] görebilirsiniz.

|Görev|Daha fazla bilgi|
|----------| - |
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Bir *tablodaki* bilgileri başka bir tablodaki yabancı anahtar alanı değerine göre görüntüleyen bir arama tablosu oluşturun.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri

Veri Kaynakları penceresindeki öğeleri **yalnızca içinde** geçerli bırakma hedeflerine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] sürükleyebilirsiniz. İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod

Veri Kaynakları penceresinden  bir öğeyi üzerine sürüklerken, Visual Studio yeni bir veriye bağlı denetim tanımlayan (veya var olan bir denetimi veri kaynağına bağlayan) bir [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] öğe [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturulur. Bazı veri kaynakları Visual Studio, veri kaynağını verilerle dolduran arka kod dosyasında da kod üretir.

Aşağıdaki tabloda, Veri Kaynakları penceresinde Visual Studio her veri kaynağı türü için oluşturulan ve [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] **kodu listele.**

| Veri kaynağı | Bir denetimi veri kaynağına bağlayan XAML oluşturma | Veri kaynağını verilerle dolduran kod oluşturma |
| - | - | - |
| Veri kümesi | Yes | Yes |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Yes | Yes |
| Hizmet | Yes | Hayır |
| Nesne | Yes | Hayır |

### <a name="datasets"></a>Veri kümeleri

Veri Kaynakları penceresinden bir tabloyu **veya sütunu** tasarımcıya sürüklerken, Visual Studio oluşturan bir [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] tablo oluşturulur:

- Öğeyi sürüklediği kapsayıcının <xref:System.Windows.Data.CollectionViewSource> kaynaklarına veri kümesi ve yeni bir ekler. <xref:System.Windows.Data.CollectionViewSource>, veri kümesinde gezinmek ve verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklersanız, XAML sürüklenen öğe için seçilen denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde <xref:System.Windows.Controls.Grid> oluşturulur.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Denetimi <xref:System.Windows.FrameworkElement.Loaded> içeren öğe için [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] bir olay işleyicisi oluşturur. Olay işleyicisi tabloyu verilerle doldurur, kapsayıcının kaynaklarından alır ve ardından ilk veri <xref:System.Windows.Data.CollectionViewSource> öğesini geçerli öğe yapar. Bir olay <xref:System.Windows.FrameworkElement.Loaded> işleyicisi zaten varsa, Visual Studio bu kodu mevcut olay işleyiciye ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri

Veri Kaynakları penceresinden bir varlığı veya varlık **özelliğini** tasarımcıya sürüklerken, Visual Studio [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturan bir varlık oluşturulur:

- Öğeyi <xref:System.Windows.Data.CollectionViewSource> sürüklediği kapsayıcının kaynaklarına yeni bir ekler. <xref:System.Windows.Data.CollectionViewSource>, varlığa veri gitmek ve verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda var olan bir denetime [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklersiniz, denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklersanız, sürüklenen öğe için seçilen denetimi oluşturur ve denetimi [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] öğeye bağlar. Denetim yeni bir içinde <xref:System.Windows.Controls.Grid> oluşturulur.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntemin adı `Get<EntityName>Query` vardır, `\<EntityName>` burada varlığın adıdır.

- Denetimi <xref:System.Windows.FrameworkElement.Loaded> içeren öğe için [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] bir olay işleyicisi oluşturur. Olay işleyicisi, varlığı verilerle doldurmak için yöntemini çağırır, kapsayıcının kaynaklarından öğesini toplar ve ardından ilk veri `Get<EntityName>Query` <xref:System.Windows.Data.CollectionViewSource> öğesini geçerli öğe yapar. Bir olay <xref:System.Windows.FrameworkElement.Loaded> işleyicisi zaten varsa, Visual Studio bu kodu mevcut olay işleyiciye ekler.

### <a name="services"></a>Hizmetler

Veri Kaynakları penceresinden bir hizmet  nesnesini veya özelliği tasarımcıya sürüklerken, Visual Studio bir veri bağımlı denetim oluşturan (veya var olan bir denetimi nesne ya da özelle bağlayan) [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur. Ancak Visual Studio ara sunucu hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapacağını gösteren bir örnek için bkz. [WPF denetimlerini bir WCF veri hizmetine bağlama.](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)

Visual Studio aşağıdakileri yapan XAML oluşturur:

- Öğeyi <xref:System.Windows.Data.CollectionViewSource> sürüklediği kapsayıcının kaynaklarına yeni bir ekler. <xref:System.Windows.Data.CollectionViewSource>, hizmet tarafından döndürülen nesnesinde verileri görüntülemek ve gezinmek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda var olan bir denetime [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] sürüklersiniz, denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklersanız, sürüklenen öğe için seçilen denetimi oluşturur ve denetimi [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] öğeye bağlar. Denetim yeni bir içinde <xref:System.Windows.Controls.Grid> oluşturulur.

### <a name="objects"></a>Nesneler

Veri Kaynakları penceresinden bir  nesneyi veya özelliği tasarımcıya sürüklerken, Visual Studio bir veriye bağlı denetim oluşturan (veya var olan bir denetimi nesne ya da özelle bağlayan) [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] oluşturur. Ancak Visual Studio, nesneyi verilerle doldurmak için kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar genel olmalıdır ve varsayılan olarak parametresiz bir oluşturucuya sahip olmalıdır. Söz dizimlerinde "nokta" olan iç içe geçmiş sınıflar olamayabilirsiniz. Daha fazla bilgi için bkz. [WPF için XAML ve özel sınıflar.](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)

Visual Studio şunları [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] yapar:

- Öğeyi <xref:System.Windows.Data.CollectionViewSource> sürüklediği kapsayıcının kaynaklarına yeni bir ekler. <xref:System.Windows.Data.CollectionViewSource>, nesnesinde gezinmek ve verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklersanız, XAML sürüklenen öğe için seçilen denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde <xref:System.Windows.Controls.Grid> oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
