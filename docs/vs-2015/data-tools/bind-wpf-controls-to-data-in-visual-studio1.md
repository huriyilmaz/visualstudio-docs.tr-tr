---
title: WPF denetimlerini verilere bağlama (Bölüm 1) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25b144409ae58f006602706a5b5cb498c0535ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540172"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri denetimlere bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] . Bu veriye dayalı denetimleri oluşturmak için, öğeleri **veri kaynakları** penceresinden içinde üzerine sürükleyebilirsiniz [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bu konuda, veri bağlantılı uygulamalar oluşturmak için kullanabileceğiniz en yaygın görevlerden, araçların ve sınıfların bazıları açıklanmaktadır [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] .

 ' De veriye bağlı denetimler oluşturma hakkında genel bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Veri bağlama hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlama ile ilgili görevler
 Aşağıdaki tabloda, öğeleri **veri kaynakları** penceresinden öğesine sürükleyerek yapılabilecek görevler listelenmiştir [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] .

|Görev|Daha fazla bilgi|
|----------|----------------------|
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Visual Studio 'da WPF denetimlerini veri](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md) bağlama|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Bir tablodaki bilgileri başka bir tablodaki yabancı anahtar alanının değerine göre görüntüleyen bir *arama tablosu* oluşturun.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri
 **Veri kaynakları** penceresindeki öğeleri yalnızca içindeki geçerli bırakma hedeflerine sürükleyebilirsiniz [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] . İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod
 Bir öğeyi **veri kaynakları** penceresinden öğesine sürüklediğinizde [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] Yeni bir veri bağlama denetimi tanımlar (veya varolan bir denetimi veri kaynağına bağlar). Bazı veri kaynakları için, veri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kaynağını verilerle dolduran arka plan kod dosyasında da kod üretir.

 Aşağıdaki tabloda, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **veri kaynakları** penceresinde her bir veri kaynağı türü için oluşturan ve kodu listelenmektedir.

|Veri kaynağı|Bir denetimi veri kaynağına bağlayan XAML oluşturma|Veri kaynağını verilerle dolduran kod oluşturma|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Veri kümesi|Yes|Yes|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Yes|Yes|
|Hizmet|Yes|Hayır|
|Nesne|Yes|Hayır|

### <a name="datasets"></a>Veri kümeleri
 **Veri kaynakları** penceresinden tasarımcıya bir tablo veya sütun sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] şunları yapar:

- Veri kümesini ve <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Veri kümesindeki verileri gezinmek ve göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- <xref:System.Windows.FrameworkElement.Loaded>Denetimi içeren öğe için bir olay işleyicisi oluşturur [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] . Olay işleyicisi tabloyu verilerle doldurur, <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynaklarından öğesini alır ve ardından ilk veri öğesini geçerli öğe yapar. Bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu kodu var olan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri
 **Veri kaynakları** penceresinden tasarımcıya bir varlık veya varlık özelliği sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] şunları yapar:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Varlıktaki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sürüklediğiniz öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

  Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntem Name Get*EntityName*sorgusuna sahiptir, burada *EntityName* varlık adıdır.

- <xref:System.Windows.FrameworkElement.Loaded>Denetimi içeren öğe için bir olay işleyicisi oluşturur [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] . Olay işleyicisi, varlığı verilerle birlikte dolduracak şekilde Get*EntityName*sorgu yöntemini çağırır, <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynaklarından alır ve ardından ilk veri öğesini geçerli öğe yapar. Bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu kodu var olan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler
 Bir hizmet nesnesini veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Bu, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] veri bağlama denetimi oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proxy hizmeti nesnesini verilerle dolduran bir kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz. [WPF denetimlerini BIR WCF veri hizmetine bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio aşağıdakileri yapan XAML oluşturur:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Hizmet tarafından döndürülen nesnedeki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sürüklediğiniz öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

### <a name="objects"></a>Nesneler
 Bir nesne veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, bunu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] bir veri bağlama denetimi oluşturur (veya varolan bir denetimi nesne veya özelliğe bağlar). Ancak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nesneyi veriyle dolduracak kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar public olmalıdır ve varsayılan olarak parametresiz bir oluşturucuya sahip olmalıdır. Bunlar, sözdiziminde "nokta" olan iç içe geçmiş sınıflar olamaz. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]şunları yapar:

- <xref:System.Windows.Data.CollectionViewSource>Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni ekler. , <xref:System.Windows.Data.CollectionViewSource> Nesnesinde gezinmek ve verileri göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir içinde oluşturulur <xref:System.Windows.Controls.Grid> .

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
