---
title: Araç Kutusu, Veri Sekmesi
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e79b80890925bdf4d6d191db759516b5545fc403
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590260"
---
# <a name="toolbox-data-tab"></a>Araç Kutusu, Veri sekmesi

Formlara ve bileşenlere ekleyebileceğiniz veri nesnelerini görüntüler. İlişkili bir tasarımcıya sahip bir proje oluşturduğunuzda **Araç Kutusunun** **Veri** sekmesi görüntülenir. **Araç Kutusu** varsayılan olarak Visual Studio tümleşik geliştirme ortamında görünür; **Araç Kutusunu**görüntülemeniz gerekiyorsa, **Görünüm** menüsünden **Araç Kutusu'nu** seçin.

> [!TIP]
> Veri Kaynağı Yapılandırma Sihirbazı'nın çalıştırıldığı iş, çoğu veri öğesini otomatik olarak oluşturur ve yapılandırır. Daha fazla bilgi için [bkz.](../../data-tools/add-new-data-sources.md)

## <a name="ui-element-list"></a>UI Öğesi listesi

Bir bileşen için doğrudan .NET başvuru sayfasına gitmek **için, Araç Kutusu'ndaki** öğeye veya tasarımcının tepsisindeki bileşen öğesine **F1** tuşuna basın.

|Adı|Açıklama|
|----------|-----------------|
|<xref:System.Data.DataSet>|Forma veya bileşene yazılı veya yazılmamış veri kümesi örneği ekler. Bu nesneyi bir tasarımcıya sürüklediğinizde, varolan bir veri kümesi sınıfLarını seçmenize veya yeni, boş, yazılmamış bir veri kümesi oluşturmak istediğinizi belirtmenize olanak tanıyan bir iletişim kutusu görüntüler. **Not:**  Yeni bir daktibl veri kümesi şeması ve sınıfı oluşturmak için Araç <xref:System.Data.DataSet> **Kutusu'ndaki** nesneyi kullanmayın. Daha fazla bilgi için [bkz.](../../data-tools/create-and-configure-datasets-in-visual-studio.md)|
|<xref:System.Windows.Forms.DataGridView>|Verileri tabular biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.|
|<xref:System.Windows.Forms.BindingSource>|Denetimleri temel bir veri kaynağına bağlama işlemini kolaylaştırır.|
|<xref:System.Windows.Forms.BindingNavigator>|Verilere bağlı bir formüzerindeki denetimler için gezinme ve işleme kullanıcı arabirimini (UI) temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Verilere Erişim](../../data-tools/accessing-data-in-visual-studio.md)
- [.NET için Visual Studio veri araçları](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Visual Studio'daki veri kümesi araçları](../../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri kümelerinde verileri edin](../../data-tools/edit-data-in-datasets.md)
- [Veri kümelerinde verileri doğrulama](../../data-tools/validate-data-in-datasets.md)
