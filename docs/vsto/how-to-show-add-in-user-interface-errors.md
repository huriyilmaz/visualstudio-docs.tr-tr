---
title: 'Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme'
description: Microsoft Office uygulamalarda kullanıcı arabirimi hatalarını program aracılığıyla kullanmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 90bb6c458d53e293cd5128e6b2b461082fd1eeb5bda593fb18a5b74f5d7867e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384138"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme
  varsayılan olarak, bir VSTO eklentisi Microsoft Office kullanıcı arabirimini (uı) işlemeyi denerse ve başarısız olursa, hata iletisi gösterilmez. ancak, kullanıcı arabirimiyle ilgili hatalara yönelik iletileri göstermek için Microsoft Office uygulamaları yapılandırabilirsiniz. Bu iletileri, özel bir şeridin neden görünmediğini veya bir şeridin neden göründüğünü, ancak hiçbir denetimin görünmediğini belirlemede yardımcı olması için kullanabilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>VSTO eklentisi kullanıcı arabirimi hatalarını göstermek için

1. Uygulamayı başlatın.

2. **Dosya** sekmesine tıklayın.

3. **Seçenekler**’e tıklayın.

4. Kategoriler bölmesinde **Gelişmiş**' e tıklayın.

5. ayrıntılar bölmesinde **VSTO eklenti kullanıcı arabirimi hatalarını göster**' i seçin ve ardından **tamam**' a tıklayın.

    > [!NOTE]
    > Outlook için, **VSTO eklenti kullanıcı arabirimi hatalarını göster** onay kutusu, ayrıntılar bölmesinin **geliştirici** bölümünde bulunur. Diğer uygulamalar için, onay kutusu Ayrıntılar bölmesinin **genel** bölümünde bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
