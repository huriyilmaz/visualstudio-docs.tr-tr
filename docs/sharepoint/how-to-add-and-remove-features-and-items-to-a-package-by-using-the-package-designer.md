---
title: 'Paket tasarımcısı: & ve öğeleri kaldırmak için pakete ekleme'
titleSuffix: ''
description: Visual Studio'da Paket Tasarımcısı'SharePoint bir pakete özellik ve öğe ekleme ve kaldırmayı Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026973"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Nasıl kullanılır: Paket Tasarımcısını kullanarak pakete özellik ve öğe ekleme ve kaldırma
  Bir çözüm SharePoint, Visual Studio varsayılan SharePoint Özellikler'i çözümde pakete ekler. Son dağıtımdan önce, proje öğelerini ve SharePoint paketinde değişiklik yapmak için bu öğeleri SharePoint kaldırabilirsiniz.

 Alternatif olarak, Paketleme Gezgini'ni kullanarak proje öğelerine SharePoint kaldırabilirsiniz. Ayrıca, pakete (.wsp) SharePoint proje öğelerinin ve Özelliklerin hiyerarşisini görüntüp değiştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Paketleme Gezgini'ni](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)kullanarak pakete özellik ve öğe ekleme ve kaldırma.

## <a name="add-features-to-a-sharepoint-package"></a>SharePoint paketine özellikler ekleme
 Bir pakete Özellikler eklemek için Paket Tasarımcısı'SharePoint kullanabilirsiniz.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Paket SharePoint özellikleri eklemek için

1. Paket **Tasarımcısı'nda 'i açın.**

    Daha fazla bilgi için [bkz. Nasıl SharePoint paketi özelleştirme.](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)

2. Aşağıdaki adımlardan birini SharePoint veya daha fazlasını gerçekleştirerek Bir veya daha fazla SharePoint Özelliği ekleyin:

   1. Eklemek istediğiniz Çözüm listesinde **Öğeler'de yer alan** her öğeye çift tıklayın.

   2. Eklemek istediğiniz öğeyi seçin ve ardından Ekle  düğmesini (>.

   3. Tüm öğeleri **aynı anda** eklemek için Tüm >> Ekle düğmesini (>>) seçin.

      Örneğin, Çözüm listesinde Öğeler listesinde bir **öğeye** çift tıklar ve bunu Paket listesinde **öğelere ekleyebilirsiniz.**

      SharePoint Project Öğeleri ve Özellikleri, Paket **listesinde Öğeler'de** görünür.

## <a name="remove-features-from-a-sharepoint-package"></a>SharePoint Paketinden Özellikleri Kaldırma
 Özellikleri bir pakete kaldırmak için Paket Tasarımcısı'SharePoint kullanabilirsiniz.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Paket SharePoint özelliklerini kaldırmak için

1. Paket **listesinde Öğeler listesinde,** kaldırmak istediğiniz öğeyi seçin ve ardından Kaldır **(<)** düğmesini seçin veya  tüm öğeleri kaldırmak için Tüm Öğeleri Kaldır düğmesini (<<) seçin.

     SharePoint Öğeleri, Çözüm **listesinde Öğeler'de** görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Çözüm SharePoint paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md)
- [Nasıl SharePoint: SharePoint paketi özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl: Paket Oluşturma](/previous-versions/ee231585(v=vs.110))