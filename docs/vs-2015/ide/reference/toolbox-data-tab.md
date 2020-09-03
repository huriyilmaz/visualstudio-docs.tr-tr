---
title: Araç kutusu, veri sekmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9349745eeee24f2f8b1e62eb2b01bd75273c86d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658593"
---
# <a name="toolbox-data-tab"></a>Araç Kutusu, Veri Sekmesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Formlara ve bileşenlere ekleyebileceğiniz veri nesnelerini görüntüler. **Araç kutusunun** **veri** sekmesi, ilişkili tasarlayıcı içeren bir proje oluşturduğunuzda görüntülenir. **Araç kutusu** , Visual Studio tümleşik geliştirme ortamında varsayılan olarak görünür; **araç kutusunu**görüntülemeniz gerekiyorsa, **Görünüm** menüsünden **araç kutusu** ' nu seçin.

> [!TIP]
> Veri kaynağı Yapılandırma Sihirbazı 'Nı çalıştırmak, çoğu veri öğesini otomatik olarak oluşturur ve yapılandırır. Daha fazla bilgi için bkz. [Visual Studio Ile veri uygulamaları oluşturma](https://msdn.microsoft.com/28edce21-220a-484c-b461-a75b0232d293).

## <a name="ui-element-list"></a>UI Öğe Listesi
 Bir bileşenin .NET Framework başvuru sayfasına doğrudan gitmek için, **araç kutusundaki** öğede veya tasarımcı tepsisindeki bileşen öğesinde **F1** ' e basın.

|Ad|Açıklama|
|----------|-----------------|
|<xref:System.Data.DataSet>|Form veya bileşene türü belirtilmiş veya türsüz veri kümesinin bir örneğini ekler. Bu nesneyi bir tasarımcıya sürüklediğinizde, var olan bir türü belirtilmiş veri kümesi sınıfını seçmenizi sağlayan bir iletişim kutusu görüntüler veya yeni, boş ve türsüz bir veri kümesi oluşturmak istediğinizi belirtebilirsiniz. **Note:**  <xref:System.Data.DataSet> Yeni bir türü belirtilmiş veri kümesi şeması ve sınıfı oluşturmak Için **araç kutusu** üzerinde nesnesini kullanmayın. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar.|
|<xref:System.Windows.Forms.BindingSource>|Temel alınan bir veri kaynağına denetim bağlama sürecini basitleştirir.|
|<xref:System.Windows.Forms.BindingNavigator>|Verilere bağlı bir formdaki denetimler için gezinti ve düzenleme kullanıcı arabirimini (UI) temsil eder.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Veri](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) kılavuzları, Visual Studio 'da verileri veri [bağlama denetimleri](../../data-tools/bind-controls-to-data-in-visual-studio.md) [Validating Data](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [alacak şekilde hazırlama](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [Windows Forms denetimleri Visual Studio 'daki verilere bağlar](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)