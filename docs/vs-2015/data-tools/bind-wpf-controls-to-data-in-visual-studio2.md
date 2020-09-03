---
title: WPF denetimlerini verilere bağlama (2. bölüm) | Microsoft Docs
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540094"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] **kaynakları** penceresini kullanarak veriye göre bağlantılı denetimler oluşturabilirsiniz. İlk olarak, **veri kaynakları** penceresine bir veri kaynağı ekleyin. Ardından, öğeleri **veri kaynakları** penceresinden**WPF tasarımcısına**sürükleyin.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a> Veri Kaynakları penceresine veri kaynağı ekleme
 Veriye dayalı denetimler oluşturabilmeniz için önce **veri kaynakları** penceresine bir veri kaynağı eklemeniz gerekir.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Veri Kaynakları penceresine veri kaynağı eklemek için

1. **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve ardından **veri kaynakları**' na tıklayın.

2. **Yeni veri kaynağı Ekle**' ye tıklayın ve **veri kaynağı yapılandırma** Sihirbazı ' nı doldurun.

3. Veri bağlantılı denetimler oluşturmak için aşağıdaki görevlerden birini gerçekleştirin:

    - [Tek bir veri alanına bağlanan bir denetim oluşturma](#simple).

    - [Birden çok veri alanına bağlanan bir denetim oluşturma](#complex).

    - [Birden çok veri alanına bağlanan bir denetim kümesi oluşturma](#details).

    - [Tasarımcıdaki verileri varolan denetimlere bağlama](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a> Tek bir veri alanına bağlanan bir denetim oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, veya gibi tek bir veri alanını görüntüleyen yeni bir veri bağlantılı denetim oluşturabilirsiniz <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Tek bir veri alanına bağlanan bir denetim oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğeyi genişletin. Bağlamak istediğiniz sütunu veya özelliği temsil eden alt öğeyi bulun. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. İsteğe bağlı olarak, oluşturulacak denetimi seçin. **Veri kaynakları** penceresindeki her öğe, öğeyi tasarımcıya sürüklediğinizde oluşturulan bir varsayılan denetime sahiptir. Varsayılan denetim, öğenin temel alınan veri türüne bağlıdır.

     Farklı bir denetim seçmek için öğenin yanındaki aşağı açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Öğeyi tasarımcıda geçerli bir kapsayıcıya sürükleyin. Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Yeni veri bağlantılı denetimi ve kapsayıcıda uygun bir şekilde <xref:System.Windows.Controls.Label> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi verilere bağlamak için ve kodu oluşturur. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a> Birden çok veri alanına bağlanan bir denetim oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, veya gibi birden çok veri alanını görüntüleyen yeni bir veri bağlantılı denetim oluşturabilirsiniz <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Birden çok veri alanına bağlanan bir denetim oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğe seçin. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. İsteğe bağlı olarak, oluşturulacak denetimi seçin. Varsayılan olarak, veri **kaynakları** penceresinde bir veri tablosunu veya nesnesini temsil eden her öğe, <xref:System.Windows.Controls.DataGrid> (projeniz .NET Framework 4 ' i hedefliyorsa) veya <xref:System.Windows.Controls.ListView> (.NET Framework önceki sürümleri için) oluşturmak üzere ayarlanır.

     Farklı bir denetim seçmek için öğenin yanındaki aşağı açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Belirli bir sütunu veya özelliği göstermek istemiyorsanız, alt öğelerini göstermek için öğeyi genişletin. Görüntülenmesini istemediğiniz sütunun veya özelliğin yanındaki açılan oka tıklayın ve ardından **hiçbiri**' ne tıklayın.

3. Öğeyi tasarımcıda geçerli bir kapsayıcıya sürükleyin (örneğin,) <xref:System.Windows.Controls.Grid> . Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kapsayıcıda veri bağlantılı yeni denetimi oluşturur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimi verilere bağlamak için ve kodu oluşturur. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a> Birden çok veri alanına bağlanan bir denetim kümesi oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra bir veri tablosu veya nesnesini bir denetim kümesine bağlayabilirsiniz. Tablo veya nesne içindeki her sütun veya özellik için farklı bir denetim oluşturulur.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Birden çok veri alanına bağlanan bir denetim kümesi oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğe seçin. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Öğenin yanındaki aşağı açılan oka tıklayın ve **Ayrıntılar**' ı seçin.

    > [!NOTE]
    > Belirli bir sütunu veya özelliği göstermek istemiyorsanız, alt öğelerini göstermek için öğeyi genişletin. Görüntülenmesini istemediğiniz sütunun veya özelliğin yanındaki açılan oka tıklayın ve ardından **hiçbiri**' ne tıklayın.

3. Öğeyi tasarımcıda geçerli bir kapsayıcıya sürükleyin (örneğin,) <xref:System.Windows.Controls.Grid> . Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kapsayıcıda yeni veri bağlantılı denetimleri oluşturur. Her denetim farklı bir sütuna veya özelliğe bağlanır ve her denetim, uygun şekilde adlandırılmış bir denetimle birlikte bulunur <xref:System.Windows.Controls.Label> . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] denetimleri verilere bağlamak için ve kodu oluşturur. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a> Tasarımcıda varolan denetimlere yönelik binddata
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, Tasarımcıda varolan bir denetime veri bağlama ekleyebilirsiniz.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Tasarımcıda varolan bir denetime veri bağlamak için

1. **Veri kaynakları** penceresinde aşağıdaki yordamlardan birini kullanın:

    - Veya gibi birden çok veri alanını görüntüleyen varolan bir denetime veri bağlama eklemek için <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView> , denetime bağlamak istediğiniz tabloyu veya nesneyi temsil eden öğeyi seçin.

    - Veya gibi tek bir veri alanını görüntüleyen varolan bir denetime veri bağlama eklemek için, <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.TextBox> verileri içeren tabloyu veya nesneyi temsil eden öğeyi genişletin ve ardından denetime bağlamak istediğiniz verileri temsil eden öğeyi seçin.

2. Seçili öğeyi **veri kaynakları** penceresinden tasarımcıda var olan bir denetimin üzerine sürükleyin. Denetim geçerli bir bırakma hedefi olmalıdır. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]denetimi verilere bağlamak için ve kodu oluşturur. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Denetim, verilere zaten bağlıysa, denetimin veri bağlaması en son denetim üzerine sürüklenen öğeye sıfırlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [WPF denetimlerini Visual Studio 'daki verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md) WPF [uygulamalarında ilgili VERILERI](../data-tools/display-related-data-in-wpf-applications.md) bir [veri kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md) bağlama [WPF denetimlerini BIR WCF veri hizmetine](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) bağlama [izlenecek yol: bir WPF uygulamasında ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
