---
title: Veri Kümesi Tasarımcısı'de DataTable oluşturma
description: Bu kılavuzda, tabloyu kullanarak bir DataTable (TableAdapter olmadan) Veri Kümesi Tasarımcısı. Yeni bir Windows Forms uygulaması oluşturun ve buna yeni bir veri kümesi ekleyin.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 08c5355ab65947ef41a45f5d7f66f5b5e82a6994e9f0f0190870b28d687ffa7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346576"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Adım adım kılavuz: Veri Tablosu oluşturma Veri Kümesi Tasarımcısı

Bu kılavuzda, Veri Kümesi Tasarımcısı kullanarak <xref:System.Data.DataTable> bir (TableAdapter olmadan) **oluşturma açık Veri Kümesi Tasarımcısı.** TableAdapter'ları içeren veri tabloları oluşturma hakkında bilgi için [bkz. TableAdapters oluşturma ve yapılandırma.](../data-tools/create-and-configure-tableadapters.md)

## <a name="create-a-new-windows-forms-application"></a>Yeni bir Windows Forms uygulaması oluşturma

1. Dosya Visual Studio Menüsünde **Yeni** Dosya'Project.   >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **DataTableWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **DataTableWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya yeni bir Veri Kümesi ekleme

1. Yeni **Project** **Ekle'yi seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Sol bölmede Veri'yi **ve** ardından orta **bölmede DataSet'i** seçin.

3. **Ekle'yi seçin.**

     Visual Studio **DataSet1.xsd** adlı bir dosyayı projeye ekler ve **Veri Kümesi Tasarımcısı.**

## <a name="add-a-new-datatable-to-the-dataset"></a>Veri Kümesine yeni bir DataTable ekleme

1. Bir **DataTable'ı** Araç **Kutusunun DataSet** **sekmesinden** **Veri Kümesi Tasarımcısı.**

     Veri **kümesine DataTable1** adlı bir tablo eklenir.

2. **DataTable1'in başlık çubuğuna tıklayın ve** olarak yeniden adlandırabilirsiniz. `Music`

## <a name="add-columns-to-the-datatable"></a>DataTable'a sütun ekleme

1. Müzik tablosuna **sağ** tıklayın. **Ekle'nin üzerine** gelin ve Ardından Sütun'a **tıklayın.**

2. sütununa adını `SongID` girin.

3. Özellikler **penceresinde** özelliğini olarak <xref:System.Data.DataColumn.DataType%2A> <xref:System.Int16?displayProperty=fullName> ayarlayın.

4. Bu işlemi tekrarlayın ve aşağıdaki sütunları ekleyin:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Tablonun Birincil Anahtarını ayarlama

Tüm veri tablolarında birincil anahtar olması gerekir. Birincil anahtar, veri tablosunda belirli bir kaydı benzersiz olarak tanımlar.

Birincil anahtarı ayarlamak için **SongID** sütununa sağ tıklayın ve ardından Birincil Anahtarı **Ayarla'ya tıklayın.** **SongID** sütununu yanında bir anahtar simgesi görünür.

## <a name="save-your-project"></a>Dosyanızı Project

**DataTableWalkthrough projesini kaydetmek** için Dosya **menüsünden Tüm** Öğeleri **Kaydet'i seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)
