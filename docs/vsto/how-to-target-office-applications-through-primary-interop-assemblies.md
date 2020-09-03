---
title: Birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60e351a15af4994d2bf64a800e3019501cf0571d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545775"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme
  Yeni bir Office projesi oluşturduğunuzda, Visual Studio, projenizi oluşturmak için gereken Microsoft Office birincil birlikte çalışma derlemesine (PIA 'lar) otomatik olarak başvurular ekler. Aşağıdaki senaryolarda diğer PIA 'lara başvuru eklemeniz gerekir:

- Projenizdeki diğer Microsoft Office uygulamalarının özelliklerini kullanmak istiyorsunuz. Örneğin, Microsoft Office Word için bir projede Microsoft Office Excel özelliklerini kullanmak isteyebilirsiniz.

- Visual Studio 'da Microsoft Office erişim gibi adanmış projelere sahip olmayan Microsoft Office uygulamaları otomatik hale getirmek istiyorsunuz.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Birincil birlikte çalışma derlemesine başvuru eklemek için

1. Office projenizi açın ve **Çözüm Gezgini**proje adını seçin.

2. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

3. **Framework** sekmesinde, **bileşen adı** listesinde istediğiniz PIA ' ı seçin. Kullanılabilir Microsoft Office birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

     Proje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonrasını hedefliyorsa, derleme başvurusunun **birlikte çalışma türlerini katıştır** özelliği varsayılan olarak **true** olarak ayarlanır. Bu ayarı kullanarak çözümünüz son kullanıcı bilgisayarlarında PIA gerektirmez. Daha fazla bilgi için bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > Office projelerinde, **com** sekmesi yerine **Başvuru Ekle** iletişim kutusunun **.net** sekmesini kullanarak her zaman Office PIA 'lara başvurular ekleyin. Daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

4. **Tamam**’a tıklayın.

     Derleme adı, **Çözüm Gezgini** **References** klasöründe görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md)
