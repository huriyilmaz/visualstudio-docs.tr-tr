---
title: WPF denetimlerini verilere bağlama | Microsoft Docs
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
ms.openlocfilehash: 12aad1f22fdc4badc024c62fbc302eef8e3937e4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670068"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] denetimlerine bağlayarak uygulamanızın kullanıcılarına verileri gösterebilirsiniz. Bu verilere dayalı denetimleri oluşturmak için, öğeleri **veri kaynakları** penceresinden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] sürükleyebilirsiniz. Bu konuda, veri bağlantılı [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] uygulamalar oluşturmak için kullanabileceğiniz en yaygın görevlerden, araçların ve sınıfların bazıları açıklanmaktadır.

 @No__t_0 ' de veriye bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio 'da denetimleri verilere bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). @No__t_0 veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlama ile ilgili görevler
 Aşağıdaki tabloda, **veri kaynakları** penceresinden [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] öğeler sürüklenerek yapılabilecek görevler listelenmiştir.

|Görev|Daha fazla bilgi|
|----------|----------------------|
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Visual Studio 'da WPF denetimlerini veri](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md) bağlama|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Bir tablodaki bilgileri başka bir tablodaki yabancı anahtar alanının değerine göre görüntüleyen bir *arama tablosu* oluşturun.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri
 **Veri kaynakları** penceresindeki öğeleri yalnızca [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] geçerli bırakma hedeflerine sürükleyebilirsiniz. İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod
 Bir öğeyi **veri kaynakları** penceresinden [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeni bir veri bağlama denetimi tanımlayan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] oluşturur (veya varolan bir denetimi veri kaynağına bağlar). Bazı veri kaynakları için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], veri kaynağını verilerle dolduran arka plan kod dosyasında da kod üretir.

 Aşağıdaki tabloda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **veri kaynakları** penceresindeki her veri kaynağı türü için [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve kodu listelenmektedir.

|Veri kaynağı|Bir denetimi veri kaynağına bağlayan XAML oluşturma|Veri kaynağını verilerle dolduran kod oluşturma|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Veri kümesi|Evet|Evet|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Evet|Evet|
|Hizmet|Evet|Hayır|
|Nesne|Evet|Hayır|

### <a name="datasets"></a>Veri kümeleri
 **Veri kaynakları** penceresinden tasarımcıya bir tablo veya sütun sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına veri kümesini ve yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. @No__t_0, veri kümesindeki verileri gezinmek ve göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Denetimi içeren [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] öğesi için <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi oluşturur. Olay işleyicisi tabloyu verilerle doldurur, kapsayıcının kaynaklarından <xref:System.Windows.Data.CollectionViewSource> alır ve ardından ilk veri öğesini geçerli öğe yapar. @No__t_0 bir olay işleyicisi zaten varsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu kodu var olan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri
 **Veri kaynakları** penceresinden tasarımcıya bir varlık veya varlık özelliği sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. @No__t_0, varlıktaki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

  Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntem Name Get*EntityName*sorgusuna sahiptir, burada *EntityName* varlık adıdır.

- Denetimi içeren [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] öğesi için <xref:System.Windows.FrameworkElement.Loaded> bir olay işleyicisi oluşturur. Olay işleyicisi, varlığı verilerle birlikte dolduracak şekilde Get*EntityName*sorgu yöntemini çağırır, kapsayıcının kaynaklarından <xref:System.Windows.Data.CollectionViewSource> alır ve ardından ilk veri öğesini geçerli öğe yapar. @No__t_0 bir olay işleyicisi zaten varsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu kodu var olan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler
 Bir hizmet nesnesini veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], proxy hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz. [WPF denetimlerini BIR WCF veri hizmetine bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio aşağıdakileri yapan XAML oluşturur:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. @No__t_0, hizmet tarafından döndürülen nesnedeki verilerde gezinmek ve bunları göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi Tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

### <a name="objects"></a>Nesneler
 Bir nesne veya özelliği **veri kaynakları** penceresinden tasarımcıya sürüklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veriye bağlı bir denetim oluşturan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nesneyi veriyle dolduracak kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar public olmalıdır ve varsayılan olarak parametresiz bir oluşturucuya sahip olmalıdır. Bunlar, sözdiziminde "nokta" olan iç içe geçmiş sınıflar olamaz. Daha fazla bilgi için bkz. [WPF Için XAML ve özel sınıflar](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aşağıdakileri yapan [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] üretir:

- Öğeyi sürüklediğiniz kapsayıcının kaynaklarına yeni bir <xref:System.Windows.Data.CollectionViewSource> ekler. @No__t_0, nesnesinde gezinmek ve verileri göstermek için kullanılabilen bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim yeni bir <xref:System.Windows.Controls.Grid> içinde oluşturulur.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
