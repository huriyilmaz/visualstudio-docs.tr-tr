---
title: 'Paket Tasarımcısı: Ekle & özellikleri ve öğeleri pakete kaldır'
titleSuffix: ''
description: Visual Studio ' deki paket tasarımcısını kullanarak bir SharePoint paketine özellik ve öğe ekleme ve kaldırma işlemlerinin nasıl yapılacağını inceleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 946b3fca7e99bf2aaf1395d63f13626f5e5e5859
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625136"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma
  bir SharePoint çözümü oluşturduğunuzda Visual Studio, çözümdeki pakete varsayılan SharePoint özelliklerini ekler. son dağıtımdan önce, SharePoint paketini değiştirmek için SharePoint proje öğeleri ve özellikler ekleyebilir ve kaldırabilirsiniz.

 alternatif olarak, SharePoint proje öğeleri eklemek ve kaldırmak için paketleme gezgini 'ni kullanabilirsiniz. ayrıca, pakete (. wsp) yerleştirilen SharePoint proje öğelerinin ve özelliklerinin hiyerarşisini görüntüleyebilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>SharePoint paketine özellikler ekleme
 bir SharePoint paketine özellik eklemek için paket tasarımcısını kullanabilirsiniz.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>paket tasarımcısıyla SharePoint özellik eklemek için

1. **Paket Tasarımcısını** açın.

    daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. aşağıdaki adımlardan birini veya birkaçını gerçekleştirerek bir veya daha fazla SharePoint özelliği ekleyin:

   1. **Çözüm listesindeki öğelerde** , eklemek istediğiniz her öğeye çift tıklayın.

   2. Eklemek istediğiniz bir öğe seçin ve ardından **Ekle** düğmesini (>) seçin.

   3. Tüm öğeleri tek seferde eklemek için **Tümünü Ekle** düğmesini (>>) seçin.

      Örneğin, bir öğeyi **paket listesindeki öğelere** eklemek için **çözüm listesindeki öğelerde** çift tıklayabilirsiniz.

      SharePoint Project öğeler ve özellikler **paket listesindeki öğelerde** görüntülenir.

## <a name="remove-features-from-a-sharepoint-package"></a>SharePoint paketinden özellikleri kaldırma
 bir SharePoint paketine özellikleri kaldırmak için paket tasarımcısını kullanabilirsiniz.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>paket tasarımcısı ile SharePoint özelliklerini kaldırmak için

1. Paket listesindeki **öğelerde** , kaldırmak istediğiniz bir öğe seçin ve ardından **Kaldır** (<) düğmesini seçin veya tüm öğeleri kaldırmak için **Tümünü Kaldır** düğmesini (<<) seçin.

     SharePoint öğeler, **çözüm listesindeki öğelerde** görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [nasıl yapılır: SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: paket oluşturma](/previous-versions/ee231585(v=vs.110))