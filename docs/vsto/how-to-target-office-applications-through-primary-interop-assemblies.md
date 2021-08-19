---
title: birincil birlikte çalışma bütünleştirilmiş kodları aracılığıyla Office uygulamaları hedefleme
description: birincil birlikte çalışma derlemeleri aracılığıyla Microsoft Office uygulamaları programlı bir şekilde hedeflemek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5172fb15b1a44961738627929ac5486302cc28d0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099639"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>nasıl yapılır: birincil birlikte çalışma bütünleştirilmiş kodları aracılığıyla Office uygulamalarını hedefleme
  yeni bir Office projesi oluşturduğunuzda, Visual Studio otomatik olarak, projenizi oluşturmak için gereken Microsoft Office birincil birlikte çalışma derlemesine (pıa) başvuruları ekler. Aşağıdaki senaryolarda diğer PIA 'lara başvuru eklemeniz gerekir:

- projenizdeki diğer Microsoft Office uygulamalarının özelliklerini kullanmak istiyorsunuz. örneğin, Microsoft Office Word için bir projede Microsoft Office Excel özelliklerini kullanmak isteyebilirsiniz.

- Microsoft Office erişim gibi Visual Studio özel projelere sahip olmayan Microsoft Office uygulamaları otomatik hale getirmek istiyorsunuz.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Birincil birlikte çalışma derlemesine başvuru eklemek için

1. Office projenizi açın ve **Çözüm Gezgini** proje adını seçin.

2. **Project** menüsünde **başvuru ekle**' ye tıklayın.

3. **Framework** sekmesinde, **bileşen adı** listesinde istediğiniz PIA ' ı seçin. kullanılabilir Microsoft Office birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

     Proje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonrasını hedefliyorsa, derleme başvurusunun **birlikte çalışma türlerini katıştır** özelliği varsayılan olarak **true** olarak ayarlanır. Bu ayarı kullanarak çözümünüz son kullanıcı bilgisayarlarında PIA gerektirmez. daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > Office projelerinde, **COM** sekmesi yerine **başvuru ekle** iletişim kutusunun **.net** sekmesini kullanarak Office pıa 'lara her zaman başvuru ekleyin. daha fazla bilgi için bkz. [Office primary ınterop assemblies](../vsto/office-primary-interop-assemblies.md).

4. **Tamam**'a tıklayın.

     Derleme adı, **Çözüm Gezgini** **References** klasöründe görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [birincil birlikte çalışma derlemelerini Office](../vsto/office-primary-interop-assemblies.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [nasıl yapılır: birincil birlikte çalışma derlemelerini Office yüklemesi](../vsto/how-to-install-office-primary-interop-assemblies.md)
