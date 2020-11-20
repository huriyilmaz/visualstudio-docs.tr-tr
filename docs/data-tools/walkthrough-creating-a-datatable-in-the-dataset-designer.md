---
title: Veri Kümesi Tasarımcısı bir DataTable oluşturun
description: Bu izlenecek yolda, Veri Kümesi Tasarımcısı kullanarak bir DataTable (TableAdapter olmadan) oluşturun. Yeni bir Windows Forms uygulaması oluşturun ve buna yeni bir veri kümesi ekleyin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0dad1e6878adc73a08753dca21500499e652602
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998258"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>İzlenecek yol: Veri Kümesi Tasarımcısı bir DataTable oluşturun

Bu izlenecek yol <xref:System.Data.DataTable> , **veri kümesi tasarımcısı** kullanarak (TableAdapter olmadan) oluşturmayı açıklar. TableAdapters içeren veri tabloları oluşturma hakkında daha fazla bilgi için bkz. [Create and configure TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Yeni bir Windows Forms uygulaması oluşturma

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. Sol bölmedeki **Visual C#** veya **Visual Basic** genişletip **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **DataTableWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **DataTableWalkthrough** projesi oluşturulup **Çözüm Gezgini** eklenir.

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya yeni bir veri kümesi ekleme

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Sol bölmedeki **veriler**' i seçin ve ardından orta bölmedeki veri **kümesi** ' ni seçin.

3. **Ekle**' yi seçin.

     Visual Studio **dataSet1. xsd** adlı bir dosyayı projeye ekler ve **veri kümesi Tasarımcısı** açar.

## <a name="add-a-new-datatable-to-the-dataset"></a>Veri kümesine yeni bir DataTable ekleyin

1. **Araç kutusunun** **veri kümesi** sekmesinden bir **DataTable nesnesini** **veri kümesi Tasarımcısı** üzerine sürükleyin.

     **DataTable1** adlı bir tablo, veri kümesine eklenir.

2. **DataTable1** öğesinin başlık çubuğuna tıklayın ve yeniden adlandırın `Music` .

## <a name="add-columns-to-the-datatable"></a>DataTable 'a sütun ekleme

1. **Müzik** tablosuna sağ tıklayın. **Ekle**' nin üzerine gelin ve ardından **sütun**' a tıklayın.

2. Sütunu adlandırın `SongID` .

3. **Özellikler** penceresinde, <xref:System.Data.DataColumn.DataType%2A> özelliğini olarak ayarlayın <xref:System.Int16?displayProperty=fullName> .

4. Bu işlemi yineleyin ve aşağıdaki sütunları ekleyin:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Tablo için birincil anahtarı ayarla

Tüm veri tabloları birincil bir anahtara sahip olmalıdır. Birincil anahtar, bir veri tablosunda belirli bir kaydı benzersiz şekilde tanımlar.

Birincil anahtarı ayarlamak için **SongID** sütununa sağ tıklayın ve ardından **birincil anahtarı ayarla**' ya tıklayın. **SongID** sütununun yanında bir anahtar simgesi görünür.

## <a name="save-your-project"></a>Projenizi kaydedin

**DataTableWalkthrough** projesini kaydetmek Için, **Dosya** menüsünde **Tümünü Kaydet**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Veriler doğrulanıyor](../data-tools/validate-data-in-datasets.md)
