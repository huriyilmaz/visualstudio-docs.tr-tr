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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f99c9a9ecbb18155ea8cd1197b94a7b383a80a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662501"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri **kaynakları** penceresini kullanarak veriye dayalı [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] denetimleri oluşturabilirsiniz. İlk olarak, **veri kaynakları** penceresine bir veri kaynağı ekleyin. Ardından, öğeleri **veri kaynakları** penceresinden**WPF tasarımcısına**sürükleyin.

## <a name="adding"></a>Veri Kaynakları penceresine veri kaynağı ekleme
 Veriye dayalı denetimler oluşturabilmeniz için önce **veri kaynakları** penceresine bir veri kaynağı eklemeniz gerekir.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Veri Kaynakları penceresine veri kaynağı eklemek için

1. **Görünüm** menüsünde **diğer pencereler**' in üzerine gelin ve ardından **veri kaynakları**' na tıklayın.

2. **Yeni veri kaynağı Ekle**' ye tıklayın ve **veri kaynağı yapılandırma** Sihirbazı ' nı doldurun.

3. Veri bağlantılı denetimler oluşturmak için aşağıdaki görevlerden birini gerçekleştirin:

    - [Tek bir veri alanına bağlanan bir denetim oluşturma](#simple).

    - [Birden çok veri alanına bağlanan bir denetim oluşturma](#complex).

    - [Birden çok veri alanına bağlanan bir denetim kümesi oluşturma](#details).

    - [Tasarımcıdaki verileri varolan denetimlere bağlama](#existing).

## <a name="simple"></a>Tek bir veri alanına bağlanan bir denetim oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, <xref:System.Windows.Controls.ComboBox> veya <xref:System.Windows.Controls.TextBox> gibi tek bir veri alanını görüntüleyen yeni bir veri bağlantılı denetim oluşturabilirsiniz.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Tek bir veri alanına bağlanan bir denetim oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğeyi genişletin. Bağlamak istediğiniz sütunu veya özelliği temsil eden alt öğeyi bulun. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. İsteğe bağlı olarak, oluşturulacak denetimi seçin. **Veri kaynakları** penceresindeki her öğe, öğeyi tasarımcıya sürüklediğinizde oluşturulan bir varsayılan denetime sahiptir. Varsayılan denetim, öğenin temel alınan veri türüne bağlıdır.

     Farklı bir denetim seçmek için öğenin yanındaki aşağı açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Öğeyi tasarımcıda geçerli bir kapsayıcıya sürükleyin. Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], yeni veri bağlantılı denetimi ve kapsayıcıda <xref:System.Windows.Controls.Label> başlıklı uygun bir şekilde oluşturur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, denetimi verilere bağlamak için [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve kod üretir. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="complex"></a>Birden çok veri alanına bağlanan bir denetim oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, <xref:System.Windows.Controls.DataGrid> veya <xref:System.Windows.Controls.ListView> gibi birden çok veri alanını görüntüleyen yeni bir veri bağlantılı denetim oluşturabilirsiniz.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Birden çok veri alanına bağlanan bir denetim oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğe seçin. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. İsteğe bağlı olarak, oluşturulacak denetimi seçin. Varsayılan olarak, veri **kaynakları** penceresinde bir veri tablosunu veya nesnesini temsil eden her öğe, bir <xref:System.Windows.Controls.DataGrid> oluşturmak (projeniz .NET Framework 4 ' i hedefliyorsa) veya <xref:System.Windows.Controls.ListView> (.NET Framework önceki sürümleri için) olarak ayarlanır.

     Farklı bir denetim seçmek için öğenin yanındaki aşağı açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Belirli bir sütunu veya özelliği göstermek istemiyorsanız, alt öğelerini göstermek için öğeyi genişletin. Görüntülenmesini istemediğiniz sütunun veya özelliğin yanındaki açılan oka tıklayın ve ardından **hiçbiri**' ne tıklayın.

3. Öğeyi tasarımcıda <xref:System.Windows.Controls.Grid> gibi geçerli bir kapsayıcıya sürükleyin. Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kapsayıcıda veri bağlantılı yeni denetimi oluşturur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, denetimi verilere bağlamak için [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve kod üretir. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="details"></a>Birden çok veri alanına bağlanan bir denetim kümesi oluşturma
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra bir veri tablosu veya nesnesini bir denetim kümesine bağlayabilirsiniz. Tablo veya nesne içindeki her sütun veya özellik için farklı bir denetim oluşturulur.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Birden çok veri alanına bağlanan bir denetim kümesi oluşturmak için

1. **Veri kaynakları** penceresinde, bir tabloyu veya nesneyi temsil eden bir öğe seçin. Görsel bir örnek için bkz. [veri kaynakları penceresi](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Öğenin yanındaki aşağı açılan oka tıklayın ve **Ayrıntılar**' ı seçin.

    > [!NOTE]
    > Belirli bir sütunu veya özelliği göstermek istemiyorsanız, alt öğelerini göstermek için öğeyi genişletin. Görüntülenmesini istemediğiniz sütunun veya özelliğin yanındaki açılan oka tıklayın ve ardından **hiçbiri**' ne tıklayın.

3. Öğeyi tasarımcıda <xref:System.Windows.Controls.Grid> gibi geçerli bir kapsayıcıya sürükleyin. Geçerli kapsayıcılar hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kapsayıcıda yeni veri bağlantılı denetimleri oluşturur. Her denetim farklı bir sütuna veya özelliğe bağlanır ve her denetim, uygun bir <xref:System.Windows.Controls.Label> denetimi ile birlikte sunulur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca, denetimleri verilere bağlamak için [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve kod üretir. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="existing"></a>Tasarımcıda varolan denetimlere yönelik binddata
 Veri **kaynakları** penceresine bir veri kaynağı ekledikten sonra, Tasarımcıda varolan bir denetime veri bağlama ekleyebilirsiniz.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Tasarımcıda varolan bir denetime veri bağlamak için

1. **Veri kaynakları** penceresinde aşağıdaki yordamlardan birini kullanın:

    - @No__t_0 veya <xref:System.Windows.Controls.ListView> gibi birden çok veri alanını görüntüleyen varolan bir denetime veri bağlama eklemek için, denetime bağlamak istediğiniz tabloyu veya nesneyi temsil eden öğeyi seçin.

    - @No__t_0 veya <xref:System.Windows.Controls.TextBox> gibi tek bir veri alanını görüntüleyen var olan bir denetime veri bağlama eklemek için, verileri içeren tabloyu veya nesneyi temsil eden öğeyi genişletin ve sonra bağlamak istediğiniz verileri temsil eden öğeyi seçin. denetimle.

2. Seçili öğeyi **veri kaynakları** penceresinden tasarımcıda var olan bir denetimin üzerine sürükleyin. Denetim geçerli bir bırakma hedefi olmalıdır. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], denetimi verilere bağlamak için [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve kod üretir. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Denetim, verilere zaten bağlıysa, denetimin veri bağlaması en son denetim üzerine sürüklenen öğeye sıfırlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [oluşturma WPF uygulamaları](../data-tools/create-lookup-tables-in-wpf-applications.md) WPF uygulamalarında [ilgili verileri](../data-tools/display-related-data-in-wpf-applications.md) [bir VERI kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md) bağlama WPF denetimleri için bir [WCF veri hizmeti](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [izlenecek yol: Bir WPF uygulamasında Ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
