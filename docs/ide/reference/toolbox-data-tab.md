---
title: Araç Kutusu, Veri Sekmesi
description: Araç kutusu penceresinin veri sekmesinde bulacağınız veri nesneleri hakkında bilgi edinin.
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
ms.openlocfilehash: c51e4ba5e75df5107ed7edd0324e581e0fc7cb6165a35eb0cf5fbb6f87f17bd2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372016"
---
# <a name="toolbox-data-tab"></a>Araç kutusu, veri sekmesi

Formlara ve bileşenlere ekleyebileceğiniz veri nesnelerini görüntüler. **Araç kutusunun** **veri** sekmesi, ilişkili tasarlayıcı içeren bir proje oluşturduğunuzda görüntülenir. **araç kutusu** , Visual Studio tümleşik geliştirme ortamında varsayılan olarak görüntülenir; **araç kutusunu** görüntülemeniz gerekiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

> [!TIP]
> Veri kaynağı Yapılandırma Sihirbazı 'Nı çalıştırmak, çoğu veri öğesini otomatik olarak oluşturur ve yapılandırır. Daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](../../data-tools/add-new-data-sources.md).

## <a name="ui-element-list"></a>UI öğe listesi

Bir bileşen için doğrudan .NET başvuru sayfasına gitmek için, **araç kutusundaki** öğede veya tasarımcı tepsisindeki bileşen öğesinde **F1** ' e basın.

|Ad|Açıklama|
|----------|-----------------|
|<xref:System.Data.DataSet>|Form veya bileşene türü belirtilmiş veya türsüz veri kümesinin bir örneğini ekler. Bu nesneyi bir tasarımcıya sürüklediğinizde, var olan bir türü belirtilmiş veri kümesi sınıfını seçmenizi sağlayan bir iletişim kutusu görüntüler veya yeni, boş ve türsüz bir veri kümesi oluşturmak istediğinizi belirtebilirsiniz. **Note:**  <xref:System.Data.DataSet> Yeni bir türü belirtilmiş veri kümesi şeması ve sınıfı oluşturmak Için **araç kutusu** üzerinde nesnesini kullanmayın. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar.|
|<xref:System.Windows.Forms.BindingSource>|Temel alınan bir veri kaynağına denetim bağlama sürecini basitleştirir.|
|<xref:System.Windows.Forms.BindingNavigator>|Verilere bağlı bir formdaki denetimler için gezinti ve düzenleme kullanıcı arabirimini (UI) temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio verilere erişme](../../data-tools/accessing-data-in-visual-studio.md)
- [.NET için Visual Studio veri araçları](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Visual Studio'daki veri kümesi araçları](../../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri kümelerinde verileri düzenleme](../../data-tools/edit-data-in-datasets.md)
- [Veri kümelerinde verileri doğrulama](../../data-tools/validate-data-in-datasets.md)
