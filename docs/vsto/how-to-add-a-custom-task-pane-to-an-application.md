---
title: 'Nasıl yapılır: uygulamaya özel görev bölmesi ekleme'
description: Office için Visual Studio Araçları (VSTO) eklentisini kullanarak uygulamalara nasıl özel bir görev bölmesi ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3477930ba181f4a0f33d8711e882cda8ba63af17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026375"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Nasıl yapılır: uygulamaya özel görev bölmesi ekleme
  VSTO eklentisi kullanarak yukarıda listelenen uygulamalara özel bir görev bölmesi ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi ekleme

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Uygulamaya özel görev bölmesi eklemek için

1. yukarıda listelenen uygulamalardan biri için VSTO eklenti projesi açın veya oluşturun. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Project** menüsünde **kullanıcı denetimi ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, Yeni Kullanıcı denetiminin adını **MyUserControl** olarak değiştirin ve ardından **Ekle**' ye tıklayın.

     Kullanıcı denetimi tasarımcıda açılır.

4. **araç kutusundan** bir veya daha fazla Windows Forms denetimini kullanıcı denetimine ekleyin.

5. **ThisAddIn. cs** veya **ThisAddIn. vb** kod dosyasını açın.

6. Aşağıdaki kodu `ThisAddIn` sınıfına ekleyin. Bu kod `MyUserControl` <xref:Microsoft.Office.Tools.CustomTaskPane> , sınıfının üyeleri olarak ve örneklerini bildirir `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet1":::

7. Olay işleyicisine aşağıdaki kodu ekleyin `ThisAddIn_Startup` . Bu kod, <xref:Microsoft.Office.Tools.CustomTaskPane> nesneyi koleksiyona ekleyerek yeni bir oluşturur `MyUserControl` `CustomTaskPanes` . Kod ayrıca görev bölmesini de görüntüler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs" id="Snippet2":::

    > [!NOTE]
    > Bu kod, özel görev bölmenizi uygulamadaki etkin pencere ile ilişkilendirir. Bazı uygulamalarda, görev bölmesinin uygulamadaki diğer belge veya öğelerle göründüğünden emin olmak için bu kodu değiştirmek isteyebilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [İzlenecek yol: bir uygulamayı özel görev bölmesinden otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
