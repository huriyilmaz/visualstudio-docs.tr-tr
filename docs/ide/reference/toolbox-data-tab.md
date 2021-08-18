---
title: Araç Kutusu, Veri Sekmesi
description: Araç Kutusu penceresinin Veri sekmesinde, veri nesneleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c9016f6cd77f750b2b1a03ef799652f1c3afbb1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117065"
---
# <a name="toolbox-data-tab"></a>Araç Kutusu, Veri sekmesi

Formlara ve bileşenlere ekleyebilirsiniz veri nesnelerini görüntüler. Araç **Kutusunun** Veri **sekmesi, ilişkili** bir tasarımcıya sahip bir proje oluşturmada görüntülenir. Araç **Kutusu,** tümleşik geliştirme Visual Studio varsayılan olarak görünür; Araç Kutusunu görüntülemeye **ihtiyacınız varsa Görünüm** **menüsünden Araç** Kutusu'nı seçin. 

> [!TIP]
> Veri Kaynağı Yapılandırma Sihirbazı'nın çalıştırıldığında çoğu veri öğeleri otomatik olarak oluşturulur ve yapılandırılır. Daha fazla bilgi için [bkz. Yeni veri kaynakları ekleme.](../../data-tools/add-new-data-sources.md)

## <a name="ui-element-list"></a>UI Öğesi listesi

Doğrudan bir bileşenin .NET başvuru sayfasına gitmek için Araç Kutusu'nda veya tasarımcı tepsisinde bileşen öğesinde **F1** tuşuna basın. 

|Ad|Açıklama|
|----------|-----------------|
|<xref:System.Data.DataSet>|Forma veya bileşene, türü yazlanmamış veya yazlanmamış bir veri kümesi örneği ekler. Bu nesneyi bir tasarımcıya sürüklerken, var olan bir türe sahip veri kümesi sınıfını seçmenize veya yeni, boş, yazılamaz bir veri kümesi oluşturmak istediğinize karar veren bir iletişim kutusu görüntülenir. **Not:**  Yeni türe sahip <xref:System.Data.DataSet> bir veri kümesi şeması **ve** sınıfı oluşturmak için Araç Kutusunda nesnesini kullanmazsınız. Daha fazla bilgi için [bkz. Veri kümeleri oluşturma ve yapılandırma.](../../data-tools/create-and-configure-datasets-in-visual-studio.md)|
|<xref:System.Windows.Forms.DataGridView>|Verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.|
|<xref:System.Windows.Forms.BindingSource>|Denetimleri temel alınan bir veri kaynağına bağlama işlemini kolaylaştırır.|
|<xref:System.Windows.Forms.BindingNavigator>|Verilere bağlı bir formda denetimler için gezinti ve düzenleme kullanıcı arabirimini (UI) temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de Verilere Erişme](../../data-tools/accessing-data-in-visual-studio.md)
- [.NET için Visual Studio veri araçları](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Visual Studio'daki veri kümesi araçları](../../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri kümelerini düzenleme](../../data-tools/edit-data-in-datasets.md)
- [Veri kümelerini doğrulama](../../data-tools/validate-data-in-datasets.md)
