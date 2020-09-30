---
title: 'Paket Tasarımcısı: Ekle & özellikleri ve öğeleri pakete kaldır'
titleSuffix: ''
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86dde3abc86ff42d2e558626abdb5faee7e5c90e
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585608"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma
  Bir SharePoint çözümü oluşturduğunuzda, Visual Studio varsayılan SharePoint özelliklerini çözümdeki pakete ekler. Son dağıtımdan önce SharePoint paketini değiştirmek için SharePoint proje öğeleri ve özellikleri ekleyebilir ve kaldırabilirsiniz.

 Alternatif olarak, SharePoint proje öğelerini eklemek ve kaldırmak için paketleme Gezginini kullanabilirsiniz. Ayrıca, pakete (. wsp) yerleştirilen SharePoint proje öğelerinin ve özelliklerinin hiyerarşisini görüntüleyebilir ve değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>SharePoint paketine özellikler ekleme
 Bir SharePoint paketine özellikler eklemek için paket tasarımcısını kullanabilirsiniz.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Paket Tasarımcısı ile SharePoint özellikleri eklemek için

1. **Paket Tasarımcısını**açın.

    Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Aşağıdaki adımlardan birini veya birkaçını gerçekleştirerek bir veya daha fazla SharePoint özelliği ekleyin:

   1. **Çözüm listesindeki öğelerde** , eklemek istediğiniz her öğeye çift tıklayın.

   2. Eklemek istediğiniz bir öğe seçin ve ardından **Ekle** düğmesini (>) seçin.

   3. Tüm öğeleri tek seferde eklemek için **Tümünü Ekle** düğmesini (>>) seçin.

      Örneğin, bir öğeyi **paket listesindeki öğelere** eklemek için **çözüm listesindeki öğelerde** çift tıklayabilirsiniz.

      SharePoint proje öğeleri ve özellikleri, **paket listesindeki öğelerde** görüntülenir.

## <a name="remove-features-from-a-sharepoint-package"></a>Özellikleri bir SharePoint paketinden kaldır
 Bir SharePoint paketine özellikleri kaldırmak için paket tasarımcısını kullanabilirsiniz.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Paket Tasarımcısı ile SharePoint özelliklerini kaldırmak için

1. Paket listesindeki **öğelerde** , kaldırmak istediğiniz bir öğe seçin ve ardından **Kaldır** (<) düğmesini seçin veya tüm öğeleri kaldırmak için **Tümünü Kaldır** düğmesini (<<) seçin.

     SharePoint öğeleri, **çözüm listesindeki öğelerde** görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: paket oluşturma](/previous-versions/ee231585(v=vs.110))