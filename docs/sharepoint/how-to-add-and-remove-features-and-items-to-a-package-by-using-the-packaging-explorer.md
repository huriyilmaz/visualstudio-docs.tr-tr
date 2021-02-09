---
title: 'Paketleme Gezgini: pakete öğe & & Ekle veya Kaldır'
titleSuffix: ''
description: Visual Studio 'da paketleme Gezgini 'ni kullanarak bir SharePoint paketine Özellikler ve öğeler ekleyin ve kaldırın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eec1468fc2e0c51d7dea7aa5f3ffa808b484ec87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923575"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma
  SharePoint öğelerini ve özelliklerini dağıtmak üzere bir paket yapılandırmak için paketleme Gezgini ' ni kullanabilirsiniz. SharePoint proje öğelerini ve. wsp dosyanızın içindeki özellikleri ayarlayabilirsiniz.

 Alternatif olarak, etkinleştirme sırasını değiştirmek için özellikleri görüntülemek ve yeniden sıralamak üzere paketleme tasarımcısını kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

## <a name="open-the-packaging-explorer"></a>Paketleme Gezginini açın
 Visual Studio çözümünüz en az bir SharePoint projesi içeriyorsa paketleme Gezgini 'ni açmak için aşağıdaki yordamı kullanabilirsiniz. Alternatif olarak, bir özellik veya paket tasarımcısını görüntülediğinizde paketleme Gezgini otomatik olarak açılır. Tüm özellik ve paket tasarımcılarını kapattıktan sonra paketleme Gezgini de kapanır.

#### <a name="to-open-the-packaging-explorer"></a>Paketleme Gezgini 'ni açmak için

1. Menü çubuğunda,   >  **diğer Windows**  >  **paketleme Gezginini** görüntüle ' yi seçin.

     **Paketleme Gezgini** **araç kutusunda** görünür.

## <a name="adding-a-feature-to-a-package"></a>Bir pakete özellik ekleme
 Paketleme Gezgini 'ni kullanarak bir pakete yeni ve var olan özellikler ekleyebilirsiniz.

#### <a name="to-add-a-sharepoint-feature"></a>Bir SharePoint özelliği eklemek için

1. **Paketleme Gezginini** açın, proje için kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

#### <a name="to-move-an-existing-sharepoint-feature"></a>Var olan bir SharePoint özelliğini taşımak için

1. **Paketleme Gezginini** açın ve aşağıdaki adımlardan birini gerçekleştirin:

    - Bir **özelliği** bir projeden başka bir projeye sürükleyin.

    - Bir özelliğin kısayol menüsünü açın, **Kes**' i seçin, özelliği taşımak istediğiniz projenin kısayol menüsünü açın ve **Yapıştır**' ı seçin.

    > [!NOTE]
    > Çözümünüzde birden fazla SharePoint projeniz varsa, bu yordamı kullanın.

## <a name="validate-a-feature-or-package"></a>Bir özelliği veya paketi doğrulama
 Dosyaları doğrulayarak SharePoint özelliklerinde ve paketlerinde olası sorunları belirleyebilirsiniz. Uyarılar ve hatalar çıkış penceresinde ve Hata Listesi penceresinde görüntülenir.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Bir SharePoint özelliğini veya paketini doğrulamak için

1. **Paketleme Gezginini** açın.

2. Bir özellik veya paket için kısayol menüsünü açın ve ardından **Doğrula**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
