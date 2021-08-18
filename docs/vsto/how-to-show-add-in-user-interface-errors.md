---
title: 'Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme'
description: Visual Studio uygulamalarında VTSO Eklenti kullanıcı arabirimi hatalarını program aracılığıyla göstermek için Microsoft Office öğrenin.
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
ms.openlocfilehash: ef5a8780e56da76476038605cfad957cfcd8ba0e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099626"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme
  Varsayılan olarak, VSTO kullanıcı arabirimini (UI) Microsoft Office başarısız olursa hiçbir hata iletisi görüntülenmez. Ancak, kullanıcı arabirimiyle Microsoft Office için iletileri görüntülemek üzere uygulama uygulamalarını yapılandırabilirsiniz. Bu iletileri, özel bir şeridin neden görüne olmadığını veya bir şeridin neden görüntülendiğinden ancak denetim görünmeden belirlemenize yardımcı olmak için kullanabilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Ek VSTO arabirimi hatalarını göstermek için

1. Uygulamayı başlatın.

2. Dosya **sekmesine** tıklayın.

3. **Seçenekler**’e tıklayın.

4. Kategoriler bölmesinde Gelişmiş'e **tıklayın.**

5. Ayrıntılar bölmesinde, Eklenti Ekle **kullanıcı VSTO hatalarını göster'i** seçin ve ardından Tamam'a **tıklayın.**

    > [!NOTE]
    > Bu Outlook, **VSTO Eklenti kullanıcı** arabirimi hatalarını göster onay kutusu ayrıntılar bölmesinin **Geliştirici** bölümünde bulunur. Diğer uygulamalar için onay kutusu ayrıntılar **bölmesinin Genel** bölümünde bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
